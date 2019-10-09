BootStrap: docker
From:ubuntu:16.04





%post


    apt-get -y update
  apt-get install -y libopenblas-dev  libcurl4-openssl-dev libopenmpi-dev openmpi-bin openmpi-common openmpi-doc openssh-client openssh-server libssh-dev wget vim git nano git cmake  gfortran g++ curl wget python autoconf bzip2 libtool libtool-bin

        apt-get -y install bedtools
    apt-get -y  install python3-dev python3-pip

    apt-get -y install fastqc
    apt-get -y install fastx-toolkit
    #apt-get -y install r-base

        #### install samtools and dependencies
        apt-get -y install gcc
        apt-get -y install make
        apt-get -y install libbz2-dev
        apt-get -y install zlib1g-dev
        apt-get -y install libncurses5-dev
        apt-get -y install libncursesw5-dev
        apt-get -y install liblzma-dev


        cd /usr/bin
        wget https://github.com/samtools/htslib/releases/download/1.9/htslib-1.9.tar.bz2
        tar -vxjf htslib-1.9.tar.bz2
        cd htslib-1.9
        make

        cd ..
        wget https://github.com/samtools/samtools/releases/download/1.9/samtools-1.9.tar.bz2
        tar -vxjf samtools-1.9.tar.bz2
        cd samtools-1.9
        make


        cd ..
        wget https://github.com/samtools/bcftools/releases/download/1.9/bcftools-1.9.tar.bz2
        tar -vxjf bcftools-1.9.tar.bz2
        cd bcftools-1.9
        make


        export PATH="$PATH:/usr/bin/bcftools-1.9"
        export PATH="$PATH:/usr/bin/samtools-1.9"
        export PATH="$PATH:/usr/bin/htslib-1.9"



        ###### install using pip
        pip3 install 'cutadapt'

	 apt-get install -y tzdata && \
        apt-get install -y software-properties-common && \
        add-apt-repository -y -u ppa:certbot/certbot && \
        apt-get install -y   r-base-core libxml2-dev



R --slave -e 'source("https://bioconductor.org/biocLite.R")'
R --slave -e 'BiocInstaller::biocLite(c("GenomicRanges"))'
R --slave -e 'BiocInstaller::biocLite(c("biomaRt"))'
R --slave -e 'BiocInstaller::biocLite(c("Biostrings"))'
R --slave -e 'install.packages(c("checkmate", "ggplot2","reshape","dplyr","plyr","tibble"), repos="https://cloud.r-project.org/")'




%environment
export LC_ALL=C
export PATH=$PATH


I couldn't find this version of gmic for the pi5. So I built it. 

```
holly@bc-holly-01 ~> which gmic
                     gmic -version
/usr/local/bin/gmic

  gmic: GREYC's Magic for Image Computing: Command-Line Interface
        Version 3.7.0 (pre-release #26011322)
        (https://gmic.eu)

        Copyright (c) 2008-2026, David Tschumperlé / GREYC / CNRS.
        (https://www.greyc.fr)

```


The source code of G'MIC is shared between several github repositories with public access. The code from these repositories are intended to be work-in-progress though, so we don't recommend using them to access the source code, if you just want to compile the various interfaces of the G'MIC project. Its is recommended to get the source code from the latest .tar.gz archive instead.

Here are the instructions to compile G'MIC on a fresh installation of Debian (or Ubuntu). It should not be much harder for other distros. First you need to install all the required tools and libraries:
$ sudo apt install git build-essential libgimp2.0-dev libcurl4-openssl-dev libfftw3-dev libtiff-dev libjpeg-dev libopenexr-dev libwebp-dev qtbase5-dev qttools5-dev-tools

Then, get the G'MIC source :
$ wget https://gmic.eu/files/source/gmic_3.6.6.tar.gz && tar zxvf gmic_3.6.6.tar.gz && cd gmic-3.6.6/src

You are now ready to compile the G'MIC interfaces:

    gmic (command-line tool),
    gmic_gimp_qt (plug-in for GIMP),
    ZArt and
    libgmic (G'MIC C++ library).


$ make cli # Compile command-line interface

and go out for a long drink (the compilation takes time).

Note that compiling issues (compiler segfault) may happen with older versions of g++ (4.8.1 and 4.8.2). If you encounter this kind of errors, you probably have to disable the support of OpenMP in G'MIC to make it work, by compiling it with:
make OPENMP_CFLAGS="" OPENMP_LIBS=""

---
title: "how to Install Libtool 2.2"
date: 2009-04-01
forum: General Help
---

### Post by Michael_925 on 2009-04-01
hi, guys

I was trying to install libtool downloaded from [http://ftp.gnu.org/pub/gnu/libtool/](http://ftp.gnu.org/pub/gnu/libtool/) when met some problems, and hope some suggestions from you.

the ubuntu is in Virtual Box for an Embedded project.

I try to install the gstreamer-ti in my (vbox-ed) Ubuntu, and the errors in the installation lead me to install libtool:

1. $ pwd
     /ICETEKWork/projects/gst-ti-plugin-full-0.99.00/ti_build
   $ sh autogen.sh              (checking stops the install)
it says:
  check for build tools
  checking for autoconf >= 2.52 ... found 2.61, ok.
  checking for automake >= 1.7 ... found 1.9.6, ok.
  checking for libtoolize >= 1.5.0 ... not found.
  checking for glibtoolize >= 1.5.0 ... not found.


Then,

 
I put the four files
(2.2.tat.gz, 2.2.tar.gz.sig, 2.2.tar.lzma,2.2.tar.lzma.sig )
in the folder:
 /home/Davinci/ICETEK/projects/

1. $ tar zxvf libtool-2.2.tar.gz     (fine)
2. $ cd libtool-2.2  
3. $ ./configure                     (looks fine, some yes&no))
4. $ make                            (looks fine)
5. $ make install                    (error)

it says:
[COLOR="Red"][COLOR="Lime"]
make  install-recursive
make[1]: Entering directory `/home/davinci/ICETEKWork/projects/libtool-2.2'
make[2]: Entering directory `/home/davinci/ICETEKWork/projects/libtool-2.2'
make[3]: Entering directory `/home/davinci/ICETEKWork/projects/libtool-2.2'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c 'libtoolize' '/usr/local/bin/libtoolize'
/usr/bin/install: can't create “/usr/local/bin/libtoolize”: Permission denied
 /usr/bin/install -c 'libtool' '/usr/local/bin/libtool'
/usr/bin/install: can't create “/usr/local/bin/libtool”: Permission denied
make[3]: *** [install-binSCRIPTS] error 1
make[3]: Leaving directory `/home/davinci/ICETEKWork/projects/libtool-2.2'
make[2]: *** [install-am] error 2
make[2]: Leaving directory `/home/davinci/ICETEKWork/projects/libtool-2.2'
make[1]: *** [install-recursive] error 1
make[1]: Leaving directory `/home/davinci/ICETEKWork/projects/libtool-2.2'
make: *** [install] error 2[/COLOR][/COLOR]

---

### Post by lloyd_b on 2009-04-01
Try "sudo make install" - it's trying to install into "/usr/local/bin", but by default that directory requires root permissions to write new files.

Lloyd B.

---


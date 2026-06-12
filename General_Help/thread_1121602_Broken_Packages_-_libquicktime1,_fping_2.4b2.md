---
title: "Broken Packages - libquicktime1, fping_2.4b2"
date: 2009-04-10
forum: General Help
---

### Post by padma on 2009-04-10
got this error when i tried to install vlc today

: unable to stat `./usr/share/locale/ca' (which I was about to install)
E: /var/cache/apt/archives/libquicktime1_2%3a1.0.2+debian-2build2_i386.deb: unable to stat `./usr/share/locale/de' (which I was about to install)
E: /var/cache/apt/archives/fping_2.4b2-to-ipv6-15_i386.deb: unable to stat `./usr/share/man/man8' (which I was about to install)

I tried to fix it with Fix Broken Packages from the menu as described on this page

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

and it returned the same errors over and over again](*,)

I tired by using command line too and got the following error

~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fping libgtk1.2-common libquicktime1
The following NEW packages will be installed:
  fping libgtk1.2-common libquicktime1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 569kB of archives.
After this operation, 2028kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe libgtk1.2-common 1.2.10-18.1build2 [209kB]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe libquicktime1 2:1.0.2+debian-2build2 [331kB]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe fping 2.4b2-to-ipv6-15 [30.0kB]
Fetched 569kB in 0s (632kB/s)
debconf: Perl may be unconfigured (Can't locate Debconf/Log.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
(Reading database ... 120862 files and directories currently installed.)
Unpacking libgtk1.2-common (from .../libgtk1.2-common_1.2.10-18.1build2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtk1.2-common_1.2.10-18.1build2_all.deb (--unpack):
 unable to stat `./usr/share/locale/ca' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libquicktime1 (from .../libquicktime1_2%3a1.0.2+debian-2build2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libquicktime1_2%3a1.0.2+debian-2build2_i386.deb (--unpack):
 unable to stat `./usr/share/locale/de' (which I was about to install): Stale NFS file handle
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking fping (from .../fping_2.4b2-to-ipv6-15_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/fping_2.4b2-to-ipv6-15_i386.deb (--unpack):
 unable to stat `./usr/share/man/man8' (which I was about to install): Input/output error
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk1.2-common_1.2.10-18.1build2_all.deb
 /var/cache/apt/archives/libquicktime1_2%3a1.0.2+debian-2build2_i386.deb
 /var/cache/apt/archives/fping_2.4b2-to-ipv6-15_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Anyone help?

thanks
:)

---


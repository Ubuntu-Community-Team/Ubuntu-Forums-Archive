---
title: "Synaptic Manager and apt-get no longer working Stale NFS Handle"
date: 2009-06-03
forum: General Help
---

### Post by nonamebrand on 2009-06-03
Hi everyone, just to start off, I'll let you know in advance that I'm a newbie to linux.

I'm having a problem with my Synaptic Manager and apt-get. They were working earlier today, but I'm getting errors now. I wanted to install VLC and mplayer and that's when I noticed something was wrong. 

I've googled my error message and tried some of the solutions (without knowing at all what I'm doing) but nothing has worked. 

Here's the output I get when I try to install VLC:

v1c@ubuntu:~$ sudo apt-get install vlc
[sudo] password for v1c: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libass1 libdca0 libdvbpsi4 libebml0 libenca0 libfaad0 libiso9660-5
  liblua5.1-0 libmatroska0 libsdl-image1.2 libtar libvcdinfo0 libvlc2
  libvlccore0 libx264-65 vlc-data vlc-nox
Suggested packages:
  mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  libass1 libdca0 libdvbpsi4 libebml0 libenca0 libfaad0 libiso9660-5
  liblua5.1-0 libmatroska0 libsdl-image1.2 libtar libvcdinfo0 libvlc2
  libvlccore0 libx264-65 vlc vlc-data vlc-nox
0 upgraded, 18 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/12.1MB of archives.
After this operation, 33.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: unable to stat triggers deferred file `/var/lib/dpkg/triggers/Unincorp': Stale NFS file handle
E: Sub-process /usr/bin/dpkg returned an error code (2)

---


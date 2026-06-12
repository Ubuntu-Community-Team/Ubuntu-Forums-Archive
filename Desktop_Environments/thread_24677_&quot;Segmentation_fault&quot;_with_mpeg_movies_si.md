---
title: "&quot;Segmentation fault&quot; with mpeg movies since today"
date: 2005-04-08
forum: Desktop Environments
---

### Post by Sam on 2005-04-08
I have a big problem for viewing movies on Hoary AMD64.

When I try to open an mpeg movie, gxine has a "Segmentation fault" and quits. It also outputs a beepy noise with some avi files (like listening data track with a cd player on a mixed data/audio cd).  But it worked fine until today ! ](*,)

It doesn't occur with asf or mov files.

I don't know what kind of information would be useful. Here are the packages I've installed before the error happens:

```
k3b (0.11.23-0ubuntu3)
k3blibs (0.11.23-0ubuntu3)
kcontrol (4:3.4.0-0ubuntu18)
kdebase-bin (4:3.4.0-0ubuntu18)
kdebase-data (4:3.4.0-0ubuntu18)
kdelibs-bin (4:3.4.0-0ubuntu3)
kdelibs-data (4:3.4.0-0ubuntu3)
kdelibs4 (4:3.4.0-0ubuntu3)
libarts1 (1.4.0-0pre1ubuntu3)
libflac++4 (1.1.1-4)
libnetpbm10 (2:10.0-8)
libopenexr2 (1.2.1-2)
menu-xdg (0.2ubuntu1)
netpbm (2:10.0-8)
cdrdao (1:1.1.9-3ubuntu2)
sox (12.17.5-4)
```

I also did an update:

```
apt (0.6.35) to 0.6.35ubuntu2
apt-utils (0.6.35) to 0.6.35ubuntu2
base-config (2.62ubuntu20) to 2.62ubuntu24
desktop-file-utils (0.10-1ubuntu1) to 0.10-1ubuntu2
dosfstools (2.11-1) to 2.11-2
eject (2.0.13deb-8ubuntu2) to 2.0.13deb-8ubuntu3
evolution (2.2.1.1-0ubuntu3) to 2.2.1.1-0ubuntu4
evolution-exchange (2.2.1-0ubuntu1) to 2.2.1cvs20050405-0ubuntu1
gnome-app-install (0+20050404-1) to 0+20050404a-1
gnome-applets (2.10.1-0ubuntu1) to 2.10.1-0ubuntu2
gnome-applets-data (2.10.1-0ubuntu1) to 2.10.1-0ubuntu2
gnome-system-tools (1.2.0-0ubuntu5) to 1.2.0-0ubuntu6
gnome-utils (2.10.0-0ubuntu1) to 2.10.1-0ubuntu1
gtk2-engines-pixbuf (2.6.4-0ubuntu2) to 2.6.4-0ubuntu3
hwdb-client (0.5-0ubuntu5) to 0.6-0ubuntu2
java-package (0.19) to 0.23
klogd (1.4.1-16ubuntu5) to 1.4.1-16ubuntu6
language-pack-en (20050404) to 20050406
language-pack-en-base (20050310) to 20050406
libdmx1 (6.8.2-9) to 6.8.2-10
libdps1 (6.8.2-9) to 6.8.2-10
libfs6 (6.8.2-9) to 6.8.2-10
libgdk-pixbuf2 (0.22.0-7ubuntu1) to 0.22.0-7ubuntu2
libgnomevfs2-0 (2.10.0-0ubuntu4) to 2.10.0-0ubuntu5
libgnomevfs2-common (2.10.0-0ubuntu4) to 2.10.0-0ubuntu5
libgtk2.0-0 (2.6.4-0ubuntu2) to 2.6.4-0ubuntu3
libgtk2.0-bin (2.6.4-0ubuntu2) to 2.6.4-0ubuntu3
libgtk2.0-common (2.6.4-0ubuntu2) to 2.6.4-0ubuntu3
libgtk2.0-dev (2.6.4-0ubuntu2) to 2.6.4-0ubuntu3
libice-dev (6.8.2-9) to 6.8.2-10
libice6 (6.8.2-9) to 6.8.2-10
libmysqlclient12 (4.0.23-3ubuntu1) to 4.0.23-3ubuntu2
libmysqlclient12-dev (4.0.23-3ubuntu1) to 4.0.23-3ubuntu2
libnspr4 (2:1.7.6-1ubuntu1) to 2:1.7.6-1ubuntu2
libnss3 (2:1.7.6-1ubuntu1) to 2:1.7.6-1ubuntu2
libsm-dev (6.8.2-9) to 6.8.2-10
libsm6 (6.8.2-9) to 6.8.2-10
libx11-6 (6.8.2-9) to 6.8.2-10
libx11-dev (6.8.2-9) to 6.8.2-10
libxau6 (6.8.2-9) to 6.8.2-10
libxaw7 (6.8.2-9) to 6.8.2-10
libxaw8 (6.8.2-9) to 6.8.2-10
libxdamage1 (6.8.2-9) to 6.8.2-10
libxdmcp6 (6.8.2-9) to 6.8.2-10
libxext-dev (6.8.2-9) to 6.8.2-10
libxext6 (6.8.2-9) to 6.8.2-10
libxfixes3 (6.8.2-9) to 6.8.2-10
libxi-dev (6.8.2-9) to 6.8.2-10
libxi6 (6.8.2-9) to 6.8.2-10
libxine1 (1.0-1ubuntu2) to 1.0-1ubuntu3
libxinerama-dev (6.8.2-9) to 6.8.2-10
libxinerama1 (6.8.2-9) to 6.8.2-10
libxkbfile-dev (6.8.2-9) to 6.8.2-10
libxkbfile1 (6.8.2-9) to 6.8.2-10
libxkbui1 (6.8.2-9) to 6.8.2-10
libxmu-dev (6.8.2-9) to 6.8.2-10
libxmu6 (6.8.2-9) to 6.8.2-10
libxmuu1 (6.8.2-9) to 6.8.2-10
libxp6 (6.8.2-9) to 6.8.2-10
libxpm4 (6.8.2-9) to 6.8.2-10
libxrandr-dev (6.8.2-9) to 6.8.2-10
libxrandr2 (6.8.2-9) to 6.8.2-10
libxss1 (6.8.2-9) to 6.8.2-10
libxt-dev (6.8.2-9) to 6.8.2-10
libxt6 (6.8.2-9) to 6.8.2-10
libxtrap6 (6.8.2-9) to 6.8.2-10
libxtst6 (6.8.2-9) to 6.8.2-10
libxv-dev (6.8.2-9) to 6.8.2-10
libxv1 (6.8.2-9) to 6.8.2-10
libxxf86dga1 (6.8.2-9) to 6.8.2-10
libxxf86misc1 (6.8.2-9) to 6.8.2-10
libxxf86vm1 (6.8.2-9) to 6.8.2-10
linux-image-2.6.10-5-amd64-k8 (2.6.10-33) to 2.6.10-34
login (1:4.0.3-30.7ubuntu15) to 1:4.0.3-30.7ubuntu16
mozilla-firefox (1.0.2-0ubuntu4) to 1.0.2-0ubuntu5
mozilla-firefox-gnome-support (1.0.2-0ubuntu4) to 1.0.2-0ubuntu5
mozilla-firefox-locale-en-gb (1.0.1lang20050309ubuntu1-0ubuntu2) to 1.0.1lang20050309ubuntu1-0ubuntu3
mysql-client (4.0.23-3ubuntu1) to 4.0.23-3ubuntu2
mysql-common (4.0.23-3ubuntu1) to 4.0.23-3ubuntu2
mysql-server (4.0.23-3ubuntu1) to 4.0.23-3ubuntu2
openoffice.org (1.1.3-8ubuntu1) to 1.1.3-8ubuntu2
openoffice.org-bin (1.1.3-8ubuntu1-1) to 1.1.3-8ubuntu2-1
openoffice.org-gtk-gnome (1.1.3-8ubuntu1-1) to 1.1.3-8ubuntu2-1
openoffice.org-l10n-en (1.1.3-8ubuntu1) to 1.1.3-8ubuntu2
openoffice.org-thesaurus-en-us (1.1.3-8ubuntu1) to 1.1.3-8ubuntu2
passwd (1:4.0.3-30.7ubuntu15) to 1:4.0.3-30.7ubuntu16
synaptic (0.55+cvs20050404-1) to 0.55+cvs20050406-1
sysklogd (1.4.1-16ubuntu5) to 1.4.1-16ubuntu6
system-tools-backends (1.2.0-0ubuntu5) to 1.2.0-0ubuntu6
ttf-opensymbol (1.1.3-8ubuntu1) to 1.1.3-8ubuntu2
ubuntu-artwork (0.2.23-1) to 0.2.24-1
ubuntu-docs (0.5-1) to 1.0-2
ubuntu-quickguide (0.5-1) to 1.0-2
update-manager (0.37.1+svn20050404) to 0.37.1+svn20050404.1
x-dev (6.8.2-9) to 6.8.2-10
x-window-system-core (6.8.2-9) to 6.8.2-10
xbase-clients (6.8.2-9) to 6.8.2-10
xfonts-100dpi (6.8.2-9) to 6.8.2-10
xfonts-75dpi (6.8.2-9) to 6.8.2-10
xfonts-base (6.8.2-9) to 6.8.2-10
xfonts-scalable (6.8.2-9) to 6.8.2-10
xlibmesa-dri (6.8.2-9) to 6.8.2-10
xlibmesa-gl (6.8.2-9) to 6.8.2-10
xlibmesa-gl-dev (6.8.2-9) to 6.8.2-10
xlibmesa-glu (6.8.2-9) to 6.8.2-10
xlibmesa-glu-dev (6.8.2-9) to 6.8.2-10
xlibs (6.8.2-9) to 6.8.2-10
xlibs-data (6.8.2-9) to 6.8.2-10
xlibs-static-dev (6.8.2-9) to 6.8.2-10
xorg-common (6.8.2-9) to 6.8.2-10
xorg-driver-synaptics (0.13.6-0ubuntu4) to 0.13.6-0ubuntu5
xserver-common (6.8.2-9) to 6.8.2-10
xserver-xorg (6.8.2-9) to 6.8.2-10
xterm (6.8.2-9) to 6.8.2-10
xutils (6.8.2-9) to 6.8.2-10
```

Thank you for your help !!!

---

### Post by Hinko on 2005-04-08
Basically, it worked before right? 

You can try Kaffeine, if you have any missing codecs it'll tell you. but since it worked before that's probably not the case. Anyway, try another media-player and look if it happens there as well. It could be your sound driver, could be some libraries

---

### Post by Sam on 2005-04-08
Ok, with xine I have the same problem: "xiTK received SIGSEGV signal, RIP." (sounds logically if it didn't work with gxine)

So I installed MPlayer, and it worked like a charm....

Ok I can forget xine, but I would try to fix the problem anyway. Has anyone a suggestion ?

---

### Post by Sam on 2005-04-11
[img]http://img229.echo.cx/img229/2899/desert5rn.gif[/img]

---

### Post by nespa on 2005-04-12
Video Lan Client works with mpg.  Could not test xine with .avi, .asf or .mov
hoary upgraded from warty on amd64.

---

### Post by hbos on 2005-04-13
I'm experiencing the same problem with hoary on amd64. I was running hoary for a few months already, but in the last week this issue got in after an update.

I hope they will fix it in the repositories. If not they might as well remove it completely. Its worthless like this.

I tested a few different video files. And somethings it plays the movie but the sounds is messed up (really loud beeps/noise in it). 

futex(0xd40848, FUTEX_WAIT, 0, {9, 999988000}xiTK received SIGSEGV signal, RIP.
) = -1 EINTR (Interrupted system call)
+++ killed by SIGABRT +++

---


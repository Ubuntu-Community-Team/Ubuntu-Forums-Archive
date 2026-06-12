---
title: "SecondLife"
date: 2009-02-13
forum: Gaming &amp; Leisure
---

### Post by S0m3th1ngw13rd on 2009-02-13
Just downloaded Second Life unpacked it, and placed the folder in home. When I try to run it I get 

```
Warning: Did not register secondlife:// handler with KDE: Directory /home/UN/.kde/share/services does not exist.
/home/UN/SecondLife-i686-1.21.6.99587/secondlife: line 110:  6031 Segmentation fault      LD_LIBRARY_PATH="`pwd`"/lib:"`pwd`"/app_settings/mozilla-runtime-linux-i686:"${LD_LIBRARY_PATH}" $LL_WRAPPER bin/do-not-directly-run-secondlife-bin --channel "Second Life Release"
*** Unclean shutdown. ***

You are running the Second Life Viewer on a x86_64 platform.  The
most common problems when launching the Viewer (particularly
'bin/do-not-directly-run-secondlife-bin: not found' and 'error while
loading shared libraries') may be solved by installing your Linux
distribution's 32-bit compatibility packages.
For example, on Ubuntu and other Debian-based Linuxes you might run:
$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl

```

I looked in synaptic and I already have ia32-libs installed. Anyone know what may be the issue. I'm using Ubuntu 8.10 64

---

### Post by Naiki Muliaina on 2009-02-13
Check all your other dependencies or try installing Second Life through a repo, and let synaptic do the work for you. Follow the link for repo guide.
[B][U][URL="http://naiux.wordpress.com/2008/11/30/cracking-news-on-second-life-front/"]
Second Life Repo Info[/URL][/U][/B]

---

### Post by zoe-scutterbug on 2009-02-14
check out

[http://omvviewer.byteme.org.uk/](http://omvviewer.byteme.org.uk/)

for an alternative sl viewer with regular rep updates

i also use other alternatives.... cool viewer and imprudence viewer...cant decide which is my fave.

zoe

---


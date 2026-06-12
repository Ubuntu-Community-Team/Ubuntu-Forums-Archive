---
title: "Fluxbox loading to slow"
date: 2005-04-11
forum: Desktop Environments
---

### Post by 014&lt; on 2005-04-11
Hi

I installed the server version of ubuntu. After that I installed the following packages:

apt-get install xserver-xorg

apt-get install x-window-system-core

apt-get install xdm

apt-get install xterm

apt-get install fluxbox

The problem is when I start up fluxbox with startx. It's is so slow. It takes ages before everyting is ready and when I move the mouse during fluxbox is loading it moves so slow. What can be the problem? I have used fluxbox on slackware before and I never experienced that problem there.

---

### Post by Whiffle on 2005-04-11
run "sudo hdparm -tT /dev/hda" (or whatever drive your root drive is) in a console.  It could be that your harddrives aren't setup right so everything is loading slowly.

---

### Post by 014&lt; on 2005-04-11
I get the following output when doing sudo hdparm -tT /dev/hda:

/dev/hda

 Timing cached reads: 248 MB in 2.03 seconds = 122.13 MB/sec
 Timing buffered disk reads: 50 MB in 3.03 seconds = 16.50 MB/sec

I have a 40 GB disk ATA (66 or 100) 5400 RPM. 

So is the output reasonable?

I installed x-window-system and then the mouse isn't slow any more, but it still takes very long time to load fluxbox.

---

### Post by NeoMayhem on 2005-06-11
[QUOTE=014<]I get the following output when doing sudo hdparm -tT /dev/hda:

/dev/hda

 Timing cached reads: 248 MB in 2.03 seconds = 122.13 MB/sec
 Timing buffered disk reads: 50 MB in 3.03 seconds = 16.50 MB/sec

I have a 40 GB disk ATA (66 or 100) 5400 RPM. 

So is the output reasonable?

I installed x-window-system and then the mouse isn't slow any more, but it still takes very long time to load fluxbox.[/QUOTE]

I have the same problem, fluxbox is taking about 1 minute to load. I know I am using a slow system, but gnome even loads faster.

---

### Post by byen on 2005-06-11
[QUOTE=014<]Hi

I installed the server version of ubuntu. After that I installed the following packages:

apt-get install xserver-xorg

apt-get install x-window-system-core

apt-get install xdm

apt-get install xterm

apt-get install fluxbox
.[/QUOTE]

 WHOA! OK I JUST INSTALLED FLUXBOX USING APT-GET INSTALL FLUXBOX AND IT SEEMED TO INSTALL WELL! IM ALREADY RUNNING GNOME SO I THOUGHT I DID NOT NEED THE OTHERS..... do i need to aptget the rest too?

PS - sorry this isnt a solution to your problem...just suprised to see the commands thats all..... go ubuntu!

---

### Post by kvidell on 2005-06-11
[QUOTE=byen]WHOA! OK I JUST INSTALLED FLUXBOX USING APT-GET INSTALL FLUXBOX AND IT SEEMED TO INSTALL WELL! IM ALREADY RUNNING GNOME SO I THOUGHT I DID NOT NEED THE OTHERS..... do i need to aptget the rest too?

PS - sorry this isnt a solution to your problem...just suprised to see the commands thats all..... go ubuntu![/QUOTE]
 He only installed those because he didn't already have them. You should already have them.
The only other package I would recomend to you all is "fluxconf":> 65/kvidell: apt-cache show fluxconf
Package: fluxconf
Priority: optional
Section: universe/x11
Installed-Size: 188
Maintainer: Emmanuel le Chevoir <mms@debian.org>
Architecture: i386
Version: 0.9.5-1
Depends: libatk1.0-0 (>= 1.6.0), libc6 (>= 2.3.2.ds1-4), libglib2.0-0 (>= 2.4.1), libgtk2.0-0 (>= 2.4.4), libpango1.0-0 (>= 1.5.2)
Recommends: fluxbox
Filename: pool/universe/f/fluxconf/fluxconf_0.9.5-1_i386.deb
Size: 33684
MD5sum: 4f4118274f01229c1514ab07a40fa4b4
Description: FluxBox configuration utility
 FluxConf is a simple GTK 2.0 application allowing fast and easy configuration
 of the Fluxbox window manager and its keyboard shortcuts.  This package also
 includes the fluxkeys, fluxmenu and fluxbare utilities.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
- Kev

---

### Post by Poul on 2005-06-12
it is loading and working way too slow on my machine as well - a lot slower than gnome - any ideas??

---

### Post by NeoMayhem on 2005-06-13
[QUOTE=Poul]it is loading and working way too slow on my machine as well - a lot slower than gnome - any ideas??[/QUOTE]

I switched to openbox which loads instantly.

---

### Post by pestilence4hr on 2005-06-15
[QUOTE=Poul]it is loading and working way too slow on my machine as well - a lot slower than gnome - any ideas??[/QUOTE]

I was having the same problem, and I have found a solution that works for me.  I have posted the fix at [http://ubuntuforums.org/showthread.php?p=214294](http://ubuntuforums.org/showthread.php?p=214294) .  Hopefully it will fix your problem as well.

---


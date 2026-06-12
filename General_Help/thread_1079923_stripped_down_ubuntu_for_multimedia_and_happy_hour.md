---
title: "stripped down ubuntu for multimedia and happy hours downloading"
date: 2009-02-24
forum: General Help
---

### Post by rvbhute on 2009-02-24
I have bought a Dell Inspiron laptop which should be delivered soon. On this machine, there is a Media Centre button which (in brief) boots a pre-selected partition - by default, that's the Dell Media Centre.

As against Ubuntu Studio and Mythbuntu, I want to set up a bare bones Ubuntu in place of this Media Centre - no frills, no bells, no whistles, no fat. Only MPlayer, VLC Player and Deluge torrent client. And of course, all the codecs possible from the Ubuntu as well as Medibuntu repos! Deluge is for my happy hours downloads :p And a network manager since I might switch between wired and wireless networks.

*That's it*.

I plan to setup a system in Virtual box first. Probably setup up a base/command line system and then a low memory system install from the help wiki.

Any suggestions are much appreciated! Specifically with respect to window managers/desktop environments. Fluxbox is whispering naughtily in my ears.

Another doubt I have is the downloads will be on partition shared with my main Ubuntu. Will there be a ownership conflict with regards to the files? They being downloaded on one Ubuntu and used on another?

---

### Post by mb_webguy on 2009-02-24
If you're going for a minimalist yet still usable system, you might want to look into Openbox.  I gave it a try a while back, and now I'm using it more than Gnome.  If you want a panel, try PyPanel.  It's simple and lightweight, yet is attractive and has the basic features you'd expect from a panel (i.e. desktop switcher, taskbar, notification/applet area, and clock).

As far as sharing your media, as long as your minimalist account has read permissions for the files and directories, you shouldn't have any problems.

By the way, I also have an Inspiron, and am very curious to see if you can actually get Linux to work like the Dell Media Center (as far as a quick boot using the Media button).  Right now, I just have the Media button set to open VLC...

---

### Post by rvbhute on 2009-02-25
I will certainly look into Openbox.

I am also planning to use the alternate Ubuntu for downloading files - so the file movement would be in both directions. I will update on this.

---

### Post by rvbhute on 2009-03-01
I received my laptop yesterday - and have installed crunchbang linux on it. Its based on Ubuntu :P I am using the amd64 build, which is in testing. But so far, there are no issues in the test build.

Regarding the alternative for media centre, I came across XBMC Live (also based on Ubuntu). But sadly, it has no means for installing to a hard disk partition. It needs the entire disk. XBMC developers pitch it to be installed on USB flash drives. I am waiting till it becomes capable of being installed on to a partition.

Regarding the manipulation of the Media Direct button, I have come across this link [http://forum.notebookreview.com/showthread.php?t=231747](http://forum.notebookreview.com/showthread.php?t=231747). I am waiting for XBMC Live to try it out :popcorn:

---

### Post by snowpine on 2009-03-01
CrunchBang would be perfect for your needs. It is basically a minimal install of Ubuntu + Openbox + medibuntu codecs + a very thoughtfully-selected suite of applications. There's also a Lite version, which pretty much just has Firefox and VLC (plus you can add your own apps, of course).

---

### Post by rvbhute on 2009-03-01
snowpine, using the 'Lite' version :biggrin: It absolutely rocks.

---


---
title: "Inspiron 15n - No hibernation after Jaunty upgrade - Remove Dell DVD player to fix?"
date: 2009-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sjhook on 2009-06-12
Hi,

I decided to start a new thread for this rather than using the previous 15n discussion since this is fairly specific. I have a 15n and really like it. I upgraded to Jaunty, using the package manager, and after the upgrade both hibernation and standby stopped working -- all that happens is my screen would be locked and require a password to log in again.

I decided to reinstall jaunty and blow off the Dell supplied version. I did this, in part, because I wanted to repartition the disk. After installing jaunty from a usb drive (you have to reconfigure the boot order in the bios) both hibernation and standby worked. I then set up the machine to play movies as well as installed a few other programs.

A day later I read on the 15n post that Dell supplied a disk with Fluento and Power DVD so I decided to install both. After installing them I noticed that hibernate and standby stopped working (no idea why). So I uninstalled the Power DVD and low and behold hibernate and standby started working again.

Can some who has upgraded confirm this result.

Thanks,

S.

---

### Post by themrfreeze on 2009-06-13
Verified!  

I upgraded my new 15 to 9.04 last night using the built-in updater, and both suspend and hibernation stopped working.  I just uninstalled Dell PowerDVD, and both now work.  

On a related note, can anybody suggest a DVD viewing program that features on-screen controls?  Maybe I'm missing something, but Movie Player and VLC's ability to play DVDs seems a bit of a hack.  If I'm ever going to convince the wife to switch from OSX to Ubuntu, she'll need an easier to use DVD player.

---

### Post by sjhook on 2009-06-13
thanks themrfreeze,

I will try and contact Dell and let them know about the problem since I also like the movie player and it would be nice if they fixed it.

I use mplayer and quite like it. The only odd issue is you have to right click on the front panel to get the menu for opening files -- you will see what I mean when you install it.

---

### Post by botulismo on 2009-06-13
Hey guys,

There is an easy fix for this and it uses VLC. I've included a screenshot of the setting you need to enable [here]("http://kimag.es/share/15613563.jpg") here. Just make sure the setting I have underlined obnoxiously in red is checked, and when you use VLC it will look similar to this [screenshot]("http://kimag.es/share/82285203.jpg").

It's my understanding that the VLC package currently included in 9.04 has issues, and I upgraded to the new release candidate by adding [this repository]("https://launchpad.net/~kow/+archive/ppa") - if you haven't added a repository yet, you just need to go System->Administration->Software Sources, then into the Third Party tab, then hit add, then add the line that begins deb (not deb-src)... Then just hit reload, and when you install VLC it will install the latest version.

Also, if you need a guide for how to make your DVDs look prettier, I wrote a [guide]("http://blog.thewombat.org/2008/11/how-to-use-vlc-096-as-upscaling-media.html") months ago for how to enable upscaling. It was written from my Vista computer but all the settings are the same. It's a little down-and-dirty with settings but it should boost the quality of your DVDs significantly (depending on how well the original source video was encoded, of course!)

---


---
title: "dell 8.04 hardy image"
date: 2008-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CptZiggy on 2008-05-12
Hi, is there a dell release of hardy? the links on the dell forum don't work

thanks

---

### Post by LMP900 on 2008-05-12
Hi CptZiggy. Which links are you referring to? As far as I know, Dell has not released a custom image of Ubuntu 8.04. Previous releases have been announced on their [**blog**]("http://direct2dell.com/one2one/archive/category/1021.aspx") and have been posted on their [**Linux wiki**]("http://linux.dell.com/wiki/index.php/Products/Client").

I'm actually waiting for the release of the custom image myself. However, if I get impatient enough I will just install the original 8.04 release on my 1420n and attempt to work around the issues mentioned on the wiki.

---

### Post by agim on 2008-05-12
I have installed Ubuntu on dell's without issue.
Try the livecd. It will tell you much of what you need to know.

---

### Post by CptZiggy on 2008-05-12
hey,
i think the links are just for the regular release actually but they still don't work. 

[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=13676]("http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=13676")

anyway, the regular release seems fine on my inspiron 6400/E1505 but I might try a older dell version and upgrade just incase of future problems, firmware upgrades or just try and work them out myself

---

### Post by fragos on 2008-05-12
Check out [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

---

### Post by LMP900 on 2008-05-12
I decided not to wait until the Dell official image. I downloaded the regular ISO via Bittorrent and installed it today. I'm happy that everything worked out of the box (Inspiron 1420n w/ X3100 graphics).

I assume the issues mentioned in the wiki are affecting only users that upgrade via update manager? I haven't ran into issues yet. Compiz even works right away without the need to edit configuration files. :)

---

### Post by fragos on 2008-05-13
Clean install is almost always the safest route. I have 1420n with Intel video as well. I'll dual boot with the 7.10 that's running well already. I'm inclined to also add the the Dell repository after the install. I've been sucessful with 8.04 on my desktop except I haven't yet had luck getting wine to run. I need to Internet Explorer to debug my web site. IE is very unpredictable even when running standards based markup.

---

### Post by undfined on 2008-05-13
I did a clean install on a brand new 1420n with the nVidia drivers.

I have a just one bug - I can't view some shares on my Windows server over my wireless connection.  I haven't tried a wired one yet..  I have a workaround in place for that: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/217137](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/217137) - although shutdown is slow now.  I'll figure that one out later.  

Compiz is sweet after loading the newer nVidia drivers and wireless worked right away with the fresh install.

I still have my 7.10 image on the HD.  I'll keep testing for a few more weeks before I run through a clean install over the entire hard drive.  I work with Excel files, which aren't always compatible with openoffice.  Luckily I have a Win2K3 server I can access for those occasional times I need it.

I'm really impressed with the media capabilities of Ubuntu (photos and music, mostly) - which was a pleasant surprise.  Gimp looks and works as great as it did in 7.10.  I'm really happy with the new machine and OS.

Having the Dell approved ISO would be the chocolate on top of the cherry, at this point.  At least for me.

edit: still some weirdness in recovering from suspend and hibernate.  Mostly related to the wireless not recovering.  This has been an issue for me for about a year on another (older) Dell laptop so I've kinda lived with it, but it needs to be dealt with.  Shutting down and rebooting are fine for now, as long as the boot times stay short - but long run it's a work-flow problem in the real world.

---

### Post by David Ehrenberg on 2008-11-09
After fighting to create the boot disc from a memory stick (my version of Nero CD burner doesn't recognize .iso files, had to get another burner), I installed Ubuntu 8.04.

Installation was straight forward, but my wireless card (plugged into the card cage) was never found--I checked with <lspci -nn>

So, I tried to use the setup disc that came with the DWL-520 (non plus version), but of course this didn't work, it's MS Windows centric.

So, I tried to download and compile <ndiswrapper>. Didn't work, won't compile.

So, I tried downloaded a driver for DWL-520. <make> claimed it was up-to-date, but I couldn't located the executable.

I think I'll just reinstall a fresh version of XP.

I'm surprise the support for cards in the cage was not included in the release. The operating system didn't locate the card and the initial set of user questions never asked.

Are the releases really this crude, or have I missed something?

DE

---

### Post by fragos on 2008-11-09
Can't imagine why you aren't using the latest Ubuntu 8.10. If you need ndiswraper it's an installable package -- no need to compile. Googling "DWL-520 +Ubuntu 8.10" I found [https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1](https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1) which might be of help. Apparently there are a number of hardware .versions of DWL-520.

---

### Post by aikiwolfie on 2008-11-09
So far as I know Dell work very closly with Canonical and contribute all their fixes and drivers to the main Ubuntu project. So stuff should work with regular Ubuntu 8.04 or 8.10.

---


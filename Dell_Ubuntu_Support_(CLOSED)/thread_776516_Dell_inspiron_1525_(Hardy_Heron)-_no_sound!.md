---
title: "Dell inspiron 1525 (Hardy Heron):- no sound!"
date: 2008-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ahlock on 2008-04-30
Hi, I am quite new to the ubuntu world and I recently purchased a Dell Inspiron 1525 laptop with pre-installed ubuntu 7.10 (gutsy gibbon).  

I decided to do a distribution upgrade to hardy heron and have had problems with the sound. Initially the drivers were not working so I followed the instructions below (follow link):-

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound)

After going through the short tutorial the drivers started to work, (the OS no longer shouted at me when I was using the volume control); however, the sound still does not operate despite the drivers seemingly being operational. 

Has anyone else had the problem and can anyone offer some help please?

---

### Post by JayeD on 2008-05-01
Hi, I know this is a fresh install and you've gone from Gutsy to Hardy via the upgrade. Maybe you could try downloading the Hardy install disc and installing Hardy from scratch rather than upgrading.

Also, are you running 32-bit or 64-bit?

---

### Post by WorldTripping on 2008-05-01
> **JayeD said:**
> Hi, I know this is a fresh install and you've gone from Gutsy to Hardy via the upgrade. Maybe you could try downloading the Hardy install disc and installing Hardy from scratch rather than upgrading.

Also, are you running 32-bit or 64-bit?

I got a Dell Inspiron 1525 with 7.10 pre-installed three weeks ago.

Hardy works fine for me after a clean install from CD.

Hope that helps.

---

### Post by WorldTripping on 2008-05-01
Aparently this works too:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade")

---

### Post by LillaEpsilon on 2008-05-01
I upgraded from Gutsy to Hardy on a Dell XPS 1330 and had a similar problem, but with a very simple solution: the sound was muted and would not be turned back on using the buttons on my computer; I had to un-mute it using the alsamixer as explained in the alsamixer section of the sound troubleshooting guide found here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Even if your problem is different, perhaps you can find some help there!

---

### Post by ceton on 2008-05-10
This is going to sound odd...

The way I got sound to work on my 1525 is to use the remote control to increase the sound.  

After doing that, sound was always available.

---

### Post by dwouters on 2009-03-09
> **WorldTripping said:**
> Aparently this works too:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade")

I followed the above and all went perfectly. It's a beautiful thing.

---

### Post by nofrills on 2009-12-14
This sounds like the fix I need, but the links are broken.
Can anybody repost the content?
Cheers,
Craig.

---

### Post by bentledr on 2009-12-18
The DELL site has changed please use the following link and check out 8.04 known issues.

[http://en.community.dell.com/wikis/linux/consumer-linux.aspx](http://en.community.dell.com/wikis/linux/consumer-linux.aspx)

---

### Post by pacharanero on 2012-12-22
Same problem for me using Dell 1525 and Ubuntu 12.04LTS. Sound was not working from install.

Drivers, Modules, ALSAmixer all tried without success.

Solved eventually using the suggestion on this forum:
[http://ubuntuforums.org/showthread.php?t=1639223](http://ubuntuforums.org/showthread.php?t=1639223)

(System Tools > System Settings > Sound > Hardware tab > Profile - set to "Analogue Stereo Output" or "Analogue Stereo Duplex")

---

### Post by oldos2er on 2012-12-22
Old thread closed.

---


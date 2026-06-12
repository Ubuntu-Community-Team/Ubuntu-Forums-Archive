---
title: "OS update causing bugs"
date: 2008-07-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Green9090 on 2008-07-06
In the previous version of Ubuntu, my computer worked fairly well. Firefox would rarely, if ever, crash. 

Since I've updated, I've noticed a few things I don't like, and no things at all that I like better.
-Firefox will sometimes crash after closing a browser based Java game (Runescape)
-Having anything open in the browser which uses sound (games, youtube, any streaming video...) will block my sound for any other applications like Rhythmbox until I close completely out of Firefox. Similarly, while Rhythmbox is working, no browser-based sound will work.
-Sometimes after closing the same browser based game, Java vm will suddenly shoot up and consume an entire CPU (I have a dual-core) until I kill the process. 
-My link to my home folder on my desktop broke (fixed that, but it was odd)

These are all problems unique to the new upgrade. Does anyone have a way to either fix these issues or a way to downgrade back to the more stable Ubuntu release?

---

### Post by EXCiD3 on 2008-07-06
Check this out for the FLash audio bug. [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) I've had the same problems with it.
The issues (minus the home folder) are all due to java and flash being proprietary problems, the company has to fix it or the ubuntu developers have to create a work around making it harder to fix those problems.

The only way for you to downgrade is to do a fresh install. :( For future reference, dont perform an upgrade always go with a fresh install. Things like this are almost guaranteed to happen on upgrade but should be fine on a fresh install. Just minor issues when upgrading version and their config files. Its a lot more work than you would think to get upgrades to work perfectly.

---

### Post by Green9090 on 2008-07-06
Thanks for the PulseAudio link, looks like just what I'm looking for!

Is there any way to perform a fresh install without wiping my data? If not I might have to wait until I finally go and buy that external hard drive I've been wanting...

---

### Post by EXCiD3 on 2008-07-06
You could install gparted and resize the partition, and move your /home folder over, then reinstall and mount the new partition as /home on the fresh install. Thats probably what you should have done in the first place anyways. :P having a separate /home keeps ALL your settings/configurations so then all you have to do is reinstall the software on a fresh install. :D

---

### Post by Green9090 on 2008-07-06
After having a look at what is involved in making a /home partition, I'm thinking I definitely want to back my data up first. 

Will doing this harm/delete the graphics drivers from Dell? If so, would I be able to get them back?

Also, using Pulseaudio seems to keep it stuck on Rhythmbox no matter what, in that nothing browser based will play even after Rhythmbox is closed and firefox is restarted... Maybe I'm using it wrong? O_o

---

### Post by EXCiD3 on 2008-07-07
Its porbably best if you back up your data first. You can resize your ubuntu partition and then use the mv command to move it over to the new partition. Heres a good tutorial on how to do this safely: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

What do you mean your graphics drivers from Dell? The graphics drivers are from either Nvidia or ATI (etc) and not Dell products. Nothing but the location of your /home folder will be changed and it will immediately be put back into place. Moving /home to a new partition is pretty much trasnparent to the operating system.

I know what you mean about the PulseAudio problem, its been pissing me off a lot! Run this in terminal and that should fix it: ```
sudo apt-get install libflashsupport
``` I havent had a chance to do this myself since im using my parents comp at the moment, lol. Let me know if that works! :)

---

### Post by EXCiD3 on 2008-07-07
Here are a couple of bug reports on the flash issues:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/196470](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/196470)
[https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/192888)

On your java issue you might want to try this: ```
sudo apt-get remove icedtea-gcjwebplugin
```Taken from: [http://www.shanktified.com/archives/solved-java-not-working-in-firefox-with-ubuntu-hardy-804/](http://www.shanktified.com/archives/solved-java-not-working-in-firefox-with-ubuntu-hardy-804/)

---


---
title: "Warty to Hoary?"
date: 2005-04-23
forum: Desktop Environments
---

### Post by ~zoey~ on 2005-04-23
I installed Warty because sound didn't work in Hoary.

I did sudo apt-get update and then sudo apt-get dist-upgrade, so what am I running now Warty or Hoary?  The sound still works and nothing looks different, although apt-get did install more files.

If I am now running Hoary, how do I add the Hoary repositories?

Thanks, zoey    :confused:

---

### Post by nad on 2005-04-23
What's in your /etc/apt/sources.list?

Dan M

---

### Post by heimo on 2005-04-23
You're probably running Warty, if you haven't changed the /etc/apt/sources.list

Is there references to warty or hoary? If you change wartys to hoarys and **then **do what you did with apt-get, you'll be closer to Hoary. But be awere of possible problems when upgrading lots of packages at once.

You may need to run dist-upgrade multiple times, use
 ```
apt-get install -f
``` 
to get missing packages and even
 ```
dpkg-reconfigure -a
``` 
to force some reconfiguring.


EDIT: Warty->Hoary

---

### Post by ~zoey~ on 2005-04-23
All Warty.  No Hoary

zoey

---

### Post by nad on 2005-04-23
No problem. But let us know if you run into any.

Dan M

---

### Post by ~zoey~ on 2005-04-23
It worked, I am now running Hoary.  No sound though, so I don't think that I will stick with it.

I thought that it was worth a try. :???: 

Thanks, zoey   :-?

---

### Post by nad on 2005-04-23
Open a terminal window and make it full width, quarter height or so is alright. Now enter the command ' alsamixer '. This should bring up the basic mixer applet for your soundcard. If you see an "m" in any of the bars, that channel is muted. Using the arrow keys to move left and right (some of your options may still be off screen to the right), the up and down arrow keys to control volumes and the "m" key to toggle the mute setting you can adjust these settings.

Without closing this window, go to another screen and open a sound app to try it out (after unmuting and turning up at least the master and pcm settings in the alsamixer window. Is there any sound?

Dan M

---

### Post by ~zoey~ on 2005-04-24
Nope.  No sound.  I had installed Hoary before and tried 6 ways to Sunday to get the sound going with no luck.  I thought that maybe if I did a dist upgrade from Warty I would be able to keep the sound, which was silly, because I would still end up with the soundless kernel!

I followed a lot of threads in this forum about Hoary sound problems so I know that I am not alone.

I am back to running Warty now and I think that I will stay with it until maybe the next version of ubuntu comes out with sound.

Thanks, zoey  :)

---

### Post by crazybill on 2005-04-24
Make sure you have Hoary installed

I modified the /etc/apt/sources.info with** vi /etc/apt/sources.info** changing "warty" with "hoary" whereever I found it.. and saved the new file.
Then **sudo apt-get update**
Then **sudo apt-get dist-upgrade**
Then **sudo apt-get install ubuntu-base ubuntu-desktop**
I then edited **/etc/mkinitrd/mkinitrd.conf **replacing the line
**#RESUME=**
with
**RESUME=/dev/hda5***** (***note that hda5 was my swap partition, but your swap partition might be different. Check it out with sudo fdisk -l or tail /proc/swap and replace hda5 with the partition that is correct for your machine)
Reboot

I hope that helps you.

---


---
title: "Inspiron1420n - No Sound Returning From Suspend"
date: 2007-08-20
forum: Dell  Ubuntu Support
---

### Post by notwen on 2007-08-20
As stated, I have no sound upon returning from Suspend on my Insipiron 1420n.  Any recommendations?  It looks to be a 50/50 thing, sometimes I can open my laptop and sound works fine, other times it refuses to output any sound.  I do not receive any errors upon resuming from suspend, I'm greeted w/ the password prompt.  =|

---

### Post by notwen on 2007-08-21
*bump* 

Any ideas at all to test sound before and after suspend?  Is there anyway I can verify that all appropriate services for sound output are running after suspend??  If it's just a simple service that can be restarted, then that would suffice.  Anyone at all? =]

---

### Post by kuja on 2007-08-21
Try running this after suspend: 

sudo modprobe -v snd_hda_intel

---

### Post by notwen on 2007-08-21
> **kuja said:**
> Try running this after suspend: 

sudo modprobe -v snd_hda_intel

Thanks, I'll give it a try next time I lose sound after suspend and post the results.  Thanks again.  =]

---

### Post by Einheit on 2007-08-21
When I return from suspend I get an error message that the sound/volume control applet has crashed and it asks me if I want to reload it. Maybe just restarting that would do the trick for you.

---

### Post by notwen on 2007-08-27
> **kuja said:**
> Try running this after suspend: 

sudo modprobe -v snd_hda_intel

Tried it, didn't work.  What processes are associated w/ your actual sound output?  Maybe I can check for those?  And my sound/volume control applet doesn't crash  it is still in my taskbar and responds to volume changes.

---

### Post by kuja on 2007-08-28
The only things I can think of related to sound would be making sure that the module is loaded and that alsa is running (which it should be). My laptop did this to me earlier and my solution was to suspend it and wake it back up and I had sound again. Very weird. (Another irksome thing I've been noticing is that sometimes when I close the lid it won't suspend, how annoying!)

---

### Post by notwen on 2007-08-28
> **kuja said:**
> The only things I can think of related to sound would be making sure that the module is loaded and that alsa is running (which it should be). My laptop did this to me earlier and my solution was to suspend it and wake it back up and I had sound again. Very weird. (Another irksome thing I've been noticing is that sometimes when I close the lid it won't suspend, how annoying!)

Very weird indeed !  I am also having the issue w/ it not suspending on closing he laptop and I tend to get funny look form my gf before bed when I open and close my laptop multiple times before I finally just manually select suspend in Gnome.  To be honest I did not have any issues w/ suspend when I first got it, hibernate has always been fubared for me though.  Post back if you stumble upon something that may be useful and I'll do the same. =]

---

### Post by kthakar on 2007-08-28
I am facing the same problem as Notwen. Sound is gone after resuming from hibernation or suspend. Hibernate and suspend work fine though.

---

### Post by john_hull-DELL on 2007-08-29
This is one of the known issues on the 1420. Workaround can be found here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly)

---

### Post by notwen on 2007-08-29
Thanks for the reply, I'll be sure to keep checking the page. =]

---

### Post by notwen on 2007-08-29
> **salomon_92 said:**
> have you checked the options for your sound card???[IMG]http://s1.metaldamage.gr/c.php?uid=16740[/IMG]

And how might one do this?

---

### Post by notwen on 2007-08-30
> **john_hull-DELL said:**
> This is one of the known issues on the 1420. Workaround can be found here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly)

I had some time and tried your workaround posted on the dell site, I'll post back after a couple of suspends.

---

### Post by inchaos on 2007-09-11
This fix does nothing for me. :(

I also am prompted to reload volume control upon almost every resume from standby.

My soundcard is detected, but no sound from the speakers.

Headphones work. :-\

---

### Post by sciurus on 2007-12-24
[https://bugs.launchpad.net/dell/+bug/122025](https://bugs.launchpad.net/dell/+bug/122025)

The Gutsy fix is to install linux-backports-modules.

---

### Post by aldenhg on 2007-12-24
If you build the drivers yourself this problem doesn't come up. There's a couple of scripts on [this]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html") page that do all the dirty work for you. 
It should be noted that you'll have to run the scripts after every kernel update.

---

### Post by blueberry17 on 2007-12-24
I tried it. It didn't work!

---


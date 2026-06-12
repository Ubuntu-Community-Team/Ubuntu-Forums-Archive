---
title: "Problems Hearing Sound through my Sound Blaster Audigy 2"
date: 2005-07-09
forum: Desktop Environments
---

### Post by Tad030 on 2005-07-09
Hi Everyone, I am new here, and new to linux.  I have read through many of the posts on how to configure Ubuntu to enable sound, but I am still having problems.  I have a Sound Blaster Audigy 2 soundcard.  The volume meter is registering sound when I put a CD into my computer, but I hear nothing.  I have checked the master volume level, etc but I hear nothing.     

Again, I'm sorry to create a new thread over sound issues when there are others, but I'm still searching for answers.  Thanks for any and all help. 


Tad

---

### Post by t2kburl on 2005-07-09
Do you hear anything ever? Like the startup sounds? Or an mp3?

---

### Post by Tad030 on 2005-07-09
no, i hear nothing.  however, the system recognizes that the sound card is there, as it is listed under volume control as a sound device.

---

### Post by t2kburl on 2005-07-09
try the config from this thread:

[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)

except, for step 1 (assuming you are using KDE) the setting is changed in KDE control center under sound system .. hardware tab.  I just set mine to ALSA (Advanced Linux Sound Architechture)

I don't have the same card as you, but maybe you'll get lucky and this will work for you too


oh yeah ... and unlike the gnome config ... I still get my startup sounds ;)

---

### Post by Tad030 on 2005-07-09
[QUOTE=t2kburl]try the config from this thread:

[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)

except, for step 1 (assuming you are using KDE) the setting is changed in KDE control center under sound system .. hardware tab.  I just set mine to ALSA (Advanced Linux Sound Architechture)

I don't have the same card as you, but maybe you'll get lucky and this will work for you too


oh yeah ... and unlike the gnome config ... I still get my startup sounds ;)[/QUOTE]

I'm not sure I need that config thread or not.  what is really confusing me is that when I boot my pc, my speakers 'pop' as if linux recongnizes the soundcard.  also, as i said before, the volume monitor is registering sound, i just cant hear it.

---

### Post by Tad030 on 2005-07-09
well, maybe i lied.  now the sound monitor registers no sound when i put in a cd, i'll try the link you suggested and see what happens.

---

### Post by Tad030 on 2005-07-09
the tutorial didn't work, i've been spending hours on this, i'm about to throw in the towel.  i was hoping ubuntu would be a great windows alternative, but figuring out sound shouldn't be this hard.

---

### Post by Tad030 on 2005-07-09
Alas, I spoke too soon.  WOOHOO!!!  It finally works.  Many hours later, it's now time for a celebratory beer....or two....  :)

Thanks for the help, 


Tad

---

### Post by t2kburl on 2005-07-09
what was it that finally did the job?

---

### Post by Tad030 on 2005-07-09
it seemed to work after i did the tutorial, rebooted my pc, and reset the volume levels to normal.  thanks again for the help. 


Tad

---


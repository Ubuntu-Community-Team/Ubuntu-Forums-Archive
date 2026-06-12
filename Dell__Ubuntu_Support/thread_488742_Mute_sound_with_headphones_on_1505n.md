---
title: "Mute sound with headphones on 1505n"
date: 2007-06-30
forum: Dell  Ubuntu Support
---

### Post by krull_etc on 2007-06-30
I've noticed on my 1505n that the speakers mute if I boot with my headphones plugged in. However, if I insert my headphones after boot up, then I have sound in both the headphones and the laptop speakers.  Is there a way to change this so inserting headphones after boot up mutes the speakers, too?

Haven't changed anything from the defaults: still HDA Intel ALSA mixer.  No option for headphones if you open Volume Control from the icon

---

### Post by kill4killin on 2007-07-06
I will have to do some research into this one, however, I have the E1505 as well and I had the same problem for a while at the beginning...I'm not sure what exactly fixed it though, but I know it doesn't do it anymore.

This probably doesn't have anything to do with fixing it but my install didn't automatically map the media keys in the front of the laptop so you will probably want to make sure that you manually take care of that. Another thing that might have had something to do with it, but should not be your first move to try and fix it, is a program called Automatix2. I think, if I remember back correctly, that the problem went away shortly after installing this and a few of their audio codecs...so I'm not saying you should try that but if all else fails it might help.

---

### Post by krull_etc on 2007-07-06
Mine seemed to magically fix itself.  the day after i posted it acted correctly, and hasn't done that any more.  I didn't intall or update anything.

---

### Post by kill4killin on 2007-07-06
I really wish I knew what was causing this to correct itself...that's basically exactly what happened to mine, but I was installing so many things in that period that I just assumed one of the programs or codecs fixed it or something.

---

### Post by revilodraw on 2007-07-09
I was having the same problem with my Inspiron 6400 but was just putting up with it; sometimes the headphones would plug in and cut out the speakers (like they should) sometimes they wouldnt...and if booted up with the headphones plugged in, damned if i could get the speakers to work after unplugging the headphones... had to reboot to use the speakers...

---

### Post by MattinTucson on 2007-08-15
Back when I used Suse on a desktop there was a little panel applet that let you set different volume levels for headphones, out, input, and other audio devices.  Is there anything like that in Gnome?  

I've been struggling with the headphones issue as well.  I would just prefer to just turn off the internal speakers and turn them on manually when I need them.  Anyone know how to do this?

One other problem I've seen on these forums is the annoyingly loud internal beep when you do something wrong.  I turned it off in the "System->Preferences->Sound" menu.

Thanks

---

### Post by MattinTucson on 2007-08-16
While I turned off the beeping with the system-preferences-sound, I now have the problem of the external buttons not controlling the sound.  When you push them, the screen still pops up the speaker picture with the volume indicator.  However, when you push the buttons nothing happens.  The pop-up picture just shows a muted speaker.  No amount of button pushing or sequencing seems to make a difference.

Also, on the headphone/speaker bug.  I run into problems in hibernate mode.  It is a real bummer because hibernate saves me time getting everything back up and ready.  

I'm almost thinking this might be a hardware bug, and not just a software setting. Do any Dell people have a workaround?

---

### Post by battlesound on 2007-10-15
I have a inspiron E1505 and I'm now getting the same thing happening to me, but only after I downloaded the linux-headers-2.6.20-16-lowlatency from the repositories (because I was constantly reminded to do it when booting up along with a system/warning beep).  I don't think there was anything else I needed to install, but I'm going to check it out more closely.  The front buttons, the headphones silenced the speakers, everything was fine before!

---


---
title: "No sound (again)"
date: 2006-08-01
forum: Desktop Environments
---

### Post by Slourte on 2006-08-01
I'm pretty sure you guys saw this title at least a thousand times. I have searched the entire forums to get an answer but now I really need help.

Two days ago I installed Ubuntu for the first time : everything worked great (even the sound)! Then I messed up some files and I decided to format the partition and to re-install the entire OS. Everything works now, except the sound. I have a Soundblaster Live Value and, strangely enough, I can hear the login sound perfectly. But when I get to the desktop, nothing. My volume control is locked and tells me some crap about devices and gStreamer. My soundcard shows up in the device manager but doesn't in the "Default sound card" in Sound preferences.

So please help another linux newbie...

Thanks

---

### Post by mlind on 2006-08-01
Does **gstreamer-properties** work ? (type it on terminal)

That "some crap about devices and gStreamer" is probably something you should post too.

---

### Post by Slourte on 2006-08-01
Sorry, here is what I get :

> The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

As for gstreamer-properties, I get a bunch of unavailable plugins before I get to the Multimedia Systems Selector windows : 

> gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4l2src'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'polypsrc'


When I test the input and output plugins I get this error :

> Autodetect : Could not establish connection to sound server

The output is set at "Autodetect" and the input at "ALSA".

Thanks

---

### Post by mlind on 2006-08-01
Make sure linux-sound-base, alsa-base and gstreamer0.10-alsa packages are installed

```

sudo aptitude install linux-sound-base alsa-base gstreamer0.10-alsa

```

Then try
```

sudo dpkg-reconfigure linux-sound-base
sudo dpkg-reconfigure alsa-base

```

Those warnings after you've started gstreamer-properties are normal.

---

### Post by Slourte on 2006-08-01
I think it's a step in the right direction : I hear a beep sound when I test the output plugin in the Multimedia Systems Selector. I can't play any audio file though. I get a "failed to open audio output : Alsa 1.2.10 output plugin" error in XMMS. And my volume control still doesn't work.

Thanks for you help again, mlind. Hope you'll be able to fix this with me.

---

### Post by mlind on 2006-08-01
> **Slourte said:**
> I think it's a step in the right direction : I hear a beep sound when I test the output plugin in the Multimedia Systems Selector. I can't play any audio file though. I get a "failed to open audio output : Alsa 1.2.10 output plugin" error in XMMS. And my volume control still doesn't work.

Thanks for you help again, mlind. Hope you'll be able to fix this with me.

Does this work?
```

aplay /usr/share/sounds/phone.wav

```

What kind of audio type are you trying to play? xmms and mp3 you probably need **alsa-xmms** and **xmms-mad** too.
For media players using gstreamer backends, you should install **gstreamer0.10-plugins-ugly**

If you try to start **gnome-volume-control** from terminal, do you get any errors?

---

### Post by Slourte on 2006-08-01
The sound in the terminal works perfectly. The SAME sound in XMMS gives me this error :
> 
Please check that:
Your soundcard is configured properly
You have the correct plugin selected
No other program is blocking the soundcard


I don't think another program is blocking the soundcard.. I may be wrong but I don't see anything right now. gstreamer0.10-plugins-ugly doesn't make any difference.

Oh my god.. I think I just might have found the problem. When I try to open gnome-volume-control as a normal user it doesn't work : "No volume control GStreamer plugins and/or devices found". But when I am as root everything runs perfect. The sound you gave me doesn't play either unless I'm root.

I think I messed up my users again...

---

### Post by mlind on 2006-08-01
> **Slourte said:**
> The sound in the terminal works perfectly. The SAME sound in XMMS gives me this error :


I don't think another program is blocking the soundcard.. I may be wrong but I don't see anything right now. gstreamer0.10-plugins-ugly doesn't make any difference.

Oh my god.. I think I just might have found the problem. When I try to open gnome-volume-control as a normal user it doesn't work : "No volume control GStreamer plugins and/or devices found". But when I am as root everything runs perfect. The sound you gave me doesn't play either unless I'm root.

I think I messed up my users again...

You must add yourself to **audio** group.
Add yourself to these groups
```

adm dialout fax cdrom floppy tape **audio** dip src video plugdev lpadmin scanner admin

```

This command adds *user* to a *group*. Replace user with your username (and group with a group where to add the user)
```

sudo adduser *user* *group*

```

---

### Post by Slourte on 2006-08-01
You're the man, mlind! Thank you so much!

---

### Post by mlind on 2006-08-01
> **Slourte said:**
> You're the man, mlind! Thank you so much!

You're welcome :mrgreen:
Ubuntu installer should have added your useraccount on these groups by default, but I dunno why it didn't.

---


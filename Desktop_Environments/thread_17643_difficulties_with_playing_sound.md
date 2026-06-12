---
title: "difficulties with playing sound"
date: 2005-03-01
forum: Desktop Environments
---

### Post by Steel3 on 2005-03-01
Hey all!

I'm having a slight bit of a problem with my computer playing sound, but I'm not sure what to attribute it to so I apologize if this is the wrong forum.  I'm running a relatively new PC (AMD 32-bit processor, 512 megs of ram) with Ubuntu on it for a few months, and I haven't really encountered any problems so far up until now.  I've recently been using cedega to emulate KotOR II, but other than that I haven't been doing anything out of the ordinary.

Anyway, today I left mplayer (installed using the directions [here](http://www.ubuntuforums.org/showthread.php?t=94)) paused for a bit in the middle of playing a file when I left for about an hour.  Prior to when I left, everything was working perfectly (I was using speakers).  However, after I came back, the sound inexplicably stopped playing back.  I restarted GNOME, then rebooted, and then turned my computer off and back on and it didn't come back.  I tried plugging some headphones into the headphone jack (which used to work), and that doesn't work either.  I'm absolutely confounded as to what's causing this.  Instead of playing back anything, I hear almost indistinguishable "pops" or "fuzz" when the machine reaches the login screen or I launch an application from the menu.

Also, it might be worth noting that I haven't set up software mixing yet.  Any help would be appreciated.  Thanks!

---

### Post by delltony on 2005-03-01
[QUOTE=Nirmal Mankani]Hey all!

I'm having a slight bit of a problem with my computer playing sound, but I'm not sure what to attribute it to so I apologize if this is the wrong forum.  I'm running a relatively new PC (AMD 32-bit processor, 512 megs of ram) with Ubuntu on it for a few months, and I haven't really encountered any problems so far up until now.  I've recently been using cedega to emulate KotOR II, but other than that I haven't been doing anything out of the ordinary.

Anyway, today I left mplayer (installed using the directions [here](http://www.ubuntuforums.org/showthread.php?t=94)) paused for a bit in the middle of playing a file when I left for about an hour.  Prior to when I left, everything was working perfectly (I was using speakers).  However, after I came back, the sound inexplicably stopped playing back.  I restarted GNOME, then rebooted, and then turned my computer off and back on and it didn't come back.  I tried plugging some headphones into the headphone jack (which used to work), and that doesn't work either.  I'm absolutely confounded as to what's causing this.  Instead of playing back anything, I hear almost indistinguishable "pops" or "fuzz" when the machine reaches the login screen or I launch an application from the menu.

Also, it might be worth noting that I haven't set up software mixing yet.  Any help would be appreciated.  Thanks![/QUOTE]
 i would go to gnome's volume control (not the little slider but the main volume control) and look to see if pcm is down or muted, or master or master mono is down or muted. If they are fine then you might want to go the shell and type alsamixer and see if mono master and or master volume is not muted.  I have noticed in my system if you get a sound conflict as in mplayer playing in multi instances it will mute the volume. and if its muted i have also noticed when i restart it keeps the settings that i had previously. So this might be your problem just check to see if they are muted or turned way down hope this helps.

---

### Post by Steel3 on 2005-03-01
[QUOTE=delltony]i would go to gnome's volume control (not the little slider but the main volume control) and look to see if pcm is down or muted, or master or master mono is down or muted. If they are fine then you might want to go the shell and type alsamixer and see if mono master and or master volume is not muted.  I have noticed in my system if you get a sound conflict as in mplayer playing in multi instances it will mute the volume. and if its muted i have also noticed when i restart it keeps the settings that i had previously. So this might be your problem just check to see if they are muted or turned way down hope this helps.[/QUOTE]

Sweet, thanks.  How do I access the main volume control?

EDIT:  Nevermind, I got it figured out.  Thanks.

---


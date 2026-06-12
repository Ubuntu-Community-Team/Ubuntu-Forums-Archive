---
title: "Volume control on logitech itouch keyboard"
date: 2006-01-05
forum: Desktop Environments
---

### Post by daedalusman on 2006-01-05
The problem is that by default in KDE the volume wheel (or whatever the thing is called) is set up to increase and decrease by 10% at a time. I really want to know how I could set this up to something else, say just 2% at a time. This is pretty annoying as a 10% change can make a lot of difference and it would be nice to have more control over my volume. Thanks for any help. Oh and by the way I'm using KDE 3.5.0.

---

### Post by DoorGunner on 2006-01-05
[http://symlink.dk/linux/config/logitech/](http://symlink.dk/linux/config/logitech/)

i took a quick look and i think this may have the info you are looking for. I have a logitech elite keyboard and used similar instructions. :)

---

### Post by daedalusman on 2006-01-05
[QUOTE=DoorGunner][http://symlink.dk/linux/config/logitech/](http://symlink.dk/linux/config/logitech/)

i took a quick look and i think this may have the info you are looking for. I have a logitech elite keyboard and used similar instructions. :)[/QUOT}

Thanks for the link, provided me with a lot of useful information but it doesn't tell me how to get the volume increment changed. Though my other keys work, I set up amarok with them. Now I just need to get the volume increment set up how I want it and things would be just about perfect.

---

### Post by f1dave on 2006-01-05
xbindkeys may be worth a look... i use it for my logitech

---

### Post by DoorGunner on 2006-01-05
that xkeybinds sounds interesting.....im going to give it a try. was the setup difficult

---

### Post by daedalusman on 2006-01-06
Well I haven't had time to check it out much yet but my back, forward mouse buttons work and I was wondering how I could get xbindkeys to start when KDE starts. This is really simple in Gnome but I can't figure it out for KDE. Thanks.

---

### Post by Hornet on 2006-01-06
[QUOTE=SYMLINK.DK]
run_command_8	XF86AudioRaiseVolume	aumix-minimal -w +5	Raise volume
run_command_9	XF86AudioLowerVolume	aumix-minimal -w -5	Lower volume
run_command_10	XF86AudioMute	aumix-minimal -w 0	Mute
[/QUOTE]


Cant you just change aumix-minimal -w +5, to aumix-minimal -w +2. And the same thing for the other?. You may also consider doing an attenuation instead of just mute.

---

### Post by daedalusman on 2006-01-06
[QUOTE=Hornet]Cant you just change aumix-minimal -w +5, to aumix-minimal -w +2. And the same thing for the other?. You may also consider doing an attenuation instead of just mute.[/QUOTE]


How do I go about doing this?

---

### Post by f1dave on 2006-01-06
[QUOTE=daedalusman]Well I haven't had time to check it out much yet but my back, forward mouse buttons work and I was wondering how I could get xbindkeys to start when KDE starts. This is really simple in Gnome but I can't figure it out for KDE. Thanks.[/QUOTE]

ln -s /usr/bin/xbindkeys ~/.kde/Autostart/

That should do you

---

### Post by daedalusman on 2006-01-07
[QUOTE=f1dave]ln -s /usr/bin/xbindkeys ~/.kde/Autostart/

That should do you[/QUOTE]


Thanks man, worked great.
> 
Cant you just change aumix-minimal -w +5, to aumix-minimal -w +2. And the same thing for the other?. You may also consider doing an attenuation instead of just mute.

The problem with that is that it's for the sawfish window manager, I'm using KDE 3.5, so its different, unless its just a config file that I don't know about. Man this is buggin' the crap out of me :mad: .

---


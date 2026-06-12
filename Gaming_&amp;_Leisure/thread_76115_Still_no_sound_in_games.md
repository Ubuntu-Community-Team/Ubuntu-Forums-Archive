---
title: "Still no sound in games?"
date: 2005-10-14
forum: Gaming &amp; Leisure
---

### Post by TheIdiotThatIsMe on 2005-10-14
I thought this was supposed to be addressed with Breezy? Oh well. The only game that the sound got fixed in was SimCity 3000 Unlimited, but Enemy Territory and Railroad Tycoon II both still dont have sound. 

When I run enemy territory I get this under sound initiation:

```
/dev/dsp: Device or resource busy
Could not open /dev/dsp
```

---

### Post by seethru on 2005-10-14
does killall esd fix it?

---

### Post by thorhr on 2005-10-19
I ran killall esd, then the sound worked with games and not with anything else, unless I reboot then sound works with everything else but not with games. Does anyone know how to fix this? :confused:

---

### Post by thorhr on 2005-10-19
i found out how to fix this first i had to run gstreamer-properties and change the default sink output to alsa and the default source to alsa and then i ran killall esd and the sound works with every thing.

---

### Post by seethru on 2005-10-19
good to know

---

### Post by Ibuntu_52 on 2005-10-20
[QUOTE=thorhr]i found out how to fix this first i had to run gstreamer-properties and change the default sink output to alsa and the default source to alsa and then i ran killall esd and the sound works with every thing.[/QUOTE]

I tried this but I still have the same issue with et.

---

### Post by Hairy_Palms on 2005-10-20
man Esd pisses me off, i was really hoping theyd take it out of breezy and use Alsa

---

### Post by phanboy_iv on 2005-10-20
I also had a problem with sound with some apps and not others.
I just turned of Sound Events in Preferences, and left everything else on default settings. It worked for me, don't ask me why.

---

### Post by Kirzzy_Boy on 2005-10-20
I had a problem with americas army and simply changed the multimedia system selector settings to ALSA and everything works fine.

---

### Post by Tsume on 2005-10-21
[QUOTE=thorhr]i found out how to fix this first i had to run gstreamer-properties and change the default sink output to alsa and the default source to alsa and then i ran killall esd and the sound works with every thing.[/QUOTE]

I had the same problem, and your solution fixed it for me, in games anyway.  Now I have no sound in the OS.  If I reboot, I have sound in the OS, but sound in games won't work unless I do killall esd, which makes it so I have no sound in the OS.

Don't know if it makes any difference, but maybe it will help them fix this in the future...

I'm on a Dell Latitude C400 laptop, and my sound controller is an Intel 82801CA-ICH3 according to Ubuntu, or in Windows "Intel AC97 Audio" and after installing the drivers, "Crystal CS4205".

---

### Post by TheIdiotThatIsMe on 2005-10-21
When I do a killall esd I get a "no processeses killed"

---

### Post by Linux Crunchie on 2005-11-24
Thanks, that worked for me too, although I don't know why, either.

---

### Post by FierceDeity on 2005-12-18
[QUOTE=TheIdiotThatIsMe]When I do a killall esd I get a "no processeses killed"[/QUOTE]

that means that you have nothing using esd; the problem isnt that processes are using your sound card

---

### Post by newuser111 on 2005-12-19
i managed to get sound working in enemy territory only after i installed the package **libsdl1.2debian-all** with synaptic, it uninstalls the libsdl1.2debian-oss package, but now sound works in ET and all other applications and games

---


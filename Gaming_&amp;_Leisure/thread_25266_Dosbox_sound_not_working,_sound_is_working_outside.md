---
title: "Dosbox sound not working, sound is working outside of dosbox though"
date: 2005-04-09
forum: Gaming &amp; Leisure
---

### Post by graigsmith on 2005-04-09
im having a problem with dosbox, it wont do any sound.  but im playing my music files right now.  so im not sure why its not working.

anyone know why its not working?

---

### Post by edubarr on 2005-04-09
[QUOTE=graigsmith]im having a problem with dosbox, it wont do any sound.  but im playing my music files right now.  so im not sure why its not working.

anyone know why its not working?[/QUOTE]
 I had the same problem. From what I understand Ubuntu uses esd for sound and this ends up locking ALSA out. What I do to get sound working for dosbox is kill the esd daemon (killall esd). This way ALSA has access to the hardware. Afterwards just type 'sudo /etc/init.d/alsa stop' and 'esd &' and '/etc/init.d/alsa start' to get esd working again.

I hope this helps.

---

### Post by graigsmith on 2005-04-09
[QUOTE=edubarr]I had the same problem. From what I understand Ubuntu uses esd for sound and this ends up locking ALSA out. What I do to get sound working for dosbox is kill the esd daemon (killall esd). This way ALSA has access to the hardware. Afterwards just type 'sudo /etc/init.d/alsa stop' and 'esd &' and '/etc/init.d/alsa start' to get esd working again.

I hope this helps.[/QUOTE]
 why can't dosbox access the esd thing instead of directly accessing the device?

---

### Post by edubarr on 2005-04-09
I really don't know why dosbox only wants ALSA, the only thing I know is that's how it works for me. Perhaps there's a way to make it work with esd, but I really didn't look a lot into this issue... Maybe there's something on their forums or mailing list. If you want to look for more info try their website:

[http://dosbox.sourceforge.net](http://dosbox.sourceforge.net)

Hope you get it working.  :-)

---

### Post by graigsmith on 2005-04-10
i havent had any luck, dosbox does not give sound.. also found out that Audacity doesn't have sound.  Plus audacity looks like crap.

---

### Post by graigsmith on 2005-04-10
why does ubuntu come with 3!!! different sound systems that interfere with eachother??

how can i make my ubuntu use either alsa oss or esd,   i just want to use one, i just want it to work.

---

### Post by zaro on 2005-08-05
By default only OSS version of the SDL Library (which dosbox uses) is installed .

$ sudo apt-get install libsdl1.2debian-all

installs the full version with esd support.

---

### Post by graigsmith on 2005-08-06
i fixed this, i removed the usb soundcard, and stuck in my old soundblaster live.  the sb live has hardware mixing and doesn't have to use esd.

---

### Post by GolerGkA on 2006-11-25
Id hasn't worked for me! I've got AC97 inboard codec, esd killed, ALSA running, but no dosbox sound! :(

---


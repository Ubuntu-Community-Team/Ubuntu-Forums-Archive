---
title: "No sound after hibernation"
date: 2005-10-08
forum: Desktop Environments
---

### Post by redbull on 2005-10-08
I have suspend to RAM working, (which is awesome) but whenever I come back from this state, there is no sound. Not from the desktop or from audio files. They still play, but with no sound. My volume is set properly. Anyone have a fix?

---

### Post by redbull on 2005-10-11
Anyone?

---

### Post by salvodam on 2005-11-17
I have the same problem after a suspend-to-disk. Everything is working but I do not hear any sound.
My notebook is a Toshiba Satellite 1900. The onboard sound card chipset is a Intel AC97

---

### Post by bissej on 2006-01-10
hi. i also have the same problem and i have been looking for a solution. i have a desktop. under both hoary & breezy, the sound worked fine but then stops working after resume from a suspend (but then works again after rebooting.)
thanks.

---

### Post by Tripmonkey_uk on 2006-01-20
Same here :( 
Using a Sony VAIO VGN-FS215E laptop
Kinda strange.. I tried to play an .mpg file through Mplayer that's setup to use **ESD**, when that had no sound, I then tried it in Totem that I _think_ uses **Alsa**, & when that didn't work I tried it in VLC which was set to use **OSS**.
That worked & the sound was fine in all of the other programs after that as well???
Just run any audio file in a player that uses **OSS** for a second or two first. 
Worked for me :D

---

### Post by Omnios on 2006-01-20
It might be that when you go into hibrination that the PCM or master slider in volum controll is getting set to mute of slid all the way down. You might want to look there to see if that is the culperate.

---

### Post by Greg T. on 2006-01-21
I had the same problem in Dapper. Solved it today.

[http://www.ubuntuforums.org/showthread.php?p=672169](http://www.ubuntuforums.org/showthread.php?p=672169)

---


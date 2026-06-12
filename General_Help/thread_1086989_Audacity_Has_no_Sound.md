---
title: "Audacity Has no Sound"
date: 2009-03-04
forum: General Help
---

### Post by Hellstudios on 2009-03-04
I open up an mp3 file and i click play and....no sound...


im running the latest version of ubuntu, my computer is a compaq presario

3..20 gHz processor
512 mb ram
and i am not sure about the sound card... D: 



if no one can figure this out can you point me in the general direction of a new sound editor?

---

### Post by emarkay on 2009-03-04
Does any other app have sound?  (seriously, is the volume turned up? - that bit me once!)

---

### Post by Meow27 on 2009-03-04
follow the above post and open up the volume control. set the 'front' volume to the max

---

### Post by Hellstudios on 2009-03-04
everything is up.....

---

### Post by Hellstudios on 2009-03-05
D:

---

### Post by Meow27 on 2009-03-05
screenshot it please. it took me a year and a half to figure it out
( the volume control manager)

---

### Post by Hellstudios on 2009-03-05
[IMG]http://i207.photobucket.com/albums/bb134/hellstudios/Screenshot-2.png[/IMG]

---

### Post by Hellstudios on 2009-03-05
OH THAT.


[IMG]http://i207.photobucket.com/albums/bb134/hellstudios/Screenshot-3.png[/IMG]

---

### Post by Nano_ext3 on 2009-03-05
What is the output of "lspci | grep audio"? Please post that here. Also you may want to go to your settings and to the "Sound" manager in Ubuntu. The ALSA driver is known to work on many occasions where the real driver fails to work. This happened to me on my desktop, which is understandable as it is choc full of custom hardware. Change each entry on the main page of the sound editor to ALSA. You can test the output by hitting the test button. Change your driver if ALSA does not work, one of the drivers in each drop down should work, but you want to keep the same driver for all if you can.

Also you will want to follow my thread on getting the EQ to work right, as Audacity and linux in general is terrible with audio.  It would be to your benefit to view my other guide as well:

[http://ubuntuforums.org/showthread.php?t=1085894&highlight=fix+audacious+nano](http://ubuntuforums.org/showthread.php?t=1085894&highlight=fix+audacious+nano)

Even though the above guide is for audacious (which is just like Winamp for windows and I suggest and prefer to use that app, check it out if you can), You should still give it a look.


Hope this helps.

Cheers

--Nano

---


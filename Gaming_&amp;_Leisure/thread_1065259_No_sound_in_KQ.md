---
title: "No sound in KQ"
date: 2009-02-09
forum: Gaming &amp; Leisure
---

### Post by Entity` on 2009-02-09
I was wondering why there is no sound in KQ.  In 7.04 I had sound, but now it seems that I can't get it to work anymore.  I tried to enable the sound, but the game won't let me.  I don't know what's wrong.  My sound card is an old Creative Labs ct4830 and it works fine for everything else, but not KQ.  Help is appreciated.

---

### Post by noobmike on 2009-02-10
I too have no sound. i had sound in 8.04 and just switched to 8.10. Now i have no sound. In 8.04, i couldn't get "Desktop effects" to work; in 8.10 it does, but where the sound in KQ worked in 8.04, it does not work on 8.10.

I guess maybe i have to choose?

Please help

---

### Post by octesian on 2009-02-27
I don't have sound either, not sure why though.

---

### Post by BoyOfDestiny on 2009-02-28
It may be pulse audio. I've personally removed it from my install.

Before running kq, in a terminal (or just press alt + f2)

killall pulseaudio

That will close the instances (it will be back next time you login). 
If that solves the issue, and doesn't cause you any others, then I'd advise either removing pulse or making sure it doesn't load via sessions.

---

### Post by GarmaZed on 2010-05-12
Hey, I'm bumping this thread since I'm currently having this problem.  No sound in the game KQ, sound works everywhere else just fine so it just may be a problem with the game.

I've tried the "killall pulseaudio" command before running it and still no change in KQ, or elsewhere for that matter.  In the game, with the config menu, it does say System Sound -- Off, and it's not allowing me to change it to On, which really makes me think it's a problem with the game.

Anyways, I'm bumpin' and subscribing to see if there is any change.

---

### Post by Daosi on 2010-06-08
system/preferences/Sound

switch all to alsa advanced linux sound architecture

 sound can now be switched on in the game menu

at least this worked for me;-)

---

### Post by Above on 2010-09-10
I tried all the steps listed here and nothing worked until I found a site that stated that pulseaudio needs to be removed for ALSA to work properly with KQ. Follow the steps listed [here]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4") to remove it and once you're done open up KQ and you will now be able to change the sound system to on.
Hope this works for you!

---


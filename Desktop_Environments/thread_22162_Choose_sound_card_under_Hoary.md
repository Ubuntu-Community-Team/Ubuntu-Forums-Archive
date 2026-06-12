---
title: "Choose sound card under Hoary?"
date: 2005-03-26
forum: Desktop Environments
---

### Post by cwaldbieser on 2005-03-26
My machine is a Dell with an OEMed Sound Blaster card that I was unable to get to work under Linux, so I bought another sound card (a Sound Blaster) and managed to get that working way back under Mandrake 9.1.

When I switched to Warty, I had no problems, as the sound card was recognized right away.  I just upgraded to Hoary, and now I am noticing that I don't hear normal system sounds or any output from XMMS.  I do get intermittent sound from some .avi movie clips I have.

I pulled up alsamixergui because I thought maybe something was just muted, but it was showing the sound card as "Dell Sound Blaster Live!", which makes me think that maybe Hoary is just trying to use the wrong card?  Is there some way I can configure which card should be used and which should be disabled?  Any help would be appreciated!

---

### Post by ntd on 2005-03-26
Try opening up the Volume Control program in gnome and going to File -> Change Device and picking the right thing...I had the same problem and this is what I did :)

you can also do an alsamixer -c (then 0 or 1) to change the mixer levels

---

### Post by cwaldbieser on 2005-03-26
Thanks!  I kept looking trying to figure out if various mixer programs or device managers would let me choose a default, but it was right there in volume, all the time.   :-)

---


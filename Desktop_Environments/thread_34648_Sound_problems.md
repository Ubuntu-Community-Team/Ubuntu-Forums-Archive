---
title: "Sound problems"
date: 2005-05-15
forum: Desktop Environments
---

### Post by TheIncredibleEdible on 2005-05-15
Sorry if this has already been covered, I searched and couldn't find anything that seemed to work for me.  I am new to Ubuntu and can't get my sound to work.  The motherboard I am using(Chaintech 7NJL6) comes with sound build in...it says AC'97 codec.  There is no sound at all.  I've tried un-muting everything with alsamixergui, but that is about it.

Any ideas?

---

### Post by abhaysahai on 2005-05-15
Hi,
Try /etc/inetd/alsa start. 
Else try rebooting. 
This happens with me, Even workin sound goes mute on my Thinkpad. When I close the Screen, the laptop goes in power saver mode and I have to reenter my boot up password to continue. But the sound never returns. The only way is to reboot.
I have tried many things but nothing seems to work. At present I am checking on various thinkpad utilitis to make it work.

Abhay

---

### Post by gratefulfrog on 2005-05-16
This is the eternal saga of sound on linux. Many many people have posted many solutions to their individual problems; The truth is that it's very complex...

Check out this link which solved my problems: [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly) 

If that doesn't work, then try playing with the options of 'aslamixer', read the man page first if you don't want to go crazy...

Good luck!

---

### Post by TheIncredibleEdible on 2005-05-17
Thanks!!!  i followed the instructions on the link and then played with alsamixer again and i now have sound.

---


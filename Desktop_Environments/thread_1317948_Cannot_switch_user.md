---
title: "Cannot switch user"
date: 2009-11-07
forum: Desktop Environments
---

### Post by jemdos on 2009-11-07
Greetings from Sunny Spain

Since I upgraded to Karmic Koala, I cannot switch users under X. I cannot login new graphical session, using gnome applets or shortcut keys (Control+Shift+F9...).

I can start non X new sessions (Control+Shift+F1) but I cannot startx from them.

I think there's some X kind Xorg or graphical driver issue here. I am using nVidia propietary drivers ('cause work much better in my BenQ 241W Z) monitor. Video Card is a 6600GT.

---

### Post by cmcanulty on 2009-11-07
Install Ubuntu Tweak from site below and then under system-security uncheck disable fast user switching
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

### Post by jemdos on 2009-11-08
Thanks for your reply. And an awesome solution.:lolflag:

I installed ubuntu-tweak (great software, I did not know about it) but fast user switching was enabled (or the disable control was unchecked).

But boldly I went, so I checked it and unchecked it again et voilà! NOW IT WORKS!

It looks like in Ubuntu 9.04 the user switching was done in a different way (now it looks like it is compulsory to write down the password every time, a thing it looks ok to me) and something went wrong while upgrading.

Thank you very much.

Now, if just someone could help me with pulseaudio and 5.1 surround working, 9.10 would be as pretty as 9.04 ):P

---

### Post by cmcanulty on 2009-11-08
Well last night my audio stopped working all of the sudden and so I went to prefs-sound- and changed the output to no amplifier and then it worked,the weird thing is I had never touched that setting but I played around a bit and now it works

---

### Post by JimiGoth on 2009-11-11
> **cmcanulty said:**
> Install Ubuntu Tweak from site below and then under system-security uncheck disable fast user switching
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

I tried this, but when I clicked on "Security" it came up with an error.

---

### Post by cmcanulty on 2009-11-12
try reinstalling tweak

---

### Post by ramrealtors on 2009-11-12
Es cierto a mi tambien me pasaba lo mismo, queria cambiar de usuario y siempre me aparecia un error, pero gracias al Concejo de jemdoslo solucione.

---

### Post by rvm1989 on 2009-11-25
Hi, i am running ubuntu amd64 and i cannot switch users either...
when i click wich user i bring me the the box of lock screen. if i click switch user there, it brings me the same thing again...

thx

---


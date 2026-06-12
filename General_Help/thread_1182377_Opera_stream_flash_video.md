---
title: "Opera stream flash video"
date: 2009-06-08
forum: General Help
---

### Post by pitroadrush on 2009-06-08
Hello everyone, I have Ubuntu 64 bit 9.04
I can't see no stream video online through Opera(youtube, hulu etc).
I had this issue with both browers Firefox and Opera.
Solve it throght Terminal, update package but still do not work in Opera.
Should I forget about Opera when it comes to stream videos?
many thanks.

---

### Post by QIII on 2009-06-08
What type of video card?

---

### Post by pitroadrush on 2009-06-09
> **QIII said:**
> What type of video card?
 Radeon HD 2600xt
Hope this help....

---

### Post by MDxm on 2009-06-09
> **pitroadrush said:**
> Radeon HD 2600xt
Hope this help....

Do you first of all have the needed codecs in either Totem, VLC or any other Video applet?
If Compiz is on, try turning all desktop effects off.
(Change Wallpaper/Desktop Background>Visual Effects)
Installing the 64 bit beta Flash always helped me. But i've had bad experiences using that together with Opera. Or if it was just Normal for that 64 bit Opera distro..sucked alot of CPU even though I had loads of ram to go around. :p
Here it is if you wanna give it a go, note you perhaps need to UNinstall all other packages for Flash then, and it probably runs ALSA audio and not Pulseaudio.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

Extract it, cd into the directory, sudo cp it over to wanted directory, and flash works. You can Test it by moving the libflashplayer.so for mozilla into /home/username/.mozilla/plugins before making anything permanent.
Opera by standard looks for libflashplayer.so in /usr/lib/opera/plugins/ or in /usr/lib/mozilla/plugins/

---


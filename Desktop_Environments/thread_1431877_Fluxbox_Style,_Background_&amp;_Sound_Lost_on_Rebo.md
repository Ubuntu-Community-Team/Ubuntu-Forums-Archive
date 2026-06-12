---
title: "Fluxbox Style, Background &amp; Sound Lost on Reboot"
date: 2010-03-17
forum: Desktop Environments
---

### Post by Rodney9 on 2010-03-17
Hello, Every time I reboot Ubuntu 9.10 64 bit Fluxbox looses the background, the style and the sound is muted.

I have added ```
fbsetbg -f ~/Pictures/109772-Metal_fb.png &
``` to startup

I have followed Ubuntu's wiki on sound and added myself to audio and also re-installed alsa,
> fgrep -ie 'audio' /etc/group shows me as ```
audio:x:29:pulse,rodney
```

I don't know how to add a style to Fluxbox .config I just add it from the menu, how do I keep the background, style and sound ?

Any Ideas ?

---

### Post by Rodney9 on 2010-03-17
Well I started the  computer this morning I had the right background but still the wrong 'Style' and the sound is still muted.

Any help would be appreciated

---

### Post by Rodney9 on 2010-03-18
Well I am slowly getting there by myself, well sort of, I added gnome-volume-control to startup, it is still muted but easier to un-mute now.
If only I could get the style to stick, I added it to the .fluxbox init file thus - ```
session.styleFile  /home/rodney/fluxbox/styles/GSM
``` 

but when I restart, it kind of loads, but with the wrong tool bar and menu colour.

---

### Post by Rodney9 on 2010-03-20
Well I re-instaled Ubuntu now the background and styles work perfectly, but I still have to un-mute the sound, hopefully this is fixed in Lucid.

---


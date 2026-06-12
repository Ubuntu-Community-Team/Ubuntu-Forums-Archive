---
title: "Gdesklets on Gnome - scaling probs"
date: 2006-01-01
forum: Desktop Environments
---

### Post by Gsundbrunn on 2006-01-01
Hi Ubuntuforum :-)

Happy new year!

I installed a blank new perfetctly working Ubuntu 5.10 on my brandnew AMD Dualcore machine - now eveything runs really fine and I tried to install the gdesklets. Works fine so far - the problem I have is that - independend on which desklet I install - the - lets say "process bar" isn't shown correctly. Diskusage, memoryusage and so on shows not a status but always a full completely full or empty statusbar. If I use different hard disk desklets they all dont show any process in their process bar. With 15% of used space I assume about 15% of the status bar should be filled - but nothing happens :-) Completely blank or completely full (one desklet shows a process bar "more than full") Thats wy I guess it could be a problem. Is it known?

I installed the desklets and -data from synapsis (latest version).

Update:

I created a screenshot with various desklets to show exactly what I mean.

[http://www.cairo-productions.com/temp/screenshot.png](http://www.cairo-productions.com/temp/screenshot.png)

Any hint for me?

Thanks in advance!

Stefan

---

### Post by Ampersand on 2006-01-01
Have you tried changing the colours of the desklets (right click on them, then go to configure)? Some of them seem to set the same colour for the background and the graphs/text by default.

---

### Post by Gsundbrunn on 2006-01-01
Hi,

yes, I tried everything possible. I additionally checked the desklet code to find any possibility to change the scale values but it seems that they use some kind of framework classes.

Check this screenshot, please:

[http://www.cairo-productions.com/temp/screenshot.png](http://www.cairo-productions.com/temp/screenshot.png)

Its a screenresolution of 1280*1024 - best view with the same resolution, I guess.

Best regards

Stefan

---

### Post by Gsundbrunn on 2006-01-02
What I found inbetween is this posting on [www.gdesklet.org:](www.gdesklet.org:)

###
GTK 2.8 changed its clipping behavior on which gDesklets relied. We are looking for a temporary workaround at the moment, but haven't found anything yet.

Version 0.40 will use a completely different rendering engine to avoid such problems. But that still takes some time.
###

Somebody mentioned there is a workaround - does anybody know, which one? 

Thanks in advance

Stefan

---


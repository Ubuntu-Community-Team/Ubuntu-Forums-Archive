---
title: "Really Slick Screesavers gone?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by kaaredyret on 2005-10-13
Where is Really Slick Screesavers? Installed, but not listed in the list of savers at all? I noticed this with the preview of Badger as well.

I had it working in Hoary, out of the box, but they are gone now. I can't find Skyrocket, my favorite! :( 

I reinstalled Really Slick Screesavers from Synaptic PM, with no success...

---

### Post by trey on 2005-10-13
[QUOTE=kaaredyret]Where is Really Slick Screesavers? Installed, but not listed in the list of savers at all? I noticed this with the preview of Badger as well.

I had it working in Hoary, out of the box, but they are gone now. I can't find Skyrocket, my favorite! :( 

I reinstalled Really Slick Screesavers from Synaptic PM, with no success...[/QUOTE]

killall xscreensaver
rss-glx_install.pl
xscreensaver -nosplash &

skyrocket is awesome! never saw these before!!

---

### Post by mojo on 2005-10-13
:mad: I got the same problem. Seems to me, the rss installed by default does not invoke the 'rss-glx_install.pl'. It may be a nasty bug. I just wait for more people to reply, if more people got the same prob, then it's a bug.

---

### Post by bryan986 on 2005-10-13
Thanks for the tip, fixed the problem for me

---

### Post by BLTicklemonster on 2005-10-13
Bummer: 

```
root@ubuntumonster:/home/bill# killall xscreensaver
root@ubuntumonster:/home/bill# rss=glx_install.pl
root@ubuntumonster:/home/bill# xscreensaver -nospash &
[1] 14351
root@ubuntumonster:/home/bill# Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver: Can't open display: :0.0
xscreensaver: initial effective uid/gid was root/root (0/0)
xscreensaver: running as nobody/nogroup (65534/65534)

xscreensaver: This is probably because you're logging in as root.  You
              shouldn't log in as root: you should log in as a normal user,
              and then `su' as needed.  If you insist on logging in as
              root, you will have to turn off X's security features before
              xscreensaver will work.

              Please read the manual and FAQ for more information:

              http://www.jwz.org/xscreensaver/faq.html
              http://www.jwz.org/xscreensaver/man.html




```

I can't find terminal. Had to manually put root terminal in the apps myself.



*edit:

Okay first off, it's spelled splash, not spash. got it.

Second, I think I'm getting the hang of some of this. I used application menu editor to to in system tools, looked at root terminal, and decided to remove gksudo from the command, and attempt creating a terminal button. It worked. muahahaha. 

Watching what looks like them install now.


Nope. and I stupided out and closed the window.

---

### Post by kaaredyret on 2005-10-13
Thanks, now I see my beloved rockets again, when too lazy to work on me thesis :???: 

But problem will be back after next reboot? I have had the problem on every breezy I installed. I think it is a bug, can someone please inform the developers etc?

---

### Post by trey on 2005-10-14
[QUOTE=kaaredyret]Thanks, now I see my beloved rockets again, when too lazy to work on me thesis :???: 

But problem will be back after next reboot? I have had the problem on every breezy I installed. I think it is a bug, can someone please inform the developers etc?[/QUOTE]


no, running rss-glx_install.pl will make it permanent, each time you reboot xscreensaver will still have the rss screensavers.

---

### Post by kudu on 2005-10-18
Yes! Just what I was looking for, thank you. Now I have Skyrocket back. But there's no sound anymore like there was in Hoary. How do I fix that ?

---

### Post by moglenstar on 2005-10-18
[QUOTE=BLTicklemonster]Bummer: 

```
root@ubuntumonster:/home/bill# killall xscreensaver
root@ubuntumonster:/home/bill# rss=glx_install.pl
root@ubuntumonster:/home/bill# xscreensaver -nospash &
[1] 14351
root@ubuntumonster:/home/bill# Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver: Can't open display: :0.0
xscreensaver: initial effective uid/gid was root/root (0/0)
xscreensaver: running as nobody/nogroup (65534/65534)

xscreensaver: This is probably because you're logging in as root.  You
              shouldn't log in as root: you should log in as a normal user,
              and then `su' as needed.  If you insist on logging in as
              root, you will have to turn off X's security features before
              xscreensaver will work.

              Please read the manual and FAQ for more information:

              http://www.jwz.org/xscreensaver/faq.html
              http://www.jwz.org/xscreensaver/man.html




```

I can't find terminal. Had to manually put root terminal in the apps myself.



*edit:

Okay first off, it's spelled splash, not spash. got it.

Second, I think I'm getting the hang of some of this. I used application menu editor to to in system tools, looked at root terminal, and decided to remove gksudo from the command, and attempt creating a terminal button. It worked. muahahaha. 

Watching what looks like them install now.


Nope. and I stupided out and closed the window.[/QUOTE]


one thing i notice straight off is you typo'd..

you typed

"rss=glx_install.pl"

you meant to type

"rss-glx_install.pl" 

that might help ;)

---

### Post by skoal on 2005-10-18
BLTicklemonster, don't ever run 'xscreensaver' as root...

If you wan't to talk about "muahahaha", I'm sure there's quite a few devious lot out there also reading your post and saying, "muahahahahahahaha...."

\\//_

---


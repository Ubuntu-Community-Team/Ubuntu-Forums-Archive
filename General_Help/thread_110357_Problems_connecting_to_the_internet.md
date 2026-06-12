---
title: "Problems connecting to the internet"
date: 2005-12-30
forum: General Help
---

### Post by msg on 2005-12-30
I just installed Ubuntu 5.10 breezy on a fairly new box. The computer is connected to my switch via a regular 50ft network cable. It was able to connect to the internet when I installed the updates, however, when using firefox, it does not load and winds up timing out. Someone on IRC suggested I ping a website from the terminal, and I did that, and it seemed to work... Before this installation I had installed edubuntu 5.10 (trial before I installed it in a relatives classroom), and had the same problem. Anyone know what the problem is/how I can fix it?

---

### Post by Odinist on 2005-12-30
Does Firefox do this on every website you try?

---

### Post by msg on 2005-12-30
Yes, except ubuntu.com and getfirefox.com, those are both in the bookmarks.

---

### Post by Odinist on 2005-12-30
Hrm...

Open a terminal, type ping [www.google.com](www.google.com) (or some other website, whatever) and let it run for a few lines. (Hit CTRL-C to stop it)

Post the output.

---

### Post by msg on 2005-12-30
i cant copypaste since its a different computer but it was 0% packet loss, 34.5 ms average, and the ttl was 240 and it was 64 bytes each ping

---

### Post by Odinist on 2005-12-30
Hrm... Have you tried opening pages with a different browser, like Epiphany, or Opera?

---

### Post by msg on 2005-12-30
No. ill try it now

and thanks for the speedy replies :KS

---

### Post by Odinist on 2005-12-30
Hahaha, no problem... I'm completely bored out of my mind at work, I'm hypercaffeinated, and I have nothing better to do other than whore around on MySpace and hang out on this forum. =)

---

### Post by msg on 2005-12-31
Hrm... I cant get opera to load, i have no idea how to install applications :razz: 

however, I just booted from a mepis liveCD and I had the same problem. Maybe its just slow and able to download small files (64 bytes when I pinged google) but unable to load huge websites. I opened the case to find its an onboard ethernet device, so I'll get an ethernet card and try that.

---

### Post by Odinist on 2005-12-31
If it is just a problem of it being really slow, try this.

Open a new window in Firefox, and go to about:config

This will bring up a configuration page. Where you can filter what's shown, type in ipv6

On the line that comes up about disabling IPv6, set it to true.

Close and restart Firefox.

This will make it go faster.

---

### Post by msg on 2006-01-03
woot, it works now. thanks a million!

---

### Post by Odinist on 2006-01-03
Hey, no problem!! ^_^

---

### Post by handy on 2006-01-03
***[EDIT]  Ooops, I replyed to the first page at the ipv6 stuff, oh well ;-)***

If you still have a problem with your internet connection?

Have a look here: 

[http://ubuntuforums.org/showthread.php?t=88639&page=2](http://ubuntuforums.org/showthread.php?t=88639&page=2)

Both sections under **_Internet Stuff:_**  were necessary for my connection to work, & to work fast.

All the best,

handy

---


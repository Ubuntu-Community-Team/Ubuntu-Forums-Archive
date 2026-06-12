---
title: "A couple of questions:"
date: 2005-12-08
forum: Desktop Environments
---

### Post by Flyn on 2005-12-08
Heya everyone,
I'm a new user to Ubuntu, I've been using it for the last two weeks, and using Windows XP less and less, but although I've read a fairly large amount of HOWTO's and whatnot, there are a couple of problems I can't seem to solve.

Just a couple of brief specs for my system:
Pentum IV 3.2 HT
Asus P4C800-E
512 MB DDR 400
ATI X800 XT PE
Creative Audigy 2
Onboard Intel Gigabit NIC
Logitech MX1000
Microsoft Multimedia keyboard

_**Problem Numero Uno**_

Whenever I try to do anything network related, that is, load a webpage, check for email, use gaim - you get the picture - programs seem to be taking an awful lot of time to look up IP addresses, despite the fact that I have configured the DNS addresses both in Ubuntu and my router, which other Windows based computers are using without any problems. I've been using Ethereal to try to see if ARP packets are being constantly resent, but so far everything looks ok.

**_Problem Number II_**

Two words. Sane. Avision 620C. Wait, thats three words...
Anyway, I've read a couple of HOWTO's , as previously mentioned, and so far, nada. I've set up the parallel ports with MAKEDEV, commented the appropriate modules in sane.d/ , yet nothing works.

**_Problem Number III_**

I'm the proud owner of a Logitech MX1000, and so far, despite reading some lengthy guides, I still only have the back and forward buttons working, xbindkeys doesn't seem to work properly, and using a modmap does no good either.

**_Problem Number IV_**
If anyone could point me towards a brief and more importantly working guide to how to get 4.0 sound with ALSA, that'd be excellent.

**_Problem Number V_**

As I said, I have a Microsoft Multimedia keyboard, but apart from a couple of keys that do work, most of the "extra" multimedia keys don't. Suggestions?



Phew! 
Thats it. If anyone could help with any of the above problems, I'd be forever grateful. Well, maybe for like 5 minutes, but thats something too. ;-)

Thanks in advance,
Adam Delman

---

### Post by stevea1210 on 2005-12-08
for problem one, you probably need to disable IPv6.  Check out this thread
[http://ubuntuforums.org/showthread.php?t=87798&highlight=disable+ipv6]("http://ubuntuforums.org/showthread.php?t=87798&highlight=disable+ipv6")
for more info.  

For the rest, I can't be of much help. Sorry.

---

### Post by canadianwriterman on 2005-12-08
> Problem Number V

As I said, I have a Microsoft Multimedia keyboard, but apart from a couple of keys that do work, most of the "extra" multimedia keys don't. Suggestions?

Try going into **System > Preferences > Keyboard Shortcuts **where you can program a wide variety of multimedia keys. It's not 100%, but I got many of my keys to work

---

### Post by Flyn on 2005-12-08
Thanks a bunch guys, I had already checked out the keyboard short cut bindings but that didn't help me, I want 100% of the keys to be usable, on the other hand, some sites load faster with the IPv6 disabled, I'll have to play around with it some more. If anyone has any other ideas what could cause DNS look ups to be slow or any of the other problems, that would be great.

Thanks a lot! :p

---

### Post by angkor on 2005-12-08
For the multimedia keys you could try:

```
apt-cache search keys | grep multimedia
hotkeys - A hotkeys daemon for your Internet/multimedia keyboard in X
```


I have no experience with so I do not know if it does what you want.

Also read this thread if you havent already:

[http://www.ubuntuforums.org/showthread.php?t=27039&highlight=multimedia+keys](http://www.ubuntuforums.org/showthread.php?t=27039&highlight=multimedia+keys)

---

### Post by Flyn on 2005-12-08
I'll give it a try as soon as I can.
Thanks a bunch!

---

### Post by Flyn on 2005-12-08
Ok, after more research, I found out that the primary DNS address my ISP is giving people isn't working. I fricking *triple* checked it with them and they insist its correct. I removed the primary DNS and sticked with the secondary one and lo and behold! everything is flying again.
Thanks again for your help concerning that one.

Ubuntu rocks!

---


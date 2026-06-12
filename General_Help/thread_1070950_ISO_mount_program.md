---
title: "ISO mount program"
date: 2009-02-15
forum: General Help
---

### Post by jfinner1 on 2009-02-15
I'm looking for a program that I used to have on Windows. The problem is, I'm not sure what it was called, or how to find the equivalent for Ubuntu. So I'm hoping that if I explain what it did, someone will be able to point me in the right direction.

So, the program I had let me take ISO files, for games that needed CDs, and play them through the program, instead of having to burn them to CD. For example, I downloaded ZooTycoon from BitTorrent, and instead of burning the ISO, I ran it through this program to install and play it. The program I had let me run multiple "CDs" at a time, without actually having the CD, but I'd be happy to just run one at a time. I hope this makes sense...

So if anyone knows what I'm talking about, I'd be very appreciative. Thanks in advance.

---

### Post by johnjohn2 on 2009-02-15
[http://www.getdeb.net/search.php?keywords=acetone](http://www.getdeb.net/search.php?keywords=acetone)

is what i believe youare looking for

Regards John

---

### Post by geirha on 2009-02-15
You can mount an iso manually from the terminal:
```
sudo mount -o loop file.iso /media/cdrom
```

You can mount as many as you like, just use different mount points for each one.

---

### Post by Dr Small on 2009-02-15
> **geirha said:**
> You can mount an iso manually from the terminal:
```
sudo mount -o loop file.iso /media/cdrom
```

You can mount as many as you like, just use different mount points for each one.
+1
That's what I was just going to recommend.

---

### Post by jfinner1 on 2009-02-15
Thanks guys. I'll try both and see what works! :-)

---

### Post by mc4man on 2009-02-15
You may be thinking of Daemon tools, which 'emulates' a cd drive.(visible in 'my computer' with a drive letter
There is something similar in linux (the name escapes me atm), but I don't believe it will do what you wish.

---

### Post by jfinner1 on 2009-02-15
That's the program I used! I remember the name now that you said it. I haven been able to try the other suggestions yet, still waiting for the ISO to download, but if they don't work I might try to install Daemon through Wine. Thanks everyone!!

---

### Post by ronelc on 2009-02-15
Thanks guys! I also needed this one. I was also looking for the same software similar to poweriso which i used in windows. It's good to know that i don't need any software to mount multiple iso.

---


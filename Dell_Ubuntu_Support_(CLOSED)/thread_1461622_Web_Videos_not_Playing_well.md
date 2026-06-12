---
title: "Web Videos not Playing well"
date: 2010-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spinlock99 on 2010-04-24
Hi everyone,

I've got a Dell Inspiron 600m and I'm running Firefox. Over the past couple of days (maybe a week) I've noticed that I can't watch videos on YouTube and other sites. Firefox also seems to be hogging all of my memory sometimes and causing my system to thrash. And, I can't even type into this text box and have Firefox keep up with my key-strokes (some keep getting dropped).

Does anybody have any ideas for how to diagnose and solve this issue? BTW I'm running a straight 9.10 installation.

Thanks,
Andy

---

### Post by wojox on 2010-04-24
Try looking at this How To [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by 2hot6ft2 on 2010-04-24
You may find this useful as well
[Make Linux faster, lighter and more powerful]("http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=379")
**But heed the warning at the top of it.**
**[COLOR="Red"]Warning Don't play in here unless you know what your doing &/or have another machine to experiment on.[/COLOR]**

And this one
[Linux – Slow Internet Browsing ??]("http://www.ultimateeditionoz.com/forum/viewtopic.php?f=23&t=727")

---

### Post by spinlock99 on 2010-04-25
> **wojox said:**
> Try looking at this How To [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

Perfect! I had the package swfdec-mozilla installed. I followed the steps in the troubleshooting thread:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

restarted firefox, and youtube videos are now playing just fine :) 

Thanks for the help guys.

Andrew

---

### Post by wojox on 2010-04-25
Your Welcome. :)

---


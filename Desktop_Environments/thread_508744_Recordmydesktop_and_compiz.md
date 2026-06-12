---
title: "Recordmydesktop and compiz?"
date: 2007-07-24
forum: Desktop Environments
---

### Post by SPW06 on 2007-07-24
Hello all

I've installed compiz fusion, kiba-dock, and  gdesktop. And everything looks awesome

Now i want to show this thing off to my friends; the videos ive seen on YouTube are silky smooth. When I record, its kinda jerky, laggy, and altogether slow. Not the impressive effect i was hoping for. Soetimes, it dosent pick up effects, like wobbly windows 1/2 the time. 

How can I get this to be smooth  like the ones I see. I only have 512 MB RAM but a dual core AMD

Is recordmydesktop the right thing to use? What configureation to use ?

Also id like to make a moive detailing each plugin of compiz...

I just need a simple video editor simlar to windows movie maker. Kdenlive maybe?


Anyway, any help would be great :)

---

### Post by upbeat.linux on 2007-07-24
Did you make sure to grab the gtk package as well?

```
sudo apt-get install recordmydesktop gtk-recordmydesktop
```

Also, try playing with the recording settings (namely video, but audio too).  I think you might be having memory threshold issues running Beryl and recording even though you have a dual core. What sort of graphics card are you running? 

Some alternatives might be:

[http://ubuntu.wordpress.com/2006/06/08/how-to-create-a-screencast-in-ubuntu/]("http://ubuntu.wordpress.com/2006/06/08/how-to-create-a-screencast-in-ubuntu/")
[http://www.neopsis.com/projects/yukon/browser/trunk]("http://www.neopsis.com/projects/yukon/browser/trunk")
[http://xvidcap.sourceforge.net/]("http://xvidcap.sourceforge.net/")

Here's a great tutorial for Edgy Eft users:

[http://screencasts.ubuntu.com/Creating_Screencasts]("http://screencasts.ubuntu.com/Creating_Screencasts")

---

### Post by SPW06 on 2007-07-24
Yes...i still dont know how to get it smooth

---

### Post by upbeat.linux on 2007-07-24
Try looking at this post:

[http://ubuntuforums.org/showthread.php?t=294605]("http://ubuntuforums.org/showthread.php?t=294605")

Looks like they got it working by updating their Nvidia drivers (possibly the proprietary Nvidia version) then using:

```
recordmydesktop --quick-subsampling --zero-compression
```

---

### Post by SPW06 on 2007-07-25
Still laggy. I wonder what to use? Maby i need fglrx?

---

### Post by weblordpepe on 2007-07-25
uh oh ATI. You're in the same boat as me. Except I'm on a laptop so I cant change anything. Take it from me. If you've got an ATi card, invest in a time machine so you can go back in time and stop yourself from buying the ATi card. Its easier than getting compiz to work fast.

---

### Post by SPW06 on 2007-07-25
> **weblordpepe said:**
> uh oh ATI. You're in the same boat as me. Except I'm on a laptop so I cant change anything. Take it from me. If you've got an ATi card, invest in a time machine so you can go back in time and stop yourself from buying the ATi card. Its easier than getting compiz to work fast.

That bad..ouch

---

### Post by SPW06 on 2007-07-25
UPDATE: I got compiz faster!

[http://ubuntuforums.org/showthread.php?t=509537](http://ubuntuforums.org/showthread.php?t=509537)

---


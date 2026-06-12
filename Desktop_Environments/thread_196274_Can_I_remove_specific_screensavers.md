---
title: "Can I remove specific screensavers?"
date: 2006-06-14
forum: Desktop Environments
---

### Post by headcronie on 2006-06-14
I'm worried that some of the more potent screensavers may be choking my machine.  Is there any way of removing a specific screensaver, so I can leave it on random?

I was streaming one of the ogg streams that comes in the default media appliation in XMMS, screen saver came on... I came back about 10 minutes later, and I was good as frozen..

My machine is an older machine (I even have to set up a /boot partition in the first few mb of the harddisk.)  IBM Aptiva 550mhz, 4gb hdd, 256mb RAM (8mb stolen for onboard graphics card), 32mb Diamond Stealth III PCI graphics card.

Please be gentle, I'm only a few days old in the world of Linux.. so you'll really need to show me step by step.

Thanks in advance.

---

### Post by max_dingemans on 2006-06-14
What I do, is enter gnome configuration editor by inserting the code below into a terminal:
```
gconf-editor
```

Then hit the expand triangle next to apps, and then find the 'gnome-screensaver' entry. Find the themes key in the righthand box, right click and edit the key. This will bring up a list of screensavers from which you can remove unwanted ones. Unfortunately, it won't preview them as you're browsing, so you'll have to decide which you do and don't want beforehand.

This may not be the easiest way, but it works for me.

Alternatively, you could try [This guide]("http://ubuntuforums.org/showthread.php?t=195557") to install xscreensaver, which has a GUI for more configuration options.

PS, Don't hesitate to ask questions if anything doesn't make sense!

---

### Post by headcronie on 2006-06-14
Ohh.  That looks pretty easy.  *fingers crossed*  I'll give that a try tonight, and report back on my results.  :) Thanks!

---

### Post by headcronie on 2006-06-14
Too easy.  I went through, found the ones that my computer couldn't handle, made a list, and removed them using the instructions above.  Very nice!  Thank you!  :)

---

### Post by headcronie on 2006-06-20
Anyone know if this is possible within Kubuntu?  Trying out new things, and oddly, Kubuntu is more responsive and stable on my old machine.  Would like to remove certain screensavers from the lineup though...

---

### Post by MemoryDump on 2008-05-09
> **max_dingemans said:**
> What I do, is enter gnome configuration editor by inserting the code below into a terminal:
```
gconf-editor
```

Then hit the expand triangle next to apps, and then find the 'gnome-screensaver' entry. Find the themes key in the righthand box, right click and edit the key. This will bring up a list of screensavers from which you can remove unwanted ones. Unfortunately, it won't preview them as you're browsing, so you'll have to decide which you do and don't want beforehand.

This may not be the easiest way, but it works for me.


is there a similar way in doing this in Hardy?
cause it doesn't appear like this works any longer.

---

### Post by rossdub on 2008-07-09
I would love to know if there is another option as well.  Love the random screensaver, but there are about four or five of the ones in Hardy that I can't stand and would like to remove from my system completely.  Let me know if you find anything out.

---

### Post by rossdub on 2008-07-10
> **MemoryDump said:**
> is there a similar way in doing this in Hardy?
cause it doesn't appear like this works any longer.

Just found this link to another thread:
[URL="http://ubuntuforums.org/showthread.php?t=854405&highlight=removing+screensaver"]
http://ubuntuforums.org/showthread.php?t=854405&highlight=removing+screensaver[/URL]

Hope it helps.

---


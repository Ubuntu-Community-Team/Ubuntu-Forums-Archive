---
title: "Azureus 2.5.0.0 on GCJ ALMOST Perfect"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Gnuklear on 2006-08-22
As some of you may know, Azureus 2.5.0.0 was released yesterday. So, I completely removed Azureus 2.4.0.2 from Synaptic, and downloaded the Azureus Project provided files for amd64, unzipped, cd'd to the directory and ran ./azureus not expecting much. To my great surprise, not only did Azureus load but EVERYTHING WORKED!!! I could close the warning messages, I could close the taskbar tabs, and azureus actually sat in the system notification area when minimized. Incredible, no? Sadly, after about 5 minutes of it running like a champ, my system froze. I don't mean azureus, I mean my whole system. Couldn't move the mouse, couldn't do anything. Suspecting azureus, I restarted azureus, waited, and the same things happened.

What commands should I run to get log/debug information that could actually be useful in diagnosing the problem? Azureus is SO close to being a completely Free Software application, and I'd love to help get it there as fast as possible.

That said, both times my system froze I was using firefox with azureus in the background, and both times in firefox I was writting into a textbox like this one? Coincidence? Let's find out.

---

### Post by Iarwain ben-adar on 2006-08-22
Please,

keep us updated (because i love azureus, but it isn't working that good on my system :( )


Iarwain

---

### Post by Gnuklear on 2006-08-22
Ok, restarted again, Azureus has been running for about 25 mintes straight now with not so much as a hiccup. Everything seems to be working great (I've downloaded about 150MB in those last 20 minutes, so I am actually connecting and such).

Well... I'm typing and Azureus hasn't crashed... not that I'm dissappointed or anything, just a bit confused... then again, I DID just upgrade xorg after the last crash. Perhaps the old xorg was making azureus flip out? Or perhaps the other way around? Just throwing around ideas.

---

### Post by Gnuklear on 2006-08-22
Scratch that. System just froze again. But, again, I was using Firefox at the time (then again, I almost alway am). Like I said before, if anyone knows of any commands I can run to get some diagnostic info, I'd appreciate the tip.

---

### Post by Gnuklear on 2006-08-22
Anyway, if anyone else would like to try this out without destroying their already working Azureus system:

WARNING: This is experimental. Don't blame me if it corrupts your torrents / breaks your system / kills your cat.

What we're going to do is simply copy the Azureus2.jar file from 2.5.0.0 and use it to replace the file from 2.4.0.2. Yes, this really does work. I'm using it like this right now. The file you need to replace is /usr/share/Azureus2.jar so if you know how, save yourself some time and don't bother with what's written below.

1. Download the 2.5.0.0 package for your architecture from azureus.sf.net
2. Extract the archive to your Desktop
3. Open a terminal and run the following commands:
```
sudo cp /usr/share/Azureus2.jar /usr/share/Azureus2_OLD.jar
cd azureus ; sudo cp Azureus2.jar /usr/share/Azureus2.jar
```

Now you should be able to open Azureus and be greeted with the improved 2.5.0.0 interface.

If you want to return to your old setup, just run the following command:
```
sudo cp /usr/share/Azureus_OLD.jar /usr/share/Azureus2.jar ; sudo rm /usr/share/Azureus_OLD.jar
```
Now you should have 2.4.0.2 back.

---


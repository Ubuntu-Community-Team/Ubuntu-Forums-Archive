---
title: "Screen shuts off in 12.10 - can't find where to turn that off"
date: 2012-10-20
forum: Desktop Environments
---

### Post by samfrimp on 2012-10-20
I have a fresh install on a desktop (Q6600, 2gb) of 12.10 (with the AMD drivers). After 10 minutes of inactivity, the screen shuts off. I don't want the screen to shut off.

I can find no setting under Power, Appearance, Displays, Brightness & Screenlock or anywhere else to disable this behaviour.

Looking for 'screensaver' under 12.10 yields nothing - it's as if one isn't even installed.

No amount of searching has provided an answer. 

Any ideas?

---

### Post by cmcanulty on 2012-10-20
install caffeine and you can disable that

---

### Post by samfrimp on 2012-10-20
Thanks. Kind of ridiculous that this functionality isn't baked in to the OS.

---

### Post by DGINSD on 2012-11-07
> **cmcanulty said:**
> install caffeine and you can disable that

Where can we get Caffeine it's no longer in the repos, and how do we disable this using Caffeine?

---

### Post by cmcanulty on 2012-11-07
see this
[http://linuxg.net/install-caffeine-in-ubuntu-12-04-and-ubuntu-12-10/]("http://linuxg.net/install-caffeine-in-ubuntu-12-04-and-ubuntu-12-10/")

---

### Post by DGINSD on 2012-11-08
Found this solution and it's working for me, make a plain text doc in your home folder and copy this into it.

```
#!/bin/bash
sleep 10 &&
xset s 0 0
xset s off
exit 0

``` 

Save the document as "screensaver_off.sh" (without quotes), then open a terminal and enter

```
chmod +x screensaver_off.sh
```

Then open up startup applications from the dash. Click on the add button, name your start up application, and enter your command as

```
/home/david/screensaver_off.sh
``` 

replacing "david" with your home folders name, then add a description and click add, reboot and your done, No more screen blanking. 

You will have to do this per each user as default settings revert after logout or reboot. 

[IMG]http://s19.postimage.org/by8230eoj/screensaver_Screenshot.png[/IMG]

---

### Post by masgeeks on 2012-11-09
Thank you for that solution the script worked...!!!  Am using Ubuntu Gnome Remix 12.10.1 on a laptop and nothing, and I mean NOTHING, had stopped the screen from going dark.  Not tinkering with any settings in dconf, not installing caffeine... no gui or command seemingly would stop it from going dark after 10 minutes.  But your script did the trick THANKS SO MUCH, the screen blanking was driving me NUTS.  I've used Ubuntu on a LOT of laptops, but never had one that disobeyed those settings.  If I WANT my screen to go blank, there's a nice little gnome shell extension for that... a click and it goes dark... but when I want it to...  :)  Of course, we shouldn't have to jump through hoops over so simple a thing like screen timeout...

---

### Post by DGINSD on 2012-11-11
> **masgeeks said:**
> Thank you for that solution the script worked...!!!  Am using Ubuntu Gnome Remix 12.10.1 on a laptop and nothing, and I mean NOTHING, had stopped the screen from going dark.  Not tinkering with any settings in dconf, not installing caffeine... no gui or command seemingly would stop it from going dark after 10 minutes.  But your script did the trick THANKS SO MUCH, the screen blanking was driving me NUTS.  I've used Ubuntu on a LOT of laptops, but never had one that disobeyed those settings.  If I WANT my screen to go blank, there's a nice little gnome shell extension for that... a click and it goes dark... but when I want it to...  :)  Of course, we shouldn't have to jump through hoops over so simple a thing like screen timeout...

Quite annoying isn't it I'm kind of curious how things like this slip through development, I don't exactly have some obscure laptop or anything but the screensaver and brightness settings have never worked on any of my machines, along with a host of other things that I have to find or develop tweaks for. Aside from those usually minor things, awesome FREE operating system, and at least when you find issues there's usually a way to work around them. It's just a matter of how important it is to you and how much time your willing to search for a solution (Usually involving multiple pages of search results).

If the screensaver gui isn't working for you, your likely having issues with brightness settings as well here's a link to a great fix [http://ubuntuforums.org/showthread.php?t=1954041]("http://ubuntuforums.org/showthread.php?t=1954041")
I could kiss the person that wrote it.

---

### Post by masgeeks on 2012-11-12
Half the fun of any Linux distro is getting there - and I love finding fixes, but the screen things drove me nuts.  However, finally getting it resolved brought much joy...  :)  I have a brand new DELL Precision laptop, and amazingly enough, ALL the hardware works, the nvidia card works beautifully, card reader works, wifi gets awesome speed - I can't complain about a thing - especially given how new the laptop is (less than a month old).  Usually I find that new machines have the most issues, and older machines don't, because enough time has lapsed where issues have been addressed and corrected.

---

### Post by nickgee667 on 2012-11-12
Right click (or left click) the battery in the system tray and go to power options?  

Or you could go into the systems settings (the equivalent of Windows' Control Panel) and go to power options.

---

### Post by masgeeks on 2012-11-12
None of the standard ways of configuring the screen idle time worked.  Period.  Nada, nyet, zip - only DGINSD's script worked.   Caffeine didn't work, either... nothing did... it was POSSESSED... honestly...

---

### Post by sundansekidd on 2012-11-21
Thanks for the script.  It solved the issue for me.  I am currently using gnome-remix 12.10 on a 64bit desktop and I didn't notice this issue until after changing from the default graphics driver to NVIDIA.

---


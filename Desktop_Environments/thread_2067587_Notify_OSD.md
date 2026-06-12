---
title: "Notify OSD"
date: 2012-10-07
forum: Desktop Environments
---

### Post by GeForce 9500GT on 2012-10-07
Hi everyone,

Everytime something is going on i get a notification at the top right side of my screen. I don't want this and i want to get rid of it. Looking for a solution on the internet [i found this]("https://sites.google.com/site/tipsandtricksforubuntu/tips-and-tricks/notify-osd") but this doesn't seem to work. Does anyone know a command/trick/tool to get rid of that big black notification OSD at the top-right? 

Many thanks!

---

### Post by zombifier25 on 2012-10-07
Remove notify-osd completely?
```
sudo apt-get remove notify-osd
```
(have yet to test code, but it can't do nothing wrong)

---

### Post by GeForce 9500GT on 2012-10-08
Still waiting for an answer/solution on how to get rid of those pop-up messages at the top-right side of my screen. When i was using Ubuntu 10.04 [this solution]("https://sites.google.com/site/tipsandtricksforubuntu/tips-and-tricks/notify-osd") worked, but not for Lubuntu 12.04. I've noticed that i have this directory: /usr/lib/notification-daemon/. Can i move this folder to another location? The notification service is disabled in the startup properties, see screenshot.

Anyone?

---

### Post by vasa1 on 2012-10-08
I've installed Lubuntu 12.10 (beta) and the notification about internet connectivity (or lack of) has an option not to see this message again.

I think the notifications are important and won't choose not to see them.

---

### Post by GeForce 9500GT on 2012-10-08
> **vasa1 said:**
> I've installed Lubuntu 12.10 (beta) and the notification about internet connectivity (or lack of) has an option not to see this message again.
 
I think the notifications are important and won't choose not to see them.
 
Hee vasa, thanks for your reply. 
 
I do get a notification after installing about network connectivity and so on which can be switched off. But the most notifications are about files which i was downloading, a paper which has been send to the printer, and so on... nothing much of importance. Under Ubuntu 10.04 i could solve this by moving this folder: /usr/lib/notify-osd. But under (Lubuntu) 12.04 this folder doesn't exist.
 
And yes, i find those pop-up notifications annoying.

---

### Post by nothingspecial on 2012-10-08
Removed unnecessary stuff.

Stay on topic please.

---

### Post by lightning slinger on 2012-10-08
The modifications at this page have worked very well for me with lubuntu 12.04


[http://www.lubuntutips.com/2012/07/notification-pop-ups-in-lubuntu.html](http://www.lubuntutips.com/2012/07/notification-pop-ups-in-lubuntu.html)

:)

---

### Post by GeForce 9500GT on 2012-10-08
> **lightning slinger said:**
> The modifications at this page have worked very well for me with lubuntu 12.04


[http://www.lubuntutips.com/2012/07/notification-pop-ups-in-lubuntu.html](http://www.lubuntutips.com/2012/07/notification-pop-ups-in-lubuntu.html)



I rather don't want to do that. With the command **sudo apt-get remove notification-daemon** it also want to remove lubuntu-desktop as well., see screenshot.

 Translate it into English and you see what i mean.

---

### Post by jerrrys on 2012-10-08
Mega packages can be removed.  If thats what it says.

---

### Post by lightning slinger on 2012-10-08
The article does draw attention to that....

>  It may prompt you with something scary about removing the  lubuntu-desktop. That didn't happen to me, but you shouldn't worry  because it's part of a meta package. Your desktop will be fine. I  promise!Didn't do anything with lubuntu-desktop in my case either. The only downside of this mod is the update manager doesn't give you the notification (obviously) about any updates. You have to run that manually!

---

### Post by vasa1 on 2012-10-08
> **GeForce 9500GT said:**
> I rather don't want to do that. With the command **sudo apt-get remove notification-daemon** it also want to remove lubuntu-desktop as well., see screenshot.

 Translate it into English and you see what i mean.

This lubuntu-desktop is a mysterious "meta" thing and I don't understand what's going on here.

I just removed the penguin games using the lubuntu software center and, without warning, the lubuntu-desktop was removed as well.

Oddly (or not), the lubuntu software center doesn't offer lubuntu-desktop for installation.  I then removed pidgin and sylpheed as well.

Then I looked in Synaptic and lubuntu-desktop is available from there. However, one can't just install the lubuntu-desktop. It wants to pull its buddies back in with it: so the penguin games, pidgin and sylpheed would make their reappearance.

Anyway, I'm going to do without the lot of them and see what happens.

BTW, 12.10 doesn't seem to have this "notification-daemon" at least when I look at the list produced by **dpkg --get-selections**.

---


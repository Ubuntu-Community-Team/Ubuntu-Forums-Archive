---
title: "CPU Monitor Missing after Upgrade to 11.04"
date: 2011-08-12
forum: Desktop Environments
---

### Post by N1GHTS on 2011-08-12
I recently upgraded from **10.04** to **11.04** in order to fix a weird problem I was having in which I was forced to reinstall **NVidia** drivers every single time I booted into **Ubuntu**. Fortunately, The problem went away after the upgrade, but it was replaced with a bigger problem called "**Unity**".

After a few minutes of being unable to literally do anything in this **Unity** interface, I logged out and used the "**Classic Ubuntu**" which would be **GNOME 2.32.1**. This interface was missing many of my old **GNOME Panel** applets, and it was unable to be patched with the unofficial **vertical task bar fix**, making "**Classic Ubuntu**" nearly as ineffective as **Unity**. 

I decided to go the route of **Avant Window Navigator** as my replacement vertical task bar. It works _great_! I have it working together with a *crippled* **GNOME Panel** with just enough functionality to be _good enough_ for my heavy development work.

There's only one problem... I can't find the **GNOME Panel _CPU Monitor_** applet! The one that comes with **Avant** does not show me _cumulative CPU usage over time_, which is what I need. This is what I had _*before*_ the upgrade. 

Anyone know how I can get it back?

---

### Post by donut123 on 2011-08-12
[SIZE=3]Hello..I had the same happen to me
 [http://ubuntuforums.org/showthread.php?t=1823378](http://ubuntuforums.org/showthread.php?t=1823378)[/SIZE]
Here is the thread..no one came to my post either...I think these dudes pick and choose what they want to answer
. U sually I find the answer no matter what I have to do..If I have to **** on my machine to fix something..then I will do it ..LOL
but I see your post is still fresh...anyway no one came to mine..and no one came at all to another post I had. 
And sometimes you get a thousand experts ...sheesh

---

### Post by N1GHTS on 2011-08-12
I'd rather never get an answer on in the **Ubuntu** forum than pay _$95_ an hour for bad support from [SIZE=1]microsoft[/SIZE].

---

### Post by donut123 on 2011-08-13
This update had to be the one  a couple of days ago..in the last updates.

---

### Post by Ubulindy on 2011-08-13
I had the same thing happen to me after upgrading, which led me to having to reformat my dual boot with Ubuntu & Windows. After the reformat, I immediately logged out of Ubuntu, booted back into classic, installed kdm, uninstalled gdm, installed Dolphin, did away with Nautilus, and did I mention I reverted back to Maverick? Oo Turns out my fav distro is now my least fav distro. This unity is one big mess. The good news is... for all you die hards who always loved your favorite distro, you can still have it... WITHOUT UNITY!!  :D  Try out Mint instead. They use the ubuntu kernels, ect, and they hate unity, AND, they are keeping gnome, even going back to the more stable gnome. Happy days are here again. Unity is messy, and if you are like me, dont like cluttered desktops, and have a million launchers in your panel, Unity just doesnt do the job. Ill wait 2 more weeks til the new Mint comes out. Boy, Canonical really f***** this up this time. Instead of mainstreaming the best of both worlds, this time, they are driving away users that had remained loyal to Ubuntu. Good thing I didnt get that Ubuntu tattoo I was gonna get, lolz, Id have to go back for a cover up at this point. Very sad in ubuland indeed.

---

### Post by N1GHTS on 2011-08-13
Interesting suggestion of using the **Mint** distro. Why not just get the latest **Ubuntu Server** and apt-get **GDM**/**KDM**/etc? It may not be an *out-of-the-box experience*, but essentially its a customised **Ubuntu**, and you can keep your *tatoo*! 

Is there really a difference?

---

### Post by Ubulindy on 2011-08-13
Yes,there is a huge difference in everything I had mentioned. As far a kdm and Dolphin vs Gnome? To me its like night and day. Well of course thats mainly bcs when you go with kdm and dolphin you're also installing most of kde along with it.Seems like the more Ubuntu tries to mainstream, and tries to get users to convert over from Windows, the more choices they take away form the end user. Unless you're a programmer, you're left with frustration. I started with Dapper and never thought Id leave Ubuntu. But Canonical it seems simply stopped listening to the end users it seems on its quest to be more like Microsoft. If you ask me, Unity is one big "cluster****" Missing icons, panel not showing randomly, and the sidebar,trying to navigate around, no way to circumvent compiz.  Oo Just visit freenode #ubuntu and see how happy people are. I already have Mint on a usb flash, unfortunately my latop wont boot Mint off a cd or dvd. Soon, its bye bye Ubuntu. None of this makes me very happy. Recently Ive had to re-install/reformat 2 friends PCs after they upgraded to Natty. One of them had me give them back Maverick, the other went with Maverick and Mint dual boot. Guess which she prefers?  ;-)

And the reason I dont go with a server edition is bcs I prefer a desktop environment,and typically with server you dont have one, altho you can install one, just seems more silly to then not start off with desktop to begin with.  :-P

---

### Post by N1GHTS on 2011-08-13
Thanks for your feedback. Its definitely something to *keep in mind* for **personal** use. 

In our business we use **Ubuntu Server**, so it does worry me if **Ubuntu** starts going the _wrong direction_ with their *desktop* development because I can only image what kinds of _lapses of judgement_ they would make in **Ubuntu Server**. One bad move with their server _update packages_ could **cost our business tons of money**. 

Of course I am _*wary*_ about using **Open Source** software in **business**. Usually the cost of extra testing and version certification can be _more expensive_ than paid server systems. I don't think I have much to worry about though, especially since all projects as big as** Ubuntu** have had their _share of mistakes_. Its an important part of **maturation**.

---

### Post by donut123 on 2011-08-14
Is that the only answer? go and use Mini? I dont have Mini..I have Ultimate Edition 2.9..10.10 Maverick Ubuntu base.

---

### Post by Ubulindy on 2011-08-14
> **donut123 said:**
> Is that the only answer? go and use Mini? I dont have Mini..I have Ultimate Edition 2.9..10.10 Maverick Ubuntu base.

No, thats not the only option. Just saying that Ubuntu has chosen to keep Unity, and Mint is not. Trying to remove Unity in the future to revert back to "classic" just simply wont work

---

### Post by Frogs Hair on 2011-08-14
If you need a work around .```
sudo apt-get install nmon
``` 

Nmon is a system monitor that opens in the terminal by typing its name and displays long term averages for the cpu . There may be something helpful at the link . [http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by N1GHTS on 2011-08-14
I appreciate your help **Frogs Hair**, but what I need is to see the CPU tracking graphic hovering over the **Gnome** or **Avant** panel _at all times_. This is a requirement because **NetBeans**, the development studio I use, is so damn **slow**. Its so slow in fact, that I have learned to wait as long as **6 minutes** before the IDE is responsive. Having instant access to the** CPU monitor** can clue me in to a **NetBeans** (**Java**) crash or a "*runaway thread*" in the program I am developing, or _something else_. I just hate not knowing how much work the CPU is doing at every moment of development.

---

### Post by Frogs Hair on 2011-08-14
The ( hardware-monitor ) applet for the Gnome panel is still in the 11.04 synaptic package manager . If it is the one I remember you will need to install ( lm-sensors ) . I am not sure if this will do what you want , but may be  worth a look .

Code:
sudo apt-get lm-sensors 

Code:
sudo apt-get install hardware-monitor

Then you will have to activate from the add to panel menu . You may needs to logout/ in or restart .

---

### Post by N1GHTS on 2011-08-14
The package **lm-sensors** was not found, but **hardware-monitor** was found. I installed it, restarted **Gnome**, and loaded the applet. It works great! 

I like it because I can make it as wide as I want, but I don't like that clicking on it does not bring up the system monitor. Either way I can live with it.

Thank you **Frogs Hair**! :D

---

### Post by phuongdt3 on 2011-08-15
hello,i'm having the semilar problem,thanks for feedback ^^

---

### Post by donut123 on 2011-08-15
Well..I was trying to get some answers but I have none..all the solutions failed. Did this happen after your updates?
Or you can use the MIni..the easy way out..which I dint have...I always do things the hard way..thats why Im steel now..and not mush.. LOL

---

### Post by N1GHTS on 2011-08-16
I get the *impression* that you don't know how to add and configure **Gnome** panel applets **donut123**. Maybe a **screen-shot** might help.

---

### Post by donut123 on 2011-09-01
> **N1GHTS said:**
> I get the *impression* that you don't know how to add and configure **Gnome** panel applets **donut123**. Maybe a **screen-shot** might help.

No..my experience with Gnome and setup is always the same. However the System Monitor has returned. 
I left it alone for  a while, and now it is back. Sometimes it happens that way, so confifuring and adding isnt so difficult. Ones have  a different impression of mr where ever I go..some one else may call me an expert, some one else may call me an idiot..its all in what one chooses to believe.
THank you I appreciate your assistance.

---

### Post by donut123 on 2011-09-01
> **phuongdt3 said:**
> hello,i'm having the semilar problem,thanks for feedback ^^

Hello..if you notice may last post , I wrote it is returned, check to see..it may be there for you.
Have   a nice day.

---

### Post by donut123 on 2011-09-01
Hello everyone...this is solved for me, however there are one or two with the issue. I wont mark it solved because it showed up again, it was not  a solved by adding or configuring.

---


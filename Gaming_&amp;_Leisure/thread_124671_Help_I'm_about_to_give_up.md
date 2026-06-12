---
title: "Help I'm about to give up"
date: 2006-02-01
forum: Gaming &amp; Leisure
---

### Post by catalytic on 2006-02-01
I have been using Ubuntu for a month now and I still cannot get any games to work.
I have tried Quake, Wow, ET, and just now TORC and LGenerals.

So far LGenerals is the only one that I think may work, problem is I don't have any scenarios, I think I know where to get them, but where do I save them as I can't find where the game directory is.

Absolutely nothing will work for me, I can listen to music and burn dvd's but that is about it. When it comes to gaming Ubuntu is seriously lacking, all that will work is the boring games like tetris.

If I can at least get the games I like to play working on here then Ubuntu stays, ohterwise I'm going back to windows. I have tried installing the games in windows then playing with wine in Linux, doesn't work.
I have tried installing games with wine in Linux that doesn't work.

Enemy Territory won't run on my system, are there any games similar that do run on Linux on an AMD athlon XP2000 with onboard graphics?

---

### Post by Digitallysick on 2006-02-01
have you looked into cedega? thats probably what you need

---

### Post by ahood on 2006-02-02
A few more details might be in order.

What graphics card are you using?

Has the graphics driver been installed?

What is the output of glxgears (in a terminal type 'glxgears -printfps', wait a few seconds for fps to appears, press ctrl+c to quit).

You earliest post was 4 weeks ago, which isn't all that long. Keep with it, post here and the community will help.

Dr. Hood

---

### Post by handy on 2006-02-02
If all else fails, try a dual boot rig, & learn it slowly... 

The learning curve is huge for ***_EVERYONE._***

Having a windoze install too, can go along way towards alleviating the frustrations involved in learning a new OS. Nobody likes feeling frustrated.  It's not good for our self esteem either!

Imagine 12 months down the track... 

If you just put time into learning Ubuntu (linux), when you want to, no deadlines...  In 12 months time you will be able to do more than you would think possible now.

Take the pressure off.

No one else will!

---

### Post by ahood on 2006-02-02
I also support handy suggestion....

I personally did not give up linux totally in one fall swoop. It was a gradual process. To give an example, I started playing around with linux back in 1999, dual booted of course. Over the years, I learned the differences between Windows and linux. The more I learned linux, the more time I spent with it. Short at first, all the time now. Now couldn't go back to using Windows.

In summary, for most users, switching to linux takes time, sometimes years, and for some never. The key to switching to linux is sticking with it, willingness to learn, and not limiting yourself to Windows apps.

Dr. Hood

---

### Post by RaiSuli on 2006-02-02
I've recently joined the Ubuntu community and couldn't agree more with what people are saying here. Don't force it. If there are some apps that you just don't want to be without, dual boot into Windows now and then. For gaming Cedega and Wine are good choices to get many, but not all games to run under Ubuntu. That being said, Linux vs Windows is not a religios war. If the alternative to not getting a game to run under Ubuntu is not to play at all, just play it under Windows. With a safety net like this, your Ubuntu experience will a lot less frustrating and far more rewarding.

---

### Post by Biased turkey on 2006-02-02
[QUOTE=catalytic]
So far LGenerals is the only one that I think may work, problem is I don't have any scenarios, I think I know where to get them, but where do I save them as I can't find where the game directory is.

If I can at least get the games I like to play working on here then Ubuntu stays, ohterwise I'm going back to windows. I have tried installing the games in windows then playing with wine in Linux, doesn't work.
I have tried installing games with wine in Linux that doesn't work.
[/QUOTE]


I wrote a complete howto about installing Lgeneral + data files at:
[http://www.ubuntuforums.org/showthread.php?t=86931&highlight=lgeneral]("http://www.ubuntuforums.org/showthread.php?t=86931&highlight=lgeneral")

I hope this can make you change your mind about erasing your Ubuntu partition.

---

### Post by LordBug on 2006-02-02
> I have tried Quake, Wow, ET, and just now TORC and LGenerals.

Quake and ET have Linux binaries, but require the original media for the game pak files.  WoW requires WINE or Cedega in order to run.  I don't even know what the last 2 are, but Biased Turkey appears to have your info for Generals.

---

### Post by catalytic on 2006-02-02
[QUOTE=ahood]A few more details might be in order.

What graphics card are you using?

Has the graphics driver been installed?

What is the output of glxgears (in a terminal type 'glxgears -printfps', wait a few seconds for fps to appears, press ctrl+c to quit).

You earliest post was 4 weeks ago, which isn't all that long. Keep with it, post here and the community will help.

Dr. Hood[/QUOTE]


I don't know it's just onboard graphics on a Gigabyte mother board, 32 mb ram though I think. No 3d acceleration.

Here's what I get from the glxgears 
759 frames in 5.7 seconds = 134.040 FPS
720 frames in 5.5 seconds = 132.018 FPS
720 frames in 5.9 seconds = 122.139 FPS
751 frames in 5.4 seconds = 139.366 FPS

I have always been running a dual boot, but the other week windows updated and nothing works anymore. I can't access the internet. 

I would try Cedega if I could find it, eveywhere I go it says I have to join something or pay something to get it. 

It seems the only games I might be able to play are games that you can't even buy in stores anymore.

I would love to just fix windows, but I'm not going to waste the time or money at the moment. Everytime it updates it kills my firewall and all internet access and adapters. Try and get support from microsoft, costs me about $100. So I do appreciate your help, but it just seems Ubuntu is not for my system.

---

### Post by catalytic on 2006-02-02
I followed the instructions to install Lgenerals to the letter, and it worked I think, Yay one game that I got installed. Lets see if it actually works.

---

### Post by handy on 2006-02-02
Your frame rates are very low.

If you don't have a motherboard manual which will tell you what graphics chip is on the board, & you can still boot into windoze?

Then one way to identify your adapter in windows, is to right click in some free space on the windows desktop, then go down to **Properties**, in the menu that pops up, then in the dialogue that appears, select the right most tab **Settings**, It may tell you what monitor & graphics card  you are using here, but for more info, select the **Advanced** button & then choose the second tab **Adapter**.

Could you please post the following:

**Chip Type:**  ?

**Memory Size:**  ?

**Adapter String:**  ?

We should atleast know what the graphics adapter is then, I therefore it's capabilities, driver posibilities etc.

We'll just do one thing at a time...  :)

---

### Post by ahood on 2006-02-04
[QUOTE=catalytic]I don't know it's just onboard graphics on a Gigabyte mother board, 32 mb ram though I think. No 3d acceleration.

Here's what I get from the glxgears 
759 frames in 5.7 seconds = 134.040 FPS
720 frames in 5.5 seconds = 132.018 FPS
720 frames in 5.9 seconds = 122.139 FPS
751 frames in 5.4 seconds = 139.366 FPS

I have always been running a dual boot, but the other week windows updated and nothing works anymore. I can't access the internet. 

I would try Cedega if I could find it, eveywhere I go it says I have to join something or pay something to get it. 

It seems the only games I might be able to play are games that you can't even buy in stores anymore.

I would love to just fix windows, but I'm not going to waste the time or money at the moment. Everytime it updates it kills my firewall and all internet access and adapters. Try and get support from microsoft, costs me about $100. So I do appreciate your help, but it just seems Ubuntu is not for my system.[/QUOTE]

Do you know the model of Gigabyte motherboard? 

Is it one of the following:.......

A. [[COLOR="Blue"]GA-K8VM800M[/COLOR]](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=1919)
CPU: AMD Athlon 64/Sempron
Chipset: VIA K8M800

B. [[COLOR="Blue"]GA-6WMMC7-1[/COLOR]](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=1696)
CPU: Intel Pentium III
Chipset: Intel 810/AC97

C. [[COLOR="Blue"]GA-6WMZ7[/COLOR]](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=1593)   / [[COLOR="Blue"]GA-6WMM7-1[/COLOR]](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=1589)
CPU: Intel Celeron
Chipset: Intel 810/AC97

I am suspecting that it is an Intel solution, choices B or C.

Dr. Hood

---

### Post by catalytic on 2006-02-05
7VM400M-RZ type A proccessor, 32mb memory,
It is a VIA KM400 chipset.
I can play enemy territory in windows, barely, it's really not playable there either. But I can play games like WoW and GTA3, max payne, none will work however on Ubuntu. So if the games I already own don't work I don't see much point in continuing to use Ubuntu.

I just re installed Ubuntu today and now nothing is working properly, I have no sound, and I can't access my windows partitions. I cannot get into my root account at all.

I'm going back to windows as soon as I can get an install CD. 

All I want to know is how I can view my files on my windows partition for the mean time.

 Everything is slow. I would have like to have used it, but the only thing that attracted me was I saw linux as being more secure as there are no viruses for it.

But that's it, I have spent a month trying to do things that I could work out how to do in windows in a couple of days. I was starting to get the hand of the terminal, but really it's just too time consuming.

Thanks anyway.. if someone could just tell me how I can at least view the files I have on here?? : )

---

### Post by kingsidy on 2006-02-05
To mount Windows partition
> 
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

this is assuming that your windows partition is ntfs.

---

### Post by catalytic on 2006-02-05
This is also frustrating that I now can't even listen to music at least on here. This is the error I get from my sound icon

No volume control elements and/or devices found.

I've looked in device manager and my sound card is showing up fine.

---

### Post by handy on 2006-02-05
Have a look in the ***Menu:***  **System / Help**

***Then choose:***  **Ubuntu 5.10 Starter Guide**

Have a look at the **Windows Partitions** topic, you may also find the **Hardware** topic helpful.  

This help is not like the windoze help, it actually does! :mrgreen:

---

### Post by catalytic on 2006-02-05
[QUOTE=kingsidy]To mount Windows partition


this is assuming that your windows partition is ntfs.[/QUOTE]
That is exactly what I did and it  didn't work. I just did it again to make sure and absolutely nothing happens. I still can't view my files.

---

### Post by catalytic on 2006-02-05
[QUOTE=handy]Have a look in the ***Menu:***  **System / Help**

***Then choose:***  **Ubuntu 5.10 Starter Guide**

Have a look at the **Windows Partitions** topic, you may also find the **Hardware** topic helpful.  

This help is not like the windoze help, it actually does! :mrgreen:[/QUOTE]
All it tells me to do is the same thing, which doesn't work. I do not have a root account, I can not log off and log into root. In fact at the moment nothing works. Synaptic wont start.

---

### Post by handy on 2006-02-05
As far as sound is concerned there is great help here:

[http://ubuntuforums.org/showthread.php?t=75382](http://ubuntuforums.org/showthread.php?t=75382)

In wiki's, searching the forums, let alone posting.  The Ubuntu Document Storage Facility, is another great place.

But this is a waste 'cause you're on your way soon.  But that's ok, you may come back when Ubuntu (linux) has developed some more, as it will allways be growing in capabilities & refinement...

---

### Post by handy on 2006-02-05
Have you a live cd?

That could make things easier, re: accessing your data.  If you don't you could maybe get one on a current linux mag', that could be a quick way, if you can not download.

Or just buy windoze & carry on...

**[EDIT:]  sudo doesn't work for you?**

---

### Post by ahood on 2006-02-05
[QUOTE=catalytic]7VM400M-RZ type A proccessor, 32mb memory,
It is a VIA KM400 chipset.
I can play enemy territory in windows, barely, it's really not playable there either. But I can play games like WoW and GTA3, max payne, none will work however on Ubuntu. So if the games I already own don't work I don't see much point in continuing to use Ubuntu.

I just re installed Ubuntu today and now nothing is working properly, I have no sound, and I can't access my windows partitions. I cannot get into my root account at all.

I'm going back to windows as soon as I can get an install CD. 

All I want to know is how I can view my files on my windows partition for the mean time.

 Everything is slow. I would have like to have used it, but the only thing that attracted me was I saw linux as being more secure as there are no viruses for it.

But that's it, I have spent a month trying to do things that I could work out how to do in windows in a couple of days. I was starting to get the hand of the terminal, but really it's just too time consuming.

Thanks anyway.. if someone could just tell me how I can at least view the files I have on here?? : )[/QUOTE]

Catalytic,

I also recommend to use a LiveCD. I recommend using [[COLOR="Blue"]SimplyMepis[/COLOR]](http://www.mepis.org/node/1462), a liveCD that uses KDE (a Windows-like desktop).

I certainly can feel the frustration you have experienced and I do hope you consider using Windows and linux in a dual boot system. 

If Ubuntu linux didn't suit your needs, then I recommend trying [[COLOR="Blue"]Linspire[/COLOR]](V) or [[COLOR="Blue"]Xandros[/COLOR]](www.xandros.com). Although these distributions are not 'free', they do a lot to ease Windows users into the linux world. I used Xandros for 2 years and it really did wonders in weaning me away from Windows. 

If you want to play games in linux, I **highly recommend** getting a **[color=red]Nvidia[/color]** graphics card. It will eliminate much of the gaming-related frustration you have described.

Good luck!

---

### Post by catalytic on 2006-02-06
I used the Ubuntu live CD for about a week before I installed a dual boot system. I still have windows, but it does not work!
My Ubuntu install now cannot access the net, I have no sound, can't access my windows partitions, and now won't even load at all.
So once again I am forced back to using the Live CD just so I can access the net.
Ubuntu has pretty much put me off tryint linux again.
I'd be interested in a distribution that is easier to set up and run on a dual boot system, something that you can actually play games on. But I doubt there will ever be such a thing. The synaptic package manager was the only thing in Ubuntu that was easy to use! 
There were things I prefered about linux, but at the end of the day, I understand windows and I prefer working in an environment that I can easily understand.
I was rarely getting virus's, all my programs worked, the only problem I have with windows is the automatic updates, that killed my internet.

---

### Post by handy on 2006-02-06
Turn off updates!

---

### Post by aliencds on 2006-02-08
im running a dual boot of xp and i have to tell you it is stressfull o i feel your pain man. after about 10 mintues i needed to go back to xp cuz i was frustrated but im just trying to figure out how to get this rig up and going and get some programs installed etc..

---

### Post by ahood on 2006-02-08
[QUOTE=catalytic]I used the Ubuntu live CD for about a week before I installed a dual boot system. I still have windows, but it does not work!
My Ubuntu install now cannot access the net, I have no sound, can't access my windows partitions, and now won't even load at all.
So once again I am forced back to using the Live CD just so I can access the net.
Ubuntu has pretty much put me off tryint linux again.
I'd be interested in a distribution that is easier to set up and run on a dual boot system, something that you can actually play games on. But I doubt there will ever be such a thing. The synaptic package manager was the only thing in Ubuntu that was easy to use! 
There were things I prefered about linux, but at the end of the day, I understand windows and I prefer working in an environment that I can easily understand.
I was rarely getting virus's, all my programs worked, the only problem I have with windows is the automatic updates, that killed my internet.[/QUOTE]


I hear you and can relate....We have all been there....Not sure where things went wrong in your case......Things can be solved with a simple wiping out of the linux partition and startng completely over.

You might want to try this nifty free partition utility [[color="blue"]Partition Logic[/color]](http://visopsys.org/partlogic/)

It is highly recommended that you consider [[color="blue"]Linspire[/color]](http://www.linspire.com) or [[color="blue"]Xandros[/color]](http://www.xandros.com)....

These distributions are easy to install (3 clicks or less), install binary graphics drivers (e.g., Nvidia) out-of-the-box, and easier to use Windows apps as they come with the utilities pre-installed (e.g., crossover office).

Good luck!

Dr. Hood

BTW - I love Ubuntu, but recognize that not all distributions are for everyone and the power of opensource is in part, the power to choose, be it Ubuntu, Xandros, Linspire, Fedora, Suse, Mepis, PCLinuxOS, Mandriva, and many of the other linux based distros.

---

### Post by ahood on 2006-02-08
[QUOTE=catalytic]7VM400M-RZ type A proccessor, 32mb memory,
It is a VIA KM400 chipset.
I can play enemy territory in windows, barely, it's really not playable there either. But I can play games like WoW and GTA3, max payne, none will work however on Ubuntu. So if the games I already own don't work I don't see much point in continuing to use Ubuntu.

I just re installed Ubuntu today and now nothing is working properly, I have no sound, and I can't access my windows partitions. I cannot get into my root account at all.

I'm going back to windows as soon as I can get an install CD. 

All I want to know is how I can view my files on my windows partition for the mean time.

 Everything is slow. I would have like to have used it, but the only thing that attracted me was I saw linux as being more secure as there are no viruses for it.

But that's it, I have spent a month trying to do things that I could work out how to do in windows in a couple of days. I was starting to get the hand of the terminal, but really it's just too time consuming.

Thanks anyway.. if someone could just tell me how I can at least view the files I have on here?? : )[/QUOTE]

Catalytic,

I looked up this motherboard at Gigabyte (see [[color="blue"]7VM400M-RZ[/color]](http://www.gigabyte.com.tw/Products/motherboard/Products_Spec.aspx?ClassValue=motherboard&ProductID=1764&ProductName=7VM400M-RZ) and the specifications sheet refers the onboard video to be a '**UniChrome Graphics Engine**'.

The VIA chipset is 'OK' and it will work with linux, but the biggest problem IMHO is the onboard video.

The good news is that you have an AGP 8x/4x slot available.

**IT IS HIGHLY RECOMMENDED THAT YOU**

[LIST=1]
[*]DISABLE ONBOARD VIDEO

[*]PURCHASE AN NVIDIA GRAPHICS CARD [[color="blue"]eVGA 256-A8-N313-LX Geforce FX5500 256MB 128-bit DDR AGP 4X/8X[/color]](http://www.newegg.com/Product/Product.asp?Item=N82E16814130197) ($54) or [[color="blue"]eVGA 128-A8-N319-LX Geforce FX5500 128MB 64-bit DDR AGP 4X/8X[/color]](http://www.newegg.com/Product/Product.asp?Item=N82E16814130207) - $48
[/LIST]
This change alone will solve many of the gaming problems you have been experiencing with linux. It won't allow you to play all Windows games, but  you will be able to play many linux and Windows games, as well as run the cool linux screensavers, and the very cool 3ddesk application that is just not available in Windows.

Don't try linux until you have got a proper 3D videocard like the ones referenced above.......

Good luck!

Dr. Hood

---


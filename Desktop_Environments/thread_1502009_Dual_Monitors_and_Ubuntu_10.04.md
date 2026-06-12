---
title: "Dual Monitors and Ubuntu 10.04"
date: 2010-06-05
forum: Desktop Environments
---

### Post by hawaiian1der on 2010-06-05
First off, I am sorry if this thread is in the wrong spot. I have been looking all over the web and the forums for answers to my questions and, if I found anything, it didn't work. I am wanting to know how to make 2 identical screens, i.e. icons, docks, panels, menus, but be able to use them as if I didn't have the "Same image on all monitors" checked. I have not the slightest clue on how to accomplish this task... If you have any insight, please help :) Much obliged.

---

### Post by cariboo on 2010-06-05
Moved to Desktop Environments, as this was definitely not a Cafe thread.

---

### Post by Austin25 on 2010-06-05
first go to here on your menu, then click here in the window, after you click detect monitors.

---

### Post by hawaiian1der on 2010-06-05
> **Austin25 said:**
> first go to here on your menu, then click here in the window, after you click detect monitors.

I don't want them to copy one another, I just want them to look alike. By that I mean I want to be able to put docky on both screens and the top panel with the menus on both screens.

---

### Post by sites on 2010-06-05
What is your graphics card?

EDIT: Actually i don't think this is possible at all.  Why do you want panels, menus, icons and the like on both screens?

---

### Post by hawaiian1der on 2010-06-05
> > **sites said:**
> What is your graphics card?

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

I know it's in there but not what its called.

---

### Post by hawaiian1der on 2010-06-05
A friend of mine led me to a link : [http://wiki.linuxquestions.org/wiki/XFree86](http://wiki.linuxquestions.org/wiki/XFree86)

That is the only thing that comes close to helping that helps, but after reading it, it sounds like a bad idea to use it.

---

### Post by Phrea on 2010-06-05
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

That's your video card.

---

### Post by hawaiian1der on 2010-06-05
> **Phrea said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

That's your video card.

And, with that said, does anyone know how to make this work?

---

### Post by hawaiian1der on 2010-06-05
I have figured out how to do the docky part, but not the panel part.

---

### Post by hawaiian1der on 2010-06-05
I did something and it made my computer explode! Not literally, of course :) With that aside, I had to reinstall Ubuntu... So I am running on a fresh install. I don't need Docky, I'll just use the panels. So now my question is: How do I make a top and bottom panel on BOTH screens without them mimicking each other, e.g. the "Same image in all monitors" button is NOT checked.

---

### Post by ubun2warrior on 2010-06-05
Generally you can mirror your dektop to diff'rent screens like when one is using an LCD projector. But then the screens mimick(as you say).
There is also an option called remote desktop but for that you need 2 pc's. That is something diff'rent..
What u are trying to do is maybe something more complex like running a server ubuntu and the other pc's connecting to that through the LAN...

---

### Post by hawaiian1der on 2010-06-05
> **ubun2warrior said:**
> Generally you can mirror your dektop to diff'rent screens like when one is using an LCD projector. But then the screens mimick(as you say).
There is also an option called remote desktop but for that you need 2 pc's. That is something diff'rent..
What u are trying to do is maybe something more complex like running a server ubuntu and the other pc's connecting to that through the LAN...

I just have a laptop with a VGA cable and a spare monitor. The spare is above the laptop. All I want is to be able to make them look alike but not them doing the same thing.

With the attached picture, this is what I am trying to say. I want the top to look likt the bottom but not copying the same image. I want to be able to drag a window to the other screen as it does now.

---

### Post by The Recorder on 2010-06-05
I have an nvidia card which has a configuration mode of 'Separate x screen", which I can set for each of my monitors, but I don't think that this is possible with your Intel integrated setup.  It's the graphics card that handles this type of setup - Some cards can do it, some can't.

---

### Post by DaMan05 on 2010-06-05
I have kind of the same question.

I run UltraMon on windows and want the same thing for Lucid. I have my monitors side by side and I want a panel on the bottom of the secondary one that shows the windows open on that monitor.

I know I can do this by adding a new panel and the adding a window list to it. But I can't seem to be able to add a panel to the second monitor. Every time I add one, it adds to the primary monitor and I can't seem to be able to move it.

---

### Post by The Recorder on 2010-06-05
> **DaMan05 said:**
> I have kind of the same question.

I run UltraMon on windows and want the same thing for Lucid. I have my monitors side by side and I want a panel on the bottom of the secondary one that shows the windows open on that monitor.

I know I can do this by adding a new panel and the adding a window list to it. But I can't seem to be able to add a panel to the second monitor. Every time I add one, it adds to the primary monitor and I can't seem to be able to move it.

After you add the panel, open up gconf-editor, go to apps > panel > default_setup > toplevels > "the 'new/extra'" bottom_panel (or top_panel, wherever you added one), and change "monitor" and "screen" from 0 to 1.  Do the same in apps > panel > toplevels > "the 'new/extra'" bottom_panel (or top_panel, wherever you added one).  (Depending on the numbering of your monitors, it could be that you have to change 1's to 0's.)  When you're changing the second set of entries, you should see the panel move to the other monitor.

---

### Post by DaMan05 on 2010-06-05
> **The Recorder said:**
> After you add the panel, open up gconf-editor, go to apps > panel > default_setup > toplevels > "the 'new/extra'" bottom_panel (or top_panel, wherever you added one), and change "monitor" and "screen" from 0 to 1.  Do the same in apps > panel > toplevels > "the 'new/extra'" bottom_panel (or top_panel, wherever you added one).  (Depending on the numbering of your monitors, it could be that you have to change 1's to 0's.)  When you're changing the second set of entries, you should see the panel move to the other monitor.

Thanks :)

After posting that I did some more fooling around in the Nvidia settings and changed the X-screen, twinview and such settings and was finally able to get it set where my mouse would span both monitors and there was a panel already there at the bottom of the second monitor. I then added and window list and boom.

thanks again though :)

---

### Post by hawaiian1der on 2010-06-06
> **DaMan05 said:**
> I have kind of the same question.

I run UltraMon on windows and want the same thing for Lucid. I have my monitors side by side and I want a panel on the bottom of the secondary one that shows the windows open on that monitor.

I know I can do this by adding a new panel and the adding a window list to it. But I can't seem to be able to add a panel to the second monitor. Every time I add one, it adds to the primary monitor and I can't seem to be able to move it.

Was this post just for The Recorder? If not, This did not work for me...

---

### Post by DaMan05 on 2010-06-07
Well, have you gotten both monitors working? If you have, then all you need to do is add a panel to the second one and add all the same stuff to that panel.

I'm a newbie here also, mind you.

---

### Post by hawaiian1der on 2010-06-07
> **DaMan05 said:**
> Well, have you gotten both monitors working? If you have, then all you need to do is add a panel to the second one and add all the same stuff to that panel.

I'm a newbie here also, mind you.

Thats okay. I have the other monitor working, but I can't get the panel part to work...

---

### Post by hawaiian1der on 2010-06-07
> **hawaiian1der said:**
> Thats okay. I have the other monitor working, but I can't get the panel part to work...

I GOT IT! :P Thanks.

---

### Post by DaMan05 on 2010-06-07
> **hawaiian1der said:**
> I GOT IT! :P Thanks.

lol why do so many people do this? it would be great if you could write out what you did to "GET IT" so that anyone else with the same problem can benefit ;)

---

### Post by hawaiian1der on 2010-06-07
> **DaMan05 said:**
> lol why do so many people do this? it would be great if you could write out what you did to "GET IT" so that anyone else with the same problem can benefit ;)

Sorry :P

All I had to do id do apps > panel > Toplevels > panel_0 and edit the monitor.

---

### Post by hawaiian1der on 2010-06-09
I have run into another problem. I have the second monitor above the first one. Because the second monitor is on top in the monitor set up, it makes the desktop default to being on that screen. That also make the icons not appear because the laptop monitor, i.e. the monitor on the bottom, is larger than the second monitor, the monitor on top. Is there any way to make the icons default to the laptop screen, bottom monitor, or make the icons default farther to the middle? Use the attached screenshot to see what I am talking about.

---

### Post by nullvariable on 2010-06-14
I just right click on any panel, choose properties and then uncheck the box for "expand" then you can drag the panel where ever you'd like open the properties and expand it again. It will respect that display from there...

---

### Post by morrcahn on 2010-10-18
So, now that we all know how to do this, how do you go about making it so that your windows won't be maximized over both of your monitors?

---

### Post by d0ti5 on 2010-10-25
Changing the Apps/Panel/Toplevels/Panel(x) only worked on my T-60 laptop *after* I opened the Monitors section in Admin.  Then it worked fine (in 10.10).

---

### Post by morrcahn on 2010-10-26
> **d0ti5 said:**
> Changing the Apps/Panel/Toplevels/Panel(x) only worked on my T-60 laptop *after* I opened the Monitors section in Admin.  Then it worked fine (in 10.10).

Do you mean opening gconf-editor as root, or what do you mean by "Monitors section"?

---


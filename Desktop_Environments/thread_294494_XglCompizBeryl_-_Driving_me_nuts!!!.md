---
title: "Xgl/Compiz/Beryl - Driving me nuts!!!"
date: 2006-11-06
forum: Desktop Environments
---

### Post by Bruegger on 2006-11-06
Been trying to install and run xgl/ compiz and beryl following Paladines guide on [www.Knowledge76.com](www.Knowledge76.com) for the past 3 days. But apart from giving me jagged crazy lines..the screen stalls at black screen with random designs on half it.
Starting beryl-xgl in terminal says:

XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl-xgl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl-xgl: No composite extension

Synaptic shows all packages for xgl, compiz and beryl are installed and upto date.
So whats wrong??

PC configuration is AMD AthlonXP 2000+,NVidia Geforce2 MX Integrated Graphics Is my card too old for it? could have sworn had seen cards older than mine running compiz and beryl.

Can someone give me a solution ordo i need to drop the whole eye-candy idea???

---

### Post by Joe_CoT on 2006-11-06
Try adding this to your xorg.conf and restart X-Window

```
Section "Extensions"
	Option	    "Composite" "1"
EndSection
```

---

### Post by Bruegger on 2006-11-07
Joe_CoT,

You are one smart dude. i finally got some parts of beryl working!!!!!!!
thanks for your advice.
Glad to know my nvidia gpu is supported and finally have those awesome effects.
 I dont see compiz and compiz plugins under gconf-editor though.
PLease tell me how to activate the water effect and the compiz plug-ins.

---

### Post by Joe_CoT on 2006-11-07
compiz-settings ?

---

### Post by Bruegger on 2006-11-07
Uhuh.
I guess i didnt tell you this is my first time with Linux.
But wondering wont compiz or beryl or emerald reflect under gconf-editor???
Read in earlier guides that compiz and its plug-ins, once installed, reflect under apps in gconf-editor???

---

### Post by PriceChild on 2006-11-07
As far as i know... those guides are pretty outdated.

If i were you i'd check out the links in my sig instead.

---

### Post by Bruegger on 2006-11-07
PriceChild,
The guide i followed for my install, [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit) is also the one mentioned in your thread.
And that same guide does refer to gconf-editor where the compiz plug-ins are located.Mine doesnt show anything.
So what am i doing wrong?

p.s. sorry to bother you with these queries but i really like the beryl feel..and want the water and a few plug-ins to work.

---

### Post by Bruegger on 2006-11-08
OKie Guys,
With a lotta searching posts and forums
Finally got Beryl and emerald working. required some editing at the xorg.conf.
As of now in beryl-manager, activating the beryl window ..loads beryl..most beryl plug-ins work except the water effect...also added it to start-up programs..so its working at gnome log-in too.
Emerald does the required theme changing in real time when selected.
They give some awesome effects i havent seen in a long time.

But still not able to see any compiz plug-ins or compiz in gconf-editor

beryl-manager also has some buttons compiz, compiz with COW and metacity.
Not able to see any difference when they are activated so not sure what exactly happens with them.

Anyone know how to load these or the commands to get these working???

---

### Post by Joe_CoT on 2006-11-10
Are you sure you even have compiz installed? Why would you need to switch to compiz over beryl? Beryl has everything compiz does, and you can set it up using the beryl manager

---

### Post by kman14 on 2006-11-10
hey there i seem to be having a similiar, yet slightly different problem.

i installed beryl using this guide:

[https://help.ubuntu.com/community/Co...nstallingBeryl](https://help.ubuntu.com/community/Co...nstallingBeryl)

when i got to the part where it said to type: beryl-manager, into the terminal - my system flickers once, places the red diamond in the system tray and then freezes.

i can move the mouse around but can't open or close anything.

it also comes up with the following:

klmc@klmc-desktop:~$ beryl-manager
klmc@klmc-desktop:~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present

.....and that's it.

then when i restart there is the berryl settings manager and the emerald theme manager in "system" - "admin".

any help would be greatly appreciated - i too am really new to linux.

cheers

---

### Post by thisllub on 2006-11-10
The NVIDIA beta driver crashes GDM with a "No screens found error" for me.

However if I sudo su and run xinit I get a bare bones X system with a terminal that allows me to start Beryl-manager and XFCE-panel.
From there I am OK but for the root login.

Very primitive but at least it works.

I have wasted far too many hours trying to get this simple thing to work seamlessly.

---

### Post by Bruegger on 2006-11-10
Joe_Cot,
Just curious to know what happens when compiz , compiz with COW do when clicked from beryl manager.Something tells me if its given as an option in beryl manager..it would surely reflect some change, wont it?
Checked in synaptic and it shows compiz,compiz-core as installed but no compiz-plugins installed. Tried installing compiz-plugins thru synaptic but no luck.it just doesnt.

kman14,
have u tried modifying your /etc/X11/xorg.conf file???
i had the same problem where XGL was not loading.Modifying the xorg.conf sorted out the issue for me to a huge extent.
btw, what is your graphics card??

---


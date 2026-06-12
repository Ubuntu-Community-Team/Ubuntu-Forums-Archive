---
title: "Assorted Compiz problems under Kubuntu"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by utkjamie on 2007-10-21
I just recently started using Compiz under Kubuntu and am running into several problems. I'm hoping someone can help:

1. On logging into Kubuntu, sometimes Compiz takes random tray icons, puts them into a tiny empty window, and displays them in the upper left hand corner of the screen. These little windows also show up as open applications on the taskbar. Right now, for instance, I've got a window showing "Main Toolbar (Konqueror), one for Power Manager, and another for Adept Notifier -- and each are showing up as open applications in my taskbar, though these are only tiny empty windows. Other times it has been the Amarok icon, Knetwork Manager, etc.

2. Soon after logging into Kubuntu, Knetwork manager triggers the Kde Wallet Service for a password so I can connect to my wireless network. About 50% of the time this window is completely grayed out, preventing me from typing in a password and consequently preventing me from connecting to my router.

Logging into Kubuntu with Compiz is sort of like rolling dice because I really don't know what is going to happen next. I'm not sure if I've done something wrong in setting it up or if these are bugs in Compiz.

I have a bash script triggered by a file in ~/.kde/Autostart. The file contains the following:
```
#!/bin/bash
compiz --replace --ignore-desktop-hints &
sleep 5
emerald --replace --ignore-desktop-hints
```

---

### Post by prince_niceguy on 2007-10-21
ya there are tons of problem which you will face in kubuntu... because compiz is more suitable for gnome rather than kde...

I too broke my head on getting all these things resolved... the best solution is to keep some sleep before starting compiz... that will give sufficient time for other apps to start and come in system tray... 

only problem i think would be adept which will still come as a window...

---

### Post by utkjamie on 2007-10-22
I added a *Sleep 40 *command to the top of the script and that seems to have cleared up the "rogue" system tray icons (at least on the last restart).

There are a few other quirks that I have to deal with, such as window titles and borders disappearing from time to time until I manually run *compiz --replace*.

Let's hope future updates make Compiz integrate better with KDE.

---

### Post by utkjamie on 2007-10-22
Virtual desktops are my biggest gripe right. Here's what I'm experiencing:

1. The taskbar icon for every application opened displays on every single desktop. My purpose in using multiple desktops is to reduce clutter so this is counter-productive. Is there a way to turn this off or is this a bug?

2. Right-clicking on the titlebar of an application and sending the application to another desktop causes it to simply vanish. It doesn't show up on *any* desktop. I suspect the app is being moved to a "real" desktop but Compiz only allows me to see virtual desktops.

3. Compiz seems to disable the default KDE desktop switching shortcuts which means even after disabling virtual desktop navigation in Compiz I am still unable to navigate KDE desktops using shortcut keys.

---

### Post by prince_niceguy on 2007-10-22
for the window decoration you can run the following command instead of compiz --replace

kde-window-decorator --replace

or

emerald --replace

as for the desktops.. it is big pain as gnome, compiz follow same technology for work spaces while kde uses different for the same. some thing related to viewport... not sure which one...

i used to remove the page applet and remove the bottom applet and used to keep avant-window-navigator... which was giving correct representation of the desktops in its pager..

i am waiting for kde4 where these all will be integrated in kde and no more problem with compiz...

---

### Post by tjk on 2007-10-24
I have most of these issues as well.  One problem that I get that you didn't mention is a larger screen resolution that extends beyond the size of my monitor.  When I login it's about 1 in 4 that I get everything the way that it should be ... very frustrating.  As well, I have only put the command "compiz --replace" in my autostartup and yet I am running emerald (I don't have to use the command "emerald --replace", as indicated in a prior msg)  Hopefully some of these bug will be dealt with by the Kubuntu team ... I really prefer KDE rather then Gnome.

---

### Post by jaygo on 2007-10-26
I've also had the tray icons appear floating in the upper left corner but I don't run compiz or beryl. I think it happens when kdm crashes or malfunctions.

You can stop the taskbar from displaying tasks from all desktops. Right click taskbar > configure panel > taskbar > uncheck "show windows from all displays".

I'm not surprised you're having compiz probs ... you can still get a lot of eye candy out of kdm. Even so, I may start experimenting too. 

GLHF

---

### Post by lgambett on 2007-10-26
Hi folks,
The most annoying problem I found using Compiz over my Kubuntu 7.10 is that using any OpenOffice application the window border disappears and the screen starts flashing... I can recover only forcefully closing Oo (i.e. sudo kill xxxx)

Any ideas ?
Thnx,
Luca

---

### Post by zeltak on 2007-11-07
had the same problem

this will solve it:

[http://ubuntuforums.org/showthread.php?t=600245&highlight=compiz+open+office](http://ubuntuforums.org/showthread.php?t=600245&highlight=compiz+open+office)

zeltak

---

### Post by reverend_HH on 2007-11-11
i dont really have a big deal with the startup programs showing up on the upper lefthand side since i really only have kmix, seems the more u have the bigger chance u have of that happening. my main concern was what utkjamie mentioned about the windows showing for all the desktops, i double checked this and when u dont run compiz and go to configure panel, the option is there. when u have compiz running and try the same it wont even have that as an option at all, it just disappears. i remember with beryl this wasnt a problem but i think thats when i had it on ubuntu not kubuntu.

---

### Post by shawnc_nmb on 2007-11-11
Wow,I must admit I have never had so many problems in my life until,. I upgraded to Gutsy and try'd to use Compiz-Fusion.   I don't understand honestly,  I personally used KDE with Beryl for the last year and had no problems at all.  Everything was perfect,  then I upgraded from Fiesty to Gutsy and that completely killed my OS.   So  I added a new set of partitions and Installed a Brand-New Kubuntu Build since my old build was messy anyway.   Now,  I tryd following various tut's on the forums and I had it working earlyer today,  then I rebooted and now I'm stuck without titlebars anywhere.  

Once i manage to disable Compiz and get Kwin back up, I will edit this post with the tuturails I followed and what happened afterwards.


  Ok, I will edit this post afew times as I locate the different paths I have tryed to make this work.  But basicly, After a Fresh Install of Gutsy, I installed the CCSM and some things worked for awhile.   But I did not have all the effects, I only had
acouple of the plugins,  and I really wanted the Expo Plugin and atleast the Show Desktop Plugin plus afew of the normal ones i liked in Beryl.   Afterwards,  I have tryd to follow 3 or 4 different methods of doing this, each time completely removing the files afterwards.  

ATM,  I have got a working Compiz in that I can Move the Desktop, use the Expo, etc  But I have No Title Bars at all. 


I will edit this post with the links to where I have followed the tuts as soon as I locate them.

---

### Post by screaminj3sus on 2007-11-11
In every KDE distro I've used Compiz has been complete crap in KDE, kubuntu being the worst. Beryl seems to run better in KDE. my computer suffers a massive performance drop runing compiz in KDE, it slows down my whole pc, while in gnome it is fine. I'd wait until KDE4 with it's native compositing support.

---

### Post by shawnc_nmb on 2007-11-11
> **screaminj3sus said:**
> In every KDE distro I've used Compiz has been complete crap in KDE, kubuntu being the worst. Beryl seems to run better in KDE. my computer suffers a massive performance drop runing compiz in KDE, it slows down my whole pc, while in gnome it is fine. I'd wait until KDE4 with it's native compositing support.


I had It running for  1 Day, until I rebooted and I have no clue what I did to make it work, and even less of a clue how I broke it but it ran execellent while I had it.  Can you even get Beryl for Gutsy,I might start looking for information down that route.  This entire upgrade to gutsy has been a complete waste of time so far in my boook.

---

### Post by reverend_HH on 2007-11-11
> **shawnc_nmb said:**
> Wow,I must admit I have never had so many problems in my life until,. I upgraded to Gutsy and try'd to use Compiz-Fusion.   I don't understand honestly,  I personally used KDE with Beryl for the last year and had no problems at all.  Everything was perfect,  then I upgraded from Fiesty to Gutsy and that completely killed my OS.   So  I added a new set of partitions and Installed a Brand-New Kubuntu Build since my old build was messy anyway.   Now,  I tryd following various tut's on the forums and I had it working earlyer today,  then I rebooted and now I'm stuck without titlebars anywhere.  

Once i manage to disable Compiz and get Kwin back up, I will edit this post with the tuturails I followed and what happened afterwards.


  Ok, I will edit this post afew times as I locate the different paths I have tryed to make this work.  But basicly, After a Fresh Install of Gutsy, I installed the CCSM and some things worked for awhile.   But I did not have all the effects, I only had
acouple of the plugins,  and I really wanted the Expo Plugin and atleast the Show Desktop Plugin plus afew of the normal ones i liked in Beryl.   Afterwards,  I have tryd to follow 3 or 4 different methods of doing this, each time completely removing the files afterwards.  

ATM,  I have got a working Compiz in that I can Move the Desktop, use the Expo, etc  But I have No Title Bars at all. 


I will edit this post with the links to where I have followed the tuts as soon as I locate them.

did u by chance happen to add the line: Option         "AddARGBGLXVisuals" "True" to your xorg.conf? this usually fixes the no titlebar issue. u add it in the section "screen" if you already havent. not sure if anything else needs to be added.

---

### Post by shawnc_nmb on 2007-11-11
no,  I finally managed to get everything working again!


Ok,  first, I cleaned out everything Ihad that was for Compiz and Emerald, removed all of them.

Next, I Installed The Bare Mins

[php]
sudo apt-get install compiz compizconfig-settings-manager emerald 
[/php]

I might have forgotten one package above, but I think that was all 4 of them

Open CCSM ( alt-F2 type "ccsm" )

Now,Look for [b]Window Decoration[b]

Look through the settings until you find **Command**  then Add

emerald --replace


And thats how I got it working for me.

---

### Post by dope.smugglaz on 2007-11-16
Its Easy

If you are not happy with Compiz and facing problems

1) sudo apt-get remove compiz

This shall remove the compiz from ur PC

2) sudo apt-get install kubuntu-desktop

All your problems will be sorted.


dope.smugglaz
[email]dope.smugglaz@gmail.com[/email]

---

### Post by Etheris on 2008-02-27
I am having problems setting up Compiz-fusion and emerald on my kubuntu 7.10 box (amd64, nvidia gforce).  Compiz is installed correctly (I think) and the graphical functions work fine, but I cannot get my window title bars to be displayed correctly.  When I start compiz ("compiz --replace") the screen restarts and I loose my title bars.  I have also noted that before I start compiz the displayed title bar is being taken from the KDE windows decorator instead of emerald and, even though I can open the emerald manager, emerald will not effect the menu display.  My guess is that when I activate compiz it is looking for an emerald theme, and since it is not active it displayes no menu.  Also, when I attempt "emerald --replace" it produces errors and stalls in the terminal.

I have tried changing my nvidia options, which appears to be working fine and I have also tried changing visual and rendering options in xorg......along with just about everything else I have been able to find online.  Please help if you can.

---


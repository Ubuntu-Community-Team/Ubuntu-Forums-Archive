---
title: "how do i install beryl?"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by shortybookit on 2007-09-20
i have ubuntu 7.04

---

### Post by overdrank on 2007-09-20
> **shortybookit said:**
> i have ubuntu 7.04

Can you tell us your graphics card?

---

### Post by Maestro23 on 2007-09-20
Feisty Starter's Guide (3d-Desktops): [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Compiz_.2F_Desktop_Effects](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Compiz_.2F_Desktop_Effects)

---

### Post by LowSky on 2007-09-20
its under synaptic package manager , just type beryl. dont forget to install the beryl-manager as well

---

### Post by XXBen on 2007-10-22
actually NO, its not under the package manager, i've looked countless time. I have downladed Beryl to my desktop, now what do i do with that package? do i put it in a diferent folder? cause when i type "sudo apt-get install beryl" it say's package not found. Can anyone help me get this working?

---

### Post by dangerpl on 2007-10-22
I would recommend compiz-fusion instead which is a combination of both compiz and beryl. and if you're going to upgrade to gutsy you have all the packages ready to install.

---

### Post by XXBen on 2007-10-22
How would i upgrade to Gutsy?

---

### Post by dangerpl on 2007-10-22
You can do it in a number of ways. First way: Go to System/Adminstration/Update Manager. New version should be available, so click upgrade. Second way: Download the alternative CD from ubuntu website, burn, and run the upgrade. Third: Download the regular version of 7.10 and do a clean install

---

### Post by dangerpl on 2007-10-22
Before you do any of these BACK UP YOUR DATA! It is very very important!

---

### Post by XXBen on 2007-10-23
7.10 is the version that i have installed. But Beryl is not in the packages to install. did i do something wrong?

---

### Post by overdrank on 2007-10-23
> **XXBen said:**
> 7.10 is the version that i have installed. But Beryl is not in the packages to install. did i do something wrong?

HI and beryl and compiz have rejoin so what is now compiz-fusion! :KS

---

### Post by ItsMitsHere on 2007-10-23
Dear xxBen u need not install beryl if you have ubuntu 7.10 (GG). compiz-fusion works out of the box on GG. you wil get everything in compiz-fusion that u were going to install beryl for. if compiz does not run at startup, u can run by typing **compiz --replace** in terminal

---

### Post by GMFreak8 on 2007-10-23
> **ItsMitsHere said:**
> Dear xxBen u need not install beryl if you have ubuntu 7.10 (GG). compiz-fusion works out of the box on GG. you wil get everything in compiz-fusion that u were going to install beryl for. if compiz does not run at startup, u can run by typing **compiz --replace** in terminal


I just want to thank you for the huge tip.  I've been trying to get compiz-fusion working, I've been searching everywhere for why it wasn't.  That simple command did the trick.  How are people supposed to know this stuff?  Why doesn't it start automatically?  I installed the Emerald Theme Manager, what other theme managers are there?  is there one built in so I didn't have to download Emerald manager?

---

### Post by Het Irv on 2007-10-23
> **GMFreak8 said:**
> I just want to thank you for the huge tip.  I've been trying to get compiz-fusion working, I've been searching everywhere for why it wasn't.  That simple command did the trick.  How are people supposed to know this stuff?  Why doesn't it start automatically?  I installed the Emerald Theme Manager, what other theme managers are there?  is there one built in so I didn't have to download Emerald manager?
Compiz-Fusion does not start automaticly because not all computers can handle it.  The way I got it to work was the compiz manager.

> sudo aptitude install compizconfig-settings-manager

---

### Post by rudeboyskunk on 2007-10-23
> **GMFreak8 said:**
> How are people supposed to know this stuff?  Why doesn't it start automatically?

That's the number one question people new to Linux ask.  There isn't an answer, either.  But just keep asking questions.  That's the best way.

Your problem is probably that you don't have all your repositories enabled.  Go to System>Administration>Software Sources, and enable all the repositories.  Then go to Synaptic Package Manager, search for Beryl, and install the appropriate packages.

Or upgrade to Gutsy, and it comes as default (AS LONG AS YOUR GRAPHICS CARD CAN HANDLE IT, you should post your graphics card info here).

---

### Post by GMFreak8 on 2007-10-23
Thanks guys.  I have gutsy installed, and I can get compiz-fusion running if I run the command "compiz --replace" in ther terminal.  My problem now is the fact that when i try to change themes with the Emerald Theme manager, nothing happens.  I'm stuck with the previous compiz-fusion theme.

My graphics card is an ATI radeon 9550 256MB.  I'm running fglrx driver.

I guess my main issues are not being able to switch themes, and how I can make compiz-fusion stay enabled.  I'm 99% positive my graphics card can handle it.

---

### Post by GMFreak8 on 2007-10-23
To expand on my last post....

If I select the theme that I want in emerald theme manager, and then I run the compiz --replace command, the theme works successfully.  I shouldn't have to run that command each time though. 

Here's what the terminal says when I run the command:

> kyle@kyle-ubuntu:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


---

### Post by yogo on 2007-10-23
I had Beryl on Feisty and it performed flawlessly, I have installed Gutsy and I have Compiz but it sucks out of the box, It seems like I have gone back to a dinosaur PC.

Granted I do not have a graphics card which I am sure would help in Gutsy but I was  pleased with how Beryl performed in Fiesty. I just have onboard  graphics with a Dell 2400. 


I almost want to go back to Feisty as Gusty does not perform well.

Gutsy removed the Beryl settings manager so I would really like to get Beryl back but their wiki is down.

Is there a Guide somewhere?


TIA

---

### Post by ItsMitsHere on 2007-10-24
> **GMFreak8 said:**
> To expand on my last post....

If I select the theme that I want in emerald theme manager, and then I run the compiz --replace command, the theme works successfully.  I shouldn't have to run that command each time though. 


if you want to start compiz by default, go to **system>preferences>sessions** and in the popup window in start-up tab (the first one) click the add button with PLUS sign on it. then in thenew popup box, in the second box (command) type compiz --replace. in other boxes you can type whatever you like. this will make sure that compiz starts at start up. this way you will not need to do compiz --replace every time!!!

CHEERS!

---

### Post by ItsMitsHere on 2007-10-24
> **yogo said:**
> I had Beryl on Feisty and it performed flawlessly, I have installed Gutsy and I have Compiz but it sucks out of the box, It seems like I have gone back to a dinosaur PC.

Granted I do not have a graphics card which I am sure would help in Gutsy but I was  pleased with how Beryl performed in Fiesty. I just have onboard  graphics with a Dell 2400. 


I almost want to go back to Feisty as Gusty does not perform well.

Gutsy removed the Beryl settings manager so I would really like to get Beryl back but their wiki is down.

Is there a Guide somewhere?


TIA

Dear TIA, 

you would probably like to update your system to work flowlessly and also you can cleane the system by **sudo apt-get clean** and also fix minor problems with **sudo apt-get --fix-missing** before update/upgrade. If you want to change settings for compiz you should run **ccsm** at terminal which will start compizconfig setting manager just like beryl settings manager. if you really wish to get beryl again then remove compiz completely (ask me if you really dont know how to remove compiz) and then install beryl (sure! you have done it before?) but i would still suggest that compiz is much more stable then beryl. stick to gutsy for a little bit and it will start working flowlessly...

CHEERS!

---


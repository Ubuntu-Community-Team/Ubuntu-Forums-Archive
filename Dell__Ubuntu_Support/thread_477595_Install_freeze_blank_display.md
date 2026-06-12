---
title: "Install freeze blank display"
date: 2007-06-18
forum: Dell  Ubuntu Support
---

### Post by dbrose1 on 2007-06-18
I have down loaded and burned the Ubuntu 7.04. When I booted the CD on my Dell laptop the boot screen came up and I choose to boot Ubuntu and install. After a couple of status bars the screen went blank. I rebooted and tried again same result. I rebooted and ran the media check. The media check was good 

The laptop is an E1505 with XP loaded by dell. About the only other software I added was OpenOffice for windoze.  I did not repartition the drive I understand it can be done at the time of install. I was going to share the one drive with XP an Ubuntu as a duel boot. 

I have used and install Fedora on a PC with a single drive as well as separate  drive all on desktop units. I wanted to use Ubuntu on this laptop as now Dell will install it at the factory.

Do I need to repartition the drive before attempting to install?  

Any help is appreciated

---

### Post by dbrose1 on 2007-06-18
I have down loaded and burned the Feisty 7.04. When I booted the CD on my Dell laptop the boot screen came up and I choose to boot Ubuntu and install. After a couple of status bars the screen went blank. I rebooted and tried again same result. I rebooted and ran the media check. The media check was good 

The laptop is an E1505 with XP loaded by dell. About the only other software I added was OpenOffice for windoze.  I did not repartition the drive I understand it can be done at the time of install. I was going to share the one drive with XP an Ubuntu as a duel boot. 

I have used and install Fedora on a PC with a single drive as well as separate drives. All on desktop units.

I chose Ubuntu as Dell will now install Ubuntu from the factory.

---

### Post by bapoumba on 2007-06-18
Threads merged and moved to "Ubuntu Dell Support".

---

### Post by neptho on 2007-06-19
What video card is it using?  There's: Intel onboard, ATI, and NVidia cards available for this system.

---

### Post by dbrose1 on 2007-06-19
I do not know the video card that is installed. I do not have the laptop here and will check the video card when I get a chance this evening. 

That being said what can I do with the knowledge of what video card is installed?

---

### Post by dbrose1 on 2007-06-19
The video card is an ATI  Mobility Radeon X14000

---

### Post by dbrose1 on 2007-06-24
OK we are in business. I did an alternate install. I even had the installer repatition the harddrive and all went smooth. until the system need to start blank screen.

The fix

type:  control alt F1 to get a command prompt

type: wget [http://mylittleubuntuguide.com/files/ati](http://mylittleubuntuguide.com/files/ati)

sudo chmod +x ati

./ati

 a menu shows up to pick the screen resolution 

X started an all seems  well 

Thanks for the help

---


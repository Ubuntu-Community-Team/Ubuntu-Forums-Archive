---
title: "Using Gnome Shell, computer crashed and now command line appears before login screen"
date: 2009-11-04
forum: Desktop Environments
---

### Post by Hobbsilla on 2009-11-04
Hey. I update to 9.10 a few days ago and I hadn't experienced any major bugs except when I used Gnome Shell (2.28 ). Just today I was using Gnome Shell and Firefox froze my computer so I Force Quit it and tried to open again and my computer crashed. When I rebooted one of two things happened:

1. The silver ubuntu icon appears and then the screen goes black
2. The silver ubuntu icon appears and then this line of text appears that says "type help to show list of commands" and I don't have access to my login screen. I'm currently using XP (and don't want to be I don't have virus protection and would like to be back on ubuntu). To make matters worse I had just gotten done downloading the Ubuntu 9.10 desktop iso file so I could make a Live CD. I was in the process of burning it but my computer crashed before it finished and I don't have anymore CDs. Does anyone have any recommendations for me? 
I've been having the worst of luck with technology this week outside of computers.

---

### Post by madmax1735 on 2009-11-05
u can choose the recovery mode from the grub menu, or u can directly log into the command line thing tht u r getting now.

after that

```
sudo update-alternatives --config x-window-manager
```

choose "metacity" from the list of avilable options

**reboot and check if this gets u bk the gui**

if it doesnt 

then remove gnome-shell depending on how u installed it.

if u installed it from karmic repos then 

```
sudo apt-get remove gnome-shell
```

or if u did the build urself u can just delete the folders where u install it.

hope this helps

luck

---

### Post by coffeecat on 2009-11-05
Agreed about booting into recovery mode, but you've experienced an unclean shutdown. The filesystem may need repairing. Try booting into recovery mode and running a "fsck" first. Post back if you need help.

---

### Post by Hobbsilla on 2009-11-05
Sweet. I'll try this out in and get back to you in a few hours. So thankful.

---

### Post by Hobbsilla on 2009-11-05
Hmm so now I went to the Recovery mode on my grub menu and this blue BIOS looking screen came up with a series of options. I chose Drop root shell with networking. Should I still run the commands you recommended (to Madmax). Okay so I entered in the code and I rebooted it worked thank you so much.

---

### Post by madmax1735 on 2009-11-06
u r always welcome :)

---


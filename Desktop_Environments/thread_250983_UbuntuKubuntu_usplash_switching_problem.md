---
title: "Ubuntu/Kubuntu usplash switching problem"
date: 2006-09-04
forum: Desktop Environments
---

### Post by khedron on 2006-09-04
Ok, I have Ubuntu desktop, but I installed the kubuntu-desktop package in Synaptic. You know, to fiddle around. I wanted to keep my desktop setup the same, so I selected gdm for the desktop manager when a choice popped up during installation.

However, the bootup splash screen is the Kubuntu one, and the mouse icons etc only become GNOME styled when I log on.

Is there a way to replace the splash screen with the default? 

And where can I find the menu to use the KDM instead of the GDM when I get round to trying it out? 

Instructions on editing a config file would be fine answers to either question - in fact, I would prefer them.

---

### Post by baldy1324 on 2006-09-04
to change splash screens try ```
sudo apt-get remove kubuntu-artwork-usplash or ubuntu-artwork-usplash
``` which everyone one you want to remove. then run ```
sudo dpkg-reconfigure kubuntu-artwork-usplash or ubuntu-artwork-uslash
``` for the one you want.

to replace kdm for gdm or vice-versa
run
```
sudo dpkg-reconfigure gdm
``` then select either gdm or kdm.
:)

---

### Post by khedron on 2006-09-06
Thanks for the help.

I removed kubuntu-artwork-usplash and reconfigured ubuntu-artwork (I couldn't find ubuntu-artwork-usplash). This causes the shutdown screen to be the Ubuntu one, but the startup screen to be the Kubuntu one. Any ideas on how to fix this?

WRT Configuring kdm and gdm, my kdm won't log in. It accepts my password, blues the screen and then returns me to the login prompt. I can get into a kde session using GNOME login, but it would be nice to get everything working.

---

### Post by user1397 on 2006-09-06
try the bottom part of the first post of the first link in my signature. i.e.[SIZE=2][ this]("http://ubuntuforums.org/showthread.php?t=205002")[/SIZE] one

---

### Post by hellfried on 2006-09-06
> **erik1397 said:**
> try the bottom part of the first post of the first link in my signature. i.e.[SIZE=2][ this]("http://ubuntuforums.org/showthread.php?t=205002")[/SIZE] one

i read the thread that u pointed to and got the 'There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.' messsage when i do 'sudo update-alternatives --config usplash-artwork.so'. i poked around in 'system > administration > login window' but can't find anything that looks as if it can change the kubuntu splash screen that i have for my gnome dapper. any help would be appreciated.

---

### Post by user1397 on 2006-09-13
> **hellfried said:**
> i read the thread that u pointed to and got the 'There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.' messsage when i do 'sudo update-alternatives --config usplash-artwork.so'. i poked around in 'system > administration > login window' but can't find anything that looks as if it can change the kubuntu splash screen that i have for my gnome dapper. any help would be appreciated.did you ever try doing the command ```

sudo dpkg-reconfigure linux-image-`uname -r`
```

---

### Post by JayTee on 2006-09-14
I had the same problem. I tried baldy1234's solution but had no luck. What I did to fix it was this.

sudo dpkg-reconfigure gdm
then from the program I chose kde and restarted.
NOTE: you'll get the kubuntu login screen. "Don't Panic!" as the late Douglas Adams would say!
next step:
sudo apt-get remove ubuntu-desktop 

you'll need to restart  yet again 
next step
sudo apt-get install ubuntu-desktop
then do this
sudo dpkg-reconfigure gdm
choose gdm and hit enter
logoff and from the menu button on the kde login screen choose restart x-server.

Best of luck, hope this works for you! Keep in mind I'm still a newbie to Ubuntu/Kubuntu but this worked for me.

---

### Post by Messire on 2006-09-14
I was looking for the same issue and I found this thread:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

No need to uninstall anything.

Great, isn'it?

---

### Post by user1397 on 2006-09-16
> **Messire said:**
> I was looking for the same issue and I found this thread:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

No need to uninstall anything.

Great, isn'it?hmm isn't it weird how that's the *exact* solution i suggested from the beginning. #-o

---


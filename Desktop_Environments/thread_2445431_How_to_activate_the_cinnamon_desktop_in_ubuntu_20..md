---
title: "How to activate the cinnamon desktop in ubuntu 20.04 (currently on Gnome)"
date: 2020-06-14
forum: Desktop Environments
---

### Post by Ranbunta_Bantubunt on 2020-06-14
Howdy, sorry for the basic question. 

I am working with a recently installed Ubuntu 20.04, with the default Gnome DE. 

I have done "sudo apt install cinnamon-desktop-environment" and this operation appeared to succeed. according to instructions such as this guide:

[https://linuxconfig.org/ubuntu-20-04-cinnamon-desktop-installation](https://linuxconfig.org/ubuntu-20-04-cinnamon-desktop-installation)

Actually, I'm not even sure why that's a "guide" as they just say, run apt install for cinnamon then reboot. But it does say that, if you do this, you will find cinnamon to be an option on reboot.

I've done this but I notice no change at all from my usual gnome DE. I am coming back to linux after a long hiatus, I never used a GUI before, my work with linux was purely command line in the past. I'm not sure what the "bootstrapping" order is so to speak when the system boots up, how it winds up launching one DE versus another. 

At any rate, if someone could let me know if there are any additional steps I should take to get Cinnamon installed/working, would be appreciated.

I also see a "cinnamon remix" distro of ubuntu available ([https://ubuntucinnamon.org/](https://ubuntucinnamon.org/)), perhaps I should download that? I am going to be installing ubuntu on a new laptop soon so perhaps on the new on I could just start from that distro. It seems to be basically ubuntu, but with cinnamon as the DE, and some theme tweaks. Worth trying? They don't really give a compelling case for why their distro is different/better than just installing any ubuntu distro and then installing cinnamon, at least on the website. But since I am doing a new install anyway and I didnt get cinnamon working yet perhaps I might as well use that.

Thanks

---

### Post by deadflowr on 2020-06-14
To use the new desktop you need to select it at the login screen.
At the login screen, when you select your user, before you enter your password there should be an icon in the bottom right area of the login screen.
This should give the option to choose which desktop session to run.
Choose the desktop you want and then enter your password.

---

### Post by Ranbunta_Bantubunt on 2020-06-14
Thanks... the part I was stuck at was, AFTER the user name is selected, but BEFORE the password is entered. I was expecting the icon to be there at the very beginning, before I selected my username. Now I see it! Thanks

EDIT: Actually I think there is something else also going on here, maybe related to hibernation. I was able to see the icon once after reading the above post. Then the screen turned black after the machine was left idle, I guess some kind of timeout. When I hit a key to bring the login page back up again, the icon was gone! I took a picture just so I can prove the icon was not there any more :). 
This again was while it was prompting for the password, when the icon should have been there. 

I tried to reproduce this again but I have not been able to. However for sure, on at least one occasion that icon did disappear when it was supposed to be there, when I woke the laptop from a blacked-out screen state. Sorry that I dont know how to reproduce this, but some kind of quirkiness seems to be hiding there somehow.

---

### Post by CelticWarrior on 2020-06-14
It won't be there if you're unlocking or waking up from suspension, obviously, because you're already logged in, you're just unlocking the running session.

---

### Post by Ranbunta_Bantubunt on 2020-06-14
>It won't be there if you're unlocking or waking up from suspension,  obviously, because you're already logged in, you're just unlocking the  running session.

Hmmm.... I hadn't thought that is what was going on, but now that you mention it, it must have been that.

---

### Post by CelticWarrior on 2020-06-14
You need to log out first and then you'll be able to select a different desktop to log in with.

---

### Post by Ranbunta_Bantubunt on 2020-06-15
BTW just in case it helps someone else, this is the command to run to set cinnamon as the default (so you dont have to choose it each time you log on)

```
sudo update-alternatives --config x-session-manager
```

It took me a while to google and figure that out, so maybe other people who hit upon this thread may also want to do that too.

Thanks for the help everyone

---

### Post by michael2009 on 2020-06-24
Just noticed and read this thread. I am surprised you needed reset the login. With my experience of Ubuntu, having installed various Desktop Environments on top of the original one, after choosing a DE and logging in from the login screen, subsequent reboots will automatically be set to the most recently used choice. With the automatic login setting, the system will just boot directly in to the DE you were previously logged into. If you have been away from linux and ubuntu for a while, it's going to take a little time for you to get acquainted with it again. That's my guess anyway.

---


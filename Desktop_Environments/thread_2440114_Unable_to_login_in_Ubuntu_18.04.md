---
title: "Unable to login in Ubuntu 18.04"
date: 2020-04-06
forum: Desktop Environments
---

### Post by warhawk472 on 2020-04-06
I am unable to login to Ubuntu because Ubuntu default gnome login screen is not coming instead some other type of login screen is coming which completely black with one dialogue box on it which says welcome to myusername and then an option for login with Ubuntu logo on right side.
After I write my username and password the dialogue box disappear and reappear again but nothing happens.

I can go into grub recovery menu and has access to root shell prompt and other options in recovery menu. But I am unable to reach login screen.

Edit:- now after uninstalling lightdm desktop manager and reinstalling it i can now see my login screen with username and password dialogue box but entering password result in blank screen and the same password screen pop up again.

---

### Post by Frogs Hair on 2020-04-06
Do you have more than one desktop environment installed ? I ask because the default for gnome is gdm and not lightdm.

---

### Post by CatKiller on 2020-04-07
> **warhawk472 said:**
> After I write my username and password the dialogue box disappear and reappear again but nothing happens... 

...now after uninstalling lightdm desktop manager and reinstalling it i can now see my login screen with username and password dialogue box but entering password result in blank screen and the same password screen pop up again.

It's not a login problem. You're technically logging in fine, it's just that your desktop environment is crashing straight away and the first thing you see when it restarts is the login screen. Graphics drivers are the usual culprit for that behaviour. 

It's not a solution, but it might stop you chasing dead ends.

---

### Post by warhawk472 on 2020-04-23
Well, I was not having ligtdm when the problem started but I installed it from root shell from within the grub recovery menu because I thought the problem was with gdm but I was wrong.
The original problem was with Graphics drivers as mentioned by @CatKiller.

Also, the links provided by @Frogs Hair were very helpful and also now I know how to enable firewalls in ubuntu which I thought would be enabled by default.

To solve the problem I made a bootable pen drive and started a live session of Ubuntu from where I was able to back up my data on an external device and then I reinstalled the ubuntu for a fresh start. (I don't mind reinstalling the OS again and again as long as my data is saved).

Also now I am using ubuntu 20.04 LTS and it supports my AMD graphics driver by default.

Thank you, everyone, for there help and support.

---


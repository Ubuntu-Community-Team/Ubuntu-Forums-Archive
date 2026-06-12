---
title: "gdm background change"
date: 2011-06-15
forum: Desktop Environments
---

### Post by boblizar on 2011-06-15
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

then log out

then set background image appropriately

then 

sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

to stop the background dialog from comming up

who came up with this mess????  this is quite possibly the ugliest solution i have ever seen to a linux problem.  why is the background dialog hidden in the first place?  why does the poor user have to be stuck in a super ugly purple background @ gdm?  little things like this drive people AWAY from distributions.

---

### Post by FormatSeize on 2011-06-15
> **boblizar said:**
> ```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```
 
then log out
 
then set background image appropriately
 
then 
 
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```
 
to stop the background dialog from comming up
 
who came up with this mess???? this is quite possibly the ugliest solution i have ever seen to a linux problem. why is the background dialog hidden in the first place? why does the poor user have to be stuck in a super ugly purple background @ gdm? little things like this drive people AWAY from distributions.
 
I happened to have given this solution earlier today. Personally, I think it's pretty cool, but to each his/her own. 
 
I actually have no idea "who came up with this mess". Seems pretty brilliant to me, though. But it probably didn't happen because a few developers somewhere thought, "Hey, it'd be cool, and pretty obvious to anyone that comes from Windows, which does everything for you, that you should have to type a bunch of commands that operate on obscure directories to change the login background."
 
It came about, most likely, as a workaround. If someone is driven away from Linux because there are many different ways of getting to a desired end, all of which aren't going to be directly apparent, then so be it. Eventually, even if there was a giant icon labeled "CLICK TO CHANGE THE LOGIN SCREEN" in the center of the desktop, those users would likely still find something else to drive them away from Linux. Linux, being a highly configurable system which assumes you know something about what you are doing (or care about what you are doing), allows these options, just as a programmer has many different ways to write a program; some options being more complex than others. 
 
This is only one way to change the login screen. I'm sure there are others. Or, future releases will include it for those that seem to care more about seeing a flower or a rocket at the login screen more so than they care about whatever it is that they are logging in to do.

---

### Post by boblizar on 2011-06-16
i would rather manipulate symlinks behind the scenes.

---

### Post by nomko on 2011-06-16
Do you mean the background of the login screen?? There's a needy tool for it to change that: GDM2setup (if you're using GDm2). It can be found here: [https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)

---

### Post by wildmanne39 on 2011-06-16
Hi, I just installed ubuntu tweak and in about 30 seconds I changed my login screen to a very cool background I had in my picture folder.

---


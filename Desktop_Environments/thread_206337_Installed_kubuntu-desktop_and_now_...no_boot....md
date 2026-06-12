---
title: "Installed kubuntu-desktop and now ...no boot..."
date: 2006-06-29
forum: Desktop Environments
---

### Post by lonegeek on 2006-06-29
So i installed kde with kubuntu-desktop , did ctrl alt backspace. Change my session to KDE. Changed some settings..it required a reboot.. Did that ..now when i boot i get some message similiar to loading back services (?)  followed by /etc/rc.local display defualt manager

Is there any way to completely remove KDE and make gnome back to default?

Please help soon..............

Zach

---

### Post by harishg on 2006-06-29
Assuming you type in your id and password everytime, in the lower left corner of the login screen select gnome from sessions and when you type your login name and password it will ask if you want to make gnome the default say yes.Then login gnome and use synaptic to remove kubuntu-desktop.

---

### Post by lonegeek on 2006-06-29
Actually i couldnt get that far... I just selected differnet kernal which allowed me to boot.. But x server was a bit messed up.. I changed to kde...then back to gnome it was fine...

I will reboot in a bit...But as of now i think its fine.....

How can i completely remove all things that got installed from kubuntu-desktop
All the weird kde apps that are useless unless in kde really....are pointless to have installed... 

I want to remove it all..not just remove kde from session options...

zach

---

### Post by lonegeek on 2006-06-29
Ubuntu only boots when i select previous kernel....

If not i get

running local boot scripts (/etc/rc.local) defualt display manager

It just hangs on that

Im thinking something is interfering with kde...but how do i remove it all completely?

zach

---

### Post by harishg on 2006-06-29
You can do it in synaptic.In synaptic select the status option from lower left corner.Then look for the installed softwares and remove the unnecessary kde files.

---

### Post by lonegeek on 2006-06-30
Hmm THats fine and all...but i've installed alot of things.... So its nearly impossible to go through it all and remove kde things.. Not to mention the fact that some are neccasary to run certain apps.....

---

### Post by harishg on 2006-06-30
If you are removing a package which is a dependency of some other package synaptic will warn you about removing the other pakcage too.In that way you can make sure you do not break the dependency,

---


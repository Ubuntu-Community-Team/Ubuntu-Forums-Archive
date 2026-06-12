---
title: "Monitor displays &quot;Out of Range&quot; but I can see logon screen and cannot use keyboard"
date: 2008-12-20
forum: Desktop Environments
---

### Post by deki on 2008-12-20
I just installed Ubuntu and I can't get it to work. The screen displays "Out of Range" at first, however after a minute it shows the logon screen. However, I cannot use the mouse nor the keyboard to type my user name. However, I am able to go into a session if I press the alt+ctrl+f1. I'm thinking it's something with the resolution...how can I change the screen resolution in the command line? Any help would be very appreciated

---

### Post by overdrank on 2008-12-20
> **deki said:**
> I just installed Ubuntu and I can't get it to work. The screen displays "Out of Range" at first, however after a minute it shows the logon screen. However, I cannot use the mouse nor the keyboard to type my user name. However, I am able to go into a session if I press the alt+ctrl+f1. I'm thinking it's something with the resolution...how can I change the screen resolution in the command line? Any help would be very appreciated

Hi and welcome, is this a wireless keyboard and mouse, or usb maybe?
You can try and boot into recovery mode, which is usually the second choice from the grub. Then you can choose the xfix option to correct graphics issue. You should be given a choice to boot normally.

---

### Post by deki on 2008-12-20
No, none of it is USB. I actually did go to the "try to fix x server" but nothing really happened. I didn't really change anything though....can you tell me more about this, since I'm a bit unfamiliar with it. Thanks

---

### Post by professorbell on 2008-12-20
Actually i am having very similar problem, the gui looks happy and healthy, but the gui is nonresponsive to keyboard and mouse. the shortcuts to tty1-6 all work, and they are all fully functional. 

I don't know how to solve it, but i know that reconfiguring xserver did not help. 

In my case, the cause seems to be the upgrade to 8.10, and reinstallation of xserver which broke after the upgrade. If i can't figure this out, i am just going to whipe and do a clean install, but i was hoping there was a less rash solution.

---

### Post by alinuxfan on 2008-12-21
> **professorbell said:**
> Actually i am having very similar problem, the gui looks happy and healthy, but the gui is nonresponsive to keyboard and mouse. the shortcuts to tty1-6 all work, and they are all fully functional...In my case, the cause seems to be the upgrade to 8.10, and reinstallation of xserver which broke after the upgrade. If i can't figure this out, i am just going to whipe and do a clean install, but i was hoping there was a less rash solution.

I am having the same issues but only with the keyboard. Well, my wife is.

I can ssh into her computer and update and upgrade and set up dyndns so that I dont lose her when her IP changes, but I still can't figure out how to get the keyboard to work.

I thought about reconfiguring xorg, but was iffy about doing that via ssh.

Here is my [post]("http://ubuntuforums.org/showthread.php?t=1017366")

Let me know if you figure it out.  I will do the same.

Adam

---

### Post by deki on 2008-12-21
Still no luck...guys let me know if something comes up and you resolve your issues. I think they're related to mine.

---


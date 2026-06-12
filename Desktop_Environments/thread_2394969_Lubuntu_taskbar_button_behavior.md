---
title: "Lubuntu taskbar button behavior"
date: 2018-06-24
forum: Desktop Environments
---

### Post by noah31 on 2018-06-24
Hi, I can't seem to find any info on this, but I recently upgraded from Lubuntu 17.10 to 18.04 and I noticed that the taskbar window buttons now show up on every desktop, instead of showing up only on the desktop they reside on. What setting needs to be changed to restore this functionality? Thanks in advance.

---

### Post by ajgreeny on 2018-06-24
I believe you can change that behaviour by right clicking on the window button applet, then changing the behaviour to show only on the workspace you are seeing.
It is either that way or in the Panel settings, "items list" tab; sorry, but I'm not on my Lubuntu system at present and may be confusing Lubuntu with Xubuntu.

Unless, of course, you are asking about a twin (or more) monitor system, and for that I have no idea how you can change the view.

---

### Post by noah31 on 2018-06-24
I just checked, the only thing there is to change the amount of workspaces, and the time it displays the switcher notification. nothing related to having a unique panel per workspace like in Lubuntu 17.10.

---

### Post by ajgreeny on 2018-06-25
I am now on my Lubuntu 18.04 system and find, much to my surprise, that you are correct and there is no way to change this behaviour; the Window Buttons do not even appear separately if you go to Panel Preferences.

However, to do what you want go to the **Application Launchbar and Taskbar** where you can change that behaviour.
Confusing I agree but it can be done!

---

### Post by Dennis N on 2018-06-25
> **noah31 said:**
> Hi, I can't seem to find any info on this, but I recently upgraded from Lubuntu 17.10 to 18.04 and I noticed that the taskbar window buttons now show up on every desktop, instead of showing up only on the desktop they reside on. What setting needs to be changed to restore this functionality? Thanks in advance.

Lubuntu 18.04:

Right Click on Panel > Panel Settings > Panel Applets Tab > Select the "Task Bar (Window List)" > Preferences Button (on right) > Check (or Uncheck) "Show Windows from all desktops"

Tested, and works correctly here.

---

### Post by noah31 on 2018-06-25
> **Dennis N said:**
> Lubuntu 18.04:

Right Click on Panel > Panel Settings > Panel Applets Tab > Select the "Task Bar (Window List)" > Preferences Button (on right) > Check (or Uncheck) "Show Windows from all desktops"

Tested, and works correctly here.
Thanks, it turns out to be the setting beneath it, "Only show windows on the same monitor as the task bar". Checking that returned the previous behavior. I wish I knew why that was unchecked by default, because it totally defeats the purpose of multiple desktops (for me, anyway). Much appreciated!

---

### Post by ajgreeny on 2018-06-25
Can I check again; are we dealing with two (or more) monitors here or is it workspaces that you are using?

---

### Post by noah31 on 2018-06-25
> **ajgreeny said:**
> Can I check again; are we dealing with two (or more) monitors here or is it workspaces that you are using?
Single monitor, multiple workspaces.

---


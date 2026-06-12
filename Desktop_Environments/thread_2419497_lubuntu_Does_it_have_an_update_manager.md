---
title: "lubuntu: Does it have an update manager?"
date: 2019-05-22
forum: Desktop Environments
---

### Post by Liamdale on 2019-05-22
I have recently installed lubuntu on an older pentium 4 computer.  I am still getting use to GUI and noticed that there does not seem to have an update manager.  Does it have to be installed independently?  My experience with Ubuntu and Mint the update manager is automatically installed on the launch panel but my version (18.10) does not have one.

---

### Post by again? on 2019-05-23
Don't use Lubuntu but looking at a 16.10 live ISO there is "Software Updater" in system tools.
Should be something similar in 18.10 in system tools.
Try running in terminal....
```
/usr/bin/update-manager
```
If you have configured software and updates to check daily and show immediately I think the updater window appears after login if updates are available.
I think update-notifier daemon should be running. Check in terminal....
```
ps aux | grep [u]pdate-notifier
```

If it's a panel indicator you're referring to... I don't know...may have to wait for a Lubuntu user.

---

### Post by cruzer001 on 2019-05-23
Per the Lubuntu 18.10 package list you have MUON package manager.

[https://packages.ubuntu.com/cosmic/lubuntu-desktop](https://packages.ubuntu.com/cosmic/lubuntu-desktop)

---

### Post by Liamdale on 2019-05-23
As suggested I checked for the update-manager (/usr/bin/update-manager) received a No such file notofication.

ps aux | grep update-notifier gave me "william 12488 0.0 0.0 10732 628 pts/0 S+ 09:18 0.00 grep --color=auto update-notifier"
I assume that these are the update-notifier preferences and that it is active.  I recognize my computer name and the time in the string but that is all.  How the update-notifier works I have no idea.

In my survey of the different installed software, I saw and executed MUON package manager.  I assumed it was similar to synaptic package manager.  I regularly use Synaptic to install new software.  
I assume it can update also but there is no automatic notification with synaptic.  The Lubuntu documentation has a section on MUON package manager, I'll read it.

---

### Post by Dennis N on 2019-05-23
I had Lubuntu 18.10 installed, but have since upgraded that to 19.04. I don't recall seeing a notification of available updates - I checked for them from the package managers. I haven't seen any panel notifications or otherwise notified.

You can check with Discover or Muon. Discover checks automatically when it's opened. Click on updates at bottom of side pane to view, and click button to update them. See attached screenshot taken when I checked - there was no prior notification of these. 

Lubuntu 19.04 has Menu > Preferences > Software Sources to configure the software sources and update preferences. Nothing in there about notifying the user that I can see. Security updates are set to be automatically installed in my preferences.

Update: Checking shows Lubuntu 18.10 and 19.04 lack the package **update-notifier**.

---

### Post by Liamdale on 2019-05-24
Thanks Dennis for the info

I used Discover to update all my software.  Had over 240 updates.

---

### Post by egeezer on 2019-05-26
The update-notifier package can be installed on Lubuntu 19.04 from the muon package manager; if you install it, the Software Updater will appear as a line  in the Preferences menu.

Be advised, update-notifier is a GTK application, and upon installation it will call in all the GTK material it needs to run inside the Qt framework of the new Lubuntu.  

The option, of course, is to run sudo apt update periodically from the terminal.

---

### Post by Liamdale on 2019-06-05
Thank-you Egeezer, presently I am updating using Discover and it seem to be going well.  I may install the updater as you suggest.

---


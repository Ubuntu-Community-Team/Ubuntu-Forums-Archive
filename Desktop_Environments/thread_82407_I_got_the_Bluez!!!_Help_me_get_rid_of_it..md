---
title: "I got the Bluez!!! Help me get rid of it."
date: 2005-10-26
forum: Desktop Environments
---

### Post by Efwis on 2005-10-26
can anyone help me get rid of the bluetooth support? its eating up resources I could use elsewhere.

I don't have nor do I plan to have bluetooth supported equipment. so how can I get rid of it without losing my desktop??

I think it really sucks that it's being shoved down my throat when I dont' need it.

---

### Post by soul_rebel on 2005-10-26
you mean a startup service or what?

---

### Post by Efwis on 2005-10-26
[QUOTE=soul_rebel]you mean a startup service or what?[/QUOTE]
yes if you want to call that, what I would really like is to not even have it load the modules up at boot time.

```
Oct 26 09:48:04 iabusinessprojects kernel: [4294743.826000] Bluetooth: Core ver 2.7
Oct 26 09:48:04 iabusinessprojects kernel: [4294743.826000] Bluetooth: HCI device and connection manager initialized
Oct 26 09:48:04 iabusinessprojects kernel: [4294743.826000] Bluetooth: HCI socket layer initialized
Oct 26 09:48:04 iabusinessprojects kernel: [4294743.845000] Bluetooth: L2CAP ver 2.7
Oct 26 09:48:04 iabusinessprojects kernel: [4294743.845000] Bluetooth: L2CAP socket layer initialized
Oct 26 09:48:04 iabusinessprojects kernel: [4294743.873000] Bluetooth: RFCOMM ver 1.5
Oct 26 09:48:04 iabusinessprojects kernel: [4294743.873000] Bluetooth: RFCOMM socket layer initialized
Oct 26 09:48:04 iabusinessprojects kernel: [4294743.873000] Bluetooth: RFCOMM TTY layer initialized
```

Now when I go into synaptic and try to remove all instances of the bluetooth system, part of the Bluez project, it says that it will remove my Ubunutu-desktop. so is there anyway to get rid of the bluetooth apps without losing my ubuntu-desktop???? and if I try to work it around so that ubuntu-desktop is re-installed it reinstalls the bluetooth system

---

### Post by sanjose on 2005-10-26
[B]sudo update-rc.d -f bluez-utils remove

[/B]it will stop bluetooth from starting at boot time.

---

### Post by Efwis on 2005-10-26
thanks, I will let you know if it worked in a moment as I'm in the process of setting up a mirror for something.

---

### Post by Efwis on 2005-10-26
YAY!!! it worked!! thanks a lot

---

### Post by Dr. Nick on 2005-10-26
For fututre refrence ubuntu-desktop is just a meta package, removing it will not lose your desktop, Its purpose it that all the default packages depend on it so installing ubuntu-desktop will automatically select all the default ubuntu packages.

If you search ubuntu-desktop in synaptic you will see
> The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).

It comes in handy if you want to update to the newest version of ubuntu and get all the new packages selected for you that are not currently installed

---

### Post by Efwis on 2005-10-26
[QUOTE=Dr. Nick]For fututre refrence ubuntu-desktop is just a meta package, removing it will not lose your desktop, Its purpose it that all the default packages depend on it so installing ubuntu-desktop will automatically select all the default ubuntu packages.

If you search ubuntu-desktop in synaptic you will see


It comes in handy if you want to update to the newest version of ubuntu and get all the new packages selected for you that are not currently installed[/QUOTE]
Thats why I didn't want to get rid of the desktop. I just wanted to get rid of the bluetooth support.

---

### Post by MaX on 2005-10-26
It doesn't eat CPU if you aren't using it. Most processes lie idle anyway and you won't notice any change when they are gone.

---

### Post by Efwis on 2005-10-27
[QUOTE=MaX]It doesn't eat CPU if you aren't using it. Most processes lie idle anyway and you won't notice any change when they are gone.[/QUOTE]
my main concern isn't cpu, what i would ultimately like is to get it off my HDD. thats the resource I watch the most since I have a lot of files I need on it. and until I get the time and money for a new one, the 5gig hdd I have is all there is. plus I am still trying to fix my cd burner to work on ubuntu. With the breezy install it doesn't want to burn any files.

---


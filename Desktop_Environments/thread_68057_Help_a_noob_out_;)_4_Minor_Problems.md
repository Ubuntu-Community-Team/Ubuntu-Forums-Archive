---
title: "Help a noob out? ;) 4 Minor Problems"
date: 2005-09-22
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2005-09-22
Okay, so I'm having a little trouble with Kubuntu (Hoary).

Problem 1: Many of my programs seem to close right away when I try to get them to load. They appear in the taskbar with a bouncing icon under the cursor, but then just dissapear. The programs include azureus and giftui.

Problem 2: Where is QT-MOC. I have QT installed, but when I try to install the application Qtella, I get an error saying it cannot find qt-moc, does anyone know where it is and how to point it there in the install?

Problem 3: My box hangs on shutdowns and reboots: for shutdown it hangs after it says LVM Volume [ok] (well something along that line) and reboot it just hangs at rebooting....

Problem 4: I can get the internet, but only after a series of commands I have to type in after boot.

This is what I type in on each startup:

sudo -s
modprobe ndiswrapper
iwconfig wlan0 key
iwconfig wlan0 enc
iwconfig wlan0 essid
/sbin/dhclient wlan0

Is there any way to automate these terminal commands to execute on bootup so I dont have to retype this everytime?

 Other than minor setback I love Kubuntu (my first experience with Linux )

---

### Post by ltmon on 2005-09-22
For Problem 1:
Can you open a terminal and type the command to start the program (e.g "azareus").  The terminal output may give more information about what exactly is going wrong.  Unless this is happening for -a lot- of programs it's probably a different problem for each one.

If you want to use giFT I would recommend downloading "apollon".  It's in the universe repository, and is a much better program for Kubuntu.  Apollon will also connect to the gnutella network.

L.

---

### Post by f1dave on 2005-09-22
For problem 2, load synaptic/kynaptic and search for qt-moc or qt. It should have a package or two that you can install.

---

### Post by mlomker on 2005-09-22
> Problem 1: Many of my programs seem to close right away when I try to get them to load. 

Azureus is a java program...probably something wrong with java.  Do a search on j2re in Synaptic/Kynaptic and make sure you have Sun's java installed.

> 
Problem 3: My box hangs on shutdowns and reboots: for shutdown it hangs after it says LVM Volume [ok] (well something along that line) and reboot it just hangs at rebooting....


Those are shutdown scripts in /etc/rc0.d.  You probably aren't using software RAID, so it'd be safe to disable them and see if that squares it away:

In a terminal:

```

sudo update-rc.d -f lvm remove
sudo update-rc.d -f mdadm-raid remove
sudo update-rc.d -f mdadm remove

```

> 
Problem 4: I can get the internet, but only after a series of commands I have to type in after boot.


In your terminal:

```

sudo nano /etc/modules  #add **ndiswrapper** at the end of the file
sudo nano /etc/network/interfaces

```

You should add an entry that resembles:

```

iface wlan0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXXXXX

```

If you want it to automatically start then add **wlan0** to the **auto** line.  Otherwise, the single command **sudo ifconfig wlan0 up** will start the works.

---

### Post by TheIdiotThatIsMe on 2005-09-23
You guys are awesome  :) Unfortunately I've managed to make my Kubuntu not even start anymore, so I'm going to start from scratch and do a clean install this weekend. I've been trying to figure out that ndiswrapper problem since I've started so thanks a bunch! We shall see my luck on the new install  :roll:

---

### Post by TheIdiotThatIsMe on 2005-09-24
[QUOTE=ltmon]For Problem 1:
Can you open a terminal and type the command to start the program (e.g "azareus").  The terminal output may give more information about what exactly is going wrong.  Unless this is happening for -a lot- of programs it's probably a different problem for each one.

If you want to use giFT I would recommend downloading "apollon".  It's in the universe repository, and is a much better program for Kubuntu.  Apollon will also connect to the gnutella network.

L.[/QUOTE]

For Azureus it shows:
StartSocket: passing startup args to already-running Azureus java process.

However, as far as I know it shouldn't already be running, I've tried restarting to a new empty session and it shows the same thing.

---


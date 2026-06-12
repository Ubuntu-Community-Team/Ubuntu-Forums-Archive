---
title: "blank after upgrade"
date: 2009-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drjugaljpatel on 2009-07-28
I have installed ubuntu 9.04 dell iso after which i added the ati .org driver and ati compatibitlity ati since the desktop effects were not getting enabled. the system is now not booting. it goes blank after few seconds, does not show the loging window.

---

### Post by MelDJ on 2009-07-28
try going into recovery mode to see what is the prob

---

### Post by FirstByté on 2009-07-28
I'm not much wiz on this issue, but it seems you problem is with the ATI driver you have installed.

To get your system up temporarily do this as MelDJ suggested or just press "Ctrl+Alt+F1" or "Ctrl+Alt+F2":
at the prompt.
```

~$ cd /etc/X11 # this takes you to the X's folder
/etc/X11$ sudo cp xorg.conf.failsafe xorg.conf # this overwrites your present xorg.conf that is having problems starting
/etc/X11$ sudo reboot # this reboots your system

```

Once you reboot, hopefully you should be able to get into the system again.

Be sure to check the ATI site for their latest driver for Ubuntu/Linux too! All the best pal!:P


You might wanna check out this link on Fixing Radeon ATI drivers [[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")] 

Good luck!

---

### Post by drjugaljpatel on 2009-07-28
> **FirstByté said:**
> I'm not much wiz on this issue, but it seems you problem is with the ATI driver you have installed.

To get your system up temporarily do this as MelDJ suggested or just press "Ctrl+Alt+F1" or "Ctrl+Alt+F2":
at the prompt.
```

~$ cd /etc/X11 # this takes you to the X's folder
/etc/X11$ sudo cp xorg.conf.failsafe xorg.conf # this overwrites your present xorg.conf that is having problems starting
/etc/X11$ sudo reboot # this reboots your system

```

Once you reboot, hopefully you should be able to get into the system again.

Be sure to check the ATI site for their latest driver for Ubuntu/Linux too! All the best pal!:P


You might wanna check out this link on Fixing Radeon ATI drivers [[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")] 

Good luck!
i removed the ati driver by sudo apt-get remove xorg-driver-fglrx.  after this the system is fine. The special effects are not working, it says could not be enabled. I downloaded the ati driver from the add/ remove list.
  how to get the proper ati drivers ????

---

### Post by drjugaljpatel on 2009-07-28
> **FirstByté said:**
> I'm not much wiz on this issue, but it seems you problem is with the ATI driver you have installed.

To get your system up temporarily do this as MelDJ suggested or just press "Ctrl+Alt+F1" or "Ctrl+Alt+F2":
at the prompt.
```

~$ cd /etc/X11 # this takes you to the X's folder
/etc/X11$ sudo cp xorg.conf.failsafe xorg.conf # this overwrites your present xorg.conf that is having problems starting
/etc/X11$ sudo reboot # this reboots your system

```

Once you reboot, hopefully you should be able to get into the system again.

Be sure to check the ATI site for their latest driver for Ubuntu/Linux too! All the best pal!:P


You might wanna check out this link on Fixing Radeon ATI drivers [[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")] 

Good luck!
i was able to fix the problem by removing fglrx driver. My lappy has intel corp mobile GM965/GL960 graphics card. now how do i go about enabling the effects

---

### Post by FirstByté on 2009-07-28
> 
i was able to fix the problem by removing fglrx driver. My lappy has intel corp mobile GM965/GL960 graphics card. now how do i go about enabling the effects 

It's good you are able to detect the graphics card you are using. It appears we use the same Intel VGA card (GM965/GL960). While it would work Out-Of-The-Box for Ubuntu 8.10 Intrepid Ibex, the architecture has been changed slightly by Intel lately, which was the case when Ubuntu 9.04 Junty was released. The issue *(as of the last time I checked)* has not been finalized by Intel **(It's not a problem with your Lovely Canonical Ubuntu OS but from Intel's new architecture)** which unfortunately is part of the Ubuntu 9.04 core (2.6.28-13-generic*)

A workaround that I did ([COLOR="Red"][SIZE="2"]Please process at your own risk[/SIZE][/COLOR]) this should get your "Extra Effects working" but might break things such as **Standy Mode**[It may not recover from a standby, *I've have disabled my system from any thing that can cause it to enter standy mode--Sleep/Screensaver--Power Management*]:

Inside the 
```

sudo gedit /usr/bin/compiz

```
search for

```

blacklist based on the pci ids 

```

and comment out *(put "#" at the beginning of the line)* the line that has "Intel 965". Mine looks like this

```

#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965

```

Check this out [http://ubuntuforums.org/showpost.php?p=7388723&postcount=71]("http://ubuntuforums.org/showpost.php?p=7388723&postcount=71")

Good Luck!:P

---

### Post by drjugaljpatel on 2009-07-29
> **FirstByté said:**
> It's good you are able to detect the graphics card you are using. It appears we use the same Intel VGA card (GM965/GL960). While it would work Out-Of-The-Box for Ubuntu 8.10 Intrepid Ibex, the architecture has been changed slightly by Intel lately, which was the case when Ubuntu 9.04 Junty was released. The issue *(as of the last time I checked)* has not been finalized by Intel **(It's not a problem with your Lovely Canonical Ubuntu OS but from Intel's new architecture)** which unfortunately is part of the Ubuntu 9.04 core (2.6.28-13-generic*)

A workaround that I did ([COLOR="Red"][SIZE="2"]Please process at your own risk[/SIZE][/COLOR]) this should get your "Extra Effects working" but might break things such as **Standy Mode**[It may not recover from a standby, *I've have disabled my system from any thing that can cause it to enter standy mode--Sleep/Screensaver--Power Management*]:

Inside the 
```

sudo gedit /usr/bin/compiz

```
search for

```

blacklist based on the pci ids 

```

and comment out *(put "#" at the beginning of the line)* the line that has "Intel 965". Mine looks like this

```

#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965

```

Check this out [http://ubuntuforums.org/showpost.php?p=7388723&postcount=71]("http://ubuntuforums.org/showpost.php?p=7388723&postcount=71")

Good Luck!:P



my system already shows 
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965

should i follow the safe method given in the provided by you?

---


---
title: "System suspend/hibernate issue - 16.04 Xenial"
date: 2016-08-04
forum: Desktop Environments
---

### Post by jg1 on 2016-08-04
I have 3 laptops running Xubuntu 16.04 Xenial: Dell Inspiron1300 (2006), Dell XPS17 (2012), PackardBell Netbook DotSE (2010).  All capable of seamless suspend/hibernate using WinXP (Inspiron1300) or Win10 (XPS17 and DotSE).

Performed fix for enabling Hibernate in Ubuntu:
working as root, add text file    com.ubuntu.enable-hibernate.pkla 
                                    to    /etc/polkit-1/localauthority/50-local.d/
containing:

[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
ResultActive=yes


Panel Action buttons work OK for suspend and hibernate, as do hardware buttons  (subject to the loss of cursor bug with hibernate - work around:  Ctl+Alt+F1 followed by Ctl+Alt+F7)
It seems that auto-suspend sometimes works when system (upower?) reaches a certain point, eg on battery low or activity timeout (clearly this needs more testing), but auto-hibernate always fails with 2 msgs on the desktop:

1)  Authentication request:  Authentication is required for hibernating the system
    An application is attempting to perform an action that requires privileges.
    Authentication is required to perform this action.  (ie enter sys-admin/root password)

    Action:  org.freedesktop.login1.hibernate
    Vendors: The systemd project

2)  Notification:
    GDBus.Error.org.freedesktop.DBus.NoReply
    Method call timed out

Entering the password frees up the system which needs to be rebooted to restore full functionality (eg Wifi connections).

I've done loads of searches to try to find out if it's a known problem but not found anything which leads me to think I've done something daft.
Any ideas, pls?
jg1

---

### Post by jg1 on 2016-08-07
Still wrestling with this issue.  Thinks ....
If I could run Power Manager as Root, it would have the necessary permissions to suspend/hibernate the system when needed.
1)  Tried to find a way to edit the Application Autostart list to change the Power Manager launcher, but it appears this has been removed from Ubuntu since 11.10
2)  Unchecked existing instance of Power Manager and added a new item with command: pkexec xfce4-power-manager.  This is launched OK at startup but appears not to connect to the session manager as it doesn't do anything visible - like suspend or hibernate the system, or dim the screen on inactivity.
Please, has anyone any ideas?

---

### Post by jg1 on 2016-08-08
Inching forward ...
Installed uswsusp and now power manager will suspend OK but still doesn't hibernate.  At least it's a bit better than hanging there waiting for authentication and just crashing when it runs out of juice.
But there has to be a better way.  I'd appreciate your thoughts.
jg1

---

### Post by jg1 on 2016-08-15
Power manager still asks for authentication from time to time, even when going for suspend.  Despite 200+ views of this thread, I'm disappointed that no-one has said anything.  Has no-one else experienced this problem or is it a known bug?  Am I wasting my time posting on this forum?

---

### Post by wildmanne39 on 2016-08-15
Most of those views are probably bots, webcrawlers, If I knew the answer I would give it but if you want people to see your thread you need to bump it to keep it in view.

One bump every twelve hours is acceptable.
Hope you get the answer you need.

---

### Post by jg1 on 2016-08-15
Tks, Wild Man
Loathed to bump as it could appear pre-emptive for a Linux numpty like me.
But will take your advice - at least for a while to see if anything comes of it.
Happy days!

---

### Post by #&amp;thj^% on 2016-08-15
> **jg1 said:**
> I have 3 laptops running Xubuntu 16.04 Xenial: Dell Inspiron1300 (2006), Dell XPS17 (2012), PackardBell Netbook DotSE (2010).  All capable of seamless suspend/hibernate using WinXP (Inspiron1300) or Win10 (XPS17 and DotSE).

Performed fix for enabling Hibernate in Ubuntu:
working as root, add text file    com.ubuntu.enable-hibernate.pkla 
                                    to    /etc/polkit-1/localauthority/50-local.d/
containing:

[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
ResultActive=yes


Panel Action buttons work OK for suspend and hibernate, as do hardware buttons  (subject to the loss of cursor bug with hibernate - work around:  Ctl+Alt+F1 followed by Ctl+Alt+F7)
It seems that auto-suspend sometimes works when system (upower?) reaches a certain point, eg on battery low or activity timeout (clearly this needs more testing), but auto-hibernate always fails with 2 msgs on the desktop:

1)  Authentication request:  Authentication is required for hibernating the system
    An application is attempting to perform an action that requires privileges.
    Authentication is required to perform this action.  (ie enter sys-admin/root password)

    Action:  org.freedesktop.login1.hibernate
    Vendors: The systemd project

2)  Notification:
    GDBus.Error.org.freedesktop.DBus.NoReply
    Method call timed out

Entering the password frees up the system which needs to be rebooted to restore full functionality (eg Wifi connections).

I've done loads of searches to try to find out if it's a known problem but not found anything which leads me to think I've done something daft.
Any ideas, pls?
jg1EDIT: Checking if hibernation works at all
```
sudo pm-hibernate
```
Your system will shut down. Once it is completely powered off, turn it on and see if your last session was restored. If it worked, you can safely proceed; hibernation will work as expected. If your session did not restore, or if you encounter errors, that can be for a number of reasons, and unless you can iron it out, it is best not to proceed with the below modifications.
Just this much works for me..
```
[Enable Hibernate in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes
```
And after I ran:  (Not Always Necessary...But you will need to reboot)
```
sudo update-grub
```
Don't know if it makes a difference but I used nano to edit
```
sudo nano /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```
And My specs
```
$ inxi -b
System:    Host: Work-Horse Kernel: 4.4.0-31-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: M3A32-MVP DELUXE v: Rev 1.xx
           Bios: American Megatrends v: 2104 date: 07/05/2010
CPU:       Quad core AMD Phenom 9600 (-MCP-) speed/max: 1150/2300 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.18.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 361.42
Network:   Card-1: Marvell 88E8056 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express)
           driver: ath5k
           Card-3: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too
Drives:    HDD Total Size: 1500.3GB (11.7% used)
Info:      Processes: 261 Uptime: 3:34 Memory: 1565.2/6975.5MB
           Client: Shell (bash) inxi: 2.2.35 


```
Hope this is useful.
Kind Regards

---

### Post by jg1 on 2016-08-16
1fallen,  tks for this.
I followed your process except that I didn't update grub.  However, I have done a kernel upgrade in the meantime so grub config has been updated (although I'm not sure that suspend or hibernate figure in it anyway).  Hibernate and suspend work OK for me with sudo, subject to the loss of cursor/pointer which is a known bug in 16.04.  Session restarts just fine in either case.  The challenge for me, is to get it to work automatically on battery-low or inactivity when specified from the Ubuntu Settings Manager.  Does this work with your set up?

At the moment with my setup, Power Manager appears to run with user rather than root permissions so when it issues a hibernate or suspend command the system says "you can't do that".  I guess it would run into the same trouble if it tried to shut the system down although I've not tried that.  Perhaps I should!

Any further info from your setup would be most helpful, particularly if it does what it says on the tin!

---

### Post by #&amp;thj^% on 2016-08-16
> **jg1 said:**
>   The challenge for me, is to get it to work automatically on battery-low or inactivity when specified from the Ubuntu Settings Manager.  Does this work with your set up?


Mine is a Tower && no laptop to test with ATM. But yes all functions work as expected.

> **jg1 said:**
> 1fallen, tks for this.
At the moment with my setup, Power Manager appears to run with user rather than root permissions so when it issues a hibernate or suspend command the system says "you can't do that". I guess it would run into the same trouble if it tried to shut the system down although I've not tried that. Perhaps I should!
I would try a clean shutdown then try your power-manager setting with hibernation or suspend which ever you prefer.  And maybe..just maybe "sudo update-grub" 
I was also wondering if you had cleared or removed your previous edits before adding my advice? But I do not get any errors.."you can't do that" or any at all.
And are you running a stock kernel?
Edit: But yes grub dose and can come into play with hibernate.
[https://ask.fedoraproject.org/en/question/67758/hibernate-on-fedora-21-does-not-resume/](https://ask.fedoraproject.org/en/question/67758/hibernate-on-fedora-21-does-not-resume/)

[https://help.ubuntu.com/community/PowerManagement/Hibernate](https://help.ubuntu.com/community/PowerManagement/Hibernate)

[https://wiki.gentoo.org/wiki/Suspend_and_hibernate](https://wiki.gentoo.org/wiki/Suspend_and_hibernate)

[URL="http://imgur.com/a/3efiL"]http://imgur.com/a/3efiL

[/URL]

---

### Post by #&amp;thj^% on 2016-08-17
Thought I would add the exact method I followed and works in my case.
From Here: [http://ordinatechnic.com/general-guides/hibernation](http://ordinatechnic.com/general-guides/hibernation)
Enabling Hibernation in Ubuntu and Ubuntu Based Systems

1.Enabling Hibernation in Ubuntu Unity

Even if the requirements of having the interface to the suspend capabilities which in the case of systems that don't use systemd is limited to pm-hibernate from the pm-utils
    having a swap partition that is as large as the amount of RAM
    specifying the swap partition in /etc/fstab
    specifying the resume device in /etc/default/grub are met, in Ubuntu based systems, a fix specific to these distributions must be made to enable hibernation.

The steps required are as follows:

    Create the file

```
   sudo nano /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```

    Add the following lines to the file and save.


   ```
 [Re-enable hibernate by default in upower]
    Identity=unix-user:*
    Action=org.freedesktop.upower.hibernate
    ResultActive=yes

    [Re-enable hibernate by default in logind]
    Identity=unix-user:*
    Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.hibernate-multiple-sessions
    ResultActive=yes
```

2.Enabling Hibernation in Xubuntu/ (Xfce Desktop)

Because Xubuntu is based on Ubuntu, which disables hibernation, and Xubuntu doesn't reverse this, the above fix presented for Unity must be made for Xubuntu.
GNOME Extension for Hibernating

The GNOME shell doesn't have any desktop environment component where hibernation can be controlled. Hibernation control can be added to the user/session menu on the panel using a shell extension. The extension I have used with GNOME on openSUSE is Hibernate Status Button, although it uses uswsusp's s2disk instead of swsusp to write to disk, which would be my preference.
Conclusion:
Besides backlight control issues, the lack of hibernation capability is the single significant issue that might need attention when installing a distribution. I hope this has provided some useful and practical information on resolving hibernation issues.

[COLOR=#0000ff]**As a side note and a Heads up if you use hibernate or suspend to disk this uses your swap space for storage. If you then boot another system that also uses hibernate (or perhaps even one that dose not) you could create some very nasty problems. I add this from my own experince. **[/COLOR]

---


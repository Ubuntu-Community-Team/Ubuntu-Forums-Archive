---
title: "Logout, shutdown, reboot"
date: 2005-08-11
forum: Desktop Environments
---

### Post by loveboat on 2005-08-11
Just up till recently there used to be a choice of rebooting or halting when you clicked the logout button. But now the only thing a can choose is to just log out. Where has halt and reboot been moved to?

//L

---

### Post by No6 on 2005-08-11
[QUOTE=loveboat]Just up till recently there used to be a choice of rebooting or halting when you clicked the logout button. But now the only thing a can choose is to just log out. Where has halt and reboot been moved to?

//L[/QUOTE]
 Souds like you have changed your display manager. Are you now using kdm?

To view all of these options in Gnome you need to use gdm.
To view all of these options in KDE you need to use kdm.

To change your display manager edit the default-display-manager and use /usr/bin/gdm or /usr/bin/kdm

sudo gedit /etc/X11/default-display-manager

HTH

---

### Post by loveboat on 2005-08-11
[QUOTE=No6]Souds like you have changed your display manager. Are you now using kdm?

To view all of these options in Gnome you need to use gdm.
To view all of these options in KDE you need to use kdm.

To change your display manager edit the default-display-manager and use /usr/bin/gdm or /usr/bin/kdm

sudo gedit /etc/X11/default-display-manager

HTH[/QUOTE]

Nope. I'm still using gdm and gnome.
This has happened on both my ubuntu machines.

Any more ideas? :)

//L

---

### Post by No6 on 2005-08-12
Do you log on with a GUI or command line?

The logout buttons are controlled by the display manager. If you are logging in graphically then there's probably some setting somewhere.

I'm scanning at the moment.

---

### Post by loveboat on 2005-08-12
[QUOTE=No6]Do you log on with a GUI or command line?

The logout buttons are controlled by the display manager. If you are logging in graphically then there's probably some setting somewhere.

I'm scanning at the moment.[/QUOTE]

I log in graphically with GDM.

//L

---

### Post by No6 on 2005-08-12
[QUOTE=loveboat]I log in graphically with GDM.

//L[/QUOTE]
 Can you execute this for me and post back your results?
```
ps -fae | grep dm
```

---

### Post by loveboat on 2005-08-12
[QUOTE=No6]Can you execute this for me and post back your results?
```
ps -fae | grep dm
```[/QUOTE]

```

$ ps -fae | grep dm
root      6377     1  0 16:48 ?        00:00:00 /usr/bin/gdm
root      6387  6377  0 16:48 ?        00:00:00 /usr/bin/gdm
root      6422  6387  1 16:48 ?        00:00:24 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
daniel    8602  8589  0 17:14 pts/1    00:00:00 grep dm

```

---

### Post by No6 on 2005-08-15
[QUOTE=loveboat]```

$ ps -fae | grep dm
root      6377     1  0 16:48 ?        00:00:00 /usr/bin/gdm
root      6387  6377  0 16:48 ?        00:00:00 /usr/bin/gdm
root      6422  6387  1 16:48 ?        00:00:24 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
daniel    8602  8589  0 17:14 pts/1    00:00:00 grep dm

```[/QUOTE]
 I'm stumped. I'll keep looking into this but if anyone else has any idea...

I'll be back.

---

### Post by loveboat on 2005-11-16
Has anybody got any idea about this or perhaps any new info?

---

### Post by tommythecat on 2005-11-18
I am having the same exact problem.  It always let me reboot and shutdown from the gui and all of the sudden the options dissappeared and I have to shutdown from a terminal.  It's not a big deal, but it woul be nice to knwo why this option mysteriously dissappeared.

---

### Post by haltect on 2006-03-06
i have the same problem here, it started when i installed kde and kept using gdm.. i couldn't find a way to put them back :/ someone know how to solve this?

---

### Post by kewl1uk on 2006-03-22
Most probably an error in the path to the default display manager in  /etc/X11/default-display-manager

The location of gdm is > /usr/sbin/gdm and the location of kdm is > /usr/bin/kdm

---

### Post by Cascara on 2006-06-05
[QUOTE=kewl1uk]Most probably an error in the path to the default display manager in  /etc/X11/default-display-manager
[/QUOTE]

Hi, i have the same problem, and i have the right path in my /etc/X11/default-display-manager

Any more ideas? :confused:

---

### Post by Codeboi on 2006-06-06
I had the same problem.  Here's what solved it for me (got back my shutdown choice, YAY!)...

In a nutshell...
1. Go to the "System" menu - select "Administration" - select "Login Window"
2. Check the "Show Actions Menu" item under the menu bar section.

Good luck!

*Note: I'm running the default Gnome install for Dapper if that wasn't clear.

---

### Post by martinbriscoe on 2006-06-06
Brilliant, 

I have been struggling with this problem ever since upgrading to dapper. What a daft set of options, I cant really understand why someone would want to have a menu which didnt show any choices.

Thanks
Martin

---


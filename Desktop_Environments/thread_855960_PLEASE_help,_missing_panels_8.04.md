---
title: "PLEASE help, missing panels 8.04"
date: 2008-07-11
forum: Desktop Environments
---

### Post by halg69 on 2008-07-11
[FONT="Tahoma"][SIZE="2"]Hello Ubuntu Community;

I'm really stuck here with those missing panels.

I was only "playing" with changing some login screens & themes and out of the blue I lost both top & bottom panels.

The ONLY thing I get is the desktop screen with my wallpaper.

I don't get any interaction from that desktop.

I can assure you I have tried everything I have found here about similar issues about the missing panels.

Here's what I tried so far....

CTRL-ALT-BackSpace
CTRL-ALT-F1
login
sudo ./etc/init.d/gdm stop 

sudo apt-get update
[LIST]
[*]sudo apt-get install / reinstall ubuntu-desktop
[*]sudo apt-get install / reinstall gnome-panel
[/LIST]

sudo ./etc/init.d/gdm restart

Of course I have type the commands correctly I just wanted to give a quick explanation of what I have done.

The ODD part is that if I try to logon to the session using the "FailSafe GNOME" option the panels do come back but only for that current session.

As I mentioned I have read multiple threads here and no luck yet.

I'm new to UBUNTU and I'm really liking this OS.

EVERYTHING works on my laptop XPS M1210.

Please if you have any ideas let me and everyone here know how.

I would hate to have to re-install, I have spent a couple of weeks "tweaking" Ubuntu to put it at a state I really like using it as my main OS.

Hopefully someone out there has the answer.

Thanks y'all.

halg69

[/SIZE][/FONT]

---

### Post by VMC on 2008-07-11
Try this from that Terminal:

```
sudo apt-get update
sudo apt-get install gnome-panel
```

---

### Post by brujoand on 2008-07-11
You have now idea how much you just helpede me right now :P

I've bin stripping of "unneeded" parts of my 8.04 install and removed almost everything related to evolution.. And it took my panels away:P

Tnx mate :)

---

### Post by halg69 on 2008-07-11
> **VMC said:**
> Try this from that Terminal:

```
sudo apt-get update
sudo apt-get install gnome-panel
```

[FONT="Tahoma"][SIZE="2"][/SIZE][/FONT]I just tried from two options

Rebooted the machine and went in FailSafe mode and ran the commands

Rebooted normally and still the same issue.

Also tried rebooting normally with the desktop with no panels and ran the command from CTRL-ALT-F6

Still nothing and even tried restarting the gdm and still no panels.

Any toughs?

Thanks

halg69

---

### Post by VMC on 2008-07-11
> **halg69 said:**
> [FONT="Tahoma"][SIZE="2"][/SIZE][/FONT]I just tried from two options

Rebooted the machine and went in FailSafe mode and ran the commands

Rebooted normally and still the same issue.

Also tried rebooting normally with the desktop with no panels and ran the command from CTRL-ALT-F6

Still nothing and even tried restarting the gdm and still no panels.

Any toughs?

Thanks

halg69

There is a more drastic approach:

You should be able to get the panel back by deleting the gnome2 folder.

Please go to a Terminal and do the following:

```
sudo rm -R ~/.gnome2
```
You may have to restart X after this, so please use the following key combination:

CTRL+ALT+BACKSPACE

---

### Post by halg69 on 2008-07-12
> **VMC said:**
> There is a more drastic approach:

You should be able to get the panel back by deleting the gnome2 folder.

Please go to a Terminal and do the following:

```
sudo rm -R ~/.gnome2
```
You may have to restart X after this, so please use the following key combination:

CTRL+ALT+BACKSPACE

That did the trick! THANK YOU!!!

[IMG]http://www.usadojo.com/Images/movies/fearless/jet-li-bow.jpg[/IMG]

---

### Post by matrooswolf on 2008-08-22
> **VMC said:**
> There is a more drastic approach:

You should be able to get the panel back by deleting the gnome2 folder.

Please go to a Terminal and do the following:

```
sudo rm -R ~/.gnome2
```
You may have to restart X after this, so please use the following key combination:

CTRL+ALT+BACKSPACE

And thanks from me too.  I had the same issue after screensaver locked my computer and I had to do a hard reboot.

Removing /.gnome2 got me back to normal.

---


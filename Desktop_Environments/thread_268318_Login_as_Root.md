---
title: "Login as Root"
date: 2006-09-29
forum: Desktop Environments
---

### Post by dontgetshocked on 2006-09-29
I have apparently forgot my password to login as root. Anyone remember what the default user name and password are? Can I not logout and log back in as root or do I have to re-boot?

---

### Post by igknighted on 2006-09-30
there is no root in ubuntu (unless you are logged in to the recovery terminal).  To get root power, use 'sudo' in front of whatever command you are typing and it will ask for you password.

if you hit escape as grub is loading you can choose the recovery terminal where you are root (and it doesnt ask for your password either)

---

### Post by dcstar on 2006-09-30
> **igknighted said:**
> there is no root in ubuntu
......

Rubbish, the root account is just disabled by default after an initial Ubuntu installation.

If you want to enable the root account, do the following:
```
sudo passwd
```
Enter **your** password for root privileges, and then enter your new root password (twice).

---

### Post by pod25 on 2006-09-30
> **dcstar said:**
> Rubbish, the root account is just disabled by default after an initial Ubuntu installation.

If you want to enable the root account, do the following:
```
sudo passwd
```
Enter **your** password for root privileges, and then enter your new root password (twice).

Erm , should that be ```
sudo root passwd
``` ??

---

### Post by aysiu on 2006-09-30
It's not rubbish at all. If the root account is disabled, it essentially doesn't exist. Yes, technically, it "exists," but for someone wanting to *log in as root*, it doesn't until you create a password for it. Additionally, if you want to log in as root graphically, you need to enable that option through GDM setup.

I don't see any reason to log in as root in Ubuntu. I think it's faster and more convenient to do things without logging in as root.

If you're at the terminal, type *sudo* in front of whatever command you want: ```
sudo nano -B /etc/apt/sources.list
``` If there are a string of commands you want to run as root but don't want to type *sudo* ten times, do ```
sudo -i
``` This will allow you to be root.

If you prefer to do things through the GUI, press Alt-F2 and type ```
gksudo nautilus
``` You can create a keyboard shortcut or launcher for that command, too, if it's something you do quite often.

The command for Kubuntu is *kdesu konqueror*. The command for Xubuntu is *gksudo thunar*.

---

### Post by kerry_s on 2006-09-30
You can log in with your user and set the root password again by running> sudo passwd root

---

### Post by aysiu on 2006-09-30
I still see no compelling reason to log in as root, especially when to OP wants to log *out* and then log in *again* as root.

How convoluted.

Just use *sudo* or *gksudo*. It's fast. It's convenient. And it's the way Ubuntu is built to be used.

---

### Post by dontgetshocked on 2006-09-30
What if i need to install lets say a print driver with root privileges?
I see no right click to login file manager with root privileges.
Some things are dimmed out and I assume it is because it needs root privileges.
New to this distro, coming from Xandros which is easier so far.
Forcing myself thru the learning curve.

---

### Post by aysiu on 2006-09-30
You don't need to force yourself through a learning curve. You *can* enable a root account--you just don't need to.

I do think, however, that Ubuntu's security model is worth exploring. After you explore it, if you still prefer the traditional root/user model, you can always enable that.

For a print driver--if it is executable through the GUI, you would do Alt-F2 (or launcher or keyboard shortcut for) ```
gksudo nautilus
``` and then right-click the file and make it executable and then double-click it and choose to run it.

Otherwise, if you prefer the terminal, you can do ```
sudo ./installprintdriver
``` if the name of the file is *installprintdriver*.

---

### Post by ardchoille on 2006-09-30
I agree with aysiu. I have been running Ubuntu since Breezy and I have never had to enable the root account. I have also been using sudo for a long while on other distros (I manually disabled the root acconts on those).

When someone tries to hack into your computer, they know there is a root account and they can't hack into the user accounts because they don't know the user names. But, when the root account is disabled, it just makes it that much harder to hack into it.

For command line apps that need to be run as root, use:

```

sudo <appname>

```
i.e. sudo apt-get install foo

For gui apps, use:

```

gksudo <appname>

```
i.e. gksudo nautilus

I have been administering many Ubuntu boxes and none of them have the root account enabled, it just isn't necessary.

---

### Post by infol on 2006-10-01
As previously mentioned, sudo is a nice way to avoid wrecking havoc on your system, but I agree that it can be annoying at times. However using ```
sudo su -
``` in the terminal will let you become root for the rest of the terminal session without having to activate the root account

---


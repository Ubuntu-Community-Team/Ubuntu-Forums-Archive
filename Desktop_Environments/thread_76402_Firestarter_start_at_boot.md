---
title: "Firestarter start at boot?"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Pig Monkey on 2005-10-15
I just perfomed a clean install of 5.10. In "Startup Programs" I have it run *sudo firestarter --start-hidden*, which used to make Firestarter launch in the tray at boot in 5.04. Now it doesn't seem to work. (Yes, Firestarter is installed). If I run the exact command myself in the terminal, it works (after asking me for a password).

---

### Post by nilfilter on 2005-10-15
In Hoary I had to follow the instructions found in the FS FAQ to make it work: 
[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

I didn't install it in Breezy though since I am now using my router's built-in firewall.

---

### Post by Rxke on 2005-10-15
I tried the above instructions, but no joy.

on the other hand: when rebooting I see : Firestarter stopped... So it *was* active?

Huh? Maybe because of one of the setting: start the firewall... while connecting... or something?

But no. ```
top
``` doesn't list Firestarter... :confused:

---

### Post by flyingbrass on 2005-10-15
I've been having problems with this too in Breezy.  Firestarter goes through spells where it won't start when I log in.  I'm not sure how I've fixed it each time.  I've reinstalled firestarter, adjusted where in the sequence it starts, changed themes back and forth, tried different session options (default, gnome, last session), restarted X, rebooted.  Eventually it works again.

The gnome session seems finicky during startup.  A few times it stalled right after the update-notifier icon appeared on the progress bar or whatever it's called.  Then the whole progress window stayed on my desktop even after gnome finished loading.  This happened again even after restarting X.  Firestarter didn't launch either time.  I reinstalled update-notifier, which solved that problem and firestarter was back again.  Perhaps update-notifier has been the problem all along.  Beats me.

You might try: sudo apt-get install --reinstall update-notifier

FWIW, I currently have firestarter set at 55 in start up programs.

> on the other hand: when rebooting I see : Firestarter stopped... So it *was* active?

I think you're seeing the firewall itself shut down, not the control panel.  The firewall starts automatically when you boot.  To see if the control panel is running: ps aux | grep firestarter

If it is you'll see something like:
root      9676  0.1  2.3  21600 12148 ?        Ssl  02:30   0:30 firestarter --start-hidden

---

### Post by peterbrowne on 2005-10-15
In my startup programs I have:

gksudo /usr/sbin/firestarter

it works every time!

---

### Post by jobezone on 2005-10-15
For all who are reading this thread, Firestarter as such is a tool to configure linux's firewall (called iptables). You don't *need* to have the GUI present for it to be running, just check the option in Firestarter's preferences window for it to be executed automatically when acessing the net, and it will do so (as you can check on the screen messages when booting ubuntu).
If you want to have the gui, then ok, this thread is for you.

---

### Post by Pig Monkey on 2005-10-15
Before I had neglected to add *username ALL= NOPASSWD: /usr/sbin/firestarter* in /etc/sudoers. Now I've done that and it still doesn't start at boot.

On top of that, if I run *sudo firestarter* from a terminal, it prompts me for a password, even with that line in /etc/sudoers.

---

### Post by Hairy_Palms on 2005-10-15
did you change the username, otherwise it wont work
username ALL= NOPASSWD: /usr/sbin/firestarter
should be
Hairy_Palms ALL= NOPASSWD: /usr/sbin/firestarter

---

### Post by Pig Monkey on 2005-10-15
Yup.
```
pigmonkey ALL= NOPASSWD: /usr/sbin/firestarter
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

```

---

### Post by nolodude on 2005-10-16
See [http://www.ubuntuforums.org/showthread.php?t=59357]("http://www.ubuntuforums.org/showthread.php?t=59357").

You need to put that line last in sudoers.

---

### Post by Pig Monkey on 2005-10-17
That seems to have fixed it. Thanks!

---


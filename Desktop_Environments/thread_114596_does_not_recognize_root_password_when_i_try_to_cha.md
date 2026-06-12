---
title: "does not recognize root password when i try to change settings in Administration menu"
date: 2006-01-08
forum: Desktop Environments
---

### Post by kundalinikat on 2006-01-08
Hey, I just installed Breezy, and I was trying to set up my wireless network...

When I logon as a normal user and then try to use something in the Administration menu, it asks for the root password. I then type in the root password and it says it's the wrong password. (It also says it's the wrong password if I type in gibberish.)

(Additionally, if I enter the password for [the thing during boot which lets you choose which kernel to start or to start Windows] when it asks for the root password, the password dialog box disappears and nothing happens; and thereafter if I try to open anything from the Administration menu I see a thing in the bar at the bottom of the screen saying "Starting [option from Admin. menu i tried to use]..." which disappears with nothing happening.)

I've tried booting from the install CD and using Rescue mode to get to the # prompt thing and type "passwd root" and enter a new password, but it still doesn't recognize it...

This is frustrating, I chose my own root password and it doesn't recognize it!

---

### Post by aysiu on 2006-01-08
Did you do an expert install?
If you didn't, you shouldn't have a root password.
For more info, read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by kundalinikat on 2006-01-08
i did do the expert install - if i do a normal install can i still choose which hard drive to install it on? because then i'll just do a normal one! :)

---

### Post by aysiu on 2006-01-08
[QUOTE=kundalinikat]i did do the expert install - if i do a normal install can i still choose which hard drive to install it on? because then i'll just do a normal one! :)[/QUOTE] Yes, you can. I never could figure out how to work the expert install, and the normal install does ask you quite a few questions, anyway!

---

### Post by tedk on 2006-01-09
Try this...
You know I don't think it's asking for a root password. It's trying to do a sudo, so use your own password. Then ensure that you are listed in /etc/sudoers as someone who can do root stuff. Use visudo to edit the sudoers file.

```

# User alias specification
User_Alias      IT=<your username>

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
IT      ALL=(ALL) ALL

```

---


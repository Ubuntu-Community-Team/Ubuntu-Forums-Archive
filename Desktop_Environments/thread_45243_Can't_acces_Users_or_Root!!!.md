---
title: "Can't acces Users or Root!!!"
date: 2005-06-29
forum: Desktop Environments
---

### Post by linuxrobot on 2005-06-29
Hello all,
I am a NEWBIE to linux.  I just installed Ubuntu 5.04.  I was trying to get the internet to work, when before it saw the wireless card, and it would show some info, but now, I've tried somethings and it thinks that *ath0* doesn't exsist.  Well, anyway, I was trying to do something else, and I deleted my main user.  (I had two users the main one, for me, and another for the rest of the family.)  I only had messed up the wireless card on mine, so I thought I could get at it from the family's user.  Wrong, It didn't work! ](*,)   Now whenever I try to get into the Root Terminal or the Users & Groups (now, this is on both users) it says something like: _Can't Access file; Child 1 status_ , or something like that.  I can't do anything, it's so annoying!  Is there a "restore to factory settings" (like Windows)?   I don't have a lot of info to loose, so I won't care!
Thanks!

**LinuxRobot**

---

### Post by jago25_98 on 2005-06-29
The helper is confused. Is this just with the gnome terminal?

don't know this error so what i'm gonna say might be useless

from reading ubuntuguide.org , 

1) to reset password

on boot > press esc > e to edit > add `init=/bin/bash` (or `rescue`) > passwd on boot > change password

2) press alt+f2 and type `xterm` in the run dialog. That should give you a terminal window to run stuff from for the time being

3) get to the commandline, like DOS was to Windows in Win95

ctrl+F2

and login as root or sudo to run these sort of commands

then you might 

killall X
or
killall gdm
or 
killall kdm

then you could try running X again with `startx`

---

### Post by linuxrobot on 2005-06-29
Ok, I'll try it...
But how do you login as "root" or "sudo"?
Thanks!

**LinuxRobot**

---

### Post by jago25_98 on 2005-06-29
o dear houston, we have a problem.

read, rinse, repeat:

[http://www.tomshardware.com/howto/20040329/](http://www.tomshardware.com/howto/20040329/)
[http://www.tldp.org/LDP/intro-linux/html/](http://www.tldp.org/LDP/intro-linux/html/)

---

### Post by linuxrobot on 2005-06-29
I don't understand how to enter those codes.  I get so far, and then it doesn't do anything.  If you don't mind, please tell me what the screen looks like when I type what;  I'm scared that I'll mess more stuff up!
I retried to enter the Root Terminal and I got the complete error megssage.
When I try to log into Root Terminal it says:
*Failed to run /usr/bin/x-terminal-emulator: Child terminated with 1 status* 
When I try to log into Users & Groups it says:
*Failed to run users-admin: Child terminated with 1 status* 
I have no idea why it says "Child", I didn't put any birthdays, or anything!  It's wierd!
So, those are the error messages, if that helps...

**LinuxRobot**

---

### Post by davahmet on 2005-06-29
The Unbuntu installer makes the assumption that the system's administrator will be the person doing the installation, so by default that first user has sudo permissions.  For security reasons, by default only that main user has sudo permission.  You can give other users permission to sudo, but the main user has to be the one to do this.

Now, the problem is that when you removed the main user, you removed the only account that had permssion to do root-type activities through sudo.  I wish I had better news for you, but honestly I don't there is any feasible way around this other than to wipe and reinstall.

The reason you get 'Child' errors is because the processes you call inturn spawn child processes thet return the error.  A '1' status is a generic error condition that gets returned by the shell.  It simply means the root terminal emulator failed to start for a non-specified reason.

---

### Post by linuxrobot on 2005-06-29
davahmet,
Thanks for the info!
I will not be so stupid again! ](*,) 
But, how do I uninstall Linux? :???: 
The last thing I want to do is wipe out my other partition (Windows) with another mistake! :roll: 
Thanks!

**LinuxRobot**  :smile:

---

### Post by davahmet on 2005-06-29
[QUOTE=linuxrobot]davahmet,
Thanks for the info!
I will not be so stupid again! ](*,) 
But, how do I uninstall Linux? :???: 
The last thing I want to do is wipe out my other partition (Windows) with another mistake! :roll: 
Thanks!

**LinuxRobot**  :smile:[/QUOTE]
 Don't be so hard on yourself.  Stupid is when we fail to learn from mistakes.  Being a newbie is only a temporary, and learning from the mistakes is the only way to move from that state.  Hehe...we've all had our shares of screwups while learning.

Now, to remove it...this is how I would do it:
- Boot from the installation CD
- Go through the steps for a fresh installation
- When it comes to the partitioning part of the installation, select manual partitioning
- List the current partitions, making note of the Window's partitions
- Delete the non-Windows partitions only, leaving Windows intact
- Rebuild your partition scheme on the Linux side of your harddrive(s)
- Continue with a normal installation

Good luck and welcome to the learning curve. :)

---

### Post by linuxrobot on 2005-06-29
Thanks for your support!
I followed your instructions and everything is working perfectly!

Thanks again for _all_ of your help!

**LinuxRobot**  :)

---


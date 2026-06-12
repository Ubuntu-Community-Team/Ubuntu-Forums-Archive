---
title: "System won't boot (will clarify if necessary)"
date: 2009-04-24
forum: General Help
---

### Post by starwardude on 2009-04-24
I hate myself SO much for this. I started my laptop (runs Xubuntu 7.10), and for whatever stupid reason, I accessed my normal account on my system, and remove its administrative privileges while granting them to my other, lesser used account (mistake 1). I reboot the computer, and try to access the new "admin" account. I forgot the password. "Okay," I thought, "I'll just reset it." So I follow the procedure outlined [here]("http://ubuntuforums.org/showthread.php?t=3609") and reset it. I successfully accessed the account, and changed its password to something better than one letter while re-granting admin privileges to the other account (mistake 2). I attempt to switch users, and the screen freezes. I restart it, and not long into the boot process, am presented with this lovely message (Not in this color, of course):

[COLOR="Green"]Unattached inode 65286

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i.e., without -a or -p options)
fsck died with exit status 4

*An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started. After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
Give root password for maintenance
(or type Control-D to continue):_
[/COLOR]
I've tried both passwords, the password from when I reset the password, nothing, a space, and pretty much every password I could think of that I've ever used. No luck. All I keep getting is this:

[COLOR="Green"]Login incorrect
Give root password for maintenance
(or type Control-D to continue):_[/COLOR]

I ctrl-d, attempt to do [this again]("http://ubuntuforums.org/showthread.php?t=3609"), and get this every time I try anything password related: 

[COLOR="Green"]passwd: Authentication service cannot retrieve info
passwd: password unchanged[/COLOR]

What should I do? I could run fsck under the passwordless root, but get the following message:

[COLOR="Green"]WARNING!!! Running e2fsck on am mounted filesystem may cause SEVERE filesystem damage.

Do you really want to continue (y/n)?[/COLOR](I chose no so far)

An idea I just had involves removing a user, but what would be the case with the passwords then? If all else fails, I could reinstall the OS, but would rather save that for when all possible solutions have been exhausted.

---

### Post by starwardude on 2009-04-25
Anyone? Should I do the fsck with the risk of damaging the filesystem, attempt to delete one of the users, or just do a complete system reinstall?

---

### Post by starwardude on 2009-04-28
Bump. No one has any ideas?

---


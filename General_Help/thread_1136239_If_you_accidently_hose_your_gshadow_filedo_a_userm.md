---
title: "If you accidently hose your gshadow file/do a usermod -G and lock yourself out"
date: 2009-04-24
forum: General Help
---

### Post by wynneth on 2009-04-24
I just learned a very good lesson, and I thought I'd post here in a worldwide searchable forum to help those in the future that make the same mistake.
First of all, please always back up your system. I use BackInTime, but you might use sBackup, or just rsync. 
Never, I repeat, never run a command without making absolutely sure the syntax is right and you know what it does.
I was reading about setting up thunderbird to check system mail and did not notice the lack of a -a in the following command (DON'T RUN THIS) ```
sudo usermod -G username mail
```
This command puts username in the mail group. The problem is without a -a (append) it MOVES the username to that group. So if you're running on a typical ubuntu installation and you use this on your username and have no other users (root is disabled by default), you're going to have problems. It took me hours to get everything working again because I didn't know just what all files this would affect. In ubuntu user group related stuff is stored in a few main files:
/etc/group
/etc/shadow
/etc/gshadow
/etc/passwd
That gshadow one? That's what was killing me. Once I figured out what the actual problem was I simply copied my backups of shadow, group, and passwd back but I was still having HELL once gnome/x loaded. (Basically, when the x window system loaded I could not type, move the mouse, ANYTHING.) Apparently this is because gshadow is the shadow information file for groups.

So if you somehow move your user to a group that has no access, you're going to need to do like I did and boot into another system (naturally I keep a few thumbdrives with various distros) and either copy over your backups, or - and this part involves knowing what you're doing - manually edit the files I listed to get them CORRECT.

Symptoms of screwing up like I did:
Immediately unable to run sudo anymore.
Unable to properly boot and run x/gnome.
Feeling like a moron.

I hope this helps someone else out there. LOL.

---

### Post by evermooingcow on 2009-04-24
Boot into single user mode (created by default). You hit some key (can't remember what) during the boot process to bring up your GRUB options and choose single user mode. Gives you a root shell.  Works for if you forget your password too.

---


---
title: "Reboot &amp; Specify OS to be Booted?"
date: 2009-05-06
forum: General Help
---

### Post by CaptnEvilStomper on 2009-05-06
I know you can reboot from the command line using reboot or shutdown -r, but can you reboot the system and specify which OS should be started? For example, my dad's PC has Ubuntu 9.04 and Windows Vista installed on it, each running an SSH server. Is there a way I could log in via SSH and tell Ubuntu to restart and load Vista? I checked the man files for both reboot and shutdown and couldn't find anything, but could I just write a script that does this or something like that?

---

### Post by Fixman on 2009-05-06
Yes, but it has nothing to do with the shutdown command.

If you have GRUB, edit the file /boot/grub/menu.lst, and seek for a line that says something like

```
default 0
```

to

```
default saved
```

(it may not exist, in that case create it in the third line).

**_IMPORTANT:_** **You should also set timeout for a little number (I have it to 5 seconds).**

Then, search for what entry in GRUB your Windows partition (if its the first partition to be shown, its 0, the second its 1, etc.) and, each time you want to boot windows just put on the terminal

```

sudo grub-set-default 7
sudo reboot

```

Changing 7 for the number of partition your Windows partition is in.

Or, if you don't mind, you can change the "default saved" line for "default 7" (again, 7 is the number of partition Windows is in), and that will ALWAYS boot windows once the timeout finishes.

---

### Post by CaptnEvilStomper on 2009-05-07
I think I was a little unclear in my first post. I've already got Ubuntu set as the default operating system, and I want it to stay that way. I have an SSH server running in both Vista and Ubuntu, and I set up a DNS host name through DynDNS that points to my dad's PC's IP so I can log in even when I'm not actually at his house. If Vista is running and I need to change something in Ubuntu I can just SSH into it and reboot from the command line, and it'll boot into Ubuntu, since that's the default OS. Here's the problem - what if I'm running Ubuntu and need to boot Vista? That's where I'm stuck. When I log in remotely via SSH, I have no way of telling it which operating system I want to boot to without editing the GRUB list every time I want to switch to a different OS, and I was hoping there was a simpler way of doing it than that. Anyone have any ideas?

---

### Post by Fixman on 2009-05-08
> **CaptnEvilStomper said:**
> I think I was a little unclear in my first post. I've already got Ubuntu set as the default operating system, and I want it to stay that way. I have an SSH server running in both Vista and Ubuntu, and I set up a DNS host name through DynDNS that points to my dad's PC's IP so I can log in even when I'm not actually at his house. If Vista is running and I need to change something in Ubuntu I can just SSH into it and reboot from the command line, and it'll boot into Ubuntu, since that's the default OS. Here's the problem - what if I'm running Ubuntu and need to boot Vista? That's where I'm stuck. When I log in remotely via SSH, I have no way of telling it which operating system I want to boot to without editing the GRUB list every time I want to switch to a different OS, and I was hoping there was a simpler way of doing it than that. Anyone have any ideas?

grub-set-default sets the GRUB entry to be saved, and so it will be the first to boot after the timeout. If you set default saved, and then put setdefault 0 to all entries (and a little timeout), then each time you run grub-set-default n and reboot throught SSH, it will boot Windows for one time, and the following times it will boot Ubuntu. It will be almost seamless if you have SSH to open up at startup on both Windows and Ubuntu.

---


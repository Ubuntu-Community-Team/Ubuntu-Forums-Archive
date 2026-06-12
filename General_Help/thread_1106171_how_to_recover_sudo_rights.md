---
title: "how to recover sudo rights ?"
date: 2009-03-25
forum: General Help
---

### Post by shelly.tumbleson on 2009-03-25
Hi. I've never had to post here because i was always able to find an answer to whatever question i had. 

This time, i've found plenty of answers; none of which have worked for me. 

I was trying to give myself write permissions for my 2nd IDE drive when i accidentally removed myself from the Administrators group. Stupid, stupid, stupid. Unfortunately i never set up Root nor had i set up another user account with Admin rights. 

I've tried editing my GRUB kernel line to go into Single User Mode (adding Single at the end of the kernel line); no go. I've tried booting off of the Ubuntu 8.10 CD and editing my sudoers file. Again, no go. Root does not appear to be enabled off of the CD. 

If anyone has experience with this or knows of a site that might provide some direction, i'd be most appreciative. 

thank you,
shelly.

---

### Post by kanikilu on 2009-03-25
I haven't tried this myself, but can you boot off the live CD, mount the hard drive with ubuntu on it, and then manually edit the /etc/group file and add your username to the admin group?

---

### Post by kpatz on 2009-03-25
Hit Esc just as Ubuntu is about to boot, to bring up the Grub menu.

Choose the topmost line that says "Recovery Mode" on it.  This will boot you into a root shell.

Then use the command **adduser yourusername admin** (replace yourusername with your actual login name).

This will put you back in the admin group.

Type exit or hit Ctrl-D to boot normally.

---

### Post by 3Miro on 2009-03-25
There is a way to start the live CD and get root rights back, but it would involve editing some specific files I am not exactly sure which ones. This for obvious reasons qualifies as Hacking, so someone with more experience has to tell you which files.

---

### Post by shelly.tumbleson on 2009-03-25
> **kpatz said:**
> Hit Esc just as Ubuntu is about to boot, to bring up the Grub menu.

Choose the topmost line that says "Recovery Mode" on it.  This will boot you into a root shell.

Then use the command **adduser yourusername admin** (replace yourusername with your actual login name).

This will put you back in the admin group.

Type exit or hit Ctrl-D to boot normally.

Kpatz,

I was so close. When i read the directions to do this the first time, i expected to go straight to a shell- in fact, i had to select the shell from an ASCII menu. I found it and added myself to the Admin group. 

Give yourself a raise, mate. Thanks!

-shell.

---


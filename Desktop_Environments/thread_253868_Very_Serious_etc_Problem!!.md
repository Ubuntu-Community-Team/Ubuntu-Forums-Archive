---
title: "Very Serious /etc/ Problem!!"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Inhumane on 2006-09-09
About 3 hours ago I accidentaly (doesn't matter how, very silly mistake) moved /etc in / into my /home/usr/Desktop... I managed to put /etc back into / with someones help after many hours, but it seems now that either half the stuff inside is corrupt, or I don't know what, because my internet won't work now, almost everything under System->Administration is busted (it just won't launch) and sudo won't work, it says I don't have userid or something, it seems the permissions were somehow fuzzed around in the process, and I'm desperate to get this running normal again because I spent countless hours applying tweaks and general optimizations to the system,90 percent of which I can't remeber. Reinstalling is very much not an option... If anyone can offer any help... :(

---

### Post by Junx on 2006-09-09
If you back up your etc settings you currently have (that were moved), you could try to reinstall, do a diff between the two, and patch it.

I'd save that for a last resort if no one else can help.

Edit: you might want to check the permissions of everything: ls -lR /etc

---

### Post by ebash on 2006-09-09
Reboot your computer with the LiveCD and compare the etc of the LiveCD with your own copy of etc.

---

### Post by funchords on 2006-09-09
> **Inhumane said:**
> ...almost everything under System->Administration is busted (it just won't launch) and sudo won't work, it says I don't have userid or something, it seems the permissions were somehow fuzzed around in the process...

That's exactly what happened.  

Put the files back where they belong, then launch with the LiveCD and access the drive through the LiveCD.

Use ls -l (that's dash ell, not dash one) to verify these permissions, and use chmod and chown to change them if needed:

[FONT="Courier New"]
**-rw-r--r--**   1 **root**   **root**      1222 Sep  6 15:36 passwd

**-rw-r--r--**   1 **root**   **root**       721 Sep  6 12:30 group

**-r--r-----**   1 **root**   **root**       403 Sep  6 12:30 sudoers[/FONT]

> **Inhumane said:**
> and I'm desperate to get this running normal again because I spent countless hours applying tweaks and general optimizations to the system,90 percent of which I can't remeber. Reinstalling is very much not an option... If anyone can offer any help... :(

You can probably recapture most of what you did by using this command:

**cat /var/log/dpkg.log | grep -v status**

The first part of this list were the original install packages.  Everything after that, you (or something under your control) did.

All your other customizations should be in your /home/username directory and in the /etc directory.  Some of these files and directories are prefixed with a period to hide them, but using the "-a" switch to the "ls" command or changing your file manager to show hidden files will show them.  They are only hidden for your visual comfort.

---

### Post by Inhumane on 2006-09-09
> **funchords said:**
> That's exactly what happened.  

Put the files back where they belong, then launch with the LiveCD and access the drive through the LiveCD.

Use ls -l (that's dash ell, not dash one) to verify these permissions, and use chmod and chown to change them if needed:

[FONT="Courier New"]
**-rw-r--r--**   1 **root**   **root**      1222 Sep  6 15:36 passwd

**-rw-r--r--**   1 **root**   **root**       721 Sep  6 12:30 group

**-r--r-----**   1 **root**   **root**       403 Sep  6 12:30 sudoers[/FONT]



You can probably recapture most of what you did by using this command:

**cat /var/log/dpkg.log | grep -v status**

The first part of this list were the original install packages.  Everything after that, you (or something under your control) did.

All your other customizations should be in your /home/username directory and in the /etc directory.  Some of these files and directories are prefixed with a period to hide them, but using the "-a" switch to the "ls" command or changing your file manager to show hidden files will show them.  They are only hidden for your visual comfort.


What do you mean put them where they belong? I'm not sure, all I did was moved the folder over to my desktop, I didn't extract anything out of it. But at least I got the problem down,gpermissions. OK once I go on LiveCD, what commands should I type out? I don't know exactly how to change permissions (chown -R /etc/ ?) and to what permissions I should set it to

OK, I figured it, well /etc/ is set to root root, isn't that the way it's supposed to be? So what's wrong

---

### Post by v6ikek6rbes on 2006-09-09
use the livecd and in the future make always backups

---


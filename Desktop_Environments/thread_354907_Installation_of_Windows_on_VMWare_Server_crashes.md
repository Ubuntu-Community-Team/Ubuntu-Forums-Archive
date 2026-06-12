---
title: "Installation of Windows on VMWare Server crashes"
date: 2007-02-06
forum: Desktop Environments
---

### Post by gadget00 on 2007-02-06
Hi all.  Im having problems installing windows with the vmware server.  

VMWare installed fine, runs fine, creates the virtual machine in a fine way; even boots the windowsCD fine! 

[I][B][U]But when I choose to do the drive format(NTFS, both regular or quick), it goes to the 0% screen, keeps there for a while, and then the virtual machine gets off by itself!
[/U][/B][/I]
If I retry the installation, then tells me **"operating system error"** and never boots.

[COLOR="Navy"]Also, all the programs running start having internal errors and crash.  I knew it because each time i launch any app, the bug-report program launched, and then crashed too![/COLOR]

I dont understand why this is happening.  I even switched the directory that keeps the virtual machine files, just in case it had any permission issues, but keeps on failing.  It was supposed to be fine.  I saw a guide here in the forums, and they didnt had problems.  Im really out of ideas now.  [COLOR="DarkRed"]**Hope for an answer ASAP.**[/COLOR]


**Also, I tried to use the recoveryCD that came with the laptop(Toshiba Satellite L10-S104) and that also gave an "Internal Memory Error" and didnt worked either.  THe difference is that doing this didnt made the apps crash.

---

### Post by veloce on 2007-02-08
Is retrying the installation actually trying to reboot off the installed system rather than the cd?

I'm about to do a new win XP vm myself, so will let you know how I get on.

Veloce.

---

### Post by veloce on 2007-02-08
Sorry, I don't get this problem.  Things I can think of:

Do you have enough disk space for the virtual drive?
Did you preallocate the space for the drive? (I didn't)

Did you try deleting the vm and starting from scratch? Did it do exactly the same thing?

Is the windows disk corrupted?

I'm installing off a disk image but can't see how that would make a difference.

Veloce.

---


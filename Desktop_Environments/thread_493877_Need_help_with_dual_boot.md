---
title: "Need help with dual boot"
date: 2007-07-06
forum: Desktop Environments
---

### Post by oldcpu on 2007-07-06
I would like to dual boot my Windows (default) and Ubuntu.

I have searched and many of them only explains how it is done when installing Ubuntu.  The thing is, my Ubuntu is already installed.

I have Windows in one hard drive, and Ubuntu in another.  I have to open up the computer case when I want to boot into another system.

When I installed Ubuntu, it was on hdc (master IDE2).  Now I have pulled out the CD-ROM and added Windows to the master IDE1.  Which boots it by default without giving me an option.

Now, what do I do in order to give me the option of booting in Windows or Ubuntu?

I take it that Ubuntu would have to be in master IDE1 and Windows would have to be in master IDE2, right?  How do I safely change all the setting from hdc to hda in Ubuntu?

---

### Post by JanvL on 2007-07-06
Hi,

What Windows, 98ME//2000/XP?

For XP you need to edit the boot.ini.
I never did this but you should search the internet in the windows-sites
with boot.ini, then you will find it.

If an old windows, you need a bootloader like lilo or grub.
It looks scary but bootloaders usualy work fine, it does take some courage.
Again search the internet for the details.

Really opening the case is not neccesary.
Lots of success.

Jan

---

### Post by oldcpu on 2007-07-06
Windows 2000.

There is no boot.ini in Windows 2000.  I do not know which file to edit in Windows.

I have already searched.  And they all assume that Linux is going to boot first so I need to edit something in Linux.  But in my case, it is Windows booting first.  So I need to edit something in Windows.

If I were to swap the hard drives around.  My Ubuntu is be sort of messed up because I installed it as hdc and not hda.  I need to know which files to edit to change all the hdc's into hda's.

---

### Post by gigaferz on 2007-07-06
i have an xp as slave and ubunut on the master .

and on the BIOS you can choose wich hard drive to boot.

you do not need to open the case, also check the jumper settings in both drives, i have them both in "cable select"

and grub will work with windows xp. you need to  edit grub for that.

right now im looking a thread to edit grub, since i just installed ubuntu.

i  just noticed something.

I sugest to reinstall ubuntu, as master and windows  move it to slave, the thing with windows is that itll show you a blue screen with some text and it'll fix it sel up to the drive it sconnected.

back up your linux data before anything, and handling the hard drives that often might cause problems are later become unusable.

---


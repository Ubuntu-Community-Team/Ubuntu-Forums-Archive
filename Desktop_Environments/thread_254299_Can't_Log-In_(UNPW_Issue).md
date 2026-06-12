---
title: "Can't Log-In (UN/PW Issue)"
date: 2006-09-09
forum: Desktop Environments
---

### Post by SFOExPat on 2006-09-09
I installed Ubuntu a while ago and played with it a bit...but haven't been on it for several weeks and I've either forgotten/lost my username and password...not sure which one is the particular issue...

After repeated attempts to use this forum today, and it only coming up 30% of the time, I've tried various things I've come across, I'm at a loss of what to do next...](*,) ...and trying to use these forums today, to get them to come up, has been frustrating at best...I have tried the following:

1. Tried to reboot from the CD, but it never gets to that point...just boots into Ubuntu...

2. Trying accessing the BIOS without success...I know during boot to press the F5 or F8 key used to work, but neither does anymore...I see a flash of where that option is, but its just that, a flash, and the boot into Ubuntu starts again...

3. I've even attempted to use a floppy based boot loader program which was mentioned on one of the forum posts without success...

3. I get to the recovery mode and am faced with:

root@sfoexpat-2nd:~#

(this tells me I have the correct username)

I'm not sure what to do now, as I can't even get to the bios to even attempt to change the boot sequence...I'm not even sure at this point how I could wipe the drive and start over, outside of hooking it up in another system as a slave and wiping it that way...

Any and all thoughts/hints/ideas would be greatly appreciated...

Dave

---

### Post by mssever on 2006-09-10
In recovery mode, type
```
ls /home
``` You'll see a folder named after your username. (What you thought was the username--in the prompt--is really your machine name.)

Type
```
passwd yourusername
``` and set a new password. Then, you can log in normally. Type "reboot" to reboot.

If you wanted to uninstall Ubuntu, you simply need to delete Ubuntu's partitions.

I don't know much about the BIOS, though.

---


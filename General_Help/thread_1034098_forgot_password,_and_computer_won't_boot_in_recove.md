---
title: "forgot password, and computer won't boot in recovery mode"
date: 2009-01-08
forum: General Help
---

### Post by enstra on 2009-01-08
I am an absolute beginner with ubuntu, and seem to have forgotten my admin password (thought I knew it, but computer isn't accepting it).  I saw a thread that advised restarting in recovery mode, but my computer won't do this (tried hitting Esc as GRUB thing was loading, but all it did was load really slowly in normal mode and then freeze my mouse when it finally did load) -  any ideas?

---

### Post by Ahadiel on 2009-01-08
You could load the liveCD,

become root
```
sudo su
```

mount your / partition
```
mkdir /mnt/os
mount /dev/??? /mnt/os
```

chroot into it
```
chroot /mnt/os
```

change your password
```
passwd username
```

then leave the chroot ('exit' or Ctrl+D) and unmount the previously mounted drive.
```
umount /mnt/os
```

Reboot and you *should* be able to login with your new password.

---

### Post by mcduck on 2009-01-08
> **enstra said:**
> I am an absolute beginner with ubuntu, and seem to have forgotten my admin password (thought I knew it, but computer isn't accepting it).  I saw a thread that advised restarting in recovery mode, but my computer won't do this (tried hitting Esc as GRUB thing was loading, but all it did was load really slowly in normal mode and then freeze my mouse when it finally did load) -  any ideas?

When you start the recovery mode it will load for a while, and then you get a dialog asking what you want to do (resume/clean/dpkg/fsck/root/xfix). The first option is to resume normal boot, which you must have selected since it continued normal boot. What you need to select here is the "root"-option, which will drop you into root shell prompt.

---

### Post by amyf on 2009-01-09
So, I have the same problem-forgot my admin password & I have a Mini 9 with no CD drive.  Can you walk me through how to change the password?

Thanks

---

### Post by mcduck on 2009-01-10
When you boot the computer, select "recovery mode" from the Grub menu (if the menu doesn't show by default you should see a message that tells you to press Esc to open the menu).

You'll see some text scrolling on the screen for a while until another menu opens, now with options (resume/clean/dpkg/fsck/root/xfix). Use the arrow keys & Enter to select "root" and you'll end in command line as root user.

Now all you need to do is to run "password *yourusername*" and you will be able to set your user's password. When you've done that, run "reboot" to restart the computer.

---

### Post by amyf on 2009-01-11
This is my first laptop with ubuntu, so sorry if this is a stupid question.  I don't understand how to get the GRUB menu to come up.  I press escape but it still boots normal.  I see no 'recovery mode option' while it is booting.  Help please??

---

### Post by mcduck on 2009-01-12
Slightly after you have turned the computer on, (After all the BIOS stuff, but before the Ubuntu logo) you should see a text appear on top of the screen, saying somehting like "Grub loading, please wait.. Press Esc to enter the menu" and a number counting down.

This text will only show for 3 seconds before Grub starts loading Ubuntu. So you need to be quick.

When you press Esc the Grub menu will appear.

---


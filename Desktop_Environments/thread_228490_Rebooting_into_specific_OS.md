---
title: "Rebooting into specific OS"
date: 2006-08-03
forum: Desktop Environments
---

### Post by allanlewis on 2006-08-03
Hi,

Does anyone know of a way to run some sort of script from Ubuntu that will restart the PC in a specific OS? (i.e. a specific grub entry)

I asked on the Gnome forums and was told to use boot-admin, which is part of the gnome-system-tools package. However, it seems that the Ubuntu version of this package doesn't include the boot-admin tool, possibly because it might clash with the Debian "automagic" system that updates grub's menu when a new kernel is installed.

Either way, does anyone know of a tool or script which can do the same job?

Thanks in advance!

---

### Post by Tomosaur on 2006-08-03
Haha more problems? The thing is, you won't be able to stop grub loading, so you can't really just boot straight into a different OS. The most you can do is set grub to whatever option you want, turn its timeout setting right down, and for the final move, hide it so it doesn't show up. I personally would be very wary of hiding grub or indeed turning the timeout right down, because if you set it to always just boot into windows, with a timeout of 0, and a hidden grub menu, then you're going to have to do a little more work to get back into Ubuntu. Although apparantly, as you pointed out, you can get XP to read and write to an ext2 or ext3 filesystem, it just seems like unneccessary work.

If you decide to do everything I said not to above, you can always just keep one of the keyboard arrow keys pressed down while your machine boots up, thereby hopefully cancelling the timeout. If you manage to do that successfully, then you can press the Esc key to show the grub menu and you should be able to select Ubuntu from that. I PMd you the latest version of my script which will allow you to do all that, but [ here's a link to the thread I mentioned it in](http://www.ubuntuforums.org/showthread.php?t=227300). I would reccommend you scrap the old script I sent you and use the new one. It's a lot safer, easier to use, and  is able to edit more of Grub's options.

---

### Post by mcduck on 2006-08-03
> **Tomosaur said:**
> Haha more problems? The thing is, you won't be able to stop grub loading, so you can't really just boot straight into a different OS. The most you can do is set grub to whatever option you want, turn its timeout setting right down, and for the final move, hide it so it doesn't show up. I personally would be very wary of hiding grub or indeed turning the timeout right down, because if you set it to always just boot into windows, with a timeout of 0, and a hidden grub menu, then you're going to have to do a little more work to get back into Ubuntu. Although apparantly, as you pointed out, you can get XP to read and write to an ext2 or ext3 filesystem, it just seems like unneccessary work.

If you decide to do everything I said not to above, you can always just keep one of the keyboard arrow keys pressed down while your machine boots up, thereby hopefully cancelling the timeout. If you manage to do that successfully, then you can press the Esc key to show the grub menu and you should be able to select Ubuntu from that. I PMd you the latest version of my script which will allow you to do all that, but [ here's a link to the thread I mentioned it in](http://www.ubuntuforums.org/showthread.php?t=227300). I would reccommend you scrap the old script I sent you and use the new one. It's a lot safer, easier to use, and  is able to edit more of Grub's options.
If the timeout is set to 0 and the menu is hidden, you still get a messae text about pushing a button to enter the menu, with a timeout of 3 seconds or something like that.

So you can hide the menu, but you can't lock yourself out of it or anything like that ;)

---

### Post by allanlewis on 2006-08-03
Thanks, both of you! Do you know if LILO is more flexible in this regard?

Also, can anyone write a windows batch-file that will do the same from the other side? (...bearing in mind that I can write to any location on my Linux partition.)

---

### Post by allanlewis on 2006-08-03
Thanks, both of you! Do you know if LILO is more flexible in this regard?

Also, can anyone write a windows batch-file that will do the same from the other side? (...bearing in mind that I can write to any location on my Linux partition.) If not, does anyone know what windows tool I could use in a batch script to edit a text file on my linux filesystem (which appears to Windows as an ordinary drive, which I called L: for Linux) *and* save it in Unix format... difficult one, methinks.

And Tomosaur, I read that other thread you linked to and your script is great! However, I notice that I have an app called "grub-set-default" (I assume it's part of the standard grub package) that can set the default entry to boot from, so I could easily make a couple of launchers on the desktop that change the default from the Ubuntu entry to the Windows entry (which I moved to the other side of the "automagic" list, i.e., position 0), and vice versa.

---


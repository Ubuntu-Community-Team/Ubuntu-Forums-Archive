---
title: "Kernal panic"
date: 2024-11-25
forum: Desktop Environments
---

### Post by tinman456 on 2024-11-25
Hi everyone,

My question is that I just started to get a kernal panic error on booting my version 24.04 on an HP dv4 laptop. It's been running perfectly well for months and I recently upgraded to the latest version (Nobel Numbat) which also was working fine until this happened.

When it crashes I have to power the laptop down and on restart it gives me a menu with Advanced Options. So I can go there and I get a sub menu that provides four options. If I go to the the first option which is "Ubuntu, with Linux 6.8.0-49" it crashes with the kernal panic but if I choose the option "Ubuntu, with Linux 6.8.0-48" it boots up as normal and seems to run fine.

The laptop passed both a memory test and a HDD test.

Any ideas on how I can fix this problem?

---

### Post by grahammechanical on 2024-11-25
I do not have any ideas on how to fix the problem but to suggest that the matter might be resolved with a further kernel update. I am using the Linux 6.8.0-49 kernel. No problems.

Here is something to watch out for. The Software Updater utility will remove older kernels when it upgrades to a newer kernel. It will remove Linux 6.8.0-48 which works. What if the new kernel is also broken. You will not be able to boot at all.

Continue using Advanced Options to load that Linux 6.8.0-48 and use the terminal to update. And do not run the autoremove command or Software Updater until you have at least two working kernels.

I was using Ubuntu 20.04 until an update broke the install. Both kernels were broken. For a few weeks I used Advanced Options recovery mode to update/upgrade 20.04 in the hopes that it would get fixed. Then I gave up and switched to using Ubuntu 24.04 which I was dual booting with. Months later I was on the point of installing over the 20.04 partition when I gave it one more try at updating/upgrade 20.04 using recovery mode. Lots of packages were downloaded and to my surprise I now have a working 20.04 installation that is in support because I had subscribed to Ubuntu Pro for that installation. I did not really want to lose 20.04.

Regards

---

### Post by yancek on 2024-11-25
If the problem is the newest kernel doesn't work for whatever reason, you can set another kernel to boot by checking the entries on the Grub menu.  One way to do it after you determine which entry has the kernel you want to boot is to change the line below in the grub.cfg file.  The entry below shows 0 as the default and since Grub counts here from zero, if the entry you want is the 3rd entry, you would change the 0 to a 2.  If you do this change in grub.cfg, do not run update-grub.

> set default="0"   

If you want a more permanent change, you can make the same edit by changing the number in the /etc/default/grub file which entry is at the top of the file.  If you use this method, do run sudo update-grub.

>  GRUB_DEFAULT=0

Another way is while booted into your Ubuntu, you change the line above in the /etc/default/grub file by replacing the 0 with the word saved.  Again run sudo update-grub.  Editing these files requires sudo privileges.  The link below to ubuntu.com explains all this and much more in detail.

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

---

### Post by tinman456 on 2024-11-25
Thank you so much. I will try what you suggested.

---

### Post by tinman456 on 2024-11-25
Again that is a great option. Thanks very much for you suggestions. I'm a lot more confident now. Appreciate everything.

---


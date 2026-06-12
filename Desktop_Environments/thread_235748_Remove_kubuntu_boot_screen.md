---
title: "Remove kubuntu boot screen"
date: 2006-08-13
forum: Desktop Environments
---

### Post by mtdewulf on 2006-08-13
So I wanted to try out KDE and I installed kubuntu via "sudo apt-get install kubuntu-dekstop".  However, I decided I did not like KDE and so I removed it with the information I found on this site:

[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

Now I am back to almost pure gnome except that when I boot up the computer, instead of seeing the orange / brown ubuntu logo, I see the blue / white kubuntu logo.  Is there anyway to get this back to normal?

Thanks,
Mike

---

### Post by vijirajan on 2006-08-13
Execute the following command and let me know the result:

```

sudo update-alternatives --list usplash-artwork.so

```

---

### Post by llamakc on 2006-08-13
I also just had & solved this problem. Changing the default /etc/alternatives/usplash-artwork.so will immediately affect the shutdown splash but to get the bootsplash working again you need to also do a 

dpkg-reconfigure linux-image`uname -r`

and reboot.

---

### Post by Leonivek on 2006-08-13
I have something similar to this.  I installed KDE, I am keeping it on, but since then, my login screen is too big to fit the screen.  If I want to access the Options menu (bottom left) on the login screen or see the date (bottom right), I have to "push" the edges of the screen to see them. This is only an issue for the login screen.  I've tried all of the above commands to see if that would fix it.  I've tried every setting I could find on the system and nothing worked.  

I realize this issue is different than the original post, but it happened because of the same reason: installing KDE in Ubuntu.  I was hoping that someone has a solution for this?

Thanks!

[Edit] Nevermind... found the solution here after using other keywords in my searches:  [http://www.ubuntuforums.org/showthread.php?t=225339](http://www.ubuntuforums.org/showthread.php?t=225339)

---

### Post by alan_new on 2007-07-17
It doesn't work for me. Same story but with Ubuntustudio. I installed it, then unistalled it (removed it completely) and the start screen with the Ubuntu logo and the progress bar is gone. I reinstalled the "usplash" and "usplash-theme-ubuntu" packages, reinstall "ubuntu-desktop" but nothing was usefull. I then followed the above procedure, but when I run "sudo dpkg-reconfigure linux-image-`uname -r`" I get this:

```
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.20-16.29 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.20-16.29 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz


You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
**[COLOR="Red"]Searching for splash image ... none found, skipping ...[/COLOR]**
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/vmlinuz-2.6.17-11-generic
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

How is possible that there's no splash image?

---

### Post by alan_new on 2007-07-17
Problem is solved.

I run G Alternatives and under usplash-artwork.so I checked the "Choise" button. It was unchecked.

---


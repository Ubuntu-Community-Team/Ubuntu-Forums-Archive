---
title: "Is it possible to *temporarily* change the boot oder of Grub2"
date: 2012-09-09
forum: Desktop Environments
---

### Post by sefs on 2012-09-09
Hi all,

Setup is Ubuntu 12.04 with grub2, and a second OS that is not linux.


My situation is that this computer is not on my location and I boot it remotely.  By default it boots to Ubuntu.  Is there a way that while to change the boot order temporarily  for just one reboot to access the other OS, and then on reboot it reverts back to Ubuntu as the default?

My problem is if I were to change the boot order via .cfg from ubuntu, once it is in the other OS there is no way to change back the boot order so it would continue to boot to this other OS until I can physically get to it.

Thanks.

---

### Post by Merrattic on 2012-09-09
Try a symlink to /boot/grub/boot.cfg to a place that both OS can read from and write to ?
 ( I am just guessing this would work)

You could do some scripting to make the swap easier

---

### Post by Cheesemill on 2012-09-09
Use the grub-reboot command.
> Set the default boot menu entry for GRUB, for the next boot only.
For example:
```
sudo grub-reboot 1
```
Will boot the 2nd entry (start counting at 0) on your grub menu for the next boot only before reverting to the default selection.

You can also use the entry title instead, for example:
```
sudo grub-reboot "Microsoft Windows 7"
```

If you want to find out your menu entry titles (because you never see the grub menu) you can do:
```
rob@arch:~$ sudo grep menuentry\  /boot/grub/grub.cfg
menuentry 'Arch GNU/Linux, with Linux ck kernel' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-ck kernel-true-f174ca41-91e0-4f9c-bec5-713a9353acdd' {
menuentry 'Arch GNU/Linux, with Linux ck kernel (Fallback initramfs)' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-ck kernel-fallback-f174ca41-91e0-4f9c-bec5-713a9353acdd' {
menuentry "Microsoft Windows 7" {
```


Take a look at the man page, it's one of the shortest I've ever seen.

---

### Post by Merrattic on 2012-09-09
Thanks Cheesemill, I learnt something there with regard to the reboot command. Your grep command doesn't work for me and I don't think you need to run sudo either? This one worked for me:
```
grep menuentry /boot/grub/grub.cfg
``` following the examples [here]("http://www.thegeekstuff.com/2009/03/15-practical-unix-grep-command-examples/") producing
```
menuentry 'Ubuntu, with Linux 3.2.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
```:)

---

### Post by Cheesemill on 2012-09-09
> **Merrattic said:**
> Your grep command doesn't work for me and I don't think you need to run sudo either? This one worked for me:
As you may have noticed I was on my Arch system at the time, which has different permissions on grub.cfg, I incorrectly presumed it would be the same with Ubuntu.
```
rob@arch:~$ ls /boot/grub/grub.cfg
-rw------- 1 root root 3.9K Sep  6 19:17 /boot/grub/grub.cfg
```Also if you didn't copy and paste there are 2 spaces between menuentry\ and /boot in my grep statement.

---

### Post by oldfred on 2012-09-09
You also need the saved setting. See drs305's comments.

[http://ubuntuforums.org/showthread.php?t=1310463](http://ubuntuforums.org/showthread.php?t=1310463)

---

### Post by sefs on 2012-09-09
Thanks guys this is exactly what I was looking for!

From the linked thread....

> 
It works like this:
In /etc/default/grub
1. Set GRUB_DEFAULT to
GRUB_DEFAULT=saved

2. sudo update-grub

3. Set default OS to load (this will load every time you reboot machine, unless option 4 is used)
sudo grub-set-default 0

4. When need to load other OS (number is a menu number of OS as in /boot/grub/grub.cfg, this will load other OS only once during next reboot - reboot to be started manually):
sudo grub-reboot 4

It works for me. More information on those commands @https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode


Some questions I have are...

I have some questions on this that I don't understand.

1/
Will this work if my grub2 is on a dedicated partition.

2/ What does this mean "unless option 4 is used" in point number "3."

2/ is sudo grub-reboot 4 going to load the 5th entry?

---

### Post by oldfred on 2012-09-09
If you have a dedicated grub, you have to manually maintain it. Then doing  sudo-update grub and any settings in  /etc/default/grub do not apply. So no.

Entries start at 0, so entry 4 will be the fourth entry if the first entry is 0. 

It just means the default is used unless you override the default with the one time setting.


If you have a separate grub partition, make it FAT32 and use scripts in each system to change the default setting.
set default="0"

---

### Post by Merrattic on 2012-09-11
> **oldfred said:**
> Entries start at 0, so entry 4 will be the fourth entry if the first entry is 0. 

0 = 1st entry
1 = 2nd entry
2 = 3rd entry
3 = 4th entry
**4 = 5th entry**

??

---


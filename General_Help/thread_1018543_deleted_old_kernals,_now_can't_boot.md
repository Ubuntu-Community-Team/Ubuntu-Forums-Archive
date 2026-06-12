---
title: "deleted old kernals, now can't boot"
date: 2008-12-22
forum: General Help
---

### Post by hudson7 on 2008-12-22
well, like the title says...

I'm running Ubuntu 8.04 upgraded to 8.10. So I deleted three old kernals and now the system won't boot...I get an error "file not found" and press escape and end up at the boot menu which just has the 8.04 kernals listed.

I know, I feel very stupid! Any advice would be greatly appreciated ;-)

---

### Post by bluefrog on 2008-12-22
with a rescue cd (or 8.04 live cd or whatever live cd) see if you reaaly have installed 8.10. basically do you have /boot/vmlinuz-2.6.27-10-generic and /boot/initrd.img-2.6.27-10-generic (or whatever number)?

if yes then it is just a matter of editing /boot/grub/menu.lst

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.27-10-generic root=/dev/hda1 ro quiet splash 
initrd		/initrd.img-2.6.27-10-generic
quiet

adapt to the topology of your disk

you could also mount your / from the live cd then chroot to it

mount /dev/hda1 /mnt
sudo chroot /mnt

and finish the install /upgrade from there
sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by amdalex on 2008-12-22
Are you sure you didn't delete the kernals for 8.10? Does it boot from any of the other kernals?

---

### Post by caljohnsmith on 2008-12-22
In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup.

---

### Post by hudson7 on 2008-12-22
Thanks guys! I booted from the livecd, mounted my local drive, ran the script and was able to edit menu.lst and now the computer is booting again.

:-) :-) :-)

---


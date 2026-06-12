---
title: "mount usb hard drive (ntfs partition)"
date: 2005-05-21
forum: Desktop Environments
---

### Post by adrislayer on 2005-05-21
Hi

I wanted to mount my usb hard drive on usb wich contains all my personnal data to move it into a linux parititon. So I searched accross the web and find that with this command you can mount it without problem:

sudo mkdir /mnt/external
sudo mount /dev/sda1 /mnt/external -t ntfs

and then you only must go into that repertory you created, it's ok, fine but...

I can't find the so called sda... In dev I haven't anything called sda1 2 etc.

So I wonder if it has another name on kubuntu, I have plenty of md1 but i don't think it is that.

Also when I go into KInfoCenter, on USB Devices I find the nVidia Corporation nForce 2 USB Controller (3) and in it the storage device connected on usb...

Now, how???, please help

---

### Post by adrislayer on 2005-05-21
sorry, it's ok, just that the usb sda sda1 appears after the usb device is installed.

I had to reboot the X server to have it with ctrl alt backspace.

The commands above works fine if someone would know how to do...

Now how to acces with another user than the root one... Thats another story

---

### Post by lamotte on 2005-06-02
I havent used ubuntu much but on my gentoo box all you had to do was add a simple line into your fstab file.  Unless youre using captive ntfs which it doesnt look like you are.

For read only permissions add:

#####/etc/fstab

/dev/sda1     /mnt/sda    ntfs  user,uid=<username>      0   0



after you do this... just type...

%  mount /mnt/sda




sorry i had to edit the "r,"   take that out of your /etc/fstab if you viewed it before i changed

---


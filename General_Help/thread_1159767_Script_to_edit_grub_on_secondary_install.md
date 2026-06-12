---
title: "Script to edit grub on secondary install"
date: 2009-05-15
forum: General Help
---

### Post by rogerdean on 2009-05-15
Hello folks

I'm a compulsive beta tester, so every time I install a secondary test distro I have to boot into it and edit /boot/grub/menu.lst to get my primary OS as default again

I'd like a little script to help me edit the test system's menu.lst from within my main OS. So for I've got this...

```
sudo mkdir /media/grub
sudo mount /dev/sda5 /media/grub
sudo gedit /media/grub/boot/grub/menu.lst
#need delay/pause here
#sudo umount /media/grub
```

(of course I'd have to change the device on line 2 every time I install to a different partition - guess there's nothing I can do about this)

It works fine, but as you can see I'd like to unmount the secondary drive automatically when I've finished editing so that it doesn't interfere with other things.

So I need a command on line 4 to pause the script until I've closed gedit. Should be simple - can anyone advise?

Many thanks!
Roger

---

### Post by lloyd_b on 2009-05-15
> **rogerdean said:**
> Hello folks

I'm a compulsive beta tester, so every time I install a secondary test distro I have to boot into it and edit /boot/grub/menu.lst to get my primary OS as default again

I'd like a little script to help me edit the test system's menu.lst from within my main OS. So for I've got this...

```
sudo mkdir /media/grub
sudo mount /dev/sda5 /media/grub
sudo gedit /media/grub/boot/grub/menu.lst
#need delay/pause here
#sudo umount /media/grub
```

(of course I'd have to change the device on line 2 every time I install to a different partition - guess there's nothing I can do about this)

It works fine, but as you can see I'd like to unmount the secondary drive automatically when I've finished editing so that it doesn't interfere with other things.

So I need a command on line 4 to pause the script until I've closed gedit. Should be simple - can anyone advise?

Many thanks!
Roger

```
sudo mkdir /media/grub
sudo mount /dev/sda5 /media/grub
sudo gedit /media/grub/boot/grub/menu.lst
read -p "Press <RETURN> after closing gedit window"
sudo umount /media/grub
```

Lloyd B.

---

### Post by rogerdean on 2009-05-15
Magic! Thanks very much

---


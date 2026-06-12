---
title: "[SOLVED] Updating /menu.lst?"
date: 2009-01-10
forum: Desktop Environments
---

### Post by alexham on 2009-01-10
Hi,

I have just downloaded the latest updates and during the installation I was asked what I wanted to do with /menu.lst  - install new or keep "locally modified".  I opted to keep the locally modified version, but I am not sure if that was the right thing to do.  There is a file menu.lst in /boot/grub but there are also 2 others called menu.lst.save and menu.lst.save.1, but these are marked with a square with diagonals in a orange dot and the system cannot open them.

If I save /boot/grub/menu.lst onto a USB memory stick, would I be able to paste it on top of the updated menu.lst if some of my peripheral stopped working?

And what shall I do about the other 2? Delete them?

Best Regards,

Alex

---

### Post by taurus on 2009-01-10
Those two versions are your backups.  If you want to edit /boot/grub/menu.lst, you need to use a text editor with a root privilege.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by alexham on 2009-01-10
> **taurus said:**
> Those two versions are your backups.  If you want to edit /boot/grub/menu.lst, you need to use a text editor with a root privilege.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thank you Taurus, but can you tell me a little more?
For instance, if I chose to upgrade menu.lst will the system automatically create a backup of the present "locally modified one" that I could revert to if need be?

Regards,

Alex

---

### Post by caljohnsmith on 2009-01-10
You could copy your current menu.lst to a different location like you mentioned (like your USB stick), and then update your current menu.lst with any new kernels by doing:
```
sudo update-grub
```
If for some reason the Grub updater doesn't do a good job about modifying your menu.lst correctly, you can easily revert to the original one by copying it back over from your USB stick. If the Grub updater does have problems though, that's usually an indication that some of the "automagic kernel list" options in your menu.lst need correcting. I would suggest running the update-grub command above, and then if for some reason your menu.lst is not what it should be, post it back here so we can help you sort out the root problem. Good luck and let us know how it goes.

---

### Post by RedMartin on 2009-01-10
I've elected to keep the locally modified version for the last two updates and only yesterday realised that I wasn't using the latest kernel.

[http://ubuntuforums.org/showthread.php?t=1035647](http://ubuntuforums.org/showthread.php?t=1035647)

Not an exact answer to your question but it might shed some light on what will happen.

---

### Post by alexham on 2009-01-11
> **caljohnsmith said:**
> You could copy your current menu.lst to a different location like you mentioned (like your USB stick), and then update your current menu.lst with any new kernels by doing:
```
sudo update-grub
```
If for some reason the Grub updater doesn't do a good job about modifying your menu.lst correctly, you can easily revert to the original one by copying it back over from your USB stick. If the Grub updater does have problems though, that's usually an indication that some of the "automagic kernel list" options in your menu.lst need correcting. I would suggest running the update-grub command above, and then if for some reason your menu.lst is not what it should be, post it back here so we can help you sort out the root problem. Good luck and let us know how it goes.
Thank you Caljohnsmith. I have done the update and everything still works as before.

Thanks again,

Alex

---


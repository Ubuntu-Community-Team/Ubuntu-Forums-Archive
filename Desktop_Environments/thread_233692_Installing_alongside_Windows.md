---
title: "Installing alongside Windows"
date: 2006-08-10
forum: Desktop Environments
---

### Post by hitman012 on 2006-08-10
After looking at Dapper on an older system, I'm going to install Ubuntu on another drive on this machine alongside my Windows installation. My concern is that Grub will overwrite the Windows bootloader, which I do not want.

I have a main 250GB drive and a 40GB one; if I install Ubuntu on the 40GB drive, will it install a bootloader to the 250 or just leave that alone? I'd rather choose which to boot from at BIOS startup than overwrite Windows' bootloader with Grub (especially given that fixboot and fixmbr don't seem to get rid of it?)

Thanks in advance.

---

### Post by bulldog on 2006-08-10
If you use the live cd you can put the power off the 250 Gyg.
So only the 40 Gyg is visible and Grub will be installed on this drive.

You could concider to download the "alternate" cd which give you the possibility to choose on which drive you want to install Grub.

You may choose which way you want it.

---

### Post by Tomosaur on 2006-08-10
The windows boot loader will not be overwritten, it doesn't work the same way Grub does. If you select Grub to boot into windows, you will be taken to the windows bootloader (if it's enabled of course).

---

### Post by hitman012 on 2006-08-10
Many thanks for your quick advice. I unplugged the 250GB drive and it's all functioning as I need it to :)

---

### Post by murataht on 2006-08-10
congratulations! smart move. 

it would not hurt if you edit the topic and add a [solved] mark. thanks.

---


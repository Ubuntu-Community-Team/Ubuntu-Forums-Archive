---
title: "How to install Live USB Creator on Mini 9?"
date: 2009-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by epb223 on 2009-05-22
I have a Mini 9 with Dell's Ubuntu 8.04 and I can't understand how to install Live USB Creator so that I can get 8.10 and then maybe 9.04. I can't seem to find any instructions online that I can understand.

Any help appreciated.

Edward

---

### Post by snowpine on 2009-05-22
Hi Edward, Live USB Creator is a feature of Ubuntu 8.10 and newer, so no luck there. However, the Unetbootin utility does the same thing and should work okay in 8.04: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Kevbert on 2009-05-22
You can use the USB-creator package that is [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/intrepid/usb-creator"). This is the package for 8.10, but it also works in 8.04. Click on 'all' under architecture and then select a download site in your country. Instead of 'Save File' select 'Open with GDebi Package Installer' to open the installer.
Once installed this will appear under System-Admin as 'Create a USB startup disk' (you may need to reboot to get this menu item, I can't remember if it's necessary).

---

### Post by anjilslaire on 2009-05-22
You can also do
```
sudo apt-get install usb-creator
```

However, I suspect you may run into issues with th LPIA architecture of the DELL-supplied 8.04 OS. However, if you can get it installed, it should be smooth sailing. 
You can also open Synaptic and select it for installation, if it's in Dell's repositories.

---

### Post by ugm6hr on 2009-05-22
Why not just download the 9.04 Netbook Remix img file.  There are easy instructions on how to create a LiveUSB directly from this file using Terminal.

[https://help.ubuntu.com/community/Installation/FromImgFiles#Ubuntu](https://help.ubuntu.com/community/Installation/FromImgFiles#Ubuntu)

---

### Post by epb223 on 2009-05-24
> **snowpine said:**
> Hi Edward, Live USB Creator is a feature of Ubuntu 8.10 and newer, so no luck there. However, the Unetbootin utility does the same thing and should work okay in 8.04: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I downloaded this program, but when I tried the command chmod +x ./unetbootin-linux, as directed in the instructions, I got this response:
chmod: cannot access `./unetbootin-linux': No such file or directory.

---

### Post by epb223 on 2009-05-24
> **Kevbert said:**
> You can use the USB-creator package that is [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/intrepid/usb-creator"). This is the package for 8.10, but it also works in 8.04. Click on 'all' under architecture and then select a download site in your country. Instead of 'Save File' select 'Open with GDebi Package Installer' to open the installer.
Once installed this will appear under System-Admin as 'Create a USB startup disk' (you may need to reboot to get this menu item, I can't remember if it's necessary).

This package installed successfully, but when I open it, the Ubuntu img file doesn't show up under "source disc", regardless of what volume it's on (Cruzer, other media).

---

### Post by snowpine on 2009-05-24
> **epb223 said:**
> This package installed successfully, but when I open it, the Ubuntu img file doesn't show up under "source disc", regardless of what volume it's on (Cruzer, other media).

I would have given you different advice if I'd known you were trying to install an .img instead of an .iso. Unetbootin and USB Creator only work with .iso.

For an .img (such as Ubuntu Netbook Remix) you need to follow these instructions: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

---


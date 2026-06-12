---
title: "New video card install problems"
date: 2006-08-18
forum: Desktop Environments
---

### Post by The Pinny Parlour on 2006-08-18
Long

Firstly, thank you to those who reply.

I have a ubuntu box happily running dapper for a while now. I had a s3 savage4 in it. today I wanted to upgrade the video card to nvidia 7600gs agp. Started the pc and xserver-xorg has freaked out. I have attempted to reconfigure using: sudo dpkg-reconfigure xserver-xorg, but when I get to "Please select your desired default color depth in bits", I select the default (24) and bang. It jumps straight out of xserver-xorg and into the CLI saying:

"xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf/20060818195139" (<--obviously date and time)
<name>@ubuntu:~$

I have reverted back to the S3 Savage4 and get the same thing now.

Any help on what to do would be most helpful.

Thanks
Ian

---

### Post by The Pinny Parlour on 2006-08-18
I just found this from user tseliot, and it worked:

<quote>
 Default  Re: Linux guru, please help. "Failed to start the X server"
Quote:
Originally Posted by PandaToledo
"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.200602071512
This just warns you that it's overwriting your xorg.conf. In other words it's not a problem.

Do this:
sudo nano /etc/X11/xorg.conf

then scroll down the file and get to the Section "Device"
and set the driver to "vesa" like in the following example:
Code:

Driver "vesa"


Press:
CTRL+O to save the file (yes, overwrite it)
CTRL+X to exit

then type:
sudo /etc/init.d/gdm stop (or "kdm stop" if you use Kubuntu)
sudo /etc/init.d/gdm start (or "kdm start" if you use Kubuntu)
__________________
UDSF | My Website | My Envy Script | My Blog 
</quote>

Thank you tseliot  :)

---


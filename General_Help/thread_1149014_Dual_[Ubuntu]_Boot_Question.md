---
title: "Dual [Ubuntu] Boot Question"
date: 2009-05-04
forum: General Help
---

### Post by rdmike on 2009-05-04
I've had Kubuntu up and running well for a few days now and today decided to try a dual boot with Ubuntu Studio. In order to get Kubuntu installed originally I had to install in safe mode and then update the video driver because of my Nvidia 6150e adapter. Anyhoo, there was no option to do this for Ubuntu Studio and so now that I have US installed I cannot see anything but a black screen. Is there a simple way to either a) update the driver or b) remove it completely while keeping Kubuntu intact?

---

### Post by brettg on 2009-05-04
To possibly make the screen visible you can try disabling the nvidia binary drivers (if they are in use). Edit xorg.conf and change "nvidia" to "nv" in there.

To remove it completely, just format the partion(s) that you installed it to (from the kubuntu install). 

sudo mkfs -t ext3 /dev/sda3 (Change the sda3 to whatever the correct drive is)

!!WARNING!! If you format the wrong partition then you WILL bork your kubuntu install.

To remove the Ubuntu Studio from your grub selection screen edit /boot/grub/menu.lst, find the entries for US and remove them.

!!WARNING!! If you remove the wrong entry you may stop your system from booting. To be sure I recommend you just rem out one of the entries (leave the recovery entry there) If after rebooting your system wont start choose the recovery option and then fix your menu.lst. If it is OK, you can remove the recovery entry as well

---

### Post by rdmike on 2009-05-05
Is there a way to boot into Ubuntu Studio in safe mode where I can then update the graphics driver?

---

### Post by brettg on 2009-05-05
For instructions on booting into single user mode (console mode) look here;

[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

---

### Post by rdmike on 2009-05-06
Ok, I followed that guide but it didn't address the issue and I still could see my desktop. 

So, it turns out  I was able to use Ctrl>Alt>F to log into the terminal. From there I was able to install the driver via the command sudo apt-get install nvidia-glx-180.

Still, I could not get a visible screen. So, I typed sudo nvidia-xconfig which produced the following error;

*"VALIDATION ERROR: Data incomplete in file /etc/x11/xorg.conf. At least one Device section is required."*

So, I tried the command sudo gedit /etc/x11/xorg.conf which produced an error stating; "*Display could not be produced*."

I'm still fairly new to linux but I think if I can get into the xorg file I can add the device section along with a command (not sure how it would be written) for the OS to use the nvidia driver.

So how do I do that? lol

---

### Post by rdmike on 2009-05-06
So whatcha think?

---

### Post by rdmike on 2009-05-07
Ok folks, this one is apparently solved.

The guide BrettG mentioned didn't help as I still couldn't see anything but in my searches after going through the guide I saw a post mentioning the use of Alt?Crtl>F2 to bring up the terminal in a similar situation. Long story short, I brought up the terminal and installed the driver via sudo apt-get; woohoo!

Thanks everyone for your replies!

---


---
title: "ubuntu 10.04, 64bit, BCM4312 don't work"
date: 2010-11-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PengMeng on 2010-11-05
My laptop is Dell Inspiron 1110 with Win 7.
I have Wubi installed Ubuntu 10.04, 64bit.
But the wireless card is not working, the wireless card is &#65314;&#65315;&#65325;&#65300;&#65299;&#65297;&#65298;&#65294;

[FONT=Arial][COLOR=black]My computer has no wire connection, also no CD driver. [/COLOR][/FONT]

[FONT=Arial][COLOR=black]How can solve the problem? Any one can help?[/COLOR][/FONT]

[FONT=Arial]P.S. [/FONT]
[FONT=Arial]I have used "lshw" command to show the hardware information.[/FONT]
[FONT=Arial]There are **three** "*network" information[/FONT] and one of them is "**disabled**".
My computer just has one wire network card and one wireless network card, I don't know why there are three network information. 

Any suggention will be appreciated!

---

### Post by Mike_tn on 2010-11-06
> **PengMeng said:**
> My laptop is Dell Inspiron 1110 with Win 7.
I have Wubi installed Ubuntu 10.04, 64bit.
But the wireless card is not working, the wireless card is &#65314;&#65315;&#65325;&#65300;&#65299;&#65297;&#65298;

Hi PengMeng and welcome. I'm almost as new as you but had the same problem with my Dell Inspiron. I tried Wubi to start also.  So I have a warning for you in a minute regarding that.  The Broadcom b43 driver problem is well documented.

This Ubuntu thread & page tells you how to get it if you can hook up to a wired connection.

[http://ubuntuforums.org/showpost.php?p=9712852&postcount=781](http://ubuntuforums.org/showpost.php?p=9712852&postcount=781)

I'll go over it here. I'll copy and paste from that page. If you look at that page just skip the links that take you to getting the latest kernel, those are old links by now and not essential to getting online.  But you need to do the rest of it probably, if you had the same problem as I did. If you can get on-line with the machine that needs the wireless driver firmware then follow this, in a nutshell summary this is the job:

1)You may be able to skip this step. Remove the Broadcom STA driver and the b43-fwcutter package, **IF** it's installed. You may have installed these in your attempt to make it work. If so, you can go into the synaptic package manager and search the names and then uninstall if needed. If they won't uninstall you may need to use the terminal to do it.  There are instructions to remove the cutter on that post.

Code> 
sudo apt-get remove b43-fwcutter bcmwl-kernel-source

2)Get somehow (the hardest part) the b43 firmware and install it.  You can make the package using the instructions on that thread. Just copy and paste the code into the terminal. It will get a source material, cut and install the driver for you. If you can't get online with a wired connection to do this then either browse some of the previous pages of that thread link above or send me a private message and I can help you that way.

Code> 
cd ~
mkdir b43-files
cd b43-files
wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2)
tar xjf b43-fwcutter-013.tar.bz2
cd b43-fwcutter-013
make
cd ..
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo ../../b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

3)The new b43 firmware might only run a minute or half hour then freeze the pc so you have to tweak some settings to keep it running. This is a one time fix. Put this code in the terminal after you install the firmware

Code
> sudo touch /etc/modprobe.d/b43.conf
echo "options b43 pio=1 qos=0" | sudo tee -a /etc/modprobe.d/b43.conf

Hit enter and reboot the machine. Should be OK

Be warned. If it works and then you do your numerous updates through the update manager you may have to do a Grub Rescue if your laptop doesn't boot right after that. When or if that happens, keep a CD copy of your Ubuntu 10.04 handy. You will need to put that CD in, boot with it and put a few lines into the terminal to get your laptop back booting right. The very top part of this thread tells you what to do. It works, I did it! And it's handy to know for other boot problems like when you might mess with your partitions or some other event and it won't boot. So get this copied **onto paper**.
*How to restore the Ubuntu grub bootloader (9.10 and beyond)*

[http://ubuntuforums.org/showthread.php?t=1014708&highlight=grub+rescue](http://ubuntuforums.org/showthread.php?t=1014708&highlight=grub+rescue)

The basic lines for a rescue as described at the link are here:

sudo fdisk -l
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
sudo grub-install --root-directory=/media/sda5 /dev/sda

But don't use these exact lines necessarily. You would likely need to insert something else for "sda5" depending on your machine.

hope that helps.

---


---
title: "Ubuntu 11.04 does not boot after upgrade from 10.10 on Dell XPS 15"
date: 2011-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by maverick280857 on 2011-05-03
Hi,

I have a Dell XPS 15 laptop (Core i7 740 QM, 6 GB RAM, NVIDIA GT435M) which was running Ubuntu 10.10 Maverick Meerkat 64-bit edition until a few hours ago.

To upgrade to Natty Narwhal, I did

```

sudo apt-get update
sudo apt-get upgrade

```

and then

```

sudo update-manager -d

```

But now, Ubuntu 11.04 does NOT boot from Grub. Sometimes, I see a splash screen with stars which freezes, and sometimes I see a blank screen.

Any ideas on how to fix this would be appreciated!

Thanks in advance.

---

### Post by krishnandu.sarkar on 2011-05-03
You should have done do-release-upgrade. Anyway I'm too much noob to comment on that, if it's right or wrong.

But welcome to the club. Many of us are facing the same problem.

My Thread : [http://ubuntuforums.org/showthread.php?t=1747190](http://ubuntuforums.org/showthread.php?t=1747190)
Probable Solution : [http://ubuntuforums.org/showthread.php?t=1743841](http://ubuntuforums.org/showthread.php?t=1743841)

---

### Post by maverick280857 on 2011-05-03
I was able to boot into the text-based login screen. Adding the acpi off option in /etc/default/grub and running sudo update-grub screwed it up further. Now I cannot boot into Ubuntu 11.04 at all! I mean, now I really do have a Black Screen of Death. All I can do is turn off my laptop using the power button.

How are you able to boot into the 'previous linux versions'? This option does not work for me.

Also, I am unable to boot from the 10.10 Live DVD for some strange reason now. I was hoping to do this:

```

sudo mount /dev/sdXX /mnt  (XX is where your installation is, e.g. sdb1)
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt

```

and restore the old /etc/default/grub file.

---

### Post by maverick280857 on 2011-05-03
Ok I was able to use the recovery mode to restore my /etc/default/grub file.

So now I am able to boot into Ubuntu 11.04 text mode. Network does not work. And I'm also unable to install the nvidia driver. I get the error "unable to find the kernel source tree for the currently running kernel". I **cannot** run 

```
sudo apt-get install kernel-source kernel-devel
```

I guess I have to somehow mount my Windows partition, back up all my Linux files into it, get hold of a Live DVD for Ubuntu 11.04 and install it clean.

---

### Post by maverick280857 on 2011-05-03
My problem is that my wireless connection is inactive from the text console. iwconfig says "Access Point: Not-Associated".

It seems that in the upgrade, many standard drivers have been removed/disabled. How do I get my wireless to work from the text based console?

---

### Post by mörgæs on 2011-05-03
If booting from the DVD drive does not work, how about booting from USB?

---

### Post by maverick280857 on 2011-05-04
I just made a fresh cd after getting the Natty ISO, backed up my data after using the commands I posted above, and did a clean install.

Nothing like a clean install :KS

---

### Post by mörgæs on 2011-05-04
Good, please mark the thread 'solved'.

A reinstall is the way to go. I hope as many as possible will pass this advice on, since it saves beginners a lot of frustration and disappointment.

---

### Post by gregory5812 on 2011-05-09
I had a similar problem from updating from 10.10
i have a toshiba satellite laptop 1135  

it would freeze up on rebooting

i pressed CTRL key plus ALT key plus F1 key all at the same time at boot of the Cdrive

I pressed it twice and the option came up to boot from a kernal

it had a option for a previous version

i chose that and it booted to ubuntu with out freezing up

i altered grub 2 as root by creating a password for root and then logging out and logging in as root to change grub.cfg in the /boot/grub/ directory

the first two kernels are freezing up the machine when it loads

i copied the pervious version kerenals as the first choices and then saved it

i had to go to properties to change the permission from read only to read and write

i saved the change in the grub.cfg file

i then changed the grub.cfg file back to read only

i then rebooted the machine and it goes straight to the log in screen with no change
i choose unity 3d it worked fine no problem so far

i rebooted tried unity 2d it worked fine so far

i rebooted then used ubuntu classic which i am using now.

i do not know if any updates will cause me problems later

it works so far.

i did the recovery option with the first kernal and it crashes and stops at the ram check at the following place

0.183954 pci 0000:00:1e.0 bridge window [mem 0x40000000-0x47fffff pref]

i am a newbie and do not know what all this means but it works so far

i installed ubuntu 11.04 on my dell insprion 9100 with no problems at all from the cd

the toshiba would not take the 11.04 cd or install from it
i used a netbook install of 10.10 i believe it was off of a usb stick

maybe this might help some one

---


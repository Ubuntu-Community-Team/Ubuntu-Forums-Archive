---
title: "purple screen of death"
date: 2013-05-12
forum: Desktop Environments
---

### Post by doogiekd on 2013-05-12
dear friends, 

i have a lemel x86 desktop with an nvidia graphics card.

the problem:
when doing a normal boot, a purple screen appears and nothing else happens. the computer is stuck on the purple screen.

weird solution:
when booting in recovery mode, then selecting "resume normal booting" the computer starts normally and the login screen appears.

any solutions to getting my computer to boot normally would be very helpful.

---

### Post by dino99 on 2013-05-13
the "purple" screen is named "plymouth"
maybe remove "quiet splash" from the boot line, to know where it lock

but it can be also the login "greeter": which one is used ? (gdm/lightdm/xdm/kdm) (can be reconfigured with : sudo dpkg-reconfigure thatpackage)

---

### Post by doogiekd on 2013-05-13
this solved the problem:


	

Here is what happened... you are TEMPORARILLY modifying the grub boot parameters. You need to permanently modify them. So you need to add nomodeset to your /etc/default/grub/

I will assume you are using Ubuntu with unity for my example: Open a terminal and type:

sudo gedit /etc/default/grub

look for the line that says: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and change it too: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" Then, (VERY IMPORTANT) save the file and run this command:

sudo update-grub

Reboot without troubles!


[http://askubuntu.com/questions/286062/upgrade-ubuntu-12-10-ubuntu-13-04-black-screen-boot-failed-with-nvidia-gefor](http://askubuntu.com/questions/286062/upgrade-ubuntu-12-10-ubuntu-13-04-black-screen-boot-failed-with-nvidia-gefor)

---

### Post by Bashing-om on 2013-05-13
doogiekd;

If I may offer, "nomodeset" is not a great solution as that option disables the kernel's mode setting.
I make the suggestion that you investigate for an appropriate driver for you graphics card:
To see your graphics card and info:
```

sudo lshw -C display
lpci -nnk | grep -iA3 vga
```

A system running at optimum is desirable, no ?[INDENT=2]
just my thought

[/INDENT]

---

### Post by grahammechanical on 2013-05-14
You do not tell us what version of Ubuntu you are using. I suggest that you use Recovery Mode>Resume to get to a desktop and then activate a video driver. Or change the driver that is already set. You should have a list on drivers to experiment with.

Until recently Resume would load the desktop without loading a video driver but since 13.04 Resume seems to use an open source driver called llvmpipe that has the purpose of providing a Unity 3D experience even on machines that are low specification.

I think that you need to experiment with available video drivers

Regards.

---

### Post by doogiekd on 2013-05-14
well i thought removing "quiet splash" from the grub menu fixed the issue, but the problem continues so i reinstalled ubuntu 13.04.

the problems:

1. the computer gets stuck on the following screen during a normal boot:

[https://docs.google.com/file/d/0BxR_PKr-FCs-SFNTOFE5cm9nQUk/edit]("https://docs.google.com/file/d/0BxR_PKr-FCs-SFNTOFE5cm9nQUk/edit")

2. selecting "recovery mode" and selecting "failsafe graphics mode" i get an error message stating that the display could not be detected and that i will need to configure it manually. it then returns to the recovery mode menu screen.

any suggestions?

---

### Post by Bashing-om on 2013-05-15
doogiekd; Hey ;

Still looking at this as a graphics issue;

What results when you boot up ubuntu's live mode: liveDVD ->shift key when purple splash screen appears, language screen, escape key to accept the default -> choose "try ubuntu".[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by editheraven on 2013-05-15
I had a similar problem. Maybe this will help you : reinstall 
 xserver-xorg 
xserver-xorg-core
xserver-xorg-input-all

At the recovery boot menu, select enable networking and then drop to shell (make sure the internet connection is working!!!) . Purge those packages and then install them. Maybe you need to delete xorg.conf too.

---

### Post by doogiekd on 2013-05-15
well i tried editheraven's advice but the problem continues.

i reinstalled ubuntu (again) and the problems stated above in the first post continues.

any suggestions?

---

### Post by editheraven on 2013-05-15
Ok. Try one more thing : drop to shell with networking, and do this
         sudo apt-get install build-essential linux-source linux-headers       
         sudo apt-get install nvidia-current       

If the first command doesn't work, try instead : sudo apt-get install linux-headers-`uname -r`

ps : btw, is the live version of ubuntu working?

---


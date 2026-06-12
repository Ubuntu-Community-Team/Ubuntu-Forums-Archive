---
title: "How to get my graphics card working?"
date: 2013-06-09
forum: Gaming &amp; Leisure
---

### Post by JamesTheAwesomeDude on 2013-06-09
I have a Radeon HD 4350 graphics card, and it's not working in Ubuntu. At all. Even after installing the proprietary Fglrx driver and rebooting, the Graphics section of of the system details panel still reports the generic VESA driver.

I'm sick and tired of searching for a *functioning* driver for my graphics card; there is supposedly an open-sorce version floating around, but I can't find any binaries.
Compiling from source is **ABSOLUTELY NOT AN OPTION**. If you tell me where to find a source tarball, it will be absolutely unhelpful. However, I would prefer an open-source driver, I only installed Fglrx as a last resort.

Ubuntu 12.04 64-bit
Radeon HD 4350

Please, I am so absolutely frustrated with getting drivers of all kinds to work on Linux, I really need some help.

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]JamesTheAwesomeDude; Hey ....

Sorry to be the bearer of sad news but :[/COLOR]

"IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13."(Mark Phelps)

As AMD is not providing drivers, open source is the viable option. Other options can be made, but are not recommended, to maintain a stable system.

[INDENT=3]
when all said and done, no fault to ubuntu

[/INDENT]
[COLOR=#000000]
[/COLOR]

---

### Post by JamesTheAwesomeDude on 2013-06-09
Okay, so the only option is an open-source driver. That's all right, because the idea of using the proprietary one kind of grossed me out anyway.

Where can I find this open-source driver then? [This page]("https://help.ubuntu.com/community/RadeonDriver") says the driver has been built in and enabled since 11.04, so why is my computer still using the VESA driver? Is it just a matter of [FONT=courier new]modprobe[/FONT]-ing the correct kernel module?

Perhaps this will be of use?```
james@james-OptiPlex-GX620:~$ lspci | grep -i VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Radeon HD 4350]
james@james-OptiPlex-GX620:~$
```

Thanks for getting back to me so quickly; I really appreciate your help. I'm such a noob at getting Linux to work with my pathetic, ancient computer...:biggrin:

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]JamesTheAwesomeDude; Welp.

Should not be to tough to remove the fglrx f(AMD/ATI) files and get pure  open source back in-place:
To see what is installed and needs removed; terminal command:
[/COLOR]```
dpkg -l | grep fglrx
```

Once the old files are removed, make sure the open source is installed:
```

sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u ##just to create a new "image" file

```

Reboot to see the effect.
[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by JamesTheAwesomeDude on 2013-06-09
> **Bashing-om said:**
> [COLOR=#000000]JamesTheAwesomeDude; Welp.

Should not be to tough to remove the fglrx f(AMD/ATI) files and get pure  open source back in-place:
To see what is installed and needs removed; terminal command:
[/COLOR]```
dpkg -l | grep fglrx
```

Once the old files are removed, make sure the open source is installed:
```

sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u ##just to create a new "image" file

```

Reboot to see the effect.[INDENT=3]
just try'n to help

[/INDENT]
Hooray, my entire Ubuntu installation is destroyed! There's absolutely no GUI, even on the login screen, and TTY7 (the one that usually has the graphical login screen) just had the usual system boot messages on it, and didn't respond to keystrokes. However, virtual consoles 1 through 6 were still up.

Even though dpkg -l | grep fglrx returned nothing, there were still traces of fglrx on my system... That was revealed by booting into safe mode.

After trying sudo modprobe -r fglrx, I could use recovery mode to boot into failsafe graphics mode, which didn't work. All I got was a box saying how I'm running in low graphics mode and will need to configure all input devices by myself, which was on a black background. There was an OK button, but there was no cursor, so I couldn't click it, and I couldn't use the keyboard to do anything.

Typing startx just gives a black screen, and I can't do anything after that. CTRL-ALT-Backspace does nothing, there's no cursor, even the power button is unresponsive. I had to hold it down to kill the computer.

---

### Post by QIII on 2013-06-09
Hi!

You still need to remove the actual driver from the kernel and get rid of the configuration file your machine is trying to use when it starts up, which was not included in the instructions above.

If you can log in to safe graphics mode, do one of the following:

1.  If you installed fglrx from the repo, do

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
```
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
```

This may not work since you have deleted the records dpkg was using to indicate that it was installed.  In that case you will have to re-install it, reboot and then follow the instructions in 1.

2.  If you installed using a package from AMD/ATI's website

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
```
sudo amdconfig --uninstall
```

The reason I have you use the mv command rather than rm is that rm is dangerous and mv can be undone.

Best wishes!

---

### Post by Bashing-om on 2013-06-09
@ [COLOR=#000000]QIII ..Thank you ..
Do not know how I missed that ...staring me right in the face !
[/COLOR][INDENT][COLOR=#000000]
regret my error

[/COLOR][/INDENT]

---

### Post by QIII on 2013-06-09
Not to worry.  I have to write my address on the inside of my underwear so I know where to go after work!  ;)

---

### Post by JamesTheAwesomeDude on 2013-06-09
> **QIII said:**
> Hi!

You still need to remove the actual driver from the kernel and get rid of the configuration file your machine is trying to use when it starts up, which was not included in the instructions above.

If you can log in to safe graphics mode, do one of the following:

1.  If you installed fglrx from the repo, do

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
```
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
```

This may not work since you have deleted the records dpkg was using to indicate that it was installed.  In that case you will have to re-install it, reboot and then follow the instructions in 1.

2.  If you installed using a package from AMD/ATI's website

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
```
sudo amdconfig --uninstall
```

The reason I have you use the mv command rather than rm is that rm is dangerous and mv can be undone.

Best wishes!

You, sir, are amazing.

The amdconfig command returned errors (I'd tried to manually remove fglrx, by deleting every shared object I could find that had fglrx in the name...) but the logfile said I could run /usr/share/ati/amd-uninstall.sh --force to forcibly uninstall, and that fixed everything!

Now, the Graphics section of the system info reports a mysterious "Unknown" driver, but this magical unknown driver gives me hardware acceleration! WOOT WOOT! I CAN FINALLY RUN MINECRAFT ON LINUX!! :popcorn:

Thank you both for helping me get this working, this has been one of my happiest computer moments ever, second only to the time I first got Linux installed. :)

---

### Post by QIII on 2013-06-09
"Unknown" is a known bug, but so minor that it is not at the top of anyone's list.

You are now running the open source driver, and it seems to be working just fine for you!

Congrats!

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]JamesTheAwesomeDude; Outstanding !

Pleased you are pleased...

-Please mark the thread as solved; aides others seeking a solution, and helps keep the forum tidy.
[/COLOR]Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
[INDENT=2]
good minds produce good results [/INDENT]

---


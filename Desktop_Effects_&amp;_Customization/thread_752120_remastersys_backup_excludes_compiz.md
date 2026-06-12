---
title: "remastersys backup excludes compiz"
date: 2008-04-11
forum: Desktop Effects &amp; Customization
---

### Post by dexter.deepak on 2008-04-11
i just installed ubuntu with my remastersys backup cd and got all my previous things working except compiz effects...which are running flawless in the backup dvd i used for install.
i have a blacklisted driver so i use
"SKIP_CHECKS=yes compiz" to run compiz but now it doesnt work :

dpak@dpak-server:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by erginemr on 2008-04-11
As far as I can remember, **remastersys** used to ask for the Ubuntu Live CD during the creation of the ISO image. not so sure but, I guess it defaults back to the default Ubuntu behavior by not including the NVidia binary drivers.

So, you may need to reinstall your NVidia driver via say, **restricted drivers manager**. Please post for more, if you need directions on how to do it.

---

### Post by dexter.deepak on 2008-04-11
in my last install, i dont remember installing the nvidia driver explicitly...so can you help me do this now ?? thanks.

---

### Post by erginemr on 2008-04-11
OK, I'll do my best. 

First let's learn your graphics card model. From a terminal:
```
lspci | grep -i vga
```
and whether you have your binary driver installed or not:
```
gfxinfo | grep -i direct
```

If the output for the second command is "no", then you didn't install the binary NVidia driver, which is needed for Compiz effects to work. In this case, there are two paths to follow:

1. First, let us try to install your NVidia driver Ubuntu's way: 
Run Main Menu- > System -> Admin -> Restricted Drivers Manager, and let Ubuntu install the binary NVidia driver.

2. If it says no driver is needed (and you have an NVidia card), then please follow the steps in:
[http://ubuntuforums.org/showpost.php?p=4563329&postcount=4](http://ubuntuforums.org/showpost.php?p=4563329&postcount=4)

First try first to install it from Synaptic and configure as I have explained in the above linked post. If it doesn't work, then download and install ENVY and let it do the dirty work for you.

---

### Post by dexter.deepak on 2008-04-12
dpak@dpak-server:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
dpak@dpak-server:~$ gfxinfo | grep -i direct
bash: gfxinfo: command not found


i tried restricted drivers manager, and it said that i dont need any restricted drivers.
all the stuff given on the link by you is for nvidia cards and is of no avail to me.

now what else should i try ??
what is envy ? and can it be of some help ??

---

### Post by dexter.deepak on 2008-04-12
i just installed envy...and it asks for installing nvidia / ati drivers.

i am very much new to these terms and dont know the difference between the two, and so cant calculate which one to go for.
i need some education on these drivers. thanks

---

### Post by erginemr on 2008-04-13
I am sorry, the correct command is:
```
**glxinfo** | grep -i direct
```
Could you please try this instead? If it says "yes", then you have 3-D enabled and one step closer to running Compiz. (although the error message complains about the absence of xgl. We shall work it out later on.)

It is now clear that you have neither NVidia nor ATI card, you have an Intel onboard chip. Hence, ENVY has no use to you. You can ditch (uninstall) it via Synaptic or with:
```
sudo aptitude remove envy
```

I will also ask you to view the X server config file and check the name of the driver there:
```
gedit /etc/X11/xorg.conf
```
In Section "Device", there should be a line describing your driver something like: "intel" ot "i810". Can you find this line and report back what it says?

I have an NVidia card, so I don't know how to handle Intel cards at all. but I'll do my best to find you relevant links to the correct path. So we need two things to proceed, the output of "glxinfo | grep -i direct" and the Driver "...." part of "/etc/X11/xorg.conf".

---

### Post by dexter.deepak on 2008-04-13
dpak@dpak-server:~/Desktop/vmware_files$ glxinfo | grep -i direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"


thanks a lot for that brotherly support !!

---

### Post by erginemr on 2008-04-13
You are most welcome!

"vesa" is the fallback / failsafe driver and is definitely not for your video card.

Here are a few reads for you:
1. For a general discussions on available drivers for Intel video cards:
[http://ubuntuforums.org/showthread.php?t=97317](http://ubuntuforums.org/showthread.php?t=97317)
(AFAIK, there are two drivers "i810" and "intel" that you can use for your graphics card, with an ongoing debate for which one is better. I suggest you to go for "intel" as it seems to have been developed later to succeed "i810")

2. For the Community howto:
[https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b26796d178114bd3fdea5600480d8ab3137274d1](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b26796d178114bd3fdea5600480d8ab3137274d1)
(Section "Install newer modesetting Intel video driver")

3. For a clear, to-the-point how to on running Compiz / Beryl on an Intel video card:
[http://ubuntuforums.org/showthread.php?t=506744&highlight=965+compiz](http://ubuntuforums.org/showthread.php?t=506744&highlight=965+compiz)
(I think you should try this after reading the above threads thorouhly)

But without further ado, you should first back up your working xorg.conf file. From a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working
```
You can then proceed with the howto above. If things go wrong, you can restore your working setup with:
```
sudo cp /etc/X11/xorg.conf.working /etc/X11/xorg.conf
```

---

### Post by dexter.deepak on 2008-04-15
the links you have provided point to intel915 series but i have intel965.
the solution given for the 965 is not working and i have to restart my system.

i am still unable to understand the fact that when i was able to run compiz earlier on the same motherboard...why is it not working now ???

---


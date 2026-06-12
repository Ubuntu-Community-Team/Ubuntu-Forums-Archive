---
title: "nVIDIA Drivers without apt-get"
date: 2005-06-19
forum: Gaming &amp; Leisure
---

### Post by Chaos5lw on 2005-06-19
Hi, i didnt know whether this should go in this forum or the beginner forum but i am new to Linux and wanted to get the nVIDIA drivers on my Ubuntu Machine so i kan play Unreal Tournament.

The problem is that i dont have a modem in my linux computer so i can only download things using this windoze computer so i dont know how to get and install the nVIDIA drivers without the super cow powers of the apt.

The graphics card in question is a "nVIDIA RIVA TNT2" and X currently has it as this in its config file:
> Section “Device”
Identifier	“NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]”
Driver	“nv”
BusID	“PCI:1:0:0”
EndSection

I am currently getting around 25-35FPS on glxgears which is extremely poor, the card is a 32MB one.

When i say i am new to linux i mean new, u may really have to use laymens terms before i understand what you are trying to tell me, hope you can help. Thanks.

---

### Post by dbloom on 2005-06-19
i'm not sure i understand... have you tried this?  

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

if you want to compile yourself, you will need to go to nvidia's web site and download the linux drivers.  read the readme.  

i haven't tried doing it this way for some time...(pre-ubuntu days) but the ubuntu package works just fine for doom3. in fact, despite what i've read, doom 3 looks considerably better in linux and performs great... go figure.

---

### Post by afonic on 2005-06-19
Just go to nVidia's site and download the drivers for Linux.

Then you need to install them. You need to close X. Hit Control-Alt-F2, login and then type

```
sudo /etc/init.d/gdm stop
``` 

then backup your xorg conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
``` 

Now you need to install the nVidia drivers. Go to the folder you have them and type:

```
sudo sh ./NVIDIA-Linux-x86-1.0-7664-pkg1.run
``` 
(make sure you get the right filename, this is my example)

Then the installation should start. The nVidia installer should configure xorg.conf for you.

You can now start the X server again, however I suggest you reboot to be on the safe side. (sudo reboot).

If everything works you should see the nVidia logo. Also when you type glxinfo in the console it should say direct rendering: Yes.

If something breaks up and X won't start just replace your old xorg.conf file.

Good luck!

---

### Post by Chaos5lw on 2005-06-20
I downloaded the "NVIDIA-Linux-x86-1.0-7664-pkg1.run" and backuped my xorg.conf file like you said but i have a problem.

When i ran the installer i got the following message:
> No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?)

--------   --------
| YES |  |  NO  |
--------  --------
As i have no modem i clicked "No", the next message i got was:
> No precompiled kernel interface was found to match your kernel; this means that the installer will need to compile a new kernel interface.

-------- 
|  OK  |
-------- 
> ERROR: Unable to find development tool 'cc' in your path; please make sure you have the package 'gcc' installed. If gcc is installed on your system, then please check that 'cc' is in your PATH.

-------- 
|  OK  |
-------- 
> ERROR: Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details. You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com)

-------- 
|  OK  |
-------- 

Any suggestions?

---

### Post by Seti on 2005-06-20
Sounds like you will have to install kernelsource for your kernel 1st before the nVIDIA driver will be able to be installed. And you'll need gcc also. 
I'm not sure, but are these packages on the Ubuntu installer disc?
Once you have these installed, you go into /usr/src/linux.xxx and do ```
sudo make all
``` 
Sorry I can't be more help.

---

### Post by Chaos5lw on 2005-06-20
I hope theyre on the cd else ill have to find a way to download them on my windoze computer. How can i check?

---

### Post by meldroc on 2005-06-20
You realize that if you have access to the internet from another machine, you can download the appropriate packages from archive.ubuntu.com, burn them to a CD or transfer them with a USB flash drive or something, then install them with dpkg -i blahblah.deb.  That's probably the most painless solution, short of finding an internet connection for your ubuntu box.

Edit: Here are some links to the relevant packages:
[http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.10/linux-restricted-modules-2.6.10-5-386_2.6.10.5-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.10/linux-restricted-modules-2.6.10-5-386_2.6.10.5-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-kernel-common/nvidia-kernel-common_1.0.7174+1_all.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-kernel-common/nvidia-kernel-common_1.0.7174+1_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.10/nvidia-glx_1.0.7174-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.10/nvidia-glx_1.0.7174-0ubuntu1_i386.deb)

---

### Post by Chaos5lw on 2005-06-21
Thanks, thats kinda the answer i was lookin for when i asked first time, a way to download the files without apt-get.

What order should i install those in?

---

### Post by afonic on 2005-06-21
Doesn't really matter.

However I still suggest you install the nVidia drivers as the ones in apt-get are pretty old.

---

### Post by Chaos5lw on 2005-06-21
Do i need all those files to install the nVIDIA drivers i downloaded before?

---

### Post by afonic on 2005-06-21
[QUOTE=Chaos5lw]Do i need all those files to install the nVIDIA drivers i downloaded before?[/QUOTE]
 Yes get all these. You will need more though, like linux-headers for your kernel and the gcc compiler.

Find the build-essential package and install this too. Keep in mind most of these packages are in the CD.

---

### Post by Chaos5lw on 2005-06-21
I managed to get all of those files off the CD and then went to try and install the nVIDIA drivers i downloaded from the nVIDIA website. The installation got to the compiling stage and got to 100% compiled and then threw out an error, i think it was  "can't find kernel.ko" or sumthing like that... sorry i didnt write it down.

I then went and installed the nvidia-glx file i got off the CD, it worked and i have the nVIDIA splash screen when i start up. When i ran glxinfo, Direct Rendering said Yes, but when i ran glxgears i am still only getting about 85FPS, if i move the mouse on the glxgears box my framerate goes down to 40FPS and if i move the mouse anywhere else it goes down to 10FPS

Once again has anyone got any suggestions? (Sorry to be a pain)

---

### Post by Bandit on 2005-06-21
If it says no "cc" found it means there is no C Compiler installed on the system.
Use Synpt Package Manager and install the following "G++, GCC, libc" That should be all you need. I am at work so I cant look it all up for you.
Your going to need those 3 files installe to be able to compile anything.
Ubuntu doesnt have these installe by defualt.
Cheers,
Joey

---

### Post by skoal on 2005-06-21
Howdy,

well...just a few observations:

1. I have an older TNT card myself on another box, running redhat 8.0.

* 2. Don't use the .deb Ubuntu packages for your card.  *Completely remove all those packages you installed*.  (I put an asterisk by this one since it's important if you want to succesfully follow the next instruction).  Any error you receive while compiling the Nvidia drivers from their website, or unresolvable "issues" from reboots are directly related to #2.  For older cards, you're a glutton for punishment using this (or any) distro package.

3. [Download a driver](http://www.nvidia.com/object/linux_display_archive.html) version from the Nvidia website prior to 6629.  For the TNT card I had, 3123 or 4496 worked great, IIRC, 5xxx got worse, and 6xxx was unbearable.

4. The 3123 driver will require a little manual effort on your part making sure all the proper links are in place, so your best best (if you don't feel comfortable doing that), is the 4496 version.

5. Try out glxgears and you should be hovering somewhere in the 800's@800x600x16.  On my older TNT card, you can play quake3 and older Loki games just fine.

** I've attached glxgears scores for these 3 driver versions to give you an idea of what kind of performance you will have.  You can see that past 4496, the scores drop to <100 fps, which is probably correctable with a symlink or a config setting, but I just didn't care to bother hunting it down.  Go with 4496!

\\//_

---

### Post by Bandit on 2005-06-21
> If it says no "cc" found it means there is no C Compiler installed on the system.
Use Synpt Package Manager and install the following "G++, GCC, libc" That should be all you need. I am at work so I cant look it all up for you.
Your going to need those 3 files installe to be able to compile anything.
Ubuntu doesnt have these installe by defualt.
Cheers,
Joey

I just realized that you siad you couldnt get on the net...
Well.. You can google for the 3 packages I mentioned in winders then install them.
Install in this order GCC --> G++ --> libc and you should be fine.
Cheers,
Joey

---

### Post by Chaos5lw on 2005-06-21
Bandit - I already got the c compiler off the CD.

skoal - Thanks, im currently downloading the 4496 nVIDIA driver. Will let you know how it goes cause i probably wont get round to trying this for a few days as i have 2 IT reports to do by friday. Would i still get the "kernel.ko" error with this driver?

---

### Post by Bandit on 2005-06-21
Good luck, let us know the outcome..
Cheers,
Joey

---

### Post by Prudentissimus on 2005-06-22
[QUOTE=Bandit]Good luck, let us know the outcome..
Cheers,
Joey[/QUOTE]
 I am trying to install NVIDIA drivers too... I dun have internet acess on my linux as well... and I am a noob like him...

Is Linux Kernel the same as Linux Kernel Tree??? Linux Kernel I downloaded off of freshmeat is about 50mb compressed and 151mb without compression... 

For some reason NVIDIA wants Linux Kernel Tree.....

---

### Post by Chaos5lw on 2005-06-23
Different drivers, different error. This time i get:
> ERROR: The kernel header file 'lib/modules/2.6.10-5-386/build/include/linux/modversions.h' does not exist. The most likely reason for this is that the kernel header files in 'lib/modules/2.6.10-5-386/build/include' have not been configured.

-------
| OK |
-------

---

### Post by skoal on 2005-06-23
chaos, it looks like you're using teh standard i386 kernel.  Just install the header package off the CD (I think it's there).  I think all you'll need to do is:

sudo apt-get install linux-headers-386

and that should pull in 3 packages: linux-headers-2.6.10-5, linux-headers-2.6.10-5-386, and linux-headers-386.

* I don't know since I use my own customer .12 kernel with header package.  You may be missing some other development tools too (as mentioned above in another reply in this thread).  Also, make sure you understand what I mean by step 2 in my post.

\\//_

---

### Post by Chaos5lw on 2005-06-23
I have the linux-header files and all of the stuff above apart from the nvidia-glx one which you told me to remove.

I still get the same error though...

---

### Post by skoal on 2005-06-23
It's been awhile and I'm sure there are countless threads concerning this, but I believe you need to make sure you don't have these packages installed:

linux-restricted-modules
nvidia-glx
nvidia-kernel-common
nvidia-settings

err...maybe 4! Although that last one don't count (for subtle reasons).  Anyways, do that, get the header package and you should be able to compile with no problems.  If you do, post back what the exact error is.

[http://www.ubuntuforums.org/showthread.php?t=39743&highlight=nvidia+howto](http://www.ubuntuforums.org/showthread.php?t=39743&highlight=nvidia+howto)

/edit what version are you trying? is it 4496? and you're still getting the missing 'modversions.h' error?

/editX2 Oops! drop your linen and start your grinnin'...i see your problem now as I went back and checked error.  We are f'd my friend.  2.6.x kernels no longer have/use 'modversions.h' (in favor of a new interface).  So, your best bet is to step up a driver version, I think the 5xxx series supported 2.6.x.  If that don't suit your needs, you might want to check out a 2.4.x kernel and see if the performance gain is worth it.  Sorry about that brother.  Looks like we ran into a dead end.  Unless...where are those old minion.de patches when you need 'em? muahahaha...

/edit X3 Triple Oops! I missed game 7 of the NBA finals trying to get this work.  I just saw bored2k's post and it looks like the Spurs put the smack down.  Anyways, I give up on getting 4496 to work on 2.6.x.  There are just 2 many kernel interface changes between now and then. I even found the old minion patch and applied 2 of my own, but I kept running into more problems.  Mo problems...mo money...

Chaos, i guess you better try 5xxx or a 2.4 kernel if you really can't get the TNT working to your liking.  As you can see from my other post, 4496 works great on 2.4.x Redhat 8.0 kernel.  Best of luck.../{edit,editX2,editX3}

\\//_

---

### Post by Chaos5lw on 2005-06-30
Ok, ive now tried the 5336 NVIDIA Drivers and i get yet another error:
> ERROR: Unable to load the kernel model 'nvidia.ko'. This is most likely because the kernel model was built using the wrong kernel source files for your kernel; on Reh Hat systems, for example, be sure you have the 'kernel-source' rpm installed. If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' command line option.

-------
| OK |
-------

---

### Post by Prudentissimus on 2005-07-01
[QUOTE=Chaos5lw]Ok, ive now tried the 5336 NVIDIA Drivers and i get yet another error:[/QUOTE]
 Ubuntu + Geforce  = BULLSHit...

I still have to find "KERNEL-SOURCE-TREE" DMAN IT!!!!

---

### Post by Chaos5lw on 2005-07-05
Prudentissimus which version of the drivers are you trying to install?

---

### Post by Prudentissimus on 2005-07-05
[QUOTE=Chaos5lw]Prudentissimus which version of the drivers are you trying to install?[/QUOTE]
 The latest one from NVIDIA... Am I doing something not right?

---

### Post by Chaos5lw on 2005-07-10
dont know, ive never been asked for a kernel source tree, have you tried using the driver which comes on the Ubuntu CD. Also does anyone know how to fix my error?

---

### Post by Jet2k5 on 2005-07-10
From looking at this threat and knowing some stuff about Nvidia is that you need the kernel source to install the video driver.  I've done it in mdk, and it worked like a charm.  I remember getting those errors because I didn't have the kernel source.  Also I heard that Ubuntu doesn't provide a kernel source?  I don't know if it's true, but that's the impresion I'm getting.  I also can't find anything in the /usr/src/linux****

Which means there is non there.  BTW I'm going to be getting the 7800GTX.  Will Ubuntu ( Hoary ) nvidia drivers be able to support this card?  Where can i find out?

*EDIT*

Here I found this [here.](http://ubuntuforums.org/showthread.php?t=43065&highlight=7800gtx) 
 this sorta shows how to get the source .. .I think  :roll:

---

### Post by Prudentissimus on 2005-07-10
[QUOTE=Chaos5lw]dont know, ive never been asked for a kernel source tree, have you tried using the driver which comes on the Ubuntu CD. Also does anyone know how to fix my error?[/QUOTE]
 The default drivers that came with Ubuntu can be enabled in Terminal...

```

sudo nvidia-glx-config enable

```

---

### Post by Chaos5lw on 2005-07-14
[QUOTE=Prudentissimus]The default drivers that came with Ubuntu can be enabled in Terminal...

```

sudo nvidia-glx-config enable

```[/QUOTE]

I know, i was asking if you had tried using those drivers?

---


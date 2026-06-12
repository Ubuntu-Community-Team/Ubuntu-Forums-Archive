---
title: "Dell Vostro Ubuntu How To"
date: 2007-08-09
forum: Dell  Ubuntu Support
---

### Post by z28pwr on 2007-08-09
I recently went through the pain of loading UBUNTU on a Dell Vostro 1700 and thanks to the community I was able to get everything working, but it took quite a bit of time to find the answers, therefore I would like to make a post with all the steps needed to get UBUNTU running a Dell Vostro to help people get their systems running (I obtained the content from other posts in the community that pertained to the vostro).


This is how I got Ubuntu to run on a Dell Vostro 1700 (Should Be The Same For OTher XX00 Vostro's)

**When you first pop in the UBUNTU Feisty CD you must do the following:**

At the LiveCD initial boot screen do the following:

Move The Cursor Down To Safe Video Mode
Select F6 for more options
Add the following option to the beginning of the options list:
break=top (and put a space after it)
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.


**Once you get everything installed your X server will have a generic driver that will not allow you to go over 800 X 600 resolution, to solve that do the following:**

Download the NVIDIA drivers from [www.nvidia.com](www.nvidia.com)

- install the build-essentials which includes 
development tools like make and gcc.
sudo apt-get install build-essential

- Then you should install the linux-headers package matching the installed Linux kernel.
sudo apt-get install linux-headers-generic #If you use generic kernel

you can look which kernel is in use with the following command

uname -r

it should print something like that
2.6.20-16-generic

- Then install the following packages
sudo apt-get install pkg-config
sudo apt-get install xsverver-xorg-dev

- Uninstall all nvidia drivers that are installed from ubuntu.
You have to look which driver is installed so I give you an example how this command could look like.
sudo apt-get remove --purge nvidia-glx

If I am right there is a nvidia-glx-new package, but you have to take a look what is installed.

- change permission of the Nvidia-installer.
chmod 777 NVIDIA-Linux-x86-100.14.11-pkg1.run

Now you have to switch to console, by pressing strg+alt+F1

login and then stop current gdm

sudo invoke-rc.d gdm stop

install the driver.

$ sudo ./NVIDIA-Linux-x86-100.14.11-pkg1.run

If installation is complete you should take a look at your xorg.conf

sudo nano /etc/X11/xorg.conf

Change the driver to nvidia
The Device Section should look like this.

Section "Device"
Identifier "Geforce 6200"
Driver "nvidia"
EndSection

save and exit nano.

now you could start gdm
sudo invoke-rc.d gdm start



**Once you get the video working you will notice that your CDROM will not work, to fix it do the following:**

add "piix" to /etc/modules.


Code:
sudo gedit /etc/modules and add


Code:
piix


If I forgot something let me know.

---

### Post by arvadawest on 2007-08-09
Wow, this is great stuff.  Thanks so much.  It's people like you that are so great and willing to share with others.  Thanks again!!

-aw

---

### Post by kamaboko on 2007-08-09
Just got my Vostro 1400 lastnight.  Perfect timing.  Question: I'm dual booting with Vista.  Anything I should change or know before I embark on this adventure?

Update...

Got pretty fugly.  I followed your instructions to a T, but was getting all sorts of weird crap.  I didn't write anything down though.  I'll wait until Vostro has been in the fields for a while and subjected to a lot of punishment via Ubuntu installs.

---

### Post by z28pwr on 2007-08-09
> **arvadawest said:**
> Wow, this is great stuff.  Thanks so much.  It's people like you that are so great and willing to share with others.  Thanks again!!

-aw

Thanks


> **kamaboko said:**
> Just got my Vostro 1400 lastnight.  Perfect timing.  Question: I'm dual booting with Vista.  Anything I should change or know before I embark on this adventure?

Update...

Got pretty fugly.  I followed your instructions to a T, but was getting all sorts of weird crap.  I didn't write anything down though.  I'll wait until Vostro has been in the fields for a while and subjected to a lot of punishment via Ubuntu installs.

Can you tell me what happened and where?
Was at the initial install?

---

### Post by kamaboko on 2007-08-09
I've got a Vostro 1400 w/the following setup:

T5470 (1.6GHz, 2MB L2 Cache, 800MHz FSB)
2GB RAM
120GB SATA HD
GeForce 8400GS

All was good until the reboot after Fiesty installed.  I just got a blank screen.  No flashing cursor..nothing.  Just prior to that though, as it was rebooting it spewed out a bunch of code and so forth.  Really fast though.  I couldn't read it.  It was like HAL lost his mind. LOL.   

In any case, I tried the entire thing again. Wiped the drive, etc.  Got the same thing.  Maybe it's my video card.

---

### Post by z28pwr on 2007-08-10
> **kamaboko said:**
> I've got a Vostro 1400 w/the following setup:

T5470 (1.6GHz, 2MB L2 Cache, 800MHz FSB)
2GB RAM
120GB SATA HD
GeForce 8400GS

All was good until the reboot after Fiesty installed.  I just got a blank screen.  No flashing cursor..nothing.  Just prior to that though, as it was rebooting it spewed out a bunch of code and so forth.  Really fast though.  I couldn't read it.  It was like HAL lost his mind. LOL.   

In any case, I tried the entire thing again. Wiped the drive, etc.  Got the same thing.  Maybe it's my video card.



After it boots in and gives you the blank screen try to exit to a shell (CTRL+ ALT + F1) and try the following:

Code:
sudo nano /etc/X11/xorg.conffind where it says driver "nv" and change the driver to "vesa"

save the changes

then do a startx

---

### Post by lucian303 on 2007-08-10
I have a vostro 1400. I got everything working but the sound won't come out of the speakers. Plug some headphones into either of the jacks and there's the sound, so the drivers and everything are working. 

Also, it doesn't fully recognize the wired lan connection. Can't connect to the network except wirelessly. I'm not sure why. I tried editing /etc/network/interfaces but it won't get a dhcp (my other computers have no problem with the same connection, including my gateway laptop) and i also tried commenting out said file and using the knetworkmanager. Still no wired LAN.

Anyone have any ideas? The wired LAN I'm still hacking at but the speaker thing has me baffled. BTW, they worked before in Vista before I wiped the hard drive clean of that sh!&. So it's not a hardware defect. 

Weird. I was going to purchase one of the dells preinstalled with ubuntu, but it was hundreds of dollars more because there were not discounts and free upgrades on the hdd, memory, etc. So it's still cheaper so far as I can tell to order a windows laptop from dell and wipe it clean. That is if you have about 24 hours or so to get ubuntu running. :)

---

### Post by nick.inspiron6400 on 2007-08-10
What about the Intel X3100 graphics?

Thanks,

Nick.

---

### Post by jsgarvin on 2007-08-11
I had to jump through a couple hoops to get my Vostro 1700 running, but it wasn't too bad. Boiled down, here's what worked for me....

Install Ubuntu with the 'Alternate' CD
.. on reboot, you'll get a blank screen
On the bootup screen, choose 'recovery mode'
.. this gets you to a command prompt
run the following two commands

sudo dpkg-reconfigure xserver-xorg
... just select the most simple/conservative answers for every question. i.e. choose 'vesa" for the video driver.  just take the default screen resolutions, etc.
sudo /etc/init.d/gdm restart

... should have gui login screen at this point.  If not, go back to the dpkg-etc command and run that again, but be more careful with your answers.

now download and install Envy ( [https://launchpad.net/envy](https://launchpad.net/envy) )
follow the instructions to run that.  It'll install the proper video drivers and all the necessary dependencies.

### Vostro 1700 ONLY!!! ####
edit your /etc/X11/xorg.conf, change any lines that look something like...
Modes           "1024x768"      "800x600"       "640x480"
to something more like
Modes           "1440x900"      "1280x800"     "1024x768"      "800x600"       "640x480"

Reboot.

---

### Post by zapcojake on 2007-08-12
Has anybody tried a Vostro 1000?

---

### Post by kamaboko on 2007-08-12
> **lucian303 said:**
> I have a vostro 1400. I got everything working but the sound won't come out of the speakers. Plug some headphones into either of the jacks and there's the sound, so the drivers and everything are working. 

Also, it doesn't fully recognize the wired lan connection. Can't connect to the network except wirelessly. I'm not sure why. I tried editing /etc/network/interfaces but it won't get a dhcp (my other computers have no problem with the same connection, including my gateway laptop) and i also tried commenting out said file and using the knetworkmanager. Still no wired LAN.

Anyone have any ideas? The wired LAN I'm still hacking at but the speaker thing has me baffled. BTW, they worked before in Vista before I wiped the hard drive clean of that sh!&. So it's not a hardware defect. 

Weird. I was going to purchase one of the dells preinstalled with ubuntu, but it was hundreds of dollars more because there were not discounts and free upgrades on the hdd, memory, etc. So it's still cheaper so far as I can tell to order a windows laptop from dell and wipe it clean. That is if you have about 24 hours or so to get ubuntu running. :)

Good show on getting Ubuntu up and running.  Right now I just want to enjoy the new lappy. I'll give it a go at a later time.

---

### Post by aldenhg on 2007-08-12
For those of you with the 1400, check out my threads. There's good advice and help within.
[http://ubuntuforums.org/showthread.php?t=515275](http://ubuntuforums.org/showthread.php?t=515275) - general setup
[http://ubuntuforums.org/showthread.php?t=523356](http://ubuntuforums.org/showthread.php?t=523356) - suspend

---

### Post by lucian303 on 2007-08-13
Dell Vostro 1400:
After three tries (installing from alternate CD) I got it to work almost completely. Actually I got it to work the first time too but as I was installing other drivers I accidentally installed a wrong backport.deb and it was back to square one.


The only things that don't work:
**WebCam **--- Anyone has any idea on where the drivers are / hot to set it up?
**Sound** --- work out of the front Jacks but not the main speakers. Speakers are fine hard-ware wise as they worked under Vi$t@

Not tested:
Phone modem. Installed the driver for it, but does anyone actually use these anymore?
Firewire port: I'm sure it works, but I don't have any firewire equipment that has linux drivers (m-audio if you're reading this ... ozonic)

Any ideas on these last two issues. Also suspend won't work, although I followed the suspend post instructions, but that's no biggie. Hibernate works. 


Check out the dell linux wiki for the debs you will need: 
[http://linux.dell.com/wiki/index.php/Clients/Products/Inspiron_1420n](http://linux.dell.com/wiki/index.php/Clients/Products/Inspiron_1420n)

Most of the debs listed under the open drivers section have no links. There is a post on here that has them for download and more detailed instructions: [http://ubuntuforums.org/showthread.php?t=509408](http://ubuntuforums.org/showthread.php?t=509408)

Note that these are for the 1400N which comes with an Intel GFX Card. You'll need to install nvidia drivers. Either from the repos or nvidia site itself. (First time it only worked from repos, second from the nvidia latest driver.) Be careful of the bug when installing nvidia-glx-new (google it).

---

### Post by aldenhg on 2007-08-13
I'd use Envy for the video drivers. As long as it's a fresh install you shouldn't run into any problems and it takes all the guesswork out of it for you. The only mistake that I had to clean up after was it set my default depth to 16 instead of 24. This resulted in no window borders, but it was easily diagnosed and fixed.

---

### Post by Linux_Punk on 2007-08-14
I have a custom built desktop with an 8600 GT running Feisty. Id have to say after multiple installs and different methods it finally runs beautifully with Beryl working. For those of you if wondering, if any, Envy is a GUI type install (the windows, next buttons and all the good stuff) i perosnally wanna say that yes Envy is easier to use i highly recommend installing Nvidia drivers, commadn prompt style. Envy is quite buggy and i got perfect results using the command prompt style. Once this Vostro ships ill mess around with Ubuntu (preloaded with XP) and will post results here. The best of luck and thanks to whom have already tried this on the Vostro series

---

### Post by enigma83 on 2007-08-14
> **lucian303 said:**
> Dell Vostro 1400:
After three tries (installing from alternate CD) I got it to work almost completely. Actually I got it to work the first time too but as I was installing other drivers I accidentally installed a wrong backport.deb and it was back to square one.


The only things that don't work:
**WebCam **--- Anyone has any idea on where the drivers are / hot to set it up?
**Sound** --- work out of the front Jacks but not the main speakers. Speakers are fine hard-ware wise as they worked under Vi$t@

Webcam is a USB Video class device, check [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) for appropriate drivers.  I've got mine working, it does 1600x1200 too :)  Haven't found any decent broadcasting software yet though.

Sound for me just worked, including the sound swapping when I plug headphones in.  Try adding "model=3stack" to the module option, not sure how Ubuntu does that.

Or check my wiki [http://www.strudel-hound.com/wiki/index.php?title=Linux_on_the_Dell_Vostro_1400](http://www.strudel-hound.com/wiki/index.php?title=Linux_on_the_Dell_Vostro_1400)
for some more ideas.

---

### Post by bibou91 on 2007-08-17
Hi alll!

I've issue. I can't connect my external drive to my vostro 1500.
It doesn't auto-mount

I did lsusb -v and it appears on it but I don't know how to mount it.

Thanks for your help

---

### Post by daageep on 2007-08-17
You can always mess with /etc/fstab or manually mount the devices.

I don't know what format your external drive is. I usually just make a directory in /mnt (it doesn't really matter where the directory is) and run sudo mount /dev/sdb1 /mnt/newdir. replace /dev/sdb1 with the device and /mnt/newdir with whatever directory you made.

---

### Post by daageep on 2007-08-17
> **lucian303 said:**
> Dell Vostro 1400:
After three tries (installing from alternate CD) I got it to work almost completely. Actually I got it to work the first time too but as I was installing other drivers I accidentally installed a wrong backport.deb and it was back to square one.


The only things that don't work:
**WebCam **--- Anyone has any idea on where the drivers are / hot to set it up?
**Sound** --- work out of the front Jacks but not the main speakers. Speakers are fine hard-ware wise as they worked under Vi$t@

I got the webcam semi working this morning. Get the driver's from the berlios website from the previous user, patch the driver with the ID of the webcam, recompile the driver, stick them in /lib/modules/...

This driver only supports v4l2 (not v4l). I installed the v4l2-related packages, and ekiga detected my webcam.

I can provide more detailed instructions if anyone cares.

My question is: does our vostro come with a mic? I think it might be the holes on the side of the webcam itself on the lid.

I have no idea how to set them up. My alsamixer doesn't pick up any mics. Any ideas?

---

### Post by amber_474 on 2007-08-17
Installing Ubuntu:

Most of the procedures in this document have been taken from the first post in  [http://ubuntuforums.org/showthread.php?t=521753](http://ubuntuforums.org/showthread.php?t=521753) and
hats off to z28pwr for summing up a complete procedure for the rest of us.

Hardware:

Intel Core 2 Duo 5470 1.6 GHz
2 GB ram
Nvidia GeForce 8400 128 MB card
Intel Pro Wireless 3945 card
1280x800 display
120 GB 5400 rpm HD


Pre-Install:


Boot from the Live CD

Press F6 to edit the command line and

remove: splash quiet

add: break=top

from the command line and press Enter

Ubuntu will boot and get you to the Busybox shell

/bin/sh: can't access tty; job control turned off
(sh)

Give the commands:

$ modprobe piix

$ exit

Ubuntu boots and X server fails to start, so do:

$ sudo  dpkg-reconfigure  xserver-xorg

Select:  'vesa' instead of 'nv' as the driver

Select  /dev/psaux for mouse

and rest is default.

$ sudo  /etc/init.d/gdm start

or

$ sudo /etc/init.d/gdm restart


Install Ubuntu

Post Install:


After the installation completes, don't reboot. We need to mount the
/ partition of the  new installation; let's assume it's /dev/sda2

$ mkdir /tmp/target

$ sudo mount /dev/sda2  /tmp/target

$ cd /tmp/target/etc/

$ sudo vim modules

Add a the following line to 'modules' file:

piix

$ cd /

$ sudo umount  /tmp/target

Now reboot

Ubuntu should start normally

Connect to the internet and install all available updates using the update manager:

$ sudo update-manager &

or

$ sudo apt-get install linux-headers-generic

And install gcc, make etc by:

$ sudo apt-get install build-essential

Now reboot

You should have the restricted modules  and linux headers installed for your kernel version. Absence of restricted modules
causes the WiFi to stop working

$ uname -r
2.6.20-16-generic


$ sudo dpkg-query -l '*restricted*' | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version        Description
+++-==========================================-==============-============================================
ii  linux-restricted-modules-2.6.20-15-generic 2.6.20.5-15.20 Non-free Linux 2.6.20 modules on x86/x86_64
ii  linux-restricted-modules-2.6.20-16-generic 2.6.20.5-16.29 Non-free Linux 2.6.20 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.20.5-16.29 Non-free Linux 2.6.20 modules helper script
pn  linux-restricted-modules-generic           <none>         (no description available)
ii  restricted-manager                         0.20           manage non-free hardware drivers


$ sudo dpkg-query -l '*linux-headers*' | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                            Version        Description
+++-===============================-==============-============================================
un  linux-headers                   <none>         (no description available)
un  linux-headers-2.6               <none>         (no description available)
ii  linux-headers-2.6.20-15         2.6.20-15.27   Header files related to Linux kernel version
ii  linux-headers-2.6.20-15-generic 2.6.20-15.27   Linux kernel headers for version 2.6.20 on x
ii  linux-headers-2.6.20-16         2.6.20-16.29   Header files related to Linux kernel version
ii  linux-headers-2.6.20-16-generic 2.6.20-16.29   Linux kernel headers for version 2.6.20 on x
ii  linux-headers-generic           2.6.20.16.28.1 Generic Linux kernel headers


Now go to nvidia.com and download the nvidia driver  'NVIDIA-Linux-x86-100.14.11-pkg1.run'

Go to the text console by pressing 'Ctrl-Alt-F1'

Stop X server

$ /etc/init.d/gdm stop

Install nvidia driver

$ sh NVIDIA-Linux-x86-100.14.11-pkg1.run

$ /etc/init.d/gdm start 
or
$ /etc/init.d/gdm restart

The nvidia driver should start showing nvidia logo. And to confirm more
login to the gnome and run

$ glxgears &

You may want to set the resolution to the native value of the screen, which in my case was 1280x800. Go to Ctrl-Alt-F1:

$ sudo dpkg-reconfigure xserver-xorg

select 'nvidia' instead of 'vesa'.  and select 1280x800, rest is default. ( mouse device should be /dev/psaux )

In my case, the nvidia driver module failed to initialize on reboot. After searching for hours on internet I found out
that if on reboot X server fails, you go to text console 'Ctrl-Alt-F1' and do the following:

$ sudo modprobe -r nvidia

$ sudo /etc/init.d/gdm restart

And nvidia module works fine. To make the solution automatic, I added the following line to /etc/rc.local

modprobe -r nvidia

and on next reboot, nvidia module was able to work properly.

---

### Post by bibou91 on 2007-08-18
I still have  the /bin/sh: can't access tty; job control turned off
Although I've updated the modules with the line piix

I don't understand why do I have to keep entering this line every time my vostro boots

---

### Post by bibou91 on 2007-08-18
i've got it fix, with a tutorial on ubuntu-fr.org :)

---

### Post by derhanfi on 2007-08-18
you have a more detailed link?? especially for the link:

I have to suffer the same prob.

---

### Post by bibou91 on 2007-08-18
[It's an inspiron  topic, but it works as well]("http://doc.ubuntu-fr.org/dell_inspiron_1720")

If you don't speak french I tell you what are the codes to apply
```

sudo -i
echo piix >> /etc/initramfs-tools/modules    
sudo update-initramfs -u        
```

Then you have to edit /boot/grub/menu.lst and make look your entries like that (You should remove break=top)

```
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=cb8927de-1b14-4e53-b4e3-d64c000bcc7d ro quiet splash locale=fr_FR
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

EdIt:
for this code "sudo echo piix >> /etc/initramfs-tools/modules" 
if you can't do it, you may log as root : "sudo -i" then enter the line " echo piix >> /etc/initramfs-tools/modules"

---

### Post by saru411 on 2007-08-18
> **amber_474 said:**
> Installing Ubuntu:



$ sudo vim modules

Add a the following line to 'modules' file:

piix

$ cd /

$ sudo umount  /tmp/target

Now reboot

 how do you use vims? ive used gedit for all of my file edits so im new to vims. when i try to type in modules while usings vims it gave me a weird error like e505 or e305(dont remember which) after which i rebooted. after reboot i had to type modprobe piix again to boot. i have since changed modules file with gedit to read 

piix
fuse
lp
rtc
sbp2

i saved after and then deleted the tmp file with the ~ after it. it still kicks me out to busybox with the same error forcing me to again enter modprobe piix then exit. im runnning feisty 7.04 64 bit on a vostro 1500 with the same specs as listed.

please help, thanks

---

### Post by bibou91 on 2007-08-18
Use my method above it works out the piix problem

You can use nano instead of vims i think it's easier to use.

---

### Post by saru411 on 2007-08-18
> **bibou91 said:**
> [It's an inspiron  topic, but it works as well]("http://doc.ubuntu-fr.org/dell_inspiron_1720")

If you don't speak french I tell you what are the codes to apply
[CODE]
sudo echo piix >> /etc/initramfs-tools/modules    # Ajout de piix dans les modules


this code gives me permission denied

---

### Post by bibou91 on 2007-08-18
Write```


sudo -i 
echo piix >> /etc/initramfs-tools/modules
```

it will work like that

---

### Post by saru411 on 2007-08-18
also, the kernel im running is 2.6.20-15-generic ....should i change your second command to read with -15 instead of -16?

---

### Post by bibou91 on 2007-08-18
You've to update the line for the kernel you use. So yes

Don't edit your grub fully, just remove the break=top in the line you already have, it will be easier and you won't make mistake

---

### Post by saru411 on 2007-08-18
nevermind...i figured it out

---

### Post by PaganImmolator on 2007-08-20
[COLOR="Red"]This relates to Vostro 1500 series. [/COLOR]

I still have the following issues outstanding:
--Suspend and Hibernate are still flaky
--Sound will cut out upon wake up
--Sound seems a little quiet compared to XP
--Wifi keeps asking for a password everytime I boot. It's probably a feature but its annoying none the les[COLOR="Blue"]s

Otherwise as far as I can tell, everything is working great. [/COLOR]

There were a few things that needed fixing intially. Like loading the Nvidia drivers. I am going to create a separate thread called Vostro 1500 how to. Mostly just for my benefit so in case my memory fails me, I can find all the workarounds in one place instead of hunting all over the forums like I did before. Thanks for all the help so far in this thread

---

### Post by amber_474 on 2007-08-21
I have installed ubuntu feisty on Vostro 1400. The problem I had was that there was no sound coming from the speakers. I looked at the following page: 
[http://www.strudel-hound.com/wiki/index.php?title=Linux_on_the_Dell_Vostro_1400](http://www.strudel-hound.com/wiki/index.php?title=Linux_on_the_Dell_Vostro_1400)

I added the following line to  /etc/modprobe.d/alsa-base

options snd-hda-intel model=5stack

---

### Post by amber_474 on 2007-08-21
In fact, adding the following line to /etc/modprobe.d/alsa-base 
works better:

options snd-hda-intel model=6stack

I have no good reason for changing from model=5stack to model=6stack. In XP I noticed that when I opened the detailed volume control application ( double click on sound icon on panel ) and I opened the speaker volume control in there, I noticed channel 6 as the highest number, so I made model=6stack. I may be wrong in doing so.

---

### Post by amber_474 on 2007-08-21
Sorry. I apologize for providing information which was not well tested. 
With 'model=6stack' the speakers don't work, although the sound quality is better, don't know why. So adding

options snd-hda-intel model=5stack

to /etc/modprobe.d/alsa-base works fine.

---

### Post by PaganImmolator on 2007-08-21
> **amber_474 said:**
> I have installed ubuntu feisty on Vostro 1400. The problem I had was that there was no sound coming from the speakers. I looked at the following page: 
[http://www.strudel-hound.com/wiki/index.php?title=Linux_on_the_Dell_Vostro_1400](http://www.strudel-hound.com/wiki/index.php?title=Linux_on_the_Dell_Vostro_1400)

I added the following line to  /etc/modprobe.d/alsa-base

options snd-hda-intel model=5stack

[SIZE="4"]Amber, was the sound problem all the time or just when you were coming out of suspend or hibernate?[/SIZE]

---

### Post by amber_474 on 2007-08-21
> **PaganImmolator said:**
> [SIZE="4"]Amber, was the sound problem all the time or just when you were coming out of suspend or hibernate?[/SIZE]

The sound problem was present all the time right from the start and if I remember that even the live cd was similar in behavior ( i.e. sound coming only from headphone jacks and not speakers).

PS: There seems to be a problem with hibernation in ubuntu. For some reason, I am not able to recover back and the systems seems to hang. But I need to investigate it in more detail.

---

### Post by saru411 on 2007-08-21
Regarding vostro 1500 

has anyone gotten the fans to work on this model. if so how did you do it? if it was i8kutilits how did you get it to run in amd64 ubuntu? this is my only issue with this laptop...everything else works great with a little research!!!

---

### Post by saru411 on 2007-08-22
my cpu is at 45 degrees C with no load. how about the rest of you? i still have not found a solution to the fan issue.

thanks for reading

---

### Post by tetractius on 2007-08-22
Does anyone encounter problems with partitioning with Vostro 1500?; I have got 4 partition 
1) EISA Configuration
2) OS ( Windows Vista)
3) RECOVERY ( of Vista, I think)
4) UNKNOW

I need of 2 Primary Partions, one for Ubuntu and the other for his swap space. How I can dual booting Ubuntu with Vista? Is it possible, or I have to remove Vista?

Thanks

---

### Post by amber_474 on 2007-08-22
> **tetractius said:**
> Does anyone encounter problems with partitioning with Vostro 1500?; I have got 4 partition 
1) EISA Configuration
2) OS ( Windows Vista)
3) RECOVERY ( of Vista, I think)
4) UNKNOW

I need of 2 Primary Partions, one for Ubuntu and the other for his swap space. How I can dual booting Ubuntu with Vista? Is it possible, or I have to remove Vista?

Thanks

Depends if you received vista installation cd and you are willing to reinstall vista. If so then you can reinstall vista with your own partitioning scheme.
Otherwise, you can make the 4th partition an extended one an install ubuntu in it. I guess you might be able to boot fine from an extended partition.

---

### Post by tetractius on 2007-08-23
I received the Vista installation DVD with other driver and application CD.
So can I remove 3) RECOVERY and 4) UNKNOW (now I think Media Direct) partion for making respectively Root directory and Swap space?
(after shrink the Vista OS partiotion)

---

### Post by dsledge on 2007-08-29
> **amber_474 said:**
> Installing Ubuntu:

Most of the procedures in this document have been taken from the first post in  [http://ubuntuforums.org/showthread.php?t=521753](http://ubuntuforums.org/showthread.php?t=521753) and
hats off to z28pwr for summing up a complete procedure for the rest of us.

Hardware:

Intel Core 2 Duo 5470 1.6 GHz
2 GB ram
Nvidia GeForce 8400 128 MB card
Intel Pro Wireless 3945 card
1280x800 display
120 GB 5400 rpm HD


Pre-Install:


Boot from the Live CD

Press F6 to edit the command line and

remove: splash quiet

add: break=top

from the command line and press Enter

Ubuntu will boot and get you to the Busybox shell

/bin/sh: can't access tty; job control turned off
(sh)

Give the commands:

$ modprobe piix

$ exit

Ubuntu boots and X server fails to start, so do:

$ sudo  dpkg-reconfigure  xserver-xorg

Select:  'vesa' instead of 'nv' as the driver

Select  /dev/psaux for mouse

and rest is default.

$ sudo  /etc/init.d/gdm start

or

$ sudo /etc/init.d/gdm restart


Install Ubuntu

Post Install:


After the installation completes, don't reboot. We need to mount the
/ partition of the  new installation; let's assume it's /dev/sda2

$ mkdir /tmp/target

$ sudo mount /dev/sda2  /tmp/target

$ cd /tmp/target/etc/

$ sudo vim modules

Add a the following line to 'modules' file:

piix

$ cd /

$ sudo umount  /tmp/target

Now reboot

Ubuntu should start normally

Connect to the internet and install all available updates using the update manager:

$ sudo update-manager &

or

$ sudo apt-get install linux-headers-generic

And install gcc, make etc by:

$ sudo apt-get install build-essential

Now reboot

You should have the restricted modules  and linux headers installed for your kernel version. Absence of restricted modules
causes the WiFi to stop working

$ uname -r
2.6.20-16-generic


$ sudo dpkg-query -l '*restricted*' | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version        Description
+++-==========================================-==============-============================================
ii  linux-restricted-modules-2.6.20-15-generic 2.6.20.5-15.20 Non-free Linux 2.6.20 modules on x86/x86_64
ii  linux-restricted-modules-2.6.20-16-generic 2.6.20.5-16.29 Non-free Linux 2.6.20 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.20.5-16.29 Non-free Linux 2.6.20 modules helper script
pn  linux-restricted-modules-generic           <none>         (no description available)
ii  restricted-manager                         0.20           manage non-free hardware drivers


$ sudo dpkg-query -l '*linux-headers*' | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                            Version        Description
+++-===============================-==============-============================================
un  linux-headers                   <none>         (no description available)
un  linux-headers-2.6               <none>         (no description available)
ii  linux-headers-2.6.20-15         2.6.20-15.27   Header files related to Linux kernel version
ii  linux-headers-2.6.20-15-generic 2.6.20-15.27   Linux kernel headers for version 2.6.20 on x
ii  linux-headers-2.6.20-16         2.6.20-16.29   Header files related to Linux kernel version
ii  linux-headers-2.6.20-16-generic 2.6.20-16.29   Linux kernel headers for version 2.6.20 on x
ii  linux-headers-generic           2.6.20.16.28.1 Generic Linux kernel headers


Now go to nvidia.com and download the nvidia driver  'NVIDIA-Linux-x86-100.14.11-pkg1.run'

Go to the text console by pressing 'Ctrl-Alt-F1'

Stop X server

$ /etc/init.d/gdm stop

Install nvidia driver

$ sh NVIDIA-Linux-x86-100.14.11-pkg1.run

$ /etc/init.d/gdm start 
or
$ /etc/init.d/gdm restart

The nvidia driver should start showing nvidia logo. And to confirm more
login to the gnome and run

$ glxgears &

You may want to set the resolution to the native value of the screen, which in my case was 1280x800. Go to Ctrl-Alt-F1:

$ sudo dpkg-reconfigure xserver-xorg

select 'nvidia' instead of 'vesa'.  and select 1280x800, rest is default. ( mouse device should be /dev/psaux )

In my case, the nvidia driver module failed to initialize on reboot. After searching for hours on internet I found out
that if on reboot X server fails, you go to text console 'Ctrl-Alt-F1' and do the following:

$ sudo modprobe -r nvidia

$ sudo /etc/init.d/gdm restart

And nvidia module works fine. To make the solution automatic, I added the following line to /etc/rc.local

modprobe -r nvidia

and on next reboot, nvidia module was able to work properly.

Thanks everyone for the excellent help!!
Nvidia is now working on my Vostro 1500
GeForce 8400M GS 256 MB
:( Now for wireless!

---

### Post by saru411 on 2007-08-29
if its the dell wireless 1390 in your system use this thread([http://ubuntuforums.org/showthread.php?t=405990&highlight=dell+1390](http://ubuntuforums.org/showthread.php?t=405990&highlight=dell+1390))

---

### Post by bibou91 on 2007-08-30
Did anyone managed to make work the keypad?

I tried to install numlockx but it doesn't seem to do anything.

Also any update about making work the audio output?

I'm currently using Gutsy

---

### Post by alya84 on 2007-08-31
> **amber_474 said:**
> Installing Ubuntu:

Most of the procedures in this document have been taken from the first post in  [http://ubuntuforums.org/showthread.php?t=521753](http://ubuntuforums.org/showthread.php?t=521753) and
hats off to z28pwr for summing up a complete procedure for the rest of us.

Hardware:

Intel Core 2 Duo 5470 1.6 GHz
2 GB ram
Nvidia GeForce 8400 128 MB card
Intel Pro Wireless 3945 card
1280x800 display
120 GB 5400 rpm HD


Pre-Install:


Boot from the Live CD

Press F6 to edit the command line and

remove: splash quiet

add: break=top

from the command line and press Enter

Ubuntu will boot and get you to the Busybox shell

/bin/sh: can't access tty; job control turned off
(sh)

Give the commands:

$ modprobe piix

$ exit

Ubuntu boots and X server fails to start, so do:

$ sudo  dpkg-reconfigure  xserver-xorg

Select:  'vesa' instead of 'nv' as the driver

Select  /dev/psaux for mouse

and rest is default.

$ sudo  /etc/init.d/gdm start

or

$ sudo /etc/init.d/gdm restart


Install Ubuntu

Post Install:


After the installation completes, don't reboot. We need to mount the
/ partition of the  new installation; let's assume it's /dev/sda2

$ mkdir /tmp/target

$ sudo mount /dev/sda2  /tmp/target

$ cd /tmp/target/etc/

$ sudo vim modules

Add a the following line to 'modules' file:

piix

$ cd /

$ sudo umount  /tmp/target

Now reboot

Ubuntu should start normally

Connect to the internet and install all available updates using the update manager:

$ sudo update-manager &

or

$ sudo apt-get install linux-headers-generic

And install gcc, make etc by:

$ sudo apt-get install build-essential

Now reboot

You should have the restricted modules  and linux headers installed for your kernel version. Absence of restricted modules
causes the WiFi to stop working

$ uname -r
2.6.20-16-generic


$ sudo dpkg-query -l '*restricted*' | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version        Description
+++-==========================================-==============-============================================
ii  linux-restricted-modules-2.6.20-15-generic 2.6.20.5-15.20 Non-free Linux 2.6.20 modules on x86/x86_64
ii  linux-restricted-modules-2.6.20-16-generic 2.6.20.5-16.29 Non-free Linux 2.6.20 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.20.5-16.29 Non-free Linux 2.6.20 modules helper script
pn  linux-restricted-modules-generic           <none>         (no description available)
ii  restricted-manager                         0.20           manage non-free hardware drivers


$ sudo dpkg-query -l '*linux-headers*' | cat
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                            Version        Description
+++-===============================-==============-============================================
un  linux-headers                   <none>         (no description available)
un  linux-headers-2.6               <none>         (no description available)
ii  linux-headers-2.6.20-15         2.6.20-15.27   Header files related to Linux kernel version
ii  linux-headers-2.6.20-15-generic 2.6.20-15.27   Linux kernel headers for version 2.6.20 on x
ii  linux-headers-2.6.20-16         2.6.20-16.29   Header files related to Linux kernel version
ii  linux-headers-2.6.20-16-generic 2.6.20-16.29   Linux kernel headers for version 2.6.20 on x
ii  linux-headers-generic           2.6.20.16.28.1 Generic Linux kernel headers


Now go to nvidia.com and download the nvidia driver  'NVIDIA-Linux-x86-100.14.11-pkg1.run'

Go to the text console by pressing 'Ctrl-Alt-F1'

Stop X server

$ /etc/init.d/gdm stop

Install nvidia driver

$ sh NVIDIA-Linux-x86-100.14.11-pkg1.run

$ /etc/init.d/gdm start 
or
$ /etc/init.d/gdm restart

The nvidia driver should start showing nvidia logo. And to confirm more
login to the gnome and run

$ glxgears &

You may want to set the resolution to the native value of the screen, which in my case was 1280x800. Go to Ctrl-Alt-F1:

$ sudo dpkg-reconfigure xserver-xorg

select 'nvidia' instead of 'vesa'.  and select 1280x800, rest is default. ( mouse device should be /dev/psaux )

In my case, the nvidia driver module failed to initialize on reboot. After searching for hours on internet I found out
that if on reboot X server fails, you go to text console 'Ctrl-Alt-F1' and do the following:

$ sudo modprobe -r nvidia

$ sudo /etc/init.d/gdm restart

And nvidia module works fine. To make the solution automatic, I added the following line to /etc/rc.local

modprobe -r nvidia

and on next reboot, nvidia module was able to work properly.

I wonder if this apply to ATI user as well..Does it?

---

### Post by bibou91 on 2007-08-31
It doesn't. You don't use Nvidia drivers if you have Ati cards.

---

### Post by muadnu on 2007-08-31
What about suspend? Has anyone got it to really work?  I followed the instructions in [http://ubuntuforums.org/showthread.php?t=523356]("http://ubuntuforums.org/showthread.php?t=523356"), and after the third or fourth time of trying them, and getting a blank screen, I figured out that if I hitted ctrl+alt+F3 (or other F) and then came back with ctrl+alt+F7, I got the video back. Moreover, when I'm using dual monitors, my external monitor  comes back fine from suspension. So maybe the problem is with the configuration of my Nvidia card... I'm posting my xorg.conf file below.

Anyway, when I can get back from suspension, it doesn't always work fine, mostly the video works very slowly. And it almost never works if I try to suspend having compiz on...

```

 nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:40:26 PDT 2007
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L1732TQ"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GS"
	Option		"NvAGP"		"1"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1440+0, DFP: nvidia-auto-select +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by robgig1088 on 2007-09-01
I seem to be having a great deal of trouble installing the webcam driver (as I have never fooled with webcams before).  I downloaded the SVN project from the berlios site.  Someone said something about modifying one of the files?  I'm quite confused.  Any help would be much appreciated!

---

### Post by jasonlfunk on 2007-09-02
> **lucian303 said:**
> I have a vostro 1400. I got everything working but the sound won't come out of the speakers. Plug some headphones into either of the jacks and there's the sound, so the drivers and everything are working. 

This is what I did to get it to work. My right speaker jack doesn't work, but the speakers and the left jack does. You can't win them all I guess. :)

    *

      Edit the file /etc/modprobe.d/alsa-base

      Code: sudo nano /etc/modprobe.d/alsa-base Edit the line "options snd-hda-intel model=ref" to read "options snd-hda-intel model=3stack" If you cannot find this line, add it. If you don't have sound after a reboot, edit the sound preference, and look for the "Front" volume option. Make sure its not muted. Same for PCM.

---

### Post by robgig1088 on 2007-09-03
> **robgig1088 said:**
> I seem to be having a great deal of trouble installing the webcam driver (as I have never fooled with webcams before).  I downloaded the SVN project from the berlios site.  Someone said something about modifying one of the files?  I'm quite confused.  Any help would be much   appreciated!

Never mind, I figured it out.  I was using a v4l application instead of v4l2.   Also, I found a great (french) site for an XPS M1330 which appears to be IDENTICAL to the Vostro.  [http://doc.ubuntu-fr.org/dell_xps_m1330](http://doc.ubuntu-fr.org/dell_xps_m1330) .  Hope that helps!

---

### Post by buttons on 2007-09-07
Question to the Vostro 1500 owners: Is your mic working?  Sound is fine, mic just doesn't work at all.

---

### Post by IndieFX on 2007-09-08
Hi. First l´ll like to thank you all for sharing all this stuff, it helped a lot.

I bought my vostro 1500 yesterday and since them I just got problems when trying to use ubuntu. 

Now the problem that most concerns me is about the video card. I have a GeForce 8400 GS. I installed the NVidia drivers manually and it is working smooth with Beryl despite of the fact that it´s very, very slow.

The xorg.conf show the following info:
 ```


Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
  
``` 

As you can see it shows NVIDIA Default Card instead of GeForce 8400 GS. Maybe that´s the problem, but I can´t find out how to solve it. 

I tried to use Envy too, but I got the same xorg output...

Has anyone with the Vostro 1500 had the same problem? 
Thank you in advance!

---

### Post by buttons on 2007-09-08
To be honest, I think it's just a slow card, sorry.

If someone can point me to the contrary, then I have the same problem as well.

---

### Post by IndieFX on 2007-09-08
Well, but it´s really slow here. Isn´t it similar to GeForce 7300LE ? Maybe even better because if I'm not mistaken 7300LE is 64bit. The pc´s in the lab of my college has an 7300 and they manage to run Beryl very smooth... That´s weird, anyway. Thank you.

---

### Post by buttons on 2007-09-08
Fixed the mic (Dell Vostro 1500).  Turns out you can't use gnome-alsamixer or xfce4-mixer to set the input, or else it won't actually set anything and you'll be left wondering why the mic is dead.  Very, very frustrating.

Use Kmix or the good old fashioned command line to set input to "Digital Mic 1"

```
amixer sset 'Digital Input Source' 'Digital Mic 1'
```

---

### Post by buttons on 2007-09-08
Haven't seen that uvcvideo error myself.  Did you compile it from svn?  You could try the stuff in that french site, but it worked for me regardless of the errors.  Well, in as much as its a v4l2 device and that only works in ekiga and patched versions of aMSN.  Supposedly.

Also, wengo 2.2 will have v4l2 support.

---

### Post by IndieFX on 2007-09-09
Hey button sorry. I had problems with the uvcvideo, but solved right after the post... so i edited the post to erase but forgot to erase that. My bad. 

Thank you about the mic tip. I´ll try that. 
See you.

---

### Post by bibou91 on 2007-09-09
> **IndieFX said:**
> Hi. First l´ll like to thank you all for sharing all this stuff, it helped a lot.

I bought my vostro 1500 yesterday and since them I just got problems when trying to use ubuntu. 

Now the problem that most concerns me is about the video card. I have a GeForce 8400 GS. I installed the NVidia drivers manually and it is working smooth with Beryl despite of the fact that it´s very, very slow.

The xorg.conf show the following info:
 ```


Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
  
``` 

As you can see it shows NVIDIA Default Card instead of GeForce 8400 GS. Maybe that´s the problem, but I can´t find out how to solve it. 

I tried to use Envy too, but I got the same xorg output...

Has anyone with the Vostro 1500 had the same problem? 
Thank you in advance!


You don't seem to have the good resolution?

---

### Post by linusr on 2007-09-12
> **amber_474 said:**
> Depends if you received vista installation cd and you are willing to reinstall vista. If so then you can reinstall vista with your own partitioning scheme.
Otherwise, you can make the 4th partition an extended one an install ubuntu in it. I guess you might be able to boot fine from an extended partition.

I too got DELL VOSTRO 1500, tried installing ubuntu. But, Gparted doesnt recognise the existing partition. Just shows thw entire 160GB single drive.

Amidst all existing partitions are mounted and accessibe in LIVE CD.

---

### Post by Hmoobgolian on 2007-09-14
> **bibou91 said:**
> I still have  the /bin/sh: can't access tty; job control turned off
Although I've updated the modules with the line piix

I don't understand why do I have to keep entering this line every time my vostro boots

You have to edit your /boot/grub/menu.lst file and remove the "break=top" from the command line and it should boot up normally...

---

### Post by pekcle on 2007-09-14
If you haven't installed it, there is a program called Automatix that can do a lot of the work for you.  It is at [www.getautomatix.com](www.getautomatix.com) and can download a lot of packages for you, including the NVIDIA drivers.  Once you get that downloaded, there is an "NVIDIA Settings" option in your menu that you can use to set your resolution.  There is also a button that will export the file to /etc/X11/xorg.conf.  However, this doesn't work properly because it doesn't have root permission to write to that file.  I exported it to my desktop, and replaced the original /etc/X11/xorg.conf with the new one (this requires root privileges, of course).  After reboot, the resolution, and correct card is set up properly, although you may have to move some of your icons and time to the correct spot again.  Hope this helps.


> **IndieFX said:**
> Hi. First l´ll like to thank you all for sharing all this stuff, it helped a lot.

I bought my vostro 1500 yesterday and since them I just got problems when trying to use ubuntu. 

Now the problem that most concerns me is about the video card. I have a GeForce 8400 GS. I installed the NVidia drivers manually and it is working smooth with Beryl despite of the fact that it´s very, very slow.

The xorg.conf show the following info:
 ```


Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
  
``` 

As you can see it shows NVIDIA Default Card instead of GeForce 8400 GS. Maybe that´s the problem, but I can´t find out how to solve it. 

I tried to use Envy too, but I got the same xorg output...

Has anyone with the Vostro 1500 had the same problem? 
Thank you in advance!

---

### Post by jfbaro on 2007-09-20
Sorry for the question.

But can I buy a Vostro laptop without being a small business?
Because the website always mention vostro is EXCLUSIVE for small business.

I work for a company I don't own one.

I couldn't find this information in the website.

Thanks!

---

### Post by buttons on 2007-09-20
> **jfbaro said:**
> Sorry for the question.

But can I buy a Vostro laptop without being a small business?
Because the website always mention vostro is EXCLUSIVE for small business.

I work for a company I don't own one.

I couldn't find this information in the website.

Thanks!

Yep.  Just enter your name.

On topic: Great laptop for linux.  I have everything working but the winmodem, which I haven't tested yet.

---

### Post by muadnu on 2007-09-21
> **buttons said:**
> Yep.  Just enter your name.

On topic: Great laptop for linux.  I have everything working but the winmodem, which I haven't tested yet.

Do you have suspend/hibernate working? That's the only thing I still haven't been able to solve... (The problem seems to be my Nvidia 8400 GS card anyway).

---

### Post by buttons on 2007-09-21
> **muadnu said:**
> (The problem seems to be my Nvidia 8400 GS card anyway).

Same here.  You might want to check out the new nvidia drivers (100.14.19), since there were enhancements to power management code on the 8 series cards.  I haven't gotten a chance to test it yet, personally.

---

### Post by bighead0618 on 2007-09-22
I have a Vostro 1400. This is my first attempt in installing Ubuntu. I am attempting to have a dual-boot system with Linux and Windows. Great post BTW.. I wouldnt have even known where to get started.. 

When installing Ubuntu, i was very wary about overwritting my windows partition and all of my data. What i did was create a new partition in windows which was unallocated. Then when starting Ubuntu, I picked the automatic disk formatting for unallocated disk space.

Also, when installing, the resolution of the screen was so low with the existing drivers that I was unable to see what options I had available. Moviing the top and bottom task bars to the side helped with this.

Thanks again. Im sure I will be posting more questions as they arise!!! :)

---

### Post by muadnu on 2007-09-24
> **buttons said:**
> Same here.  You might want to check out the new nvidia drivers (100.14.19), since there were enhancements to power management code on the 8 series cards.  I haven't gotten a chance to test it yet, personally.

I just tried it and it seems to be working! At least the video came back without any problems, and now it seems to be working fine in general... I haven't tried everything yet, but for now I'm happy :)...

---

### Post by CuBone on 2007-09-24
I followed this guide and I got everything to work. My only problem is that the refreshrate of the screen is locked to 59.17 Hz according to nvidia x server settings. Is it possible to get a higher refreshrate? The resolution is set to 1920x1200.

---

### Post by PizzaHog on 2007-09-29
Thanks folks!

This thread was of incredible value, and I'm sure to be checking it as things progress.  But, with all of your suggestions, I've got my Vostro 1500 working very well!


Thanks again!

PH

---

### Post by supaman2slick on 2007-10-25
> **amber_474 said:**
> I have installed ubuntu feisty on Vostro 1400. The problem I had was that there was no sound coming from the speakers. I looked at the following page: 

I added the following line to  /etc/modprobe.d/alsa-base

options snd-hda-intel model=5stack

Freakin finally, I have sound! muchos gracias

---

### Post by Toufas on 2007-10-28
> **nick.inspiron6400 said:**
> What about the Intel X3100 graphics?

Thanks,

Nick.
same here, i want proper graphics not vesa :/

---

### Post by briansvgs on 2007-11-26
Using model=5stack instead of model=3stack, I was finally able to get both my headphone jacks (there are two headphone jacks) and my speakers  working on my vostro 1400 working. However, using this method, linux seems to recognize the second headphone jack as another speaker, and when I plug a pair of headphones or speakers into the first heaphone jack, it mutes both the second headphone jack and the speakers. Is it possible to make it mute just the speakers when a device is plugged into the first headphone jack, leaving the other jack functioning? How would I do this? 

         Also, would it be possible to set up some sort of a switch to leave all three devices working for surround sound when I am doing something like gaming or watching a movie, but otherwise just make the speakers deactivate when something is plugged into the first headphone jack?

Thanks,
Brian

---

### Post by jfbaro on 2007-12-02
Has anyone here be able to make sound work on Vostro 1700 + 7.10 Kubuntu... I think I tried 15 different approaches, no one makes the thing work!!

I got it working only once, just after rebooting from the G solution (from ubuntu help), but after that nothing is working.

Thanks guys

---

### Post by MRAB54 on 2007-12-03
I just installed 7.10 on my vostro 1700.  One problem that I had was getting my wireless to work.  The card in my laptop is a broadcom 1390 and I had to go to System | Administration | Software Sources and enable proprietary drivers for devices.  At this point you will need to have a wired Internet connection.  Next, go to System | Administration | Restricted Drivers Manager and enable the broadcom driver.  It will ask you to locate the driver but click on the button to download from the supplied URL.  All that seemed to work for me.  That seemed to be the only major problem I've run into thus far.

---

### Post by MRAB54 on 2007-12-03
> **jfbaro said:**
> Has anyone here be able to make sound work on Vostro 1700 + 7.10 Kubuntu... I think I tried 15 different approaches, no one makes the thing work!!

I got it working only once, just after rebooting from the G solution (from ubuntu help), but after that nothing is working.

Thanks guys


I had to install the backports module. I think it was something like : sudo apt-get install linux-backports-modules

Make sure the backports repository is enabled as well.

Sound works, if it is kind of quiet, click to add the "front" in the sound mixer.  I think I read there is an issue that the sound volume increases exponentially, so it gets real loud real quick towards the max volume.

---

### Post by arokicki on 2007-12-10
add line to /etc/modprobe.d/alsa-base

options snd-hda-intel probe_mask=1 model=3stack
This was taken from:
[URL="add line to /etc/modprobe.d/alsa-base

options snd-hda-intel probe_mask=1 model=3stack
This was taken from:
http://www.linux-on-laptops.com/hosted/Dell-Vostro-1400-Ubuntu-Gutsy.html"]http://www.linux-on-laptops.com/hosted/Dell-Vostro-1400-Ubuntu-Gutsy.html[/URL]

---

### Post by seaq on 2008-02-07
I made sometime ago a wikipage for vostro 1700.

I've solved the audio issue with the Dells' s conexant provided modules

[https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700)

---

### Post by rkulp on 2008-03-31
I just installed 7.10 on my Vostro 1000 along with Vista Business. It was very easy:

1. Repartitioned the hard drive using the Vista disk manager.
2. Booted the live CD
3. Installed following the instructions/screens
4. Grub boot loader works very well.

The problem I have is that I don't know how to configure the built-in wireless card for roaming a public network. Eth0 is recognized, but I think that may be the wired port (I just thought of it but am in Windows now so can't check.) Once the wireless is working I can do updates, etc. I am currently on the road so can't check the wired network connection. Suggestions about the wireless would be appreciated.:confused:

---

### Post by peter.martinson on 2008-04-24
Hello all,

I installed Ubuntu 7.10 on my Vostro 1400 about a week ago, and have it running pretty smoothly now.  I have it dual-booting with schvindows XP.  I have one recurring problem, which has me worried, though, and I haven't seen this on any other posts:

I installed the i8kutils and Gkrellm, which is running in the background, in order to control my fans.  I installed the drivers for my NVIDIA GeForce 8400 card with the Envy program, and am currently running the Compiz effects package.  Periodically, something takes over my CPUs and cranks them up to around 100%, which drives the temperature up near 60C (so far!).  When I open a terminal and run <top>, the processes that are jamming everything up appear to be either 1) gnome-panel and Xorg, or 2) Network-Manager.  The taskbar on my desktop also becomes unresponsive, though I can switch between windows and desktops just fine using the keyboard shortcuts.  The only thing I can do, is restart the computer from the terminal, and it restarts with everything working normally.  What seems to spark this coup d'etat, is switching between desktops rapidly and doing administrative tasks, though I haven't nailed one particular offending application.

Any ideas?  I don't really know how to diagnose the problem yet, since I'm relatively new to Linux.

Peter

---

### Post by speirint on 2008-05-21
This might not be the problem, but I recall a lot of people (myself included) having problems with trackerd.  When I was checking htop I saw it would take up a whole CPU at times.

---


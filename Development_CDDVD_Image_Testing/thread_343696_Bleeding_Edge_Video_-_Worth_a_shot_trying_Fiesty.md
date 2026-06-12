---
title: "Bleeding Edge Video - Worth a shot trying Fiesty?"
date: 2007-01-21
forum: Development CD/DVD Image Testing
---

### Post by Kerry Lange on 2007-01-21
I've installed some new hardware:

Asus P5LD2
Intel Core 2 6600
nVidia 8800 GTX
DDR2 667

The Edgy Live CD barfed on my new hardware.  Would I have any better luck with Fiesty?

---

### Post by Henry Rayker on 2007-01-21
I think it would be helpful to anyone who sees this for you to list the problems you encountered.

---

### Post by bodycoach2 on 2007-01-21
Might try the alternate install CD. Some seem to have a much easier time with it.

---

### Post by Kerry Lange on 2007-01-22
Where can I get the alternate install CD?  In the following thread I see a link to an alternate CD but the link is broken:

[http://www.ubuntuforums.org/showthread.php?t=343545](http://www.ubuntuforums.org/showthread.php?t=343545)

---

### Post by pochu on 2007-01-22
This is the right link. Images are updated daily:

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by leegg009 on 2007-01-22
We are Vedio Games and Ipods wholesalers,we have all brands and 
consouls of old to the lastest games for sale at very cheap prices.We 
also have all brand of new ipods for sale and they come in different 
colour's  at a very cheap prices.We sell our games and ipods at a 
reasonable prices.We do ship all over the world.Do kindly contact us 
on our email: [email]mobile_electronics_limited@yahoo.com[/email] or our contact phone number 
44-7031844324,44-7031844313 if you are interested in buying some games 
and ipods from us,thank's and God bless. below are some Ipods and vedio games prices,do check them out and let 

us know what you think about them:

HERE IS THE PRICE LIST.
 
 Xbox 360,Ps1,2,3,psp,nintendo64,nintendo gameboy advance,gamecube, 
 
 Apple 4 GB iPod Mini Blue M9802LL/A ........$90.00
 Apple 4 GB iPod Mini Pink M9804LL/A ....... $120.00
 Apple 4 GB iPod Mini Green M9806LL/A ...... $100.00
 Apple 6 GB iPod Mini Blue M9803LL/A ....... $80.00
 Apple 6 GB iPod Mini Silver M9801LL/A ..... $90.00 
 Apple 20 GB iPod M9282LL/A................. $125.00
 Apple 4 GB iPod Mini Pink M9435LL/A ....... $95.00
 Apple 40 GB iPod photo .....................$75.00
 Apple 4 GB iPod Mini Silver M9160LL/A ..... $80.00
 Apple 60 GB iPod Photo M9830LL/A ...........$100.00
 Apple 60 GB iPod photo ................... .$90.00 
 Apple 30 GB iPod Photo M9829LL/A .......... $75.00
 Apple 512 MB iPod Shuffle MP3 Player M9724LL/A ... $50.00
 Apple iPod 1GB Shuffle .................... $40usd
 Apple 4 GB iPod Mini Blue M9436LL/A ........$80.00 
 Apple 20 GB iPod U2 Special Edition ....... $130.00 
 Apple 6 GB iPod Mini Green M9807LL/A........$150.00
 Apple Ipod Nano 2GB ....................... $90:00
 Apple Ipod Nano 4GB ........................$110:00
 Ipod video 30GB............................$145:00
 Ipod video 60GB............................$170:00
Microsoft Xbox 360 Platinum Bundle Console .........$160:00
Microsoft Xbox 360 Core System .........$100:00
Sony PSP Metal Gear Bundle ...$105:00
Sony PS1 System.................$50:00
Sony PlayStation 2 PS2 Video Game Console - SONY 97011...$60:00
Sony PlayStation 3 (PS3) ......$190:00
Nintentendo GameCube System in Platnium....$65:00
Nintendo Of America GameBoy Advance SP, Onyx AGS S ZKA...$50:00
Nintendo Gameboy Advance System - NEW...$20:00
Brand New Limited Edition NINTENDO 64 ...$40:00
Brand New Nintendo Wii Console.......$260:00


Contact us at : 

MOBILE ELECTRONICS LIMITED 

Tel : 44-7031844324,44-7031844313
EMail Address : [email]mobile_electronics_limited@yahoo.com[/email]

Key Contact : Lee Butcher.  

Thanks, 
Lee Butcher.

---

### Post by pochu on 2007-01-22
Henrik, moderators: SPAM

Non related with the topic...

---

### Post by Kerry Lange on 2007-01-22
Okay, I tried a build I downloaded yesterday evening.  The Live CD went fine until it tried loading the video drivers.  I got that screen that displays when the GDM won't load and here's the short output I got:

Failed to start your X server...

Fatal server error:
(EE) No devices detected
No screens found                  f"

That was it.  When I looked for the details, I saw all of the cards the video driver supports and the 8800 isn't one of 'em.  I guess it's a case of waiting until we get support for the 8800 series nVidia card.

---

### Post by Saibot on 2007-01-23
Thought you might like to know I just got Edgy working with my 8800GTX today - it's even running Beryl with Twinview  over two 20.1" screens (and crazy fast too).  I tried to get Feisty to work this weekend, but the installer kept hanging so I didn't get far.
I never had any luck installing the nvidia drivers myself with edgy and the 8800,(not sure what I was doing wrong) but I recently discovered this:

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

I probably did it the hard way, but whatever - it worked for me.  After the Edgy install puked and kicked me to the cute little flashing cursor I manually downloaded and installed the 'Envy' script and ran it.   It did it's thing and downloaded the right drivers and now Ubuntu works for me again.
For the record my hardware is Asus A8N-SLI Premium with Athlon X2 4800,  8800GTX, and lot's of goodies.  I know the motherboard and processor aren't really cutting edge anymore,  but the video is (for a while anyways).
You might have to jump through hoops to get it working, but it is possible, and hopefully when Feisty is done it will just 'work'.

---

### Post by Kerry Lange on 2007-02-03
Okay, after an adventure trying to install Edgy using the Alternate CD (didn't work because I have an Intel 965p-based chipset, which doesn't seem to work with Linux), I tried the Alternate Feisty CD and I got Feisty installed.

However, I still get the X server error and the GUI won't run.  So, I'm going to give Envy a try to see if the latest nVidia drivers will allow the GUI to load.

---

### Post by Kerry Lange on 2007-02-03
I've been able to download a copy of the latest nVidia driver now and tried installing it using the utility they include.  However, when I do that the utility tells me I need to have "libc" installed.  

How do I install "libc".  

Is it as easy as "sudo apt-get libc" or something like that?

Anyone?

---

### Post by Master Ar2ro on 2007-02-03
I'm no guru, but I'd bet libc should already be there if you managed to install the system. Perhaps the versions don't match...

---

### Post by Kerry Lange on 2007-02-03
Well, I installed something called "libc6" but that wasn't it.  The error message I get says I need a "libc development package." 

Anybody know what that is?

---

### Post by Master Ar2ro on 2007-02-03
Try installing libc6-dev ;). As for libc, apart from libc6 there are no other libc packages.

---

### Post by Kerry Lange on 2007-02-04
Finally!  It worked!

Thanks.  I've got Feisty working with my hardware.  So, here's what worked:

1.  Used the alternate CD to get everything installed.  At this point the X server didn't work with my nVidia 8800 card.

2.  I got the latest nVidia drivers from the nVidia site and, using Windows, saved them to a CD.

3.  I booted to Ubuntu and used the command line to install the nVidia drivers.  

4.  I mounted the CD and copied the drivers to the file system.  I could probably have run the driver utility from CD but I did it from the HDD.

5.  The drivers come with a utility to configure the X server so there was no need to manually edit the X server config file.  Before the installation utility would work, though, I had to have "libc6-dev" installed first.

6.  When I rebooted, everything came up as you'd expect!

---

### Post by snickkers on 2007-02-08
So, you didnt end up using that "Envy" script in the end?

---

### Post by Kerry Lange on 2007-02-18
Oops.  Sorry for not responding earlier.  That's right.  I didn't use envy.  I simply used the files provided by nVidia.

---

### Post by MetalMusicAddict on 2007-02-18
The Feisty repos should have the newest nVidia drivers.

---

### Post by Raptormn on 2007-03-01
oh thank you! you have made my day. :) :KS 


> **Kerry Lange said:**
> Finally!  It worked!

Thanks.  I've got Feisty working with my hardware.  So, here's what worked:

1.  Used the alternate CD to get everything installed.  At this point the X server didn't work with my nVidia 8800 card.

2.  I got the latest nVidia drivers from the nVidia site and, using Windows, saved them to a CD.

3.  I booted to Ubuntu and used the command line to install the nVidia drivers.  

4.  I mounted the CD and copied the drivers to the file system.  I could probably have run the driver utility from CD but I did it from the HDD.

5.  The drivers come with a utility to configure the X server so there was no need to manually edit the X server config file.  Before the installation utility would work, though, I had to have "libc6-dev" installed first.

6.  When I rebooted, everything came up as you'd expect!

---

### Post by NZ-Wanderer on 2007-03-02
Today I installed a Geforce 8800GTS on my Vista partition, but when I went over to my Kubuntu partition it wouldn't work, after reading some other threads (one of which after following I lost all screen display (including text)) I found your method so am going to re-install Kubuntu using the alternate CD.

Can you tell me if you think the the steps you did would work for Edgy please??

If you think they could, could you possibly explain your steps 3, 4 and 5 in a bit more detail please (I not too good at command stuff)

And also, where exactly on the Nvidia site did you get the drivers from :) :)

Any and all help would be very much appreciated....

> **Kerry Lange said:**
> Finally!  It worked!
Thanks.  I've got Feisty working with my hardware.  So, here's what worked:
1.  Used the alternate CD to get everything installed.  At this point the X server didn't work with my nVidia 8800 card.
2.  I got the latest nVidia drivers from the nVidia site and, using Windows, saved them to a CD.
3.  I booted to Ubuntu and used the command line to install the nVidia drivers.  
4.  I mounted the CD and copied the drivers to the file system.  I could probably have run the driver utility from CD but I did it from the HDD.
5.  The drivers come with a utility to configure the X server so there was no need to manually edit the X server config file.  Before the installation utility would work, though, I had to have "libc6-dev" installed first.
6.  When I rebooted, everything came up as you'd expect!

---

### Post by Kerry Lange on 2007-03-03
You can read some instructions I left in another thread as follows:

[http://ubuntuforums.org/showthread.php?t=351205&page=2](http://ubuntuforums.org/showthread.php?t=351205&page=2)

The process *should* work with Edgy as well.

Regarding the drivers, I just went to the nVidia site, clicked on driver downloads & followed the links from there.  You just select your OS & away you go.

---

### Post by NZ-Wanderer on 2007-03-03
Thanks for the reply, I actually managed to solve it yesterday myself (a first for me..)

This is what I ended up doing....

I typed: ```
sudo wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run
```
(to get the latest drivers)

Then I typed ```
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
```
(And followed all the prompts)

Then just rebooted the computer and it WORKED :) :)


> **Kerry Lange said:**
> You can read some instructions I left in another thread as follows:
[http://ubuntuforums.org/showthread.php?t=351205&page=2](http://ubuntuforums.org/showthread.php?t=351205&page=2)
The process *should* work with Edgy as well.
Regarding the drivers, I just went to the nVidia site, clicked on driver downloads & followed the links from there.  You just select your OS & away you go.

---

### Post by technics on 2007-03-22
gonna try and install edgy tonight with my 8800GTS, hope itll go alright using your methods. thanks for writing down ur problems and solutions!

---

### Post by underthehour2000 on 2007-03-23
This is how i installed my 8800gts card, am still using dapper, but this will work for edgy :)  So i used the alternative cd, installed normally, then rebooted and bam, there goes the x server error.  As noted earlier drivers with ubuntu @ mo dont work.  So it was a quick edit of the xorg.conf files (sudo nano /etc/X11/xorg.conf), to change "nv" to "vesa" drivers.  1 reboot later, and up comes the gui.

But we want 3d drivers right... so i tried both methods:

1st method, by downloading the nvidia drivers directly off the nvidia site.  (As the latest drivers in synaptic packagemanager or apt dont work).  Before you can use the nvidia driver from the nvidia site though, you need to settle library dependicies.  

The nvidia installer prompts u what libraries are needed when running the installer, if there not already loaded onto your ubuntu machine.  Basically the dependancies needed are the compiling tools, such as build-essentials, linux headers, gcc, make etc... i cannot remeber the exact files needed, off the top of my head! but if you run the installer it will mention them.

OK now you need to, exit out of ubuntu gui and into a terminal, for this trick try the following commands... Otherwise the nvidia installer wont run.

ctrl+alt+f1, 

then type @ the command prompt 
sudo killall gdm 

This kills all gui ubuntu interface you was just in, and then your ready to try to run the installer.  If This above command dont work for you, try restarting your computer and selecting recoverymode @ the grub menu. 

Ok so back @ the terminal, goto the directory where u installed the nvidia drivers, for instance i installed my drivers on the desktop, so the command would be;

cd /home/user/desktop/

and run the installer with 

sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run (note the nvidia installer u downloaded may have a different name).

The installer then runs, follow the screen prompts and happy days (Default selections should work).  

Reboot once your done and your drivers should be working.  Try glxgears and glxinfo to see if direct rendering says yes. 

2nd Method;

Ok now how to install envy, 1st you need to go to [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) 

1) Download and install the deb package:

double click on the deb package in Ubuntu or right click on the deb package and select install"

2) Make sure that all the dependencies were installed by typing:
sudo apt-get install -f

3) Launch Envy's GUI (inside a Desktop Environment such as GNOME, by selecting it in the "Applications/System Tools" menu

OR if you need to use Envy's textual interface you will have to type:
sudo envy -t

This should work for you edgy folks. However for dapper like me, i had to do it this way;

1st exit out of ubuntu gui, and into a terminal, for this trick try the following commands... 

ctrl+alt+f1, 

then type @ the command prompt 

sudo killall gdm  

sudo envy

Follow envy's instructions and then your all good.  You will need an active internet connection when using envy so it can download the latest nvidia installer and any other additional packages.

I hope this helps you folks.  What i have noticed though, my desktop is not as smooth with windows resizing moving etc..., but on the other hand q4 runs so delicious so i can live with this :lolflag: 

Also if you update your kernal/system, apparently you will have to reinstall these drivers again.

What i really would like to know though, if i try out fiesty fawn will the drivers be automatically installed? or will ubuntu atleast start the xserver on fresh install to avoid all this xorg.conf tweaking @ start?  Also if any1 has tried out the new fiesty fawn, does the nvidia driver work nice and smooth, and can you install the driver via synaptic packagemanger or apt?

K folks, pardon my grammer and typos.  This is my 1st real contribution on a how to and hope it works out for ya.

ultm8

---

### Post by doriard on 2007-04-22
> **Kerry Lange said:**
> Finally!  It worked!

Thanks.  I've got Feisty working with my hardware.  So, here's what worked:

1.  Used the alternate CD to get everything installed.  At this point the X server didn't work with my nVidia 8800 card.

2.  I got the latest nVidia drivers from the nVidia site and, using Windows, saved them to a CD.

3.  I booted to Ubuntu and used the command line to install the nVidia drivers.  

4.  I mounted the CD and copied the drivers to the file system.  I could probably have run the driver utility from CD but I did it from the HDD.

5.  The drivers come with a utility to configure the X server so there was no need to manually edit the X server config file.  Before the installation utility would work, though, I had to have "libc6-dev" installed first.

6.  When I rebooted, everything came up as you'd expect!

I tried installing libc6-dev (so that I could install the GeForce 7600GT NVidia drivers) but the Synaptics installeer gave me the error message:

The following packages have unresolvable dependencies...
Depends: libc6 (=2.3.5-1ubuntu12.5.10.1) but 2.5-0ubuntu14 is to be installed

I am new to Linux/Ubuntu.  Any ideas on how to resolve this?  I looked for marked packages waiting to be installed (is that what it was talking about?) but didn't see any.  What is the '2.5-0ubuntu14' waiting to be installed that it's talking about?  

I just installed Fiesty Fawn for my first Linux install today and I'm still getting used to it.  I need to get dual monitors working.

---

### Post by ruibuntu on 2007-05-07
You should have the build-essential and the linux-source package installed.

And then install the driver by running it as a super user

---


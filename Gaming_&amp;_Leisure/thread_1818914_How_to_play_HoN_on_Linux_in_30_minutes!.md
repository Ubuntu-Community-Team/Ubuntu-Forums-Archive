---
title: "How to play HoN on Linux in 30 minutes!"
date: 2011-08-05
forum: Gaming &amp; Leisure
---

### Post by rootfairy on 2011-08-05
[for windows, parallel operating systems]

[IMG]http://tux.crystalxp.net/png/photozel-linux-mint-18142.png[/IMG]

hi there,

today i am going to show you, how you can install and configure a linux on your computer pretty easily to play HoN in linux with a few mouse clicks and without any dangers for your computer. :)

advantages of linux:
- benchmarks have proven that the gaming performance of windows 7 and linux are equal
- its a free, stable, fast and dynamic operating system
- no pre-existing knowledge necessary
- easy to use

_**info:**_
in general, the recommendations to run a linux smooth on your computer arent very high, but you should ascertain, that your hardware meets the HoN minimum system requirements specifications to be sure, that HoN will run smooth in linux also. you must have a suitable nvidia or ati card installed to be able to play HoN in linux. to put it simple: if you can run a 3d-game with opengl in windows (HoN, cs, q3, lol, wow, etc. etc.) with enough frames per second, you should be able to run the game in linux at the same speed.

HoN minimum system requirements [Windows and Linux]:
[http://www.heroesofnewerth.com/specs_pop.html](http://www.heroesofnewerth.com/specs_pop.html)

ok, enough of that wacky theories - lets get ourselves a linux!

as some of you may know, there are really a lot of linux distributions out there, but which one is the best for HoN you are asking yourself now? the answer is simple. there are a lot of good distributions for gaming out there, but the performance of a linux system depends on your knowledge of linux, so, yeah, i think we all get the point.

our linux of choice for [this guide] will be **[COLOR=Lime]linux mint[/COLOR]** which comes from ubuntu, which comes from debian. as you may heard of ubuntu, you could try that, or kubuntu or xubuntu, but i do not recommend it. you should be and stay connected to the internet during this installation, because of the automatic update function of linux, which functions during and after the initial installation.

prepare yourself. you are about to install a new operating system. do this on your own risk. i provide the information for a procedure, that i repeated myself more than 50 times, without any damage to my system or any other installed operation systems. the method is quite simple and officially distributed, so everything should be fine and you dont need to worry in case you are uncertain now. of course i dont take any responsibility for any caused harm. everything i use or link in here is absolutely proven safe and free!
    
go [here]("http://www.linuxmint.com/download.php") and download the iso image "CD No Codecs". you can choose between 32bit and 64bit. if you are uncertain, choose 32bit. if you know, you have a 64bit processor, you can choose 64bit, but you could choose 32bit, too. there wont be any huge differences. save the file in windows [xp/vista/7] in your download folder, just any folder you use to save downloads, for example: C:\Downloads.
    
install daemon tools lite from [here]("http://disc-tools.com/request?p=4c9886689142ecc8a677345dce7e4466/DTLite4413-0173.exe"), its free. let daemon tools create a virtual drive for you. the installation should be very simple. [here]("http://forums.heroesofnewerth.com/amber.cit.cornell.edu/citweb/software/swl/.../daemonhowtoinstall_final.pdf") is a guide [pdf file / university of cornell], which shows you how to install it. after the installation it may require you for a restart, do so. after restarting, daemon tools will be in tray. right click on it and follow this [guide]("http://www.digital-digest.com/articles/mount_watch_iso_files_page1.html") to set your virtual drive and mount the linux image you downloaded. if you are prompted for any action select no. we only want to mount the image, do nothing more than that.
    
after you have mounted the linux iso image file in daemon tools, the content of the cd will appear in your windows explorer. click on the drive to open it. now you will see several folders and files. click on mint4win to start the installer. choose install in windows.
    
now you can choose your username and password, the hard drive you want linux to be installed on and the size it should use [recommended 10gb, 5gb min.]. dont worry about your windows installation, i installed win7 64 and out of that, windows xp and out that, i installed linux by the way mentioned here many, many times. you will have no boot loader problems after this installation. after the installation there will be a text menu in which you can select your operating system with the arrow keys your keyboard (the buttons you used to play doom with).
    
if you have set everything correctly and you are sure, that you want to install it, then check again if everything has been set to your needs and then click on install. the installation will go very quickly. after that you can reboot. then you can choose linux to boot, do so.
    
**_info:_**
if you have multiple windows or other operating systems, choose the boot section of the windows you installed linux in order to boot linux. for example i can choose in the bootloader of windows 7:
              > 
Other Windows Operating Systems
              Windows 7
              Linux Mint
    when i choose linux mint now, it says it cant boot, but thats ok, because linux was installed in windows xp, which is in the boot section Other Windows Operating Systems. if i go there, i see Linux Mint again and Windows XP now and can boot it from there.
    
now, that everything went well and you booted linux, it will complete the installation in a few minutes. after that, it will reboot, so dont be scared. boot into linux again then, enter your login and stay on the desktop for a few seconds to one minute, to let everything load [the updater is working and checking]. ignore the welcome screen for the time being. after you notice your computer is idle [hard disk activity], you will see some notifications, like updates or additional drivers. dont enable drivers yet. first, click on the update shield icon in your tray and enter your password. now it will check some stuff.
    
the update manager will tell you, you need to update, so click on install actualizations / updates. after that, run the update manger again, e.g. let him check for updates again and you will see a lot of updates. install them all! :) after that, reboot your computer.
    
after your rebooted your computer you must choose the driver for your graphic card. 

_**ATI:**_ click on Menu -> Control Center -> Additional Drivers. there you will see a proprietary ati driver for your ati card, which can be activated. do so and let it install. then reboot. the installation is complete. you dont need to download catalyst drivers from ati. actually these are bugged since three versions and cant be used right now. linux will use a proprietary ati catalyst 11.4 driver, ati catalyst are bugged since 11.5 until 11.7. maybe 11.8 will fix the bug. you can play hon with the linux proprietary excellently, so there is no need for ati catalyst most up to date version at all, and the linux proprietary drivers are as good as equal to the 11.4 ati catalyst driver or even better in performance. 

_**NVIDIA:**_ the opposite is true for nvidia. they have very good drivers for linux and windows. so go to nvidia.com and download the suitable driver version for your nvidia card, but the installation is a bit more complicated. save the file somewhere you can find it again, usually /home/user/Dowloads. click on Menu and then Terminal. now enter: > user@linuxmint ~ $ gksudo gedit /etc/modprobe.d/blacklist. this will open a text editor. enter the following at the beginning in the first free line, so that it looks like this: 
> 
# This file lists those modules which we don't want to be loaded by
    # alias expansion, usually so some other driver will be loaded for the
    # device instead.

    [B]blacklist nv
    blacklist nv nvidia_new
    blacklist vga16fb
    blacklist nouveau
    blacklist rivafb
    blacklist nvidiafb
    blacklist rivatv[/B]

    # evbug is a debug tool that should be loaded explicitly
    blacklist evbug

    # these drivers are very simple, the HID drivers are usually preferred
    blacklist usbmouse
    blacklist usbkbd[...]
now save the file and quit gedit, but stay in the terminal
    
now enter: > user@linuxmint ~ $ sudo apt-get install build-essential xserver-xorg-dev linux-headers-`uname -r` libc6-i386 libc6-i386 is only needed when you have a 64bit system. this will download and install some stuff. now comes a procedure, where you dont have a graphical userface, so print this guide out or write it down, to know, what you have to do.
    
when you press strg + alt + f1 you will go into a text terminal. login there. now enter: > user@linuxmint ~ $ sudo /etc/init.d/gdm stop. the graphical userface will stop in the background. now enter: > user@linuxmint ~ $ cd /home/user/Downloads. enter > user@linuxmint ~ $ ls [l like lion, s like swiftblade] to view the contents of the folder. there you will see your downloaded nvidia driver file. now enter: > user@linuxmint ~ $ sudo chmod +x filenameofdriver, if you enter the beginning of the filename you can press tab for completion of the filename. then press enter.
    
now enter: > user@linuxmint ~/Downloads $ sudo sh ./filenameofdriverfollow the installations. select no, when asked to download anything. after the installation run > user@linuxmint ~ $ sudo nvidia-xconfig. you are done. now enter: > user@linuxmint ~ $ sudo /etc/init.d/gdm start to start the graphical interface again. nvidia should work now. if not, try a complete reboot. > user@linuxmint ~ $ sudo reboot you can configure it in Control Center with nvidia settings manager. see here for further and official documentation:
    [http://linux.die.net/man/1/nvidia-xconfig](http://linux.die.net/man/1/nvidia-xconfig)
    [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
    [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

now you only need to download HoN for linux. after you downloaded it, go to the terminal and go to your download folder. then enter: > user@linuxmint ~ $ sudo chmod +x HoNClient-2.1.0.1.sh, then enter > user@linuxmint ~ $ sudo sh ./HoNClient-2.1.0.1.sh and let it install. after it is installed you can run HoN from the menu or go to the installation path in terminal or it it doesnt start: > user@linuxmint ~/HoN $ sudo chmod +x hon.sh hon-x86 hon-x86_64, then > user@linuxmint ~/HoN $ ./hon.sh.

thats it. if you have any problems or questions ask here.

you can upgrade linux mint to the dvd version in the welcome screen or if you go Menu -> Search: dvd -> Upgrade to DVD. in the same way you can add multimedia codecs.

---

### Post by rootfairy on 2011-08-05
if you have problems with frames per second, log yourself into gnome [no effects] session. which you can choose at the login screen from below.

or you can disable compiz and composite for better performance and vs. overlay errors. go to Menu -> Control Center -> Compiz Config Settings Manager -> demark OpenGL and Composite [this is just overlay]. and / or check vsync options in OpenGL, Composite and your respective gfx-settings manager [nvidia-settings / amdcccle]. disabling vsync can help slow frame rates or lame behaviour.

to start nvidia-settings or amdcccle open a terminal and enter:

> user@linuxmint ~ $ gksudo nvidia-settingsor 

> user@linuxmint ~ $ gksudo amdcccle

---

### Post by thatguruguy on 2011-08-05
Tell me more about this Linux Mint you have mentioned.

It sounds fascinating.

---

### Post by rootfairy on 2011-08-05
yeah, its the wrong forum maybe... :Z i couldnt post it in the hon forum... maybe i should note, that x/k/ubuntu can be installed in the same way with wubi.

-.-

Linux Mint 11 LXDE RC [http://www.youtube.com/watch?v=NzbRFd-dAkQ](http://www.youtube.com/watch?v=NzbRFd-dAkQ)
Linux Mint 11 Katya [http://www.youtube.com/watch?v=E9QUm3jbMbo&feature=fvwrel](http://www.youtube.com/watch?v=E9QUm3jbMbo&feature=fvwrel)

---

### Post by DanieeeLmc on 2011-08-05
I don't know what to do, I'm a real noob with ubuntu... I installed the driver, logged in no effects mode disable all effects from hon, but I still can't play...

---

### Post by Basher101 on 2011-08-05
did you install the proper drivers for your graphic card? in your system preferences is an icon that says hardware drivers. Try that and report the outcome

---

### Post by rootfairy on 2011-08-06
you probably have a nvidia card and installed proprietary drivers. stick to the guide and it will work.

---


---
title: "How to get HP 1020 work on Ubuntu?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by pmilin@ptt.yu on 2005-10-18
After unsuccessfully trying to get my HP 1020 work under linux I must conclude that none of the proposed "solutions" work:
a) I did HPLIP Installation, but 'apt-get install libsnmp5-dev' was not possible, because of unresolvable dependencies
b) I tried HPLIP from Ubuntu repositories, but that wasn't successful too for unknown reasons
c) HP Laserjet 1020 driver for Linux with 'foo2zjs' upgraded driver - unsuccessful! Reasons: first, 'make install-hotplug' cannot be done and that has been explained somewhere here, but after some hand-job, it was a success, yet printing is not working. Moreover, there are no HP 1000 or 1005 drivers.

Can anyone help with this matter?!?

I am new with Linux/Ubuntu, and getting to be seriosly frustrated. At least some things are much easier under MS Windows. 

Sincerely, pmilin:(

---

### Post by tigrez on 2005-10-24
Try this:

 cat /usr/share/foo2zjs/firmware/sihp1005.dl > /dev/usb/lp0

It upload the firmware to work in my 1005. I don't know if it is the same for 1020... Anyway, this the only thing that CUPS don't do at startup...

---

### Post by cagljevic on 2005-10-25
i too am in the very same boat.  i have scoured all the google results on "linux hp 1020" and have followed all of these suggestions.  here is my current status:

the firmware is loaded, although i must do it manually each time.  the only usable drivers that recognize the printer so far that i know are the hp laserjet 1000 and laserjet 1005.  when i attempt to print from any source (open office, gedit, firefox, etc) i get blurred text.  i noticed in some spot that also attempted to address this issue that text is printed clearly only if a4 page size is selected.  guess what, i have done that and the output is still blurred.  i am completely stumped.  i feel i am close to getting it working since the printer does print something, its just useless garbage output though...

-mark

---

### Post by Johnp_g on 2005-11-11
Hi,

I've just migrated over to Ubuntu (from all manner of Linuxes - lastly Debian sarge) and also recently got an HP1020.

It was a hassle to get it to work under Sarge, but last night I got it going under Breezy.

You need to get the udev patched version of foo2zjs at:-

[http://support.ideainformatica.com/hplj1020/foo2zjs-patched.tar.gz]("http://support.ideainformatica.com/hplj1020/foo2zjs-patched.tar.gz")

I'm not sure if you need the "normal" foo2zjs package already installed (my system had it there anyway).

Once you untar the archive (tar zxvf foo2zjs-patched.tar.gz) you need to cd into the new foo2zjs directory and 

make
sudo make install

this will install the drivers and firmware.

Next edit the file (in the foo2zjs directory you're currently in) called 58-foo2zjs.rules (or some such) to correct a bug (it took me ages to work out why udev wouldn't upload the firmware)

look for the entry for the 1020 - specifically change 

SYSFS{idProduct}=="2B17"

to 

SYSFS{idProduct}=="2b17"

(the typo prevents udev from spotting the printer being plugged in!)

now install the udev scripts/rules :-

sudo make install-udev

I don't know if you need to restart udev (I messed about so much last night I got lost) but it can't hurt (?)

sudo udevstart

When you power cycle the printer you should hear it whirring as it powers, then whirring again as the new firmware is uploaded.

To check the firmware is in look at /var/log/messages - -there should be some note of successful upload of firmware.

Now you need to restart cupsys 

sudo /etc/init.d/cupsys restart

Next use the normal gnome printer config tool to install the HP1020 - you should see the option to use the correct HP1020 foo2zjs driver.

(btw you might need to install the "build-essential" package - and "make" - to compile the foo2zjs package)


Hope this helps someone!

I also found it necessary to install "cupsys-bsd" to get the cups versions of "lpr lpq" etc, and also :-

sudo lpoptions -o cpi-12 -o lpi=7 -o page-left=36 -o page-right=36 -o page-top=36 -o page-bottom=36

to make plain (lpr) text fit nicely on the page.

Cheers,

John

---

### Post by Johnp_g on 2005-11-11
Of course - I've just noticed this thread is in "Hoary" & I don't know if Hoary uses udev (having just installed Breezy as my first taste of Ubuntu).

If is doesn't you might like to upgrade to Breezy first?

John

---

### Post by Pointwood on 2005-11-11
That made it print (I'm using Kubuntu with KDE 3.5beta2), but the output was completely fuzzy and for a few moments felt really unhappy again :p
However, changing the paper size from letter to A4 (which is what we uses here in Europe ;) ), fixed that :)

Thanks a lot for the explanation!

---

### Post by Johnp_g on 2005-11-11
Yes, I'd seen rubbish printed with the wrong paper size selected while I was using Debian. When I got it working with Ubuntu it must have been already set to A4.

Glad I've helped someone!

Cheers

John

---

### Post by lizardking on 2005-11-13
Thnk U to all.
It works for me...:KS :KS :KS :KS :cool: 

Great ubuntu and great ideainformatica howto..

Thnaks for All everybody

---

### Post by gasparov on 2005-11-21
[QUOTE=Pointwood]That made it print (I'm using Kubuntu with KDE 3.5beta2), but the output was completely fuzzy and for a few moments felt really unhappy again :p
However, changing the paper size from letter to A4 (which is what we uses here in Europe ;) ), fixed that :)

Thanks a lot for the explanation![/QUOTE]

I've changed the paper size in gnome printing config utilty but :

```
Nov 21 21:45:12 localhost foo2zjs-wrapper: foo2zjs-wrapper -P -r600x600 -p1 -s7 -m1 -d1 -n1 -I0
Nov 21 21:45:14 localhost foo2zjs-wrapper: gs -sPAPERSIZE=letter -g5100x6600 -r6 00x600 -sDEVICE=pbmraw
Nov 21 21:45:14 localhost foo2zjs-wrapper: foo2zjs -r600x600 -g5100x6600 -p1 -m1  -n1 -d1 -s7  -u 102x102 -l 102x106     -P

```

How did you change papersize?

---

### Post by gasparov on 2005-11-21
I still don't know what exactly was the problem but it seems it was related to my locale (english)
1)dpkg-reconfigure libpaper1--->chose a4 in my case
2)remove and reinstall printer with gnome utility

these two steps solved the problem

---

### Post by Pointwood on 2005-11-21
gasparov: I changed it in the KDE printing manager. I'm not really familiar with Gnome.

---

### Post by gasparov on 2005-11-23
well know it works,thks in any case:)
I changed the foo2zjs-wrapper script in /usr/bin so that it "wraps" a4 pages by default by replacing 1 to 9 somewhere at the begining (everything is explained inside the script) then printing from non gnome applications such as Acroread was fine so i searched the forum and find out that on my system I have a library that tells my system what kind of paper I use..:D

---

### Post by pedersen on 2005-11-23
thank you : i been having the same problems with my printer and yiipppe now it works

---

### Post by Kokanee on 2005-11-27
Well this sucks.  My printer works but will only print on A4 sized paper.  I really wish it would print on Letter sized.  My Canon i960 doesn't really work either.  It sort of does but print quality is poor.   Well it looks as my decision is made now....No more Linux.  This piss poor printing support is driving me up the wall.  I guess it's time for a Mac :(

---

### Post by Pointwood on 2005-11-28
The Laserjet 1020 (and several others I believe) is a "windows" printer and HP therefore doesn't provide drivers for it for Linux. I was stupid enough to buy it anyway for some odd reason :p

---

### Post by kmarker on 2005-11-28
Ok, I got my 1020 to print test pages but If I try to anything else to print (Open Office) I get nothing.  Any Suggestions?

---

### Post by Kokanee on 2005-12-01
I have noticed on the [official foo2zjs website]("http://foo2zjs.rkkda.com/") that the driver has been updated to support the HP 1020!  Woot!  See the [changelog here]("http://foo2zjs.rkkda.com/ChangeLog").

It's been tested in FC3.  Lets all get testing and hope this can make it into Dapper!

---

### Post by Kokanee on 2005-12-01
UPDATE!

I downloaded it from the website and compiled and installed it and it worked!!  Letter sized paper and all! Woo hoo! :D:D:D

---

### Post by Sophisto on 2005-12-04
Just to say that the new foo2zj drivers worked for my LaserJet 1020! I only have one questions: How do you set the dpi? 

(at the proporties section for the printer there is a field which says "resolution" but it is unmakred)

---

### Post by earth_walker on 2005-12-05
I had the foo2zjs-patched setup from earlier on in this thread, which would only print on A4 and only some of the time.

So I tried to install this new version mentioned by kokanee following the instructions on that page.

Now the gnome printing panel doesn't even detect that the printer is there. Manually setting the location to usb printer 1 doesn't work either.

This new version uses hotplug, while using the patched driver I had it working using udev. Could this be the problem? Did Sophisto and Kokanee do anything other than the instructions given wiht the latest driver?

---

### Post by earth_walker on 2005-12-05
Please help. I must have put 20 hours into false starts and bad advice getting this printer to work (mostly), and really should have left well enough alone, but since 2 people had no problems at all, I thought it would be safe to upgrade to the latest foo2zjs drivers. After installation, the gnome printing panel stopped detecting my printer. 

So I tried to apply the udev patch given at [http://support.ideainformatica.com/hplj1020/](http://support.ideainformatica.com/hplj1020/) to the new foo2zjs driver, with no luck. 

After having no luck with the new foo2zjs drivers, I tried to reinstall the older patched udev foo2zjs drivers again using Johnp_g's post above. 

However, the gnome printing panel still doesn't detect my printer! I've tried everything - rebooting, restarting udev, restarting cupsys, restarting the printer, reinstalling in different directories. 

For various commands I get as follows:
$ cat /proc/sys/kernel/hotplug
   /sbin/udevsend
and
$ sudo cat /usr/share/foo2zjs/firmware/sihp1020.dl > /dev/usb/lp0
   bash: /dev/usb/lp0: Permission denied
and finally 
$ sudo usb_printerid /dev/usb/lp0
   Error: Input/output error: GET_DEVICE_ID on '/dev/usb/lp0'

So the printer is definitely not being recognised. It is on. It has been turned off and on many times.

I have no clue where to go from here - up til now the problem has been with the printer giving errors, but it has always been detected at least. 

Which components control this behaviour, and how do I restart/reinstall them?
Is there some way to check what's going on in udev? Has one of the installation scripts messed things up?
Is there a way to turn on 'hotplug' so that it may detect the usb printer instead?

Should I:
reinstall udev?
reinstall some other version of foo2zjs?
uninstall everything printer-related and start again? How would I go about that?

---

### Post by Kokanee on 2005-12-07
[quote=earth_walker]I had the foo2zjs-patched setup from earlier on in this thread, which would only print on A4 and only some of the time.

So I tried to install this new version mentioned by kokanee following the instructions on that page.

Now the gnome printing panel doesn't even detect that the printer is there. Manually setting the location to usb printer 1 doesn't work either.

This new version uses hotplug, while using the patched driver I had it working using udev. Could this be the problem? Did Sophisto and Kokanee do anything other than the instructions given wiht the latest driver?[/quote]

When I installed mine I didn't use hotplug.  I had first installed the patched driver then I installed the new official one.  I skipped the hotplug step and it worked.

---

### Post by Kokanee on 2005-12-08
I openned a bug report asking that the official package in Ubuntu be updated.  [http://bugzilla.ubuntu.com/show_bug.cgi?id=20648]("http://bugzilla.ubuntu.com/show_bug.cgi?id=20648")

---

### Post by brainkilla on 2005-12-13
I've just bought the printer, plugged it in, installed the driver, rebooted, and it worked! Did the make install-hotplug step too, and it loaded the firmware upon rebooting, no problemos... earth_walker, if I were you I would check the USB cable, I had a really nasty experience with the bad cable once, all kind of wierd problems (mouse not working, and such). The only problem I have is calibration: printouts are not centred properly, and not aligned as they should be... Also, is there any way to switch to other resolution/economic mode since I need to print text primarily (greyed out in gnome-cups-manager, cups web interface disabled for security reasons!!!)? Is PPD files editing/tweaking (and how to perform such a task) a viable solution to my problems? Thanx

---

### Post by earth_walker on 2005-12-13
Thanks to both Kokanee and Brainkilla for your suggestions. 

The latest foo2zjs drivers do not work for me at all, and any attempt at installing these completely kills Ubuntu's ability to even detect my printer. To get back to a working state I have to reinstall all of the printing packages (cups, etc) AND manually erase every file that was modified by the two foo2zjs driver packages by rerunning them and taking note. 

From this 'base', (and only from this base - believe me, I've tried every permutation, including using the latest ppd files with the patched driver), I can get the udev-patched foo2zjs driver kindof working so that my networked windows computers can print fine, although in Ubuntu I can only print text and pdf files. All Open Office printouts are garbage.

I noticed that there has been an update to the foo2zjs tarball at [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/"), however each time I attempt to install this driver it takes me 3-4 hours to get the minimal printing capabilities I have back. So needless to say I'm hesitating to try this again. 

This is pretty close to useless situation for me since it teathers me to my windows computers for any actual work, but I don't have the time to reinstall Ubuntu completely. 

Is there an easier way that I can get my printer, udev and hotplug settings back to a 'fresh ubuntu install' state so I can retry the latest drivers?

---

### Post by brainkilla on 2005-12-13
Ok, so its not a USB cable ;) . I am really sorry to hear that this driver caused you so much trouble, since it seems that everybody else here experienced just the opposite. And if somebody could point me to a tweaking manual in order to get lower res and few more options, if that's even possible, I would really appreciate it. When I take a look at options hplip offers, I get rather envious, since 1020 predecessor 1010 is fully supported. But, what the hell, at least it works...

---

### Post by Jenda on 2005-12-15
Hmm
Still doesn't work. I changed the paper size in the gnome utility, but that isn't enough. Does anyone know how to do this?

---

### Post by Pointwood on 2005-12-15
I haven't got any solution, instead I seem to have b0rked my install, but that is most likely own fault :) 

That what you get when you experiment...

---

### Post by Jenda on 2005-12-15
I found the solution for my problem.
Do a
sudo gedit /etc/cups/ppd/LaserJet-1020.ppd
And look for Default page size or something. Change it to A4 and save. Maybe you now have to restart cups and/or udev. Maybe not :), but it worked for me.

---

### Post by Jenda on 2005-12-18
Nope... that doesn't solve it. It prints test pages OK, but when I need to print something from OO.org, it's still borked.

---

### Post by urza on 2005-12-23
I get it works with both of the drivers, the a4-solo one and the all one... I also try to print some images and it works fine for me, with software like eog or gthumb. Printing under the gimp seems impossibile, since it doesn't list correct driver for hp 1020... 
When I try to get it works on another computer, I got this message in /var/log/syslog:

printer.c: usblp0: failed reading printer status

I cannot solve the problem: I tried in every manners, nothing! I simply did what I've done on the other computer. It doesn't work.
I guess I've got a usb port broken or whatever (maybe poor supported by linux, but I've tried several kernels...).

---

### Post by Jenda on 2005-12-24
Hmm... my problem is now solved: I finally managed to set A4 as the default paper in OO.org's printer settings.

---

### Post by GavLac on 2005-12-26
[QUOTE=Johnp_g]

Next edit the file (in the foo2zjs directory you're currently in) called 58-foo2zjs.rules (or some such) to correct a bug (it took me ages to work out why udev wouldn't upload the firmware)

look for the entry for the 1020 - specifically change 

SYSFS{idProduct}=="2B17"

to 

SYSFS{idProduct}=="2b17"

(the typo prevents udev from spotting the printer being plugged in!)

now install the udev scripts/rules :-

sudo make install-udev
[/QUOTE]

This change of 58-foo2zjs.rules file is the greatest trick that I ve ever seen!!!
That was my resolve on my third day of sufferings!
Johnp_g  you are a very great guru!!!

Thx,
GavLac

---

### Post by thebigjc on 2005-12-28
If anyone is still dealing with blurry images on US Legal paper, you can try this out:
[http://forums.gentoo.org/viewtopic-t-378173.html]("http://forums.gentoo.org/viewtopic-t-378173.html")

---

### Post by earth_walker on 2005-12-29
Simply using the latest (Dec 28th) driver from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) fixed everything, including letter-size printing.

Since the udev setup from the older driver version was detecting the printer well, I did not "make install-hotplug" at this install. Otherwise I followed the instructions in the INSTALL file.

Thanks to everyone for your suggestions.

---

### Post by urza on 2005-12-30
I'm desperate! I can't get it work my printer again!!!
I followed all the instruction you've provided here, but nothing!
When I attached my printer to the computer, I got this in my /var/log/syslog:

usb 1-3: new high speed USB device using ehci_hcd and address 2
usb 1-3: device descriptor read/64, error -110

It's not the usb cable, since I tested it on a windows machine and it worked!

What can I do???:( :( :(

---

### Post by gooboo on 2006-01-01
Y'all:

I had the same problem. Turns out there is a minor bug in the latest version of the foo2zjs printer driver.

Get the latest version of the driver and untar as instructed. Change the rules file hplj10xx.rules to change the entry for LaserJest 1020 to be as follows: SYSFS{idVendor}="2b17" instead of 03f0 as given. This seems to fix the auto-detect problem, and uploads the correct firmware to the printer. Similar fix for 1005; get the correct value from last foo2zjs install. Follow the rest of the instructions as given.

Thanks to John for twigging me on to this fix. BTW, the new driver means that all the fiddling previously required (including papersize) is no longer required.

Cheers,
GooBoo

---

### Post by urza on 2006-01-09
no way, even with that trick it doesn't work!!!
i even shutdown hotplug and let udev do the hard stuff. nothing!
very weird support for linux!
i'm considering buying another printer!
when i run usb_printerid:

Error: Input/output error: GET_DEVICE_ID on '/dev/usb/lp0'

i can't fix it!

---

### Post by brainkilla on 2006-01-14
[QUOTE=urza]
usb 1-3: device descriptor read/64, error -110
[/QUOTE]

Seems to me that this is kernel message, i.e not udev/hotplug specific one. Check that your cable is functional (it's me again with the cable thinggy, but I had some nasty experience with those). Does the printer work in Windows, if you have Windows that is? Perhaps this printer itself doesn't function as it should?

tail -f /var/log/messages

Jan 14 15:42:54 localhost kernel: [4342660.432000] usbcore: registered new driver usblp
Jan 14 15:42:54 localhost kernel: [4342660.432000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Jan 14 15:42:54 localhost usb.agent[5484]:      usblp: loaded successfully
Jan 14 15:42:54 localhost usb.agent[5484]:      hplj1020: loaded successfully
Jan 14 15:42:55 localhost /etc/hotplug/usb/hplj1020: loading HP LaserJet 1020 firmware /usr/share/foo2zjs/firmware/sihp1020.dl to /dev/usb/lp0 ...
Jan 14 15:42:56 localhost /etc/hotplug/usb/hplj1020: ... download successful

This is the tail output: as you can see, kernel does its thing first registering the generic printing driver and than loading foo2zjs through hotplug... if I am not mistaken, this is the correct explanation of the process...

---

### Post by urza on 2006-01-14
ok, now it worked for me.
but it still has got a lot of problems: with large documents, it only prints 15-20 pages then it hangs and needs to be restarted.
i think is a driver problem, which is probably immature...

---

### Post by zlogic on 2006-01-18
I've downloaded the updated foo2zjs package from
[http://packages.ubuntu.com/dapper/text/foo2zjs](http://packages.ubuntu.com/dapper/text/foo2zjs)
and it works!
However all non-foo2zjs HP printers have vanished...

---

### Post by zlogic on 2006-01-18
Ah, it appears that new foo2zjs drivers name all foo2zjs HP printers "Hewlett-Packard" while all other HP are named "HP".

---

### Post by gostview on 2006-04-18
[QUOTE=Johnp_g]Hi,

I've just migrated over to Ubuntu (from all manner of Linuxes - lastly Debian sarge) and also recently got an HP1020.

[cut...]

Hope this helps someone!

Cheers,

John[/QUOTE]
[B]
GREAT, IT WORKS!! [/B]

tnx so much :)

---

### Post by edopizza on 2006-07-27
> **Johnp_g said:**
> Hi,

Once you untar the archive (tar zxvf foo2zjs-patched.tar.gz) you need to cd into the new foo2zjs directory and 

make
sudo make install

this will install the drivers and firmware.

John

I am already lost at the second step, with the command make I get: 

me@ges1:~/install/foo2zjs$ make
bash: make: command not found
me@ges1:~/install/foo2zjs$ sudo make install
sudo: make: command not found
me@ges1:~/install/foo2zjs$ 

Do I need to install a "make" command?

---

### Post by paulmilliken on 2006-07-27
Yes, you need the make command.  It's in the build-essentials package if my memory is correct.

---

### Post by Jenda on 2006-07-30
Almost correct:
```
sudo apt-get install build-essential
```

---

### Post by RH9R on 2007-05-24
You Gotta be Freaking kidding me. I sit here w/ a 2 hr old HP 1020 and have to edit an unzipped tarball , do several makes just to get a freaking page printed. This is crap. I absolutely love Feisty, but this printing crap will drive away alot of people. No response to my posts about getting an HP 1100 to work. I like the OS enough to spring for a new printer, and get the same crap. This is NO BUENO. 
 
I'm glad Dell is shipping Ubuntu now (and still charging as though they paid MS the $100+), but if you can't print, who cares?

---

### Post by mdurham on 2007-05-24
I have the 1020 working fine on Ubuntu but I'd like to print from another machine (the wife's) over the network, but XP doesn't have a network driver for the 1020. What to do?
I can install the printer on Windows and print from Linux, but I's not convenient. How can I print over the network from XP to Linux?
Thanks, Mike

---

### Post by Pointwood on 2007-05-25
> **RH9R said:**
> You Gotta be Freaking kidding me. I sit here w/ a 2 hr old HP 1020 and have to edit an unzipped tarball , do several makes just to get a freaking page printed. This is crap. I absolutely love Feisty, but this printing crap will drive away alot of people. No response to my posts about getting an HP 1100 to work. I like the OS enough to spring for a new printer, and get the same crap. This is NO BUENO. Yeah, because it is clearly the Linux developers fault that HP hasn't created drivers for your printer ;)

Now, the situation is a bit more complicated because the printer you have (which I have as well) is one of those crappy windows printers.

---

### Post by docadams on 2007-06-07
Here is how to get the HP1020 to work under kubuntu 7.04 in June 2007.

Assuming that you have not installed any printer or do a clean install before
trying this.  The steps below done after new install of 7.04, did system updates
to get to kernel 2.6.20-16.28 and did a reboot.

1.   sudo vi /etc/papersize

     change a4 to letter if you are using letter size as we do in the USofA

2.  wget -O foo2zjs.tar.gz  [http://foo2zjs.rkkda.com](http://foo2zjs.rkkda.com)
     tar -xvf foo2zjs.tar.gz
    cd foo2zjs
    make
    ./getweb 1020
    sudo make install
    sudo make install-hotplug

3.  cat /usr/share/foo2zjs/firmware/sihp1020.dl  > dev/usblp0

    if you do this correctly, printer will startup and front lights will alternate

4.  sudo vi /etc/hotplug/usb/hplj1020

     in line 32  /dev/usb/lp0  changed to  /dev/usblp0
     in line 33  DEV=""           changed to  #DEV=""

5.  kaddprinterwizard

    take steps to go through process by going to next pages after each of the following:

    local printer  (parallel, usb, ... )
   select USB HP LaserJet 1020  last one in list of ports
   HP  for manufacturer and LaserJet 1020 foo2zjs

   and name printer hp1020

  also print the test page when asked and if it prints you are home free

6.  lpoptions -d hp1020

7.  lpstat -t

    this should show hp1020 as default printer, scheduler is running and hp1020 is accepting print jobs


Hope this helps someone.  

FYI

:D

---

### Post by weiersc on 2007-06-10
I'm also hoping that somebody could give simple instructions to get a Windows XP box to print to the HP1020 installed on my Ubuntu Feisty machine.

---

### Post by amrishodiq on 2007-06-12
> **docadams said:**
> 

2.  wget -O foo2zjs.tar.gz  [http://foo2zjs.rkkda.com](http://foo2zjs.rkkda.com)
     tar -xvf foo2zjs.tar.gz
    cd foo2zjs
    make
    ./getweb 1020
    sudo make install
    sudo make install-hotplug

3.  c**at /usr/share/foo2zjs/firmware/sihp1020.dl  > dev/usblp0**

    if you do this correctly, printer will startup and front lights will alternate


I failed in this step.

Something like this occure:

sudo cat /usr/share/foo2zjs/firmware/sihp1020.dl > /dev/usblp0
bash: /dev/usblp0: Permission denied

i think you missed /dev/usb/lp0 but this doesn't work either

:(

---

### Post by weiersc on 2007-06-12
I don't know if this helps anybody, but I had very little problems getting my HP 1020 printer to work on a fresh install of Ubuntu Feisty.

Feisty immediately recognises the printer and automatically loads the foozjs-driver.

The only think that it does not do (because it is not allowed to due to restrictions) is to automatically load the firmware to the computer. This is however just a short two or three step process.

At the command line a person downloads the firmware by using the command: getweb 1020

It downloads a sihp1020.img  file. This file needs to be converted to a sihp1020.dl file (If I understand it correctly all that happens is that a certain header needed by the printer is added to the file.).

To convert a person just uses:

sudo arm2hpdl sihp1020.img > sihp1020.dl

Now a person has the sihp1020.dll file and all that remains is to copy this file to the directory/folder where the printer will actually pick it up:  /usr/share/foo2zjs/firmware/
(Note... you need to have root priveledges to do this because the /usr/share/foo2zjs/firmware/ folder has restricted access)

Once this is done I am able to go go to the System Menu, Select printing, install the printer and it works perfectly every time.

----------------------------------------------------------------------------------
Note: What I found much more difficult was to share the printer over a network so that somebody on a Windows XP computer could print from it. In order to do that a person has to edit the samba configuration file.

---

### Post by mdurham on 2007-06-12
> Note: What I found much more difficult was to share the printer over a network so that somebody on a Windows XP computer could print from it. In order to do that a person has to edit the samba configuration file.
weiersc, can you explain more about this please. I'd like to print from Windows to a printer connected to a Linux box, but I don't see any driver in Windows. I tried an (incorrect model) HP driver just to see what happened and the file got sent to the Linux print queue but didn't print of course. Shouldn't HP supply a network driver for this printer?

Cheers, Mike

---

### Post by weiersc on 2007-06-12
Hi Mike

Important Disclaimer:  I do not understand the ins and outs of what I did. I did get it to work eventually, but when I have the time, I will try to understand why it is working.

1. I think the simplest thing to do at first, would be to install the printer directly on your Windows Box. Usually when you buy the printer you get the windows driver with the printer. If the printer can work on your Windows Box, you should be able to print to it when you connect it up to the Linux and print over the network.  (When I got my Windows XP to see the printer on the linux machine, Windows automatically popped up a notice that it could not find the driver on the SMB server and asked me if I had the driver. At that time I inserted the driver CD that came with the printer and a minute later I was able to print.)

2. The more tricky part for me was to set up Samba. I took a few steps. I am not sure if it matters in which order a person does them. 

a) you need to add a user to Samba with the same user name as the user name on the Windows XP box. If I recall, I added this with the following command:

```
# sudo smbpasswd -a user_name
```

(Replace user_name with the user name that you want to use. It should ask for a password and then it will ask you to repeat the password.)

b) Edit the smb.config file

I use: 
```
# sudo gedit /etc/samba/smb.conf 
```
to do that

I found long descriptions on the internet on how to do this. I honestly did not understand them. But here are two references for if you are more computer literate than me:  
[https://answers.launchpad.net/ubuntu/+question/2439](https://answers.launchpad.net/ubuntu/+question/2439)
[http://www.linuxforums.org/servers/howto:_fileserver_with_samba_and_printserver_with_cups.html](http://www.linuxforums.org/servers/howto:_fileserver_with_samba_and_printserver_with_cups.html)

I honestly found the smb.conf file a little bit confusing. It did not resemble the examples that I saw on the internet, so I made a backup copy of the one on my computer and just copied the one that I found in the link above into my original smb.conf file. My smb.conf file now looks like this:
```

[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = cups
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        printing = cups
        print command =
        lpq command = %p
        lprm command =

[printers]
        comment = All Printers
        path = /var/lib/samba
        printer admin = root
        create mask = 0700
        guest ok = Yes
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /etc/samba/drivers
        write list = root
```


Note (again):  I do not have a big need at the moment to use the file sharing functions of samba. I might have broken that. I just needed to get the printer to work. That is why I just deleted everything that was there. If I need to do filesharing later on, I will have to force myself to begin to understand what I did.

Note (beginning of some understanding) - the [print$] section of the smb.conf file seems to provide the path to the folder where you could leave a windows print driver in order for the other computer to pick it up if it needs it. I have not experimented with this. If you have the windows print driver for the particular printer, you might be able to copy it in there and any windows system that then connects to your linux system might be able to find the print drivers that it needs right there. (I'm talking under correction here.)

c). After I set up a user and the smb.conf file I went to my wife's Windows XP computer. I requested it to install a network printer. It would not show the printer when I browsed for it, but i typed in my computer name and my printer (//weiers/LaserJet-1020). It immediately prompted me for a username and a password (which i put in) and then asked me if I had the driver to install.

I know this is very long and wordy. I hope it helps. If somebody who understands what happens here better sees where I've given the wrong directions, please correct me.

Weiers

---

### Post by mdurham on 2007-06-12
> Important Disclaimer:  I do not understand the ins and outs of what I did.

Hi Weiers, Thanks for your very full description of how you got your printer working. I gave me enough confidence that I wasn't wasting my time. I followed some of your instructions and guess what...... It worked!
I guess that my wife, like yours, will be happy that she can print from her own computer and doesn't have to ask me to print for her.
Once again Weiers, thanks for your help.
By the way I find the 1020 a great (and cheap) printer.
Cheers, Mike

---

### Post by Maxtorm on 2007-06-12
Ack!  Followed the instructions to update the firmware on the 1020.  Nothing seemed to happen.  Thought a reboot might do the trick.  No such luck though the printer did cycle during the reboot, which was a first.  I'm thinking the printer cycling is a good sign, but would not appear so.  When I go to add the printer, the USB device doesn't even show up.  "Use a detected printer" used to list the USB device, now there are no devices detected.  In fact, under the port list, USB doesn't show up either.  Anyone have any idea what happened?  And more importantly how to restore the USB port/printer?

---

### Post by mdurham on 2007-06-12
> **Maxtorm said:**
> Ack!  Followed the instructions to update the firmware on the 1020.  Nothing seemed to happen.  Thought a reboot might do the trick.  No such luck though the printer did cycle during the reboot, which was a first.  I'm thinking the printer cycling is a good sign, but would not appear so.  When I go to add the printer, the USB device doesn't even show up.  "Use a detected printer" used to list the USB device, now there are no devices detected.  In fact, under the port list, USB doesn't show up either.  Anyone have any idea what happened?  And more importantly how to restore the USB port/printer?
Just a suggestion Maxtorm, if you are connecting through a hub, Linux doesn't like that. Try a direct connect. Sorry, that's all I can offer.
Cheers, Mike

---

### Post by Maxtorm on 2007-06-12
> **mdurham said:**
> Just a suggestion Maxtorm, if you are connecting through a hub, Linux doesn't like that. Try a direct connect. Sorry, that's all I can offer.

Thanks for the suggestion Mike, but it is indeed directly connected (never been on a hub).  Argh.  Looks like it's time to poke through dmesg etc. to see if it gives any clues.

---

### Post by armaud on 2007-06-21
I have read the instructions and followed them 4 times but each time i have failed. The problem is that when i enter the command 'make' a long list appears and at the end it says one error. Because of this i am not able to follow the next command './getweb 1020'.  I am pasting some of the list that appears when i enter make. I have downloaded the latest foo2zjs file. Please help as i have been trying to run my printer HP 1020 for quite some time now. I am new to Linux so please keep this in mind when explaining what to do.
foo2zjs.c:1513: error: expected ‘;’ before ‘media’
foo2zjs.c:1518: error: ‘struct <anonymous>’ has no member named ‘b’
foo2zjs.c:1519: warning: implicit declaration of function ‘blank_page’
foo2zjs.c:1520: error: ‘struct <anonymous>’ has no member named ‘e’
foo2zjs.c:1522: error: ‘struct <anonymous>’ has no member named ‘b’
foo2zjs.c:1522: error: ‘struct <anonymous>’ has no member named ‘e’
foo2zjs.c:1530: warning: implicit declaration of function ‘load_tray2’
foo2zjs.c:1532: warning: implicit declaration of function ‘fseek’
foo2zjs.c:1532: error: ‘SeekMedia’ undeclared (first use in this function)
foo2zjs.c:1533: error: ‘media’ undeclared (first use in this function)
foo2zjs.c:1534: warning: incompatible implicit declaration of built-in function ‘fwrite’
foo2zjs.c:1540: error: ‘struct <anonymous>’ has no member named ‘b’
foo2zjs.c:1540: error: ‘struct <anonymous>’ has no member named ‘e’
foo2zjs.c:1541: error: ‘struct <anonymous>’ has no member named ‘b’
foo2zjs.c:1542: error: ‘struct <anonymous>’ has no member named ‘e’
foo2zjs.c:1542: error: ‘struct <anonymous>’ has no member named ‘b’
foo2zjs.c:1543: warning: implicit declaration of function ‘getc’
foo2zjs.c:1548: warning: implicit declaration of function ‘end_doc’
foo2zjs.c:1550: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [foo2zjs.o] Error 1

---

### Post by Maxtorm on 2007-07-02
In case any one happens to run into the same problem I did (i.e. firmware appears to update, but then the printer disappears from the list of available printers and USB ports are no longer listed in the New Printer window), I seem to have solved it.  I rebooted with the printer unattached and unpowered.  I then plugged the printer into a different USB port and turned the printer on.  It was then detected correctly and I am able to print to the 1020.

---

### Post by mariuss on 2007-07-07
> In case any one happens to run into the same problem I did (i.e. firmware appears to update, but then the printer disappears from the list of available printers and USB ports are no longer listed in the New Printer window), I seem to have solved it. I rebooted with the printer unattached and unpowered. I then plugged the printer into a different USB port and turned the printer on. It was then detected correctly and I am able to print to the 1020.

Thanks for the tip!

I followed weiersc's instructions, but I replaced 1020 with 1000, since I had to install a LaserJet 1000. At the end I had remove the existing printer, power down the printer remove USB cable, reboot, power printer up, connect USB in a different port and then add printer again.

Why on earth is this process so complicated?

Thanks again,
Marius

---

### Post by idx on 2007-07-07
Pls try [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

---

### Post by mariuss on 2007-07-07
> **idx said:**
> Pls try [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

Thanks for the link.

Unfortunately the two printers mentioned here are not supported:
> **Question: Are drivers available for the Deskjet 710C, 712C, 720C, 722C, 820Cse, 820Cxi, 1000Cse, 1000Cxi; or LaserJet 1000, 1005, 1020, 3100; or Color LaserJet 1500, 2600 printers?**

Answer: These are non-standard host based printers. Currently there are no plans to support these printers in HPLIP. Ghostscript print filters for the Deskjet products can be found at the pnm2ppa project.

---

### Post by dimeotane on 2007-07-19
To get this printer working in feisty I followed the instructions posted here:
[http://benaiah41.wordpress.com/2007/07/06/installing-a-hp-laserjet-1020-on-ubuntu-feisty/](http://benaiah41.wordpress.com/2007/07/06/installing-a-hp-laserjet-1020-on-ubuntu-feisty/)


and I can print in inkscape but not from GIMP

In inkscape the greys appear to very low resolution screen (about 60 lines per inch?)

Anyone have any suggestions?

---

### Post by Maxtorm on 2007-07-19
Not that this helps, but the GIMP issues seems to be a known problem.  See: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020) and scroll down to the Debian 3.1 section.

---


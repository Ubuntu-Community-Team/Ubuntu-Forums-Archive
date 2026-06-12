---
title: "Driver for CanoScan 8800F ??"
date: 2009-05-03
forum: General Help
---

### Post by Soren1972 on 2009-05-03
Hello

I am a very new user of Ubuntu. So far I am very happy, but I am looking for at driver for my Scanner CanoScan 8800F. As far as I know Canon do not support Linux, but I can not be only one with this problem. 

Please help - if possible :-)

---

### Post by jon_gunnar on 2009-05-03
> **Soren1972 said:**
> Hello

I am a very new user of Ubuntu. So far I am very happy, but I am looking for at driver for my Scanner CanoScan 8800F. As far as I know Canon do not support Linux, but I can not be only one with this problem. 

Please help - if possible :-)

I'v given up Canon,but you may have a look at [SANE]("http://www.sane-project.org/") , asfar as I could see it's not supported. But have a look.

---

### Post by scherrey on 2009-09-15
Has anyone had any luck with this scanner? Canon does seem to be a PITA for Linux support but, unfortunately I cannot find another scanner that scans 120 format negatives that doesn't cost an insane amount of money so this is what I'm stuck with. I hate having to boot into Windows or borrow the wife's Mac every time I need to scan film. If nothing else I'd be curious to know what the hangup is with Canon scanners so I'd know how best to follow up.

  many thanx,

 -- Ben Scherrey

---

### Post by lars.ostlund on 2009-11-17
I also have an 8800F. The only solution I saw was to install VMware Player
with XP and scan from there. I also use that solution when printing photo quality pics with my Canon PIXMA iP4200. No more Canon for me.

Lars

---

### Post by maluka on 2010-02-09
Is there a solution to this problem yet?

---

### Post by oshunluvr on 2010-02-09
I have of these for the same reasons you do (cheap but high-res).

I got it working with vuescan but not very well so I just relented to using it via a virtualbox XP install and moved the scans to my linux box via a networked folder. 

Kind of a long process but it was better than dual booting or losing some of the features. 

Currently - I am using a new install (because of a hd failure) and the scanner is at my Mom's house because I talked her into scanning the family slides in her spare time!

So I can't relate any settings from my old setup - sorry.

---

### Post by Tourdog on 2010-02-09
Same sad story with my "CanoScan 5000F" .  I tried Xsane but no solution.  Telephone call got zero satisfaction.   Money wise their scanners are excellent values I think, but if they won't support Linux ................  XP takes forever to bootup.  
Our new CanoScan 8800F needs a 'yet to be written' driver even for Win7 (full features) ! 

 "Not a happy camper here."

---

### Post by asavik on 2010-04-04
I've been looking for it a while myself, though it works nicely through Virtualbox.

Recently (March 2010) I came across a thread in the sane development mailing list, [http://lists.alioth.debian.org/pipermail/sane-devel/2010-March/026319.html](http://lists.alioth.debian.org/pipermail/sane-devel/2010-March/026319.html)

> Hehe, no, because in the last few weeks I got this scanner supported fully at all resolutions, with help from Allan and Nicolas and Milan (another 8800F owner). Works for all resolutions up to 4800 both paper and film negatives ( haven't tried positives yet ). Only problems remaining are:
1) 4800x9600 mode
2) misalignment for negatives/positives in y-direction (need to
specify some offset for scan to select same area as in preview
window).

So my question was in order to find out if any of the other Canon
scanners also work using the pixma protocol, which as you say, is
fairly easy to use.

Regards,
Gernot

I haven't been able to find any more info, though.

---

### Post by Shutter4U on 2010-04-24
There is a fix!!! :guitar:

As of about 2 weeks ago, support for this scanner was added to the sane-backends in the git repository.

To get this working, here are the steps to take:

1) You need some usb libraries, so, in a terminal type:

**sudo apt-get install libusb-dev build-essential**

2) To get the sane backends from git you need git-core. If you don't already have it, type this (also in a terminal):

**sudo apt-get install git-core**

3) Now use the git that was just installed to get the sane backends using the following command:

**git clone git://git.debian.org/sane/sane-backends.git**

That downloads the backends and puts them in a folder called sane-backends in your home folder.

4) Change directory into the new sane-backends folder and compile them:

**cd sane-backends**

**./configure &#8211;prefix=/usr &#8211;sysconfdir=/etc &#8211;localstatedir=/var**

**make** <--- this one takes a while

**sudo make install**

Now everything is installed, but you still won't be able to scan (except as root) until you set up some permissions. 

5) You need to edit a file, but you need to be root to edit it, so:

**sudo gedit /lib/udev/rules.d/40-libsane.rules** 

and add the following 2 lines:

[B]# Canon CanoScan 8800F
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1901", ENV{libsane_matched}="yes"[/B]

save the file, exit gedit, exit terminal, reboot, and...

SCAN AWAY! 
:):):):):)

---

### Post by rylleman on 2010-05-07
This is interesting news!
I'm currently needing a new scanner and the 8800F seemed great but my hopes was low until I found this thread.
So, should I dare to buy the 8800F and hope that this new sane-fix will work well?

---

### Post by f6eea on 2010-05-08
It works! :p:p:p
Xsane sees and uses my Canoscan 8800F, now.

I just had to change 
[B]./configure –prefix=/usr –sysconfdir=/etc –localstatedir=/var
[/B]in
[B]./configure prefix=/usr sysconfdir=/etc localstatedir=/var
[/B]
(My OS is Lucid Lynx)

Many thanks
JeanYves

---

### Post by Captain Giraffe on 2010-05-08
Great news. 
@rylleman It works perfectly for me.
I also needed to change the ./configure as f6eea suggested.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156040&d=1273333800[/IMG]
Many thanks.

---

### Post by dangmc on 2010-05-09
rylleman:

        by all means get the 8800f Canon. I just finished my first 'canoscan' in Ubuntu! (lucid lynx x64) Just finished installing 'sane-backports' and now scanning with 'xsane'. Simple scan also works. Now if only somebody could port drivers for my Pro9000 printer! Good job Shutter4U!

---

### Post by rylleman on 2010-05-10
> **dangmc said:**
> rylleman:
        by all means get the 8800f Canon....
Alright thanks! I'll hold you responsible if it doesn't turn out working... ;)

So how is the color reproduction with sane? I'm considering this scanner because color accuracy is said to be very good. Would this be the same with sane as under windows with native drivers?

---

### Post by rylleman on 2010-05-12
Ok, went and bough the 8800F and got it working in Ubuntu 8.10.

As others had to remove the "-"s from the line
**./configure –prefix=/usr –sysconfdir=/etc –localstatedir=/var**

Also in 8.10 **/udev/rules.d/** is not in /lib but in **/etc** so;
**sudo gedit /etc/udev/rules.d/40-libsane.rules **
40-libsane.rules didn't exist in rules.d so I had to add it with the two lines from the guide in it.

---

### Post by steeneveld on 2010-05-17
I have the same user permission problem as others as I have one of the earlier ubuntu distros which do not have any entry of **40-libsane.rules**. It is not in **/udev/rules.d/** or in [B]/etc/udev/rules.d/40-libsane.rules.

[/B]The easy fix is to alter 40-basic-permissions.rules  from
 
USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",        MODE="0664"

to
 USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device",        MODE="0666"

and restart which allows all users access.

---

### Post by revidnus on 2010-05-17
Thanks!  I have a canonscan 8800F and scan slides with it. THIS FIX WORKS GREAT! This fixed my problem. I wasn't having any luck with virtual box.

NOTE: I did have to take out the dash's in this line

(example) ./configure prefix=/usr sysconfdir=/etc localstatedir=/var

---

### Post by adatol on 2010-05-19
I feel like I'm about an inch away from having this solved.

I'm running Lucid (64-bit). The install ran fine, no errors. 

"scanimage -L" returns:

device `pixma:04A91901' is a CANON Canoscan 8800F multi-function peripheral

"scanimage -T -d " returns:

scanimage: open of device pixma:04A91901 failed: Device busy

**UPDATE: (blush) if you leave XSANE open on another workspace, the device is going to be busy. However, re-running it still fails with:

scanimage -T -d pixma:04A91901
   scanimage: scanning image of size 638x877 pixels at 24 bits/pixel
   scanimage: acquiring RGB frame, 8 bits/sample
   scanimage: reading one scanline, 1914 bytes...	FAIL Error: Operation was cancelled

This is the case whether I run as myself or SUDO. 

Any advice would be appreciated!

---

### Post by watchpocket on 2010-05-23
> **revidnus said:**
> NOTE: I did have to take out the dash's in this line

(example) ./configure prefix=/usr sysconfdir=/etc localstatedir=/var


I copy-&-pasted the line, which caused the hyphens to change into wider dashes.

I replaced the wide dashes with actual hyphens (rather than remove them, which is what everyone so far in this thread has done) and all was well.

---

### Post by jiex on 2010-05-27
Hi there folks - 
I too have a Canon 8800F and need it to work in Lucid (I'm new to ubuntu so please be patient with me!)
Could someone post the instructions in a blow by blow sequence? I'm flummoxed by some of the directions in the earlier posts. 
In anticipation, many thanks

---

### Post by lemort on 2010-05-28
jiex, 

First, please read and do like instructed on this thread in post #9, by Shutter4U.

After reboot type:
scanimage image.pnm

This should scan your image to your home folder. But if this gives you some access to source denied error, type:
sudo gedit /lib/udev/rules.d/50-udev-default.rules

And find the following:
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"

and replace it with:
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"

Reboot.


P.S. See also [http://www.sane-project.org/man/scanimage.1.html](http://www.sane-project.org/man/scanimage.1.html)


Cheers,
~lemort

---

### Post by cj_nza on 2010-05-28
I read and did like instructed on this thread in post #9, by Shutter4U.

I am now able to use the scanner for flatbed scanning.

When trying to use the transparency adapter to scan negatives and 35mm slides, no joy.

Any suggestions ??

---

### Post by Captain Giraffe on 2010-05-29
@dangmc:  Most likely this is still an open issue.

---

### Post by acreech on 2010-06-07
> **cj_nza said:**
> I read and did like instructed on this thread in post #9, by Shutter4U.

I am now able to use the scanner for flatbed scanning.

When trying to use the transparency adapter to scan negatives and 35mm slides, no joy.

Any suggestions ??

I am looking at purchasing this scanner for the purpose of scanning negatives and slides. Xsane shows that this has complete support. I was considering using gimp and Xsane to run the scanner. 

Can someone with this scanner give some feed back on how well it functions when scanning negatives in? Is there another option for a flatbed scanner that also scans negatives and slides?


thanks for the suggestions.


acreech

---

### Post by mtopro on 2010-06-12
Sweet!  Been waiting a long time for this!  Works great guys.  Followed the steps provided by Shutter4U and just had to change the long dashes to normal hyphens.

I also added the permission change as suggested by lemort above changing "664" to "666" just for the heck of it.

Canoscan 8800F works awesome in Ubuntu!  Thank you to everyone for your hard work.

---

### Post by MrKimi on 2010-06-14
> **Shutter4U said:**
> There is a fix!!! :guitar:

As of about 2 weeks ago, support for this scanner was added to the sane-backends in the git repository.

To get this working, here are the steps to take:

1) You need some usb libraries, so, in a terminal type:

**sudo apt-get install libusb-dev build-essential**

2) To get the sane backends from git you need git-core. If you don't already have it, type this (also in a terminal):

**sudo apt-get install git-core**

3) Now use the git that was just installed to get the sane backends using the following command:

**git clone git://git.debian.org/sane/sane-backends.git**

That downloads the backends and puts them in a folder called sane-backends in your home folder.

4) Change directory into the new sane-backends folder and compile them:

**cd sane-backends**

**./configure –prefix=/usr –sysconfdir=/etc –localstatedir=/var**

**make** <--- this one takes a while

**sudo make install**

Now everything is installed, but you still won't be able to scan (except as root) until you set up some permissions. 

5) You need to edit a file, but you need to be root to edit it, so:

**sudo gedit /lib/udev/rules.d/40-libsane.rules** 

and add the following 2 lines:

[B]# Canon CanoScan 8800F
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1901", ENV{libsane_matched}="yes"[/B]

save the file, exit gedit, exit terminal, reboot, and...

SCAN AWAY! 
:):):):):)

I am keen to use this but I hit a problem:
> 
roger@ambrose9400:~/sane-backends$ ./configure –prefix=/usr –sysconfdir=/etc –localstatedir=/var
configure: error: invalid variable name: –prefix
This is on Ubuntu 10.04 on i386 (specifically a Dell Inspiron 9400, though I doubt this matters)
Everything seemed happy up to this point in your instructions.
Thanks

---

### Post by MrKimi on 2010-06-14
Okay, I see what you mean by long dashes now. Just in case others get as easily confused as I do you need to delete the '-' in the command and replace with your own '-' for each instance. Your dash will look shorter than the one you pasted into the command line. This is good.

---

### Post by Shutter4U on 2010-06-20
For scanning negatives, I've found it does work, just not like other programs on win/mac. 

In the xsane dialog box - the one with most of the settings on it, you select "film negative" from one of the pull down menus...

When you select "preview", it scans the whole flatbed and you see your negative strip.

You will likely need to zoom in to select the frame you want to scan.

I suppose you could select the whole strip and scan them into one big image file and then sort it out in gimp later... I haven't tried that (I'm posting this from work, so I can't try it yet).

Another note, even though the film I was scanning was Kodak, selecting "Kodak negative" had really poor results (really washed out images). Selecting "standard negative" had much better results.:lolflag:

---

### Post by mdc001 on 2010-07-22
WOW... a big thank you for these clear, concise set of instructions.
SCAN away indeed!.
Running Ubuntu 10.04 and my 8800F works great.  One less reason to go to VirtualBox/XP.

Thanks a bunch.
Marc

> **Shutter4U said:**
> There is a fix!!! :guitar:

As of about 2 weeks ago, support for this scanner was added to the sane-backends in the git repository.

To get this working, here are the steps to take:

1) You need some usb libraries, so, in a terminal type:

**sudo apt-get install libusb-dev build-essential**

2) To get the sane backends from git you need git-core. If you don't already have it, type this (also in a terminal):

**sudo apt-get install git-core**

3) Now use the git that was just installed to get the sane backends using the following command:

**git clone git://git.debian.org/sane/sane-backends.git**

That downloads the backends and puts them in a folder called sane-backends in your home folder.

4) Change directory into the new sane-backends folder and compile them:

**cd sane-backends**

**./configure –prefix=/usr –sysconfdir=/etc –localstatedir=/var**

**make** <--- this one takes a while

**sudo make install**

Now everything is installed, but you still won't be able to scan (except as root) until you set up some permissions. 

5) You need to edit a file, but you need to be root to edit it, so:

**sudo gedit /lib/udev/rules.d/40-libsane.rules** 

and add the following 2 lines:

[B]# Canon CanoScan 8800F
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1901", ENV{libsane_matched}="yes"[/B]

save the file, exit gedit, exit terminal, reboot, and...

SCAN AWAY! 
:):):):):)

---

### Post by mbott on 2010-07-30
Works great in 9.10 also.  Thanks!:D:D:D

-- 
Mike

---

### Post by AlP36 on 2010-08-08
Hey - This is great to hear.
Now - Has anyone tried to get a Canoscan 8400F to work with this driver? Or do I have to try it out myself? I sure hate to spend another $200+ for a negative/slide scanner and even HP's G4050 is not supported. I am using 9.10. 

Even though I like the Canon scanner I have sworn to never buy another of their products until they give us some support.

---

### Post by joostvdw on 2010-08-21
Hello evryone,

thanks a lot : since i switched definitive from windows to ubuntu, my canoscan 8800F was workless. I was trying to sell it by secondhand without results, but now can use it again !!

the support is, as far as i can mention - 100% . tested evrything, except negative scanning.

Joost van der wulp from belgium

---

### Post by dangmc on 2010-10-10
> **joostvdw said:**
> Hello evryone,

thanks a lot : since i switched definitive from windows to ubuntu, my canoscan 8800F was workless. I was trying to sell it by secondhand without results, but now can use it again !!

the support is, as far as i can mention - 100% . tested evrything, except negative scanning.

Joost van der wulp from belgium

To everybody in this thread-my 8800f Canonscan worked fine with 'Maverick' 10.10rc.
Update-I just installed ubuntu 10.10_
amdx64-simplescan & xsane both work fine without any adjustments. I tried the hack with Lucid  and ran into problems

---

### Post by dangmc on 2010-10-20
Update-I'm having a real problem with Xsane; after trying to adjust the settings the program quit working. I've reinstalled everything having to do with scanning with no luck. Simple scan works fine. When program loads part of it fades off to the left of my screen. I was, however able to get things going running from terminal. ( xsane -dbg

(xsane:2055): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/dangmc/.recently-used.xbel', but the parser failed: Error reading file '/home/dangmc/.recently-used.xbel': Is a directory.) This message was the result when I closed it. Any Ideas? Thank you.
I'm now using Ubuntu 10.10_amd_X64 due to having this same issue in Lucid.

---

### Post by dangmc on 2010-10-21
bump-


I filed a bug report #664912

---

### Post by dangmc on 2010-10-25
Bump

---

### Post by Anjalis on 2010-10-31
I followed the instructions and it all went well so far. When I restarted my computer I tried to start "Xsane Image Scanning Program" but it didn't work
I got this message:
Couldn't open unit pixma:04A91901 Access to resors is denied (or something like that. I translated it from swedish).
What to do?

---

### Post by Shutter4U on 2010-11-10
> **Anjalis said:**
> I followed the instructions and it all went well so far. When I restarted my computer I tried to start "Xsane Image Scanning Program" but it didn't work
I got this message:
Couldn't open unit pixma:04A91901 Access to resors is denied (or something like that. I translated it from swedish).
What to do?

Well, I know that some people using Ubuntu versions other than Lucid Lynx reported that the file they needed to edit in step 5 of my post was actually located in a subdirectory of /etc instead of /lib - I haven't tried scanning in Maverick Meerkat yet, so I don't know if it has changed locations again. From your error message it seems like the problem has to do with setting or changing permissions somewhere.

from my original post (#9 in this thread):

5) You need to edit a file, but you need to be root to edit it, so:

**sudo gedit /lib/udev/rules.d/40-libsane.rules** 

and add the following 2 lines:

[B]# Canon CanoScan 8800F
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1901", ENV{libsane_matched}="yes"[/B]

You may need to do **sudo gedit /etc/udev/rules.d/40-libsane.rules** and add the 2 lines mentioned above. Or you might need to do what steeneveld posted in post #16.

---

### Post by dangmc on 2010-11-13
> **dangmc said:**
> Bump

Just want to let everybody know I finally found a fix-removed .sane directory @home-then reinstalled everything having to do with 'sane'/'xsane'. Xsane now works properly; however I still don't understand what went wrong.

---

### Post by skippylou on 2010-11-26
Using ubuntu 10.10

Followed steps in post #9.  Lots of warnings in the compilation but no errors reported.

xsane reports no devices available.

Using a rather old motherboard, if that matters.  Asus P4SGX-MX.

Scanner works fine with XP.

Any suggestions?

---

### Post by cruzalong on 2010-12-04
> **Shutter4U said:**
> 5) You need to edit a file, but you need to be root to edit it, so:

**sudo gedit /lib/udev/rules.d/40-libsane.rules** 

and add the following 2 lines:

[B]# Canon CanoScan 8800F
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1901", ENV{libsane_matched}="yes"[/B]

save the file, exit gedit, exit terminal, reboot, and...

You could replace step five with the following command to automatically generate a new 40-libsane.rules file for you:

```
sudo sh -c 'if [ ! -f /lib/udev/rules.d/40-libsane.rules.bak ]; then cp -a /lib/udev/rules.d/40-libsane.rules /lib/udev/rules.d/40-libsane.rules.bak; fi; tools/sane-desc -s doc/descriptions -m udev > /lib/udev/rules.d/40-libsane.rules'
```

---

### Post by teamsuperoxide on 2010-12-12
Thank you very much for the instructions! My scanner is up and running!

---

### Post by lab3745 on 2010-12-28
The instructions provided by [oshunluvr]("http://ubuntuforums.org/member.php?u=927765") worked perfectly.  

I didn't purchase this scanner until I had identified it as supported in the SANE supported products database: [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)  I was a little disappointed when it did not work on Ubuntu out of the box. (So much does!).  Follow these instructions to the letter however, and you will be good to go.  :D

---

### Post by kumarN00 on 2011-01-06
Hi - I am new user to Ubuntu and using 8800F. Thanks for your posts (Shutter4U Post# 9, steeneveld Post# 16)I could get my scanner to work. 
Only point I would like to make is to remove the # mark in step 5.
change "# Canon CanoScan 8800F" to "Canon CanoScan 8800F".

Best regards,
Kumar.

---

### Post by MrPahn on 2011-02-07
Hi!
I could really need som help with getting my scanner (CanoScan 8800F) to work.

At the moment I'm using Linux Mint 10.10, but I hade the same problem with Ubuntu 10.10.

I got the scanner working the last time I used Linux, but now I'm stuck.


I've tried everything in this and many other threads, bot no luck. The computer finds the scanner and all, but if I run for example Xsane and try to scan, I get "Error during device I/O" message, and then I have to restart the computer, it kind of locks, sometimes it freezes totally.

If I run scanimage in terminal I get:

```
sudo scanimage --test
[sudo] password for mrpahn: 
scanimage: scanning image of size 638x877 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 1914 bytes...    FAIL Error: Error during device I/O
```scanimage -L:

```
scanimage -L
device `v4l:/dev/video0' is a Noname Microsoft® LifeCam Cinema(TM) virtual device
device `pixma:04A91901' is a CANON Canoscan 8800F multi-function peripheral
```lsusb:

```
lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 056a:00b0 Wacom Co., Ltd Intuos3 4x5
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04a9:1901 Canon, Inc. CanoScan 8800F
Bus 002 Device 002: ID 07d1:3c0a D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT2870]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 045e:075d Microsoft Corp. LifeCam Cinema
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
I've tried to uninstall everything with sane/xsane and reinstalled, but ended up with the same result.
I must have missed something but I can't figure out what it is.

Any suggestions?

---

### Post by MrPahn on 2011-02-07
I got it working!
It's kinda wierd.... I changed the scanner to a different USB-port, and it worked at once.
At first I had it connected to a PCI USB-card, and now I moved it to a port directly on the motherboard.
Should that make a difference?
It must be something with the drivers or permissions to the card then?

Oh well, at least i works! I'm happy again. :razz:

---

### Post by deano.florida on 2011-04-11
I got my 8800f working by following the directions above. Thanks to those who posted them. But I am having  a big problem with scanning negatives. Using "preview" in xsane I can get the color balance looking fairly well tweaking the sliders but when I scan the negative the color balance is very far off (way way way too RED). 

If I experiment by reducing the red component (the preview image gets very blue) the trial scans gets better but wow, tweaking color without being able to rely on the preview image !!! I'll be all day scanning one frame. I'm hoping there is some simple switch setting or other fix for this that I just don't know about. Otherwise it's a show stopper. Anyone got a suggestion?

---

### Post by TrombaMarina on 2011-07-19
I just got mine to work by typing:

sudo apt-get install sane

That was it.  A year ago, I had to compile code.  Now it's a simple install.  Nice!

---

### Post by dangmc on 2011-07-26
> **TrombaMarina said:**
> I just got mine to work by typing:

sudo apt-get install sane

That was it.  A year ago, I had to compile code.  Now it's a simple install.  Nice!

Just want to mention that with 11.04_x64 my Canoscan 8800f just works without any issues. (Simple Scan) I then installed Xsane and it now works without any hacks necessary. I also went through all the frustration having purchased my scanner over 2 years ago. Now---any suggestions for my Canon Pro9000 printer? (not Turboprint)

---

### Post by iheartubuntu on 2011-10-06
Unable to get my 8600F working. I followed all directions without any errors, replacing the last part with:

# Canon CanoScan
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2229", ENV{libsane_matched}="yes"

as it pertains to my particular scanner and should work, but does not.

"sane-find-scanner" gives me this output:

found USB scanner (vendor=0x04a9 [Canon], product=0x2229 [CanoScan], chip=GL845) at libusb:001:007

running "scanimage -L" gives me:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

### Post by rulorojo on 2011-10-18
ATTRS{idProduct}=="2229"  , other post used id nr 1901


but as a matter of fact, the best scanning software is Vuescan, to be found at [www.hamrick.com](www.hamrick.com)

---


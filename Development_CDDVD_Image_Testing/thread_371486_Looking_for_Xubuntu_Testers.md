---
title: "Looking for Xubuntu Testers"
date: 2007-02-27
forum: Development CD/DVD Image Testing
---

### Post by j1mc on 2007-02-27
Hello All,

We're trying to get more testers for Xubuntu in the run-up to the release of Feisty Fawn, so if you have a spare hard drive (or can spare a few partitions on a current hard drive), please consider putting Xubuntu through it's paces.  :)  

We've done quite a bit to revamp the Xubuntu Testing portion of the ubuntu wiki, so please take a look.  You can find out more info, and [get started here]("https://wiki.ubuntu.com/Xubuntu/Testing").   Thanks very much for your help!

Jim

---

### Post by Juzz on 2007-02-27
I'll give it a go ;)

---

### Post by Juzz on 2007-02-27
The amd64 image boots up AND I can use "Network Settings" to get my wireless config up and running :)
I am typing this from the first image boot up - this looks very interesting.

In the normal Ubuntu I couldn't use any graphical tool to get the wireless connection going, so that's a good thing it works in Xubuntu (and that the amd64 image boots up entirely).

EDIT:
When entering step 7 of the install (and after having chosen Danish as language), the sub title and two of the buttons are still in english - sub title is "Ready to install" and one button shows "Advanced..." the last button shows "Install" - these minor things should perhaps be translated as well now that most of the other things have been translated.

---

### Post by johnnymac on 2007-03-06
I'm running it now.  For the most part it's quite stable (Herd5), I haven't had any hiccups yet.

I'm still monkeying with it but I've got my development environment running, vpn'ing into work, and jackin' around with the composite settings (WHICH I LOVE!)

J-mac

---

### Post by dermotti on 2007-03-07
I'll give it a shot.

---

### Post by Henrik on 2007-03-07
I'd like to add my support to this call. For Beta and onwards we will involve the whole distro team in active testing of ISOs. Unfortunately we will not be dedicating core developers to Xubuntu testing, so the community contribution is really important here.

j1mc, will you be coordinating the Xubuntu testing effort? Please email me at henrik AT ubuntu DOT com so we can get all the ducks lined up.

---

### Post by Trespasser on 2007-03-07
I tried Xubuntu Herd 5 three days ago. Pretty nice. Installed good. Ran fine. It's a bit spartan looking at first glance but I soon learned how to deal with it. Nice job.

---

### Post by jerrylamos on 2007-03-08
Last time I tried Xubuntu I couldn't find an equivalent to Places, Network Servers which is similar to Windows Network Neigborhood.  There are 5 systems on our local LAN, which are powered down when not in use, and come up with different addresses every time (same name, tho).

If there's a way to do Network Neighborhood on Xubuntu I can give it a try on some of our systems.  Anyone have a clue?

Thanks, Jerry

---

### Post by johnnymac on 2007-03-08
So I'm not much for the graphical tools - I usually have scripts and my own python, perl/zenity utilities I use for such things.  I'm a HUGE Xubuntu fan due to the resources consumed so it's a perfect tool for server deployment and development boxes.

BTW, I'm still running Herd5 and no problems...

---

### Post by Alex6969 on 2007-03-08
I'm in

---

### Post by jerrylamos on 2007-03-10
I went searching for Xubuntu CD Live Feisty Herd 5 cdimage and couldn't find it - anyone have a pointer to how to get it?

Thanks, Jerry

---

### Post by bernied on 2007-03-10
Is [this](https://wiki.ubuntu.com/Xubuntu/Testing/TestingInfo) it?

---

### Post by jerrylamos on 2007-03-10
Yep, that was it.  It uses the same cdimage name as Ubuntu which confused me.  The big clue was size at 553MB, compared to Ubuntu at 703MB (Oversize, won't fit on a CD).  I'm downloading now.  

Thanks, Jerry

---

### Post by Agafonov on 2007-03-13
I can't burn current (oversized) iso to test xubuntu. Am I forced to use Herd-5? :confused:

---

### Post by erothoff on 2007-03-13
I will try again testing Xubuntu, and I really like it, and actually on those computers that must run windows, I have installed alot of Xubuntu's programs on it. Abiword, Gnumeric, etc.

  One problem though, can we have an easy place or directions to find the ISO's to test? I had set up on my computer to rsync the nightly builds, but I had to change computers, and need to redo everything. And I never have found the herd* builds, only the nightly builds.

  I now that the suggestions are closed for "improvements" for fiesty, so I would like to know when suggestions can be made for the net version...
Thanks.

---

### Post by jerrylamos on 2007-03-13
As far as I can tell, the "Herd" designations are called at some point in time, and the "daily build" at about that time or a day or two later are what they are referring to as Herd 5, Herd 4, etc.  I haven't found a way to tell if the daily-builds are large or small changes other than doing an rsync and seeing how much data is transferred.

What works for me is:

rsync --avzpPv --stats rsync://cdimage.ubuntu.com/cdimage/xubuntu/daily-live/current/feisty-desktop-i386.iso .

all that stuff from the "rsync" to the " ." (note the blank before the .) is on one line.

Replace xubuntu with kubuntu or ubuntu as desired, the different iso's all have the same filename.

Note for me, both instances of the word "cdimage" are required.

I make an exec that rsync's the .iso, rsync's the MD5SUMS, and md5sum's the local .iso.  And yes, U, K, and X are in different directories or I'd be lost altogether.

And yes I had to poke around a while to find the URL's, and sometimes they change the URL's on me.

Note if the word OVERSIZE appears, the .iso won't fit on a CD.  That's been Ubuntu lately.  I've heard Gnome has a change in the works but I don't know if this is related to the OVERSIZE.

Cheers, Jerry

---

### Post by j1mc on 2007-03-14
> **Henrik said:**
> I'd like to add my support to this call. For Beta and onwards we will involve the whole distro team in active testing of ISOs. Unfortunately we will not be dedicating core developers to Xubuntu testing, so the community contribution is really important here.

j1mc, will you be coordinating the Xubuntu testing effort? Please email me at henrik AT ubuntu DOT com so we can get all the ducks lined up.

Henrik, I am heading up the Xubuntu testing efforts.  I'll drop you a line.

---

### Post by j1mc on 2007-03-14
Sorry for not responding to more of these responses sooner, but I really appreciate everyone's willingness to help test Xubuntu.

If you aren't subscribed to either the Xubuntu Developer or Xubuntu User mailing list, I encourage you to do so, but [here is a brief update]("https://lists.ubuntu.com/archives/xubuntu-devel/2007-March/003284.html") about Xubuntu testing that I sent out to the mailing lists this evening.

I've subscribed to this thread now so I should be able to keep better tabs on responses.

I also encourage anyone who's interested in testing any of the *ubuntu flavors to read Henrik's postings in this part of the forums.  He's leading these things up quite nicely.  :-)

---

### Post by pochu on 2007-03-14
[Henrik's post]("http://ubuntuforums.org/showthread.php?t=383067") ;)

---

### Post by diskotek on 2007-03-14
i can not download cd images; due to my connection :(

---

### Post by kvonb on 2007-03-14
Could someone PLEASE seed the bloody thing!  We can't test if we can't get it!

---

### Post by j1mc on 2007-03-14
> **kvonb said:**
> Could someone PLEASE seed the bloody thing!  We can't test if we can't get it!

kvonb, are you trying to get the nightly image via bittorrent?

---

### Post by kvonb on 2007-03-15
> **j1mc said:**
> kvonb, are you trying to get the nightly image via bittorrent?

Yup, looks like I was :rolleyes:.

Man, I got 70% of the bugger too!

---

### Post by j1mc on 2007-03-15
> **kvonb said:**
> Yup, looks like I was :rolleyes:.

Man, I got 70% of the bugger too!

kvonb, i'm afraid i can't promise much in the way of seeding the bittorrent.  have you looked into using jigdo or rsync to keep your nightly image current?

---

### Post by jftuga on 2007-03-17
Hi all!  Is it too late to start helping out with the testing of the Feisty Fawn version of Xubuntu?  If not, I would like to voulunteer.  I have 2 machines that I can test on.  If it is not too late, how can I get the latest version of the ISO and how can I report bugs?  Also, are any parts that need to be tested more than others?  What specifically needs the most testing?

Thanks,
-John

---

### Post by jmc1024 on 2007-03-17
I tried to boot the feisty-desktop-i386.iso (build 2070301).  It fails on three machines with: 
     Loading isolinux: Disk error 32, AX = 4200, drive 9F

I'm probably shouldn't be trying it out as I don't know how to proceed from here, but I _really_ want to upgrade all my machines to Xubuntu 7.0 when it's ready.  I figured testing the prerelease versions was the best way to be sure it'll work for me.
Mark

---

### Post by j1mc on 2007-03-17
> **jftuga said:**
> Hi all!  Is it too late to start helping out with the testing of the Feisty Fawn version of Xubuntu?  If not, I would like to voulunteer.  I have 2 machines that I can test on.  If it is not too late, how can I get the latest version of the ISO and how can I report bugs?  Also, are any parts that need to be tested more than others?  What specifically needs the most testing?

Thanks,
-John

Hi John,

No, it is not too late to help out with testing Xubuntu Feisty Fawn.  In fact, you're coming along at just the right time.

[Here]("https://lists.ubuntu.com/archives/xubuntu-devel/2007-March/003284.html") is an email sent out to the Xubuntu developer and user mailing lists.  It should help get you started.  Thanks for offering your help!!

---

### Post by j1mc on 2007-03-17
> **jmc1024 said:**
> I tried to boot the feisty-desktop-i386.iso (build 2070301).  It fails on three machines with: 
     Loading isolinux: Disk error 32, AX = 4200, drive 9F

I'm probably shouldn't be trying it out as I don't know how to proceed from here, but I _really_ want to upgrade all my machines to Xubuntu 7.0 when it's ready.  I figured testing the prerelease versions was the best way to be sure it'll work for me.
Mark

Hi Mark,

If you wish to test Xubuntu, please make sure that you are using the most recent nightly release.  The Ubuntu developer team fixes bugs every day, so an ISO from March 1st will probably have some bugs in it that have been fixed by March 17th.  

Please see[ this listserve message]("https://lists.ubuntu.com/archives/xubuntu-devel/2007-March/003284.html") concerning our most recent testing procedures.  

And thank you for volunteering to test!  :-)

---

### Post by netboy541 on 2007-03-18
If I can get my hands on it... I have 9 IBM dual p3 eServers that are in a 8 foot rack that I will run the development version on at least two....

I'm in the process of building up the rack with the file server and whatnot, and some of the IBMs won't be working... so this is a good thing to make them do!

---

### Post by TuxCrafter on 2007-03-21
I finished my test report, here it is.

is this the correct place too post it?

Xubuntu Feisty Herd 5 Test Report
20-03-2007
version 1.0
Jelle de Jong
jelledejong@powercraft

This is my test report for the Herd 5 version of Xubuntu 7.04 Feisty release.

I have done some testing for this release with the following hardware set-up:

Motherboard:
- VIA Epia Mini-ITX EN12000E
Hard disk: 
- Samsung HM080HI - 80 GB - 12ms 8mb 5400rpm - Serial ATA 150 - SpinPoint M80S
Memory:
- Kingston Dimm 1Gb DDR2 PC2-4200 533Mhz
BIOS setting:
- Default optimized settings

I am only going to point out the problems that I encountered while testing. I am not
going to discuss all the good points, because this will take to long. So please
don't put me in a box of being a freaked complainer :-D

1: The dependencies of the Gaim Internet Messenger package are weird. Gaim is
installed standard on Xubuntu and should not depend on GNOME package dependencies.
But when I enter the following command: sudo apt-get install gaim it wants to
install all kinds of GNOME packages.

2: The Time and Date configuration tool (time-admin) is working strange. If you
select a different date or time and press the synchronize button there is no process indicator?. 
This is very confusing, sometimes it works and sometimes it doesn't. 
Also the help button doesn't do anything.

3: The xsrceensaver has 3D rendering themes enabled by default. This is not very
handy. I don't have 3D rendering support installed by default. When manually
compiled and installed 3D rendering will eat up all my cpu power, and power consumption will be higher. 
I also had an AMD Geode with SiS741CX chip for testing. 
This motherboard will even crash when trying to attempt 3D rendering. So the xscreensaver will crash 
that motherboard. Also control + alt + delete will enable the xscreensaver screen
lock function, this works but I think the looks are very ugly. People around me
don't like it either. So the appearance can be improved drastically.

4: When I install DVD playback support I need CSS to decode encrypted DVD's.
Normally there is a script called “install-css.sh”,  that installs some *.deb package files from the internet. 
But this script is nowhere to be found in feisty. I had to download this package manually. 
I am talking about the libdvdcss package and the /usr/share/doc/libdvdread3/install-css script.

5: The new thunar volume management system is not fitting to my needs! They said
this feature could be disabled easy. But I can't find a working option to get the
old behavior back. When I plug in a normal USB 2.0 1GB usbstick. Thunar says I have
plugged in a USB 2.0 Music Player. This is absurd and very annoying and confusing.
Make it possible to get the old system back so I can make a usbdisk mount automatic
to /media/usbdisk and when I plug in a usbstick it will mount automatic to
/media/usbstick

6: I wanted to download the daily ISO and burn it to a CD, but the ISO was more than
700MB and it will not fit on a normal CD. This probably is caused by the rsync
system that makes an image bigger when changes are added. The ISO was 712MB, please keep it under 700MB.

7: When pressing control + alt + backspace the gdm-greeter will not be shown again
after the x session is terminated. Checking with the top command it will have 100%
CPU load on the gdm package. I have to do sudo pkill gdm and startx to get x up
again.

8: Please don't use The GIMP as the default image viewer but use GQview instead. I
don't like loading The GIMP by default when I only want to watch a *.jpg image.

9: xfce4mixer will not update/synchronize with ALSA when the combo boxes in the
switches section are changed. You can test this when running alsamixer and
xfce4mixer at the same time and compare their settings.

10: System beeps sounds from openoffice.org are played over the motherboard speaker
and the normal speaker. This happens for example when trying to close an unsaved
document. Please only use the normal sound speakers so that people next to me are not annoyed.

11: I think the two new options in the title bar of windows for sticking and
shading are creating too many options and are confusing for normal users. I know people
that still have trouble with maximizing and minimizing. Also where can these new
window options be enabled or disabled?

12: There is a problem with the task list space system. Every button in the task
list seems to have an almost fixed size. When you have an item in the task list with
only a few letters, there will be a big, empty and ugly space before it. Please only set a
maximum size and let the minimum size of a button be determent by the number of
characters used in the task list label.

13: The visual appearance of the Xubuntu gdm-greeters are not my style, I think 
it's ugly. The boot-up flash screen is a lot better, but I would like more symmetry
in it. (just a comment)

14: The tool that previous was called Add and Remove is now called package manager
and there is also the Synaptic package manager. Those two different programs also
have the same icons. I think this is very confusing.

15: The icons in the list on the left side of the package manager tool (add and
remove) are all the same. So the games, office, internet etcetera have the same
icons. I don't believe this will look very appealing.

16: Shutdown and restart won't work in a normal gdm-greeter started x session. 
Instead it will return to the gdm-greeter screen. it will not power off or reboot.


17: When shutting down by clicking on the shutdown button in gdm-greeter or with the
sudo shutdown -h now command, can both result in a system displaying that the system
is halted. But then the system is still powered on. Pressing the power button will
result in messages of enabling and disabling devices, but it will not shutdown. I
have to reset or hold the power button for more than 5 seconds.

18: Thunar is not updating its current view when files are changed or added in that
directory!

19: When a hard disk is in sleep mode it is not spinning, this is fine. But when I
try to power down the system it will turn on the hard disk. 
Resulting in a disc that is spun  up for one second before the system powers down. 
This is not very healthy for the hard drive.
 The life cycle of the hard drive is partially determent by the number of spin ups.

20: When openoffice.org is installed the links installed in the menu->office section
are wrong. All those links are pointed to the ooffice command but they should be
pointed to the specific application like: oowriter, oomath, ooimpress, oocalc and
oobase.  Now hitting the OpenOffice.org Writer link will not start oowriter but will
start ooffice! This is also the case with the other oo links.

21: There is a font displaying resolution problem in the Ubuntu distributions. 
The commands: xdpyinfo | grep resolution and xrdb -q | grep Xft should give the same resolution (DPI) but they are way off, resulting in blurry fonts in some applications, like in openoffice.org. 
Normally I was able to solve this by calculate and adding a DisplaySize option in the xorg.conf monitor section. 
But that does not work with feisty!

22: When I do a search for the program penrose in the xfc4appfinder and then right
click for more information on the penrose item, it will show a window that has a width that is far to big!. 
The window will be way of the screen.

For the moment these are my bad points. If you need help debugging, or need more
information you can contact me. 
It is possible to solve some of these problems, by changing the settings that are default, but the purpose is to get it right form the start!

I put a lot of time and effort into this, I hope it will be used useful.

Keep up the good work!

Best regards,

Jelle de Jong

---

### Post by j1mc on 2007-03-21
Jelle,

Thanks for your very thorough test, and sorry for not responding to it yet.  I'll be in touch soon.  :)

Jim

---

### Post by j1mc on 2007-03-22
As a note to anyone following this thread, the Xubuntu beta ISO's were recreated last night, and are now available for testing.  I've run some tests on the i386 live cd, and the AMD64 alternate cd, but other testing is appreciated.  Thanks!!

---

### Post by racoq on 2007-03-23
I don't know if this post cames to late or this issue as been addressed. Sorry just reporting now (i am a busy person ;)) However im using Xubuntu feisty herd4, and when i'm away from the computer, the screen saver loads, which seems to be normal. However when the screen saver appears my computer freezes (with the default settings). Even the ctrl + alt + backspace doesn't do the trick, i  have to restart in the reset button. The only way i have resolved this was to activate the option blank screen only. The mode random screen saver locks my computer. 

My computer specifications are: 
Pentium III 800 MHZ,
512 MB RAM, 
Mainboard DFI CA61 Rev B+
MSI Geforce 4 TI4200 64 MB ddr, 
running the proprietary nvidia Drivers. 
The nvidia drivers i'm using are NVIDIA-Linux-x86-1.0-9631-pkg1 (the last ones that support my graphic card from nvidia). 

Oh and i've installed feisty from the Live CD i386 version (of course :D). 

I haven't done any upgrade to the system so basically the packages are the defaults from herd 4.

If this bug wasn't detected, please post me for further instructions on how to give u more information.

---

### Post by j1mc on 2007-03-23
Hi racoq.  Thanks for taking the time to let us know about your issues.  One of the key things with testing the ISOs, though, is the recency of the sources used to report the test results.  In this case, Herd 4 was released on February 15th, which was over a month ago, and the developers have certainly updated a lot of packages since then.  :)

In your case, if you don't want to do a fresh install, hopefully you can at least update your packages (using either synaptic, or "sudo apt-get update && sudo apt-get dist-upgrade" from the command line), and see if your system still exhibits those same behaviors.

If you update your system and the problems still persist, please file a bug report.  The "Helping With Bugs" wiki page is a good place to start.  :)  

If you'd like to contribute to the ISO testing process, please see this section of the forums for further information.  The heading at the top of the page, "Development CD/DVD Image Testing" has some good "stickie" threads in it, and should provide some initial direction.  :-)  

As a final note, we just completed the testing prior to the Beta release, so we'll have a bit of a break in ISO testing before the Herd 6 release.

---

### Post by jmc1024 on 2007-03-24
> **j1mc said:**
> Hi Mark,

If you wish to test Xubuntu, please make sure that you are using the most recent nightly release.  The Ubuntu developer team fixes bugs every day, so an ISO from March 1st will probably have some bugs in it that have been fixed by March 17th.  

Please see[ this listserve message]("https://lists.ubuntu.com/archives/xubuntu-devel/2007-March/003284.html") concerning our most recent testing procedures.  

And thank you for volunteering to test!  :-)

Actually, I've had this problem on every ISO I've downloaded since last fall.
Probably tried 6-7 versions.  The most recent version was from two nights
ago.
I hope I can help sort this out, but I'll need pointers.
Thanks,
Mark

---

### Post by j1mc on 2007-03-24
> **jmc1024 said:**
> Actually, I've had this problem on every ISO I've downloaded since last fall.
Probably tried 6-7 versions.  The most recent version was from two nights
ago.
I hope I can help sort this out, but I'll need pointers.
Thanks,
Mark

Ok, when I search for your particular error on google ( Disk error 32, AX = 4200, drive 9F ), I don't find a whole bunch of solutions.  There is a rather lengthy thread on the gentoo forums about it, and some people found things that helped them, though.  It just doesn't seem like the fixes worked for all people.  

For starters: check to make sure that the md5sum of the image you downloaded matches the md5sum of the page you downloaded it from.
- Check to make sure the disk image isn't corrupt (test the cd image when it goes to the initial "Do you want to install xubuntu" screen.)

- If you don't get that far, check to make sure that the image is burnt to the cd correctly.  (What program are you using to burn the cd?)  Check to make sure that your settings are set up properly to burn the cd.
- If you're burning the cd from linux, maybe try to burn it from the command line  navigating to the folder where the ISO is stored, and then entering "cdrecord -v dev=/dev/cdrom name_of_file.iso" works for me.  (if you have more than one cd/dvd drive, you might need to use "dev=/dev/cdrom0" instead.

The fact that many other distros come up with the same error makes me want to check those things first.  I hope this helps!

---

### Post by racoq on 2007-03-24
For those who don't know Xubuntu Feisy Beta, is already available, get it [here]("http://cdimage.ubuntu.com/xubuntu/releases/feisty/beta/").

I'm downloading the CD and i will do a upgrade from herd4 latter tonight. I will them post them here if my issues remain in this new beta.

---

### Post by jmc1024 on 2007-03-24
> **j1mc said:**
> Ok, when I search for your particular error on google ( Disk error 32, AX = 4200, drive 9F ), I don't find a whole bunch of solutions.  There is a rather lengthy thread on the gentoo forums about it, and some people found things that helped them, though.  It just doesn't seem like the fixes worked for all people.  

For starters: check to make sure that the md5sum of the image you downloaded matches the md5sum of the page you downloaded it from.
- Check to make sure the disk image isn't corrupt (test the cd image when it goes to the initial "Do you want to install xubuntu" screen.)

- If you don't get that far, check to make sure that the image is burnt to the cd correctly.  (What program are you using to burn the cd?)  Check to make sure that your settings are set up properly to burn the cd.
- If you're burning the cd from linux, maybe try to burn it from the command line  navigating to the folder where the ISO is stored, and then entering "cdrecord -v dev=/dev/cdrom name_of_file.iso" works for me.  (if you have more than one cd/dvd drive, you might need to use "dev=/dev/cdrom0" instead.

The fact that many other distros come up with the same error makes me want to check those things first.  I hope this helps!

I'm sorry to have taken up everyone time at sure a time critical period.  After
making a stack of coasters, I tried to burn an old iso I used to build a couple 
of machines,  I'm getting an error from cdrecord:
Track 01:   35 of  528 MB written (fifo 100%) [buf  99%]   8.1x.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 47 53 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 03 00 00 44 D9 0A 00 2B 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 17625 (valid) 
resid: 63488
cmd finished after 5.310s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

A google search indicates it might be a hardware problem.  I burnt a herd 5
iso on my server and it boots fine.  I'll report my results on this testing later.
Again sorry for wasting your time,
Mark

---

### Post by j1mc on 2007-03-24
> **jmc1024 said:**
> A google search indicates it might be a hardware problem.  I burnt a herd 5 iso on my server and it boots fine.  I'll report my results on this testing later. Again sorry for wasting your time, Mark

Hey Mark, you didn't waste my time.  :)  I'm glad that we were able to figure out what the problem was, and now you'll get to burn CD's that work.  That's good news!

Enjoy your weekend.  We'll get to more testing when we approach Herd 6.  :-)

---

### Post by racoq on 2007-03-25
AS promised i have upgraded my herd4 to the latest beta, using the alternate CD, that solution resolved all my issues. However i am getting a error at startup. Can anyone tell me which file i can see, for viewing the complete log of the startup process? thats important for me to help with the tests.

---

### Post by j1mc on 2007-03-26
> **racoq said:**
> AS promised i have upgraded my herd4 to the latest beta, using the alternate CD, that solution resolved all my issues. However i am getting a error at startup. Can anyone tell me which file i can see, for viewing the complete log of the startup process? thats important for me to help with the tests.

Hey racoq, check out the log files in the /var/log folder.  Perhaps maybe syslog?  I read about which log file to check last night, but now I can't remember exactly which one it was.  I'm pretty sure it was syslog, though.  :-)

---

### Post by racoq on 2007-03-26
Forgot to mention, while i was upgrading, i have found a md5 checksum error, on linux-restricted-modules-2.6.20-12-generic package which kept me from upgrading that package from the cd (i've had to download the package from the ubuntu feisty packages homepage, and installed it manually)

The md5 checksum error only occurred on this package! Is this a bug on the alternate CD?

---

### Post by j1mc on 2007-03-26
> **racoq said:**
> The md5 checksum error only occurred on this package! Is this a bug on the alternate CD?

Racoq, I wouldn't worry about it.  It probably just didn't burn correctly when you made the CD.

If you had a problem with the package that you downloaded and installed, then you might want to see if a bug already existed for your problem, and (if not) report the bug.  

Have a good day!

---

### Post by ghostboy on 2007-05-16
Im in! This looks like something I would really like to get into.  Ill start testing today!

---

### Post by j1mc on 2007-05-16
> **ghostboy said:**
> Im in! This looks like something I would really like to get into.  Ill start testing today!

Hi Ghostboy.  :)  Thanks for offering to help out.  However, right now we're kind of laying low until we start testing the initial test releases of Xubuntu 7.10, the Gutsy Gibbon.  :-)  The initial alphas aren't ready yet, so there's nothing to test right now.

If you'd like, please subscribe to this thread, by selecting "Instant Notification" from the Thread Subscription option.  That way you'll be notified when things change, and when we get ready to start testing again.

Take care,

Jim

---

### Post by reidms on 2007-05-17
Ill help!

---


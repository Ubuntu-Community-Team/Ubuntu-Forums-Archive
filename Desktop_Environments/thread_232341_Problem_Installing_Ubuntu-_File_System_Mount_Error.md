---
title: "Problem Installing Ubuntu- File System Mount Error"
date: 2006-08-08
forum: Desktop Environments
---

### Post by thistlebrae on 2006-08-08
Hello all,

Will keep it brief.  I am attempting to install 6.06 LTS.  The GUI install program gets to the second step (titled something like mounting primary file system) but then hangs.

I think the problem is that the drive is new and not formatted.  Is there not a formatting capability in the Ubuntu installer for a virgin drive.  If I had an operating OS on the drive I probably wouldn't be installing Linux on the drive.  Can anyone help?  Is there a minimum formatting option I can use and how can I do that?  Would I have to mount it externally and then use something like Partition Magic.  Does it have to be formatted as a bootable drive?

Any help would be most appreciated.

Thanks,
Todd

---

### Post by vijirajan on 2006-08-08
You don't have to format the hard drive before hand. Ubuntu 6.06 LTS installer can do that for you.

If you can list all the steps in the installer that went thru fine before it hung, it will be helpful.

---

### Post by thistlebrae on 2006-08-08
Thanks for the quick response...I like your answer..hope you can help.

I changed the boot order to boot from CD.  The Ubuntu menu appears and I selected Start/Install Ubuntu.  The screen then changed to a loading kernel ...... dotted line and then a status barometer appeared.  The first task completed (in just a few seconds) then it went on to the second.  Which was the comment in my original post.  Something like mounting system volume.  It hangs there for a long time (about 5 minutes) before changing back to black and white screen with a bunch of errors.

Hope that helps.  Whatever the second task in the start install process is is the problem.

---

### Post by bscbrit on 2006-08-08
If I were you I would install using the alternate install binary and not using the live disk - which is what I assume you are trying to do.  The Alternate doesn't expect there to be anything on the disk and will do exactly what you want whereas I suspect that the live disk expects the disk to be formatted.  It might mean another long download though....

[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

However, wait a few minutes to see if anyone else has a brighter suggestion!


By the way, if nobody answers your first post in 20 minutes or so, it probably means that nobody who knows the answer has yet read it.  There isn't much point in posting the same problem twice :D

---

### Post by vijirajan on 2006-08-08
I agree with bscbrit, the Alternate Install CD is the way to go.

---

### Post by thistlebrae on 2006-08-08
Thanks bscbrit...

Two questions for you.  I am downloading the alternate CD now.  It appears to be an ISO image so I should just be able to boot from it once I burn it to a CD correct?

Secondly,  did my posting post twice?  I only see it once.  I hit post and then got a fatal error so I reposted the text from the clipboard.  I didn't mean to post twice nor can I see it twice.  Would be interested in finding out where the first post went.  You obviously saw it...but I can't.:sad: 

Thanks again...
Todd

---

### Post by thistlebrae on 2006-08-08
DOH!  Now I see it (posted twice)[-X .  Don't I just have egg all over my face?

Thanks folks.  Let's hope the alternate CD is the magic!

---

### Post by bscbrit on 2006-08-08
No problems - good luck with the alternate CD install.

---

### Post by thistlebrae on 2006-08-09
Maybe Ubuntu is not for me...

I downloaded the ISO file for Ubuntu's alternate CD format and burned to a CD via the Ubuntu help file using their recommended freeware burner.  Made progress ... at least I don't have the drive issue.  But now I have these:

No matter how I try I cannot get swap space defined on the drive. I define a partition and then try to find a way to designate it as the swap volume.  No luck.  I just end up with a multi partitioned drive and the error message indicating that I have dedicated/identified no SWAP space and that I may get errors.  Finally I just said o.k.... the machind has have half a gig of RAM ...how much swap space could it need when it already has half a gig of RAM?

Issue #2
Once I start the install I get a standard screen telling me that it is installing the base system.  It hangs at 6% and when I follow the go back prompts it gets me error after error about how it couldn't download this and that package.  Question here....isn't everything it needs on the CD?  Do I have to have a live internet connection to load Ubuntu from the alternate CD?  Is it attempting to download and install these packages over the internet?

I am finding the whole process very wearing, time consuming and frustrating.  If I am headed for this type of struggle as a daily ritual...I guess I better think about passing on Ubuntu.  Not ready to quit yet...please help.

---

### Post by bscbrit on 2006-08-09
You don't have to do anything to make a swap partition other than to call it /swap in the installer.  However, you probably wouldn't notice much of a hit if you had no swap partition at all.  There are other threads where can can read of other users' experiences regarding sizes of swap partitions or whether they are even needed.

If it is having problems installing then I suggest that you burn your CD at a low speed.  Corrupt writes to the CD could cause some of the problems that you are seeing.  You do NOT need an internet connection for the base system but you will if you want to update it or add packages that are not on the CD.  Spend an extra 10 minutes burning your disk and save hours on the installation.

---

### Post by thistlebrae on 2006-08-09
Thanks BSCBRIT (as usual...you have some sensible alternative)

Will burn the CD at slower speed now.  As far as the swap..where exactly in the install do you define the /swap.  I filled it in as the answer to the "mount point".  As in Mount Point: /sWAP

It labeled it as such when it was preparing to format the drive but I still got the same message about having no swap defined.  If I am ready to install with the new burn and am only hung up on that then I will bypass that choice and go without the swap space.

Will check for an answer before I try a reinstall in a few minutes.

Thanks again...

---

### Post by bscbrit on 2006-08-09
My copy of the Alternate Installation (which I confess is not the latest) goes into GParted to allow partitions to be created and then into a page which enables me to define which partition is used for which purpose.  It always seems to find the swap drive by default. Now to be honest, I have always installed to a hard drive already containing a swap partition and simply told the installation prog to use the same partition again.  Perhaps (and I cannot remember clearly - must be my age...!) you have to format it under GParted in a specific manner.

Please forgive me for not trying this myself but as I am packing up my home to move elsewhere I am down to my last computer and I do not want to cock it up to find the answer. (OK, its a pretty lame excuse for not trashing my own hard drive but I hope you will accept it!)

If you haven't already started the installation why not experiment a few times before you finally settle on your own configuration.  You could at least then come back and tell me what you found even if everyone else claims that already they know!  And it will make you sound so much more knowledgable when you help someone else solve the same problem in a few weeks time.  "When I did this, I realised that you have to do this, push that, blah blah blah".

---

### Post by bscbrit on 2006-08-09
Just a thought - you are formatting it as a swap partition and not as ext3 aren't you?

---

### Post by thistlebrae on 2006-08-10
BSCBRIT..

Good News...SUCCESS!  After several more downloads and CD burns of the Alternated distribution ISO image I discovered the problem.  Was booting from a CD/RW which (for whatever strange reasons) thought that they CD was corrupt (even though it passed the integrity check).  I disconnected that device, connected the DVD ROM above it and installed from there with the exact CD and ... Voila!  I got all of the expected partitioning prompts you explained earlier (and that are in the various books I now own).  Can't believe the entire set of prompts in the installation program were different.

Now I have a new (minor annoyance) issue.  I want to change the resolution of my screen higher (currently 640x480 - Kindergarten mode I call it).  When I go to change that I have no options.  Wondering if I have to install some packages etc.

Secondly, my wireless networking is not working so I don't have internet connectivity...that appears to be a well known issue and will work on it as time permits.  In the interim I may attempt using a network hub and hardwiring to my XP machine that has the shared internet connection.

Thanks for you help....

---

### Post by maniacmusician on 2006-08-10
thistlebrae; regarding your resolution, what driver are you using for your video card? it is in xorg.conf. in Terminal, type

sudo gedit /etc/X11/xorg.conf

make sure to capitalize the X in X11. In the file about halfway down usually is your video card. for example mine says:
> 
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200 (RC410)"
	Driver		"vesa"
	BusID		"PCI:1:5:0"
EndSection


post back with this and we'll try to work on it

---

### Post by thistlebrae on 2006-08-10
ManiacMusician,

Thanks for chiming in.  Did what you asked and have inserted the results below:
___________________________________________________
Section "Device"
	Identifier	"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"IBM P76"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR]"
	Monitor		"IBM P76"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
______________________________________

Looking forward to whatever help you can provide....

Thanks!

---

### Post by thistlebrae on 2006-08-11
ManiacMusician

Happy to report I solved the issue!

Many thanks and you were on the right track.  In the late afternoon yesterday I lucked onto this document (posting here so that others may "luck" onto easier than I did](*,) )

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

It containted all the answers.  In brief, the part about "nv" versus "nvidia" in the xorg.conf file was the magic bullet..while I did all steps "to the letter" it was when I made that final change that I reached nirvana!

Now I am really lovin' UBUNTU!

Thanks again for jumping in....

Todd

---


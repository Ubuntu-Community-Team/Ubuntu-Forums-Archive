---
title: "Lock-up at Login"
date: 2005-07-04
forum: Desktop Environments
---

### Post by radix on 2005-07-04
Hello,
 
        Let me give you some background on my mindset.

        I hate microsoft.  I dont want windows.  But the linux community apparently doesn't actually work.  
        I downloaded 10 CD's worth of Fedora Core iso's, all bad, no matter what I tried, always failed checksum. Gave up on Fedora Core.  I don't care what anyone thinks they have to say on the matter; I don't need to retry 6 times to get a working ISO. Period.
        Moving on, found Gentoo.  Failed.  Case-in-point, fdisk sucks.  Period.  "You just don't know how to use it."  What?  Yeah, it should just be everyones new welcome to have to reboot back into Windows 8 to 13 times to get online and try to figure out why I can't write a partition scheme to the MBR from fdisk, right?  End of story.
        Found SuSE.  Saw Novell logo.  Nuff said.
        Came across Ubuntu, looked promising.  Got the ISO (passed chksum first time) and installed just fine as well.  I really was excited.  I really got into the whole "world" jive of the distro.  So I came up to the login screen, and it froze.  No-matter what I tried, (BIOS configs, lowering the resoulution) it would freeze when i put in my user-id and p/w to login.
        So, undauted, I rebooted into good 'ol windows to pull up firefox and find out what to do.  I found that others have been having the same problems, but unfortunately, since no-one seems to be able to form proper english grammar to convey ideas (yes, they were american), the reports of how they worked around their problems were largly unintelligible drivel.
        
        So, last chance for Ubuntu, and Linux in general.  Note, I'm very computer literate.  I even took some classes offered by my local LUG (uh, Linux Users Group of course) at my college.  But it shouldn't be my responsibillity to try and decipher someone elses verbal excrement when it comes to getting around in Linux.  And it just shouldn't be this difficult to do.  Theres many things in life that deserve great persistence; getting a simple GUI up on your system isn't one of them.
       
        Heres what I've tried:

        Installing the proprietary ATI drivers.  This would't happen.  Logged on as root through the recovery console, i mounted my CD drive which contained the .run driver file, typed in ./atidriver-whatever.... Got "Permission Denied."
Researched this error.  Well then, if Ubuntus default install doesn't give freakin' root ownership of the system, maybe someone who develops it needs to sit down and think about themselves for awhile.  Hopefully there's a nicer explanation. 
        Also read that, when  GNOME starts up, it wants to play a sound, and that it could be the sound drivers that are causing the freeze.  This made sense to me, because it does jitter and freeze when the sound begins to play, although it also freezes when i pull up the menu that offers to start GNOME in failsafe and other options.  So I found the open-source AC97 drivers (yes, I need the AC97 drivers, thank you for asking), pulled up the install instructions and, what?  More mental excrement.  And I realize that an admin with a few years exp would work right through it, but, should everyone just believe that everyone else interested in open-source understands their poorly concieved and implemented directions?
        So, I'm asking that any help be presented in a logical step-by-step command structured response, without reveling in assumed expertize.  The best way to learn what you know is to teach it.  I know there has to be some simple work arounds to get GNOME running, so I can at least get the drivers installed from the desktop console (since apparently root cant do this from ./).  I've seen the posts about turning off parameters, or deleting "hidden" GNOME files, but again, always presented in an "I'm three steps down the line, hope you know how I got here" approach.    
        
        Does Ubuntu run on MSI motherboards?  ATI X600 graphics cards?  AC97 audio Devices? 1GB of RAM? 80GB SATA disks? PS/2 keys and mouse?  

        Please, first step basis.  If you feel too haughty to be able to help a newbie, may all the mixed blessings of Bill Gates be bestowed upon you and your software.  Lets work the problem.

---

### Post by Morimando on 2005-07-04
[QUOTE=radix]
        Installing the proprietary ATI drivers.  This would't happen.  Logged on as root through the recovery console, i mounted my CD drive which contained the .run driver file, typed in ./atidriver-whatever.... Got "Permission Denied."[/QUOTE]
For this you need to do
 ```
chmod a+x ati-whatever
./ati-whatever

```
note that you need to have the kernel-headers installed (at least with the nvidia drivers).

Just a quick note for your other stuff (as i am using the intel8x0 module for sound and never had too much issues, i won't comment on this one): I am from Germany and have been using Mandrake, Gentoo, Slackware and now Ubuntu, with all of them i got along just fine, by just using the material that's found online and the HowTos that so many people in the community take the time to write. If you aren't able to read them, then maybe you're doing something extremely wrong, as most of them are quite understandable, especially at the Gentoo forums.
Now please, stop that unqualified babbling on and just sit down, take some time (yeah, right, when switching to Linux you still need to invest some time to get an insight to how things work) and if you don't find a solution that you can understand online, come back to the Ubuntu forums, ask for help with a problem you got and please don't forget to attach all errors given to you and the appropriate system settings (like your fstab when talking about problems w/ mounting), for without them, we can only guess.

---

### Post by varunus on 2005-07-04
Radix:

Here are a couple of things to try to see if you can get past your login screen issues.  Ubuntu is a great distro, and I've always found the community to be very helpful.  Don't give up on us yet!

The first thing to try:  When you're at the login screen, you said it freezes after you type in your username and password.  So, try clicking "session" and choosing "Failsafe GNOME" and see if it still freezes.  If it doesn't, then I can help you solve the problem (this would be the delete hidden gnome files thing, I'll guide you step by step).  If it still freezes, try "Failsafe Terminal," and if that works but GNOME doesn't, then post that back here.

Another thing to try, if neither of the above works:  Once you get to the login screen, don't enter your username and password.  Instead, hit CTRL-ALT-F1.  You'll see a text console.  Type in your username and password there.  It will log you in to a console prompt.  Type:

```
sudo /etc/init.d/gdm stop
``` 

It will ask you for your password; enter it.  This will shut down the login manager.  Then, type:

```
startx
``` 

Thiss will attempt to log you straight into GNOME and bypass the login manager.  If this works, then post back here; we've at least identified the problem is with the login manager then.

Good luck, and I hope one of the above 3 methods lets you login; if so, we can get you up and running.  Don't give up on the Ubuntu community yet; I've found everyone to be quite helpful.

---

### Post by Morimando on 2005-07-04
Oh and post your fstab please, if it's an issue concerning your home partition
(vim /etc/fstab or more /etc/fstab)

---

### Post by glasscleaner on 2005-07-04
upgrading my kernel from i386 to k7 (amd cpu) (i686 intel) correct this for me.

---

### Post by radix on 2005-07-05
I do not have any problems mounting my HDD! I dont even know why anyone would THINK I did, I never said anything about HDD problems! jeez.  

what I AM having problems with is STILL trying to get the ATI driver installed.  i tried that chmod a+x command. OK, people, thats great that YOU know a command, but again, as I MADE CLEAR, I DONT KNOW WHAT THESE COMMANDS DO! so explain it!

when I did do chmod a+x ati... its fine, until I do "sudo ./ati..." it keeps telling me that I cannot write to a read only file system.  so I need to know what to do to give my user the abillity to change the root file sytem OFF READ ONLY, and be able to write to the fs.

---

### Post by radix on 2005-07-05
BTW, I tried bypassing the login thing, I still got to the Ubuntu screen that plays the opening sound and it froze.  And If you would have read my first post again, youll see that I already said that it freezes when I try to change to GNOME failsafe or whatever else. It freezes.  I have a feeling it is the graphics driver, but I still cant get that installed until I can change the filesystem to allow me to write files to it, because it keeps telling me its READ ONLY, even when I do "SUDO whatever..."

---

### Post by radix on 2005-07-05
and I'm sorry if I seem pissed off.  Im really tired of things never working.  And I hate windows.

---

### Post by varunus on 2005-07-05
Hm...it tells you that you have a read-only filesystem?  Try entering the command "mount" at a console prompt (at the CTRL-ALT-F1 for example).  This will list your drives, and how they are mounted.  Is your hard drive mounted read-only?  This would be strange, but it may be the case if the ATI driver isn't installing.  It could also be the source of gnome lockups, if gnome is trying to modify a file when you log in.  This is why having your /etc/fstab may help; it lists how your hard drives are set to mount.  If there is some strange issue with how your hard drives are being mounted that is showing itself in a strange way (like gnome lockups, the ATI drivers not installing) then we can fix it.

Also, I have an AC97 in my computer, and it works with the included intel8x0 sound card drivers.

And sorry if I sounded condescending or something in this and my earlier post, I didn't mean to make you pissed off.  I'm just trying to help.

---

### Post by Morimando on 2005-07-05
Well.. there is a reason i asked for the contents of fstab, as there definetely seems to be a filesystem that's not equipped with the proper mount options.
If sudo / root can't write, that means NOONE can write, that means there's something wrong and that's most likely in /etc/fstab.
And FYI chmod a+x means "add (**+**) e**X**ecution rights for **A**ll users. also possible is instead of the "a" => "u","g" (user/group), for "x" => "r" "w" (read/write) and for the "+" also "-" is possible, to remove the rights (r/w/x) for a given group (a/u/g) ... now please show your mounttable (fstab), also please 
```
ls -lA <directory-name-containing-ati-drivers> 
```
(FYI: "ls" = list, "-lA" => shows all attributes for file/folder)

---

### Post by radix on 2005-07-05
hey, thanks yall.  I feel like were getting somewhere.  I'm going to try and get my fstab up here now, but I'm going to have to write it down by hand, so if its really big i'm just going to include the parts about my hdd.  also, i'm also rather confused how it could be write only, since this is just a clean install from the CD. 

Heres the steps I took to install from CD, this might help.

First install: 

Partitioned a 16.2GB swap at beginning of drive (first partition)

Partitioned a 26.1GB partition at beginning of drive.  I set this as / and labled it /, [COLOR=Red]reserved 6% of drive for root[/COLOR], and marked the bootable flag ON. (second partition)  

Partitioned 26.1GB for a third partiton for miscellaneous data, labled /var, no space reserved for root, bootable flag OFF.

and then went ahead with install.  Now, heres how iv'e tried to install the driver.  The driver is the GRAPHICAL 8.14.13 driver at the ATI site right now, I burned it to a CD, and then to access it from linux CONSOLE, i typed:

"sudo mount /media/cdrom0 -o unhide" (this how it was done somewhere I read)

the drive mounts, and I can ls and see the ATI file in the /media/cdrom directory.  So, while in /media/cdrom, I type 

"./ati-driver-install...." and got "Permission Denied" (logged in as both root and user)

So I tried 

"sudo ./ati-driver-install...." and got "Permission Denied"

So then I tried like suggested 

"chmod a+x ati-driver..."

"sudo ./ati-driver-install..." and got "Filesystem Read Only"

This was from both root and user.

I'm wondering if maybe the fact that this is a GRAPHICAL installer has anything to do with it.  At ATIs site they have some stuff for X, like XOrg and something else. what are these for, and how do I mount or install them? Are they neccecary? How would I mount or install .rpm's from a CD?  

thanks guys

---

### Post by radix on 2005-07-05
BTW this is also a SATA drive, but i didn't have any problems with install.  another intersting thing to note, no matter WHAT, kubuntu or the KDE upgrades gotten through apt-get WILL NOT intstall properly, theres always errors.  but interestingly, all the other upgrades from apt-get install just fine. I'll try to get my fstab up here for us now.

---

### Post by Morimando on 2005-07-06
Yeah.. I C the problem... 
copy the ati driver file from the cd to you /home directory, THEN do the chmod a+x ati-driver and then ./ati-driver.
```
cp ati-driver /home/<username>/
cd /home/<username>
chmod a+x ati-driver (maybe you need sudo here)
sudo ./ati-driver
```
As files burnt to a CD can't be changed (except for Packet-Writing Media) you can't chmod the ati-driver as long as you still got it on a CD since the changing of mode would mean you had to write to the file to insert the new rights. Thus copy it to a harddisk where you have right to r/w and chmod it there and start it there. It should run.

---

### Post by Morimando on 2005-07-06
[QUOTE=radix]
I'm wondering if maybe the fact that this is a GRAPHICAL installer has anything to do with it.  At ATIs site they have some stuff for X, like XOrg and something else. what are these for, and how do I mount or install them? Are they neccecary? How would I mount or install .rpm's from a CD?  

thanks guys[/QUOTE]
.rpm s you can install using "alien" (=> 'man alien'). Most times it won't work from a CD, programs you have to extract from an archive or execute are better run from your /home directory. 
From your description it sounds as if there was an installer that you can start when in X.org and one that you can use when you're 'console only'. I'd suggest you try the console only first, but then again i don't own an ATI and thus have no experience with that.

---

### Post by radix on 2005-07-06
well, thank you all for your help so far. I gat the driver installed! but so close, yet so far.  It doesnt lock-up when I pull up the boot selection menu ("last" "GNOME failsafe" ...) anymore, but when I login, it does the same thing, The sound plays, and the sound seems to freeze it up.  I want to try an install of the sound drivers now, but I don't understand the instructions.  Maybe you all can help me with that. Before that though, is there anyway to turn all the sound off in xorg.config first to see if that really is the problem? Ill submit the instructions later so yall can explain them to me.

---

### Post by Morimando on 2005-07-07
Try muting the channels by issuing "alsamixer". The interface that pops up after starting "alsamixer" is pretty self-explanatory. Also look up, if the loaded module for sound is the right one for your card. [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

---

### Post by radix on 2005-07-07
dude, I cant get into GNOME.  How do I call alsamixer from console? thats the whole point man, I cant understand how to install the sound drivers, the instructions make no sense, they gice commands to execute, but they're incomplete. here they are: 

Step 1. unzip source code
        tar xfvj azx-021705.tar.bz2

Step 2. Turn on sound support (soundcore module, default turn on)

Step 3. Complied source code
	a. ./configure
	b. make
	c. make install
	d. ./snddevices

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)

Step 5. reboot your machine

Now this mustv'e been written by a foreigner, or a two year old. read this:

Note: 	1. [COLOR=DarkOrange]The most detail information, can refer the [/COLOR]alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2. ...

"the most detail information, can refer the?" wtf? 

Anyway, hopefuly someone can translate for me.

---

### Post by Morimando on 2005-07-07
Sheesh. Alsa sound should be installed with Ubuntu right from the start. If you use the normal kernel (do you?) there should be all drivers available as modules and yours should be in modprobe's list ^^ The HowTos you read are to install ALSA from scratch, as far as i see. You shouldn't have to do that..
Show me the output of 'lsmod' and if 'alsamixer' works, please. So we'll see if the modules are loaded and the alsa package is installed.

---

### Post by varunus on 2005-07-07
I don't know if this is clear from Morimando's post, but alsamixer is a console program to adjust your volume. :)  Hm...I don't know if its the sound...can you try typing "startx" from the console instead of using the login manager and tell us what happens?

---

### Post by Morimando on 2005-07-08
[QUOTE=varunus]I don't know if this is clear from Morimando's post, but alsamixer is a console program to adjust your volume. :)  Hm...I don't know if its the sound...can you try typing "startx" from the console instead of using the login manager and tell us what happens?[/QUOTE]
good idea. If 'startx' fails, you'll have the errormessages that we need in your console and can post them here so that we can sort out the problem faster.

---

### Post by Morimando on 2005-07-11
Solved?

---

### Post by radix on 2005-07-23
no.

---

### Post by radix on 2005-07-23
I cant waste anymore time with this crap. So, hopefully, Ubuntu will support my hardware upon next release.

MSI NEO4-F (nForce 4) 
AMD Venice 3000+
1GB Ram (256x4)
ATI A.I.W X600 Pro
Integrated AC97 sound

....maybe in 6 months huh?

---


---
title: "Ubuntu on a Dell 1720"
date: 2007-07-29
forum: Dell  Ubuntu Support
---

### Post by AndyQ on 2007-07-29
Well, got my Inspiron 1720 on Friday and set about seeing whether I could get Linux installed on it. It took a while but its almost all completely much working and whats left is not too important.

Anyway, this is what I,ve done (might be of some help to someone else:

I first started from the Live CD to make sure that it would work. This didn't go too well as I was pretty quickly dumped to a terminal with a very cryptic message (something like tty not started). Tracked this down to the DVD drive not being loaded correctly. Sorted this out by adding break=top to the startup parameters (F6 at boot screen), and then when you get dumped to the terminal screen enter "modprobe piix" followed by exit.
This allowed me to boot Ubuntu which then failed when starting the X server.

This was fairly obvious why this failed, the default NVidia drivers don't support the 8600M GT, so I changed my xorg.conf to use the vesa driver (change "nv" to "vesa"). This allowed X to start and I could then download and install the latest NVidia drivers which worked straight off.

Booting into X, the sound was recognised, and the wireless lan also worked staright away which was nice. 

At this point, I wasn't totally confident that a straight install would be possible (although I think it would probably work fine afer more playing) so I decided to install using Wubi (installs a disk image within a Windows filesystem and boots from that - NOT a virtual machine). Wubi uses the aternate image and the install went fine and pretty much everything was detected fine and worked.

After installing the NVidia drivers again, I found an annoying problem where it would keep the new driver after a reboot. Tracked this down to it still having the old drivers around so I cheated and removed them from /lib/linux-restricted-modules/2.6.20-16-generic (renamed all the nvidia folders to nvidia.._ and reinstalled the new driver) which fixed that problem.

The only issue I have at the moment is the trackpad, It is only detected as a standard PS/2 mouse and the synaptics driver just won't with it. I have absolutely no idea why - I'm guessing its a new component which isn't yet supported by the driver. This means that I get false taps sometimes (very annoying), and I can't use the scroll areas on the pad (again annoying) but it does emulate a 3 button mouse (press both buttons together) so I can scroll in Firefox using that. Whilst this is annoying, its not a huge issue (except from a completeness point of view)

Oh, I also installed CompizFusion which worked first time - no problems and is pretty cool :)

So all in all, I'm pretty pleased (still haven't managed to get a Linux install on any PC - going back to Slackware 3 - where every component just worked though), and it wasn't too tricky.

Anyway, hope this helps someone (although I mainly wrote it so I had a record of what I did when I next re-install :))

---

### Post by DC@DR on 2007-07-29
Cool, thanks for sharing useful info :-)

---

### Post by vcallaway on 2007-07-30
Thanks for posting this.  Dell tells me mine is supposed to be here the week of 8/13.  At least I know what to look forward to.

---

### Post by breusshe on 2007-08-22
Think I found the answer to your mouse issue:

[http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/)

Take a look at it and let us know.

---

### Post by AndyQ on 2007-08-24
This thread fixed my mouse problem.
[http://ubuntuforums.org/showthread.php?t=510516&page=1](http://ubuntuforums.org/showthread.php?t=510516&page=1)

Only two problems let now - suspend/hibernate I can't get working and the webcam/microphone still isn't working.

---

### Post by daemon_damodred on 2007-08-24
I was having the same issue with my 1720 as well, so thanks for the post.  I haven't had much experience (any) with Linux, so I don't know the command lines.  You edit the /etc/X11/xorg.conf file with sudo nano right?  After that, how do you continue loading Ubuntu?  I tried X, but that didn't do much for me.

---

### Post by Aonxe on 2007-08-24
> **daemon_damodred said:**
> I was having the same issue with my 1720 as well, so thanks for the post.  I haven't had much experience (any) with Linux, so I don't know the command lines.  You edit the /etc/X11/xorg.conf file with sudo nano right?  After that, how do you continue loading Ubuntu?  I tried X, but that didn't do much for me.

I did sudo gdm stop and it loaded into the live CD for me.


Now for my question, I installed ubuntu and then when I went to boot from Grub I got the same cannot use tty error I had been getting.  I went to grub and checked to make sure it was doing break=top in the bootup and it was so I am stumped atm.. :(

---

### Post by AndyQ on 2007-08-24
> **daemon_damodred said:**
> I was having the same issue with my 1720 as well, so thanks for the post.  I haven't had much experience (any) with Linux, so I don't know the command lines.  You edit the /etc/X11/xorg.conf file with sudo nano right?  After that, how do you continue loading Ubuntu?  I tried X, but that didn't do much for me.

sudo nano would work - althoug I'm  vi fiend so I use sudo vi.

To restart X - just type startx

---

### Post by AndyQ on 2007-08-24
> **Aonxe said:**
> I did sudo gdm stop and it loaded into the live CD for me.


Now for my question, I installed ubuntu and then when I went to boot from Grub I got the same cannot use tty error I had been getting.  I went to grub and checked to make sure it was doing break=top in the bootup and it was so I am stumped atm.. :(


If you didn't add piix to the /etc/modules, then I'd suggest entering the boot menu (I have to press Escape at the grub prompt),then press F6 to set the boot options, move to the beginning of the line and add break=top as the first parameter (no idea why it has to be first, but it works so I haven't bothered experimenting too much)

---

### Post by daemon_damodred on 2007-08-24
So how did you get the actual drivers installed?  I hit ctrl-alt-backspace to shut down X server, but that just sends me to the login screen.  If I press ctrl-alt-F1, it sends me to a console.  I tried sudo /etc/init.d/gdm stop, but it still gave me an error saying I need to exit X server first.  I fought with it for about 3 hours before I had to shut it down to go home.  Now its time for round 2.  Would it be easier to install Ubuntu before installing the Nvidia drivers?

---

### Post by AndyQ on 2007-08-25
Well, what I did was to look for the gdm processes and kill them:
ps -deaf | grep gdm
sudo kill -9 <process id>

Then, CTRL-Backspace to kill the X-session when I installed the drivers.

I did have a few issues where when I rebooted - it was loading old modules but I resolved that by renaming all the nvidia modules - but there is a better way of doing that (can't remember which thread its in though).

---

### Post by Aonxe on 2007-08-25
How did you get Compiz Fusion working, I got it all installed easy but I have the no title bar bug, I tried installing emerald but I'm still not getting the title bars.

---

### Post by samb0057 on 2007-08-28
I just got a 1720 and ive had some problems with it. i did get wireless working which was a pain but is now fixed.

I have always been pleased with Dell's hardware choices due to its Ubuntu compatibility (I have installed Ubuntu on numerous Dell machines). But I still have problems which i have no idea how to fix. Internet cuts off and i have to log off or restart to get it back up again, and occasionally (every few days) the screen kind of blanks out, shows a bunch of gray block-like things and i have to restart completely (ctrl-alt-backspace doesn't even work).

---

### Post by sceptre-313 on 2007-09-09
Hey all, first post, so be kind:

Don't know if you all have solved this one, but on the /bin/sh tty job control issue:

If you type in "modprobe piix", then "exit", you system will continue to boot (provided you added "break=top" to the boot string at setup).

Once you place piix into /etc/modules (and /etc/initramfs-tools/modules on my system), the computer will continue to stop at boot time.

REASON:  the Grub boot loader added the "break=top" string to all non recovery boot image lines.

FIX: edit /boot/grub/boot.lst (that's an L!), find all instances of "break=top" (mine had 2, one for kernel 2.6-20-15 and one for kernel 2.6.20-16) and remove them!

save and then next time you reboot, voila, not stopping.

Cheers,

---

### Post by vcallaway on 2007-09-09
I had to edit my boot.lst file as well.

After nearly two months it was nice to get my computer.  It came friday.

After working with it all I can say is it was worth the wait.  The only issue I have left to resolve is sound.  I'm getting sound out the speakers and headphone jack at the same time.

It would really be nice if Dell added the 1720 to the Ubuntu lineup.

---

### Post by ahai on 2007-09-24
this might help as well:

[http://ubuntuforums.org/showthread.php?t=555990](http://ubuntuforums.org/showthread.php?t=555990)

---

### Post by meuge on 2007-09-24
> **AndyQ said:**
> 
After installing the NVidia drivers again, I found an annoying problem where it would keep the new driver after a reboot. Tracked this down to it still having the old drivers around so I cheated and removed them from /lib/linux-restricted-modules/2.6.20-16-generic (renamed all the nvidia folders to nvidia.._ and reinstalled the new driver) which fixed that problem.
Hey.

Sorry to bother you, but I saw that you got the Nvidia drivers working on the 8600M on your 1720 Dell. I have been struggling with trying to get the drivers to work on a 1520 with a 8400M.

The problem is that I cannot actually run the downloaded install program from Nvidia's site (the file with the .run extension). I follow the instructions (sh ... whatever) but then it gives me a message: cannot start (blah). I was hoping you could help me and point out what I am doing wrong with the installation.

I cheated by using Envy to install the drivers... which worked... but now my entire desktop experience is really really slow. It takes a couple of seconds to minimize windows... and many Beryl effects also take SECONDS to work. The entire system seems very very sluggish... compared to a lower power system with ATI as well as Intel. If you've had this problem and solved it, please let me know how.

---

### Post by thomasdersozpaed on 2007-09-26
hello, 
I have this 1720 inspiron and got ubuntu installed with this help. thanks a lot. But now my graphic card  is the problem. (nvidia 8600M GT)
which pakets do I have to install? I installed nvidia-glx-new and changed the driver manually from vesa to nividia und restart. the screen turned to black after a while and I used the recovery mode to change it to vesa again. 
How did you do this:

>  then download and install the latest NVidia drivers which worked straight off.

Booting into X, the sound was recognised, and the wireless lan also worked staright away which was nice. 

Thanks a lot for your help!
greetings
thomas

---

### Post by Skweek on 2007-09-27
thomasdersozpaed, I've just installed a new 1720 - I solved my 8600M driver problem using envy - just download envy and run in graphics mode from your vesa powered desktop. That worked for me anyway.   Envy will fetch the latest nvidia drivers as part of it's job.

Although I have to say that Beryl at least does run slower than my old dell x300 with intel gfx, hopefully this will be fixed by the time gutsy is released.

---

### Post by thomasdersozpaed on 2007-09-27
thanks for this answer. do you know about ubuntu supported drivers for this card? AndyQ solved this problem  on another way. 
do you have any ideas for wlan as well?

---

### Post by dardack on 2007-09-28
Wanted to add a few things that I found that helped me getting my 1720 working, the 8400 nvidia drivers, etc.

As far as the modprobe piix and the changing of th nv to vesa yep.  As far as booting after install i did this, taken from Pumalite in the archives:
> 
After Install do NOT reboot, instead:
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

That worked for booting after install.  I know you said it was DVD, i thought it was SATA drives having issues with the ubuntu installer.  Anyhue.

My sound worked, great.  My mic didn't.  No matter what settings i played around with, nothing out of the mic.  So i upgraded to the development versions of alsa found here:

[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

You want the utils, driver, and lib.  I then followed this guide for installation:

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

However, I only followed the heading for Update to the Latest Version of ALSA, and once i rebooted, mic worked great after increasing the volume of it.

Just wanted to add to this since i had alot of your same issues.

For people having problems with nvidia 8400/8600, install with the VESA driver, and get envy once you've installed.  envy installed the latest and greatest nvidia drivers for me and i had to really not do anything.  I did have to manually edit the xorg.conf file again to add the 1440x900 resolution since envy didn't put it in there originally, but no biggy.

---

### Post by ~takumi~ on 2007-10-02
Hi, I was just about to settle for this laptop, now the XPS 1710 looks like a better choise when it gets to out-of-the-box experience from others...

anyway, the problems described here... has anyone tested if they still apply to the Beta of the next Ubuntu release Gutsy?

---

### Post by AndyQ on 2007-10-07
I tried the livecd of the new Beta. The good news was that it booted straight up into X - no hacking with boot parameters. Sound didn't work but WLan did. Didn't really try much else but suspect that the sound would probably have worked after a full install (but not really willto take a gamble on the beta)

---

### Post by BoomShaka on 2007-10-18
So... whose taking the plunge and heading for gutsy glory on the 1720?

I would have attempted a clean install tonight (wiping my vista and fiesty dual boot setup), except the CD I burnt at work is somehow corrupted... woot.

I may try steal an hour at work tomorrow to see if I can get it running smoothly and post any issues I run into. I guess this warrants a new thread eh?

---

### Post by Mountaineer on 2007-10-19
I've been running Gutsty on my 1720 for about a month now.
There's been a few video and sound related issues, the sound for instance has broken with each and every kernel update bar the latest (finally!).
The graphics are working fine with binary drivers that I installed through the restricted drivers manager.
Still no boot or shutdown splash, just a black screen until I'm at the login screen and vga=791 doesn't work anymore to fix it (I've removed it as at least then I can access tty1-6).
My webcam doesn't work, and it used to under feisty.  Not a big deal for me, just something I noticed.
The biggest bonus is wifi working without any screwing around, not even with restricted binary drivers.  This is with that fancy n-class intel chip.

---

### Post by Mountaineer on 2007-10-19
I've just checked and the webcam DOES work in ekiga and cheese, but not in camorama.
Don't know why, haven't invested any time into it :P

---

### Post by Skweek on 2007-10-19
I'm afraid a clean install of 64bit Gutsy on my 1720 was a no go, I had too many problems getting either the NVIDIA restricted drivers or 100.14.19 from NVIDIA (8600 GT)  to work perfectly.  The sound card wasn't detected, msttcorefonts gave me problems too. (For a while I had no readable font on screen) - and these were just the problems I could see.  On Feisty everything worked perfectly - so it's back to 7.04 for me.  In fact I re-installed 7.04 before I came to work this morning. How effin sad is that?

---

### Post by BoomShaka on 2007-10-19
On a scale of 1 to sad... thats about a 10 :)

Eeuuw, I didn't even know I could install the 64-bit version.
My processor is: Core2 Duo T7300 @ 2.00GHz
I googled it and it seems it is after all... meh. I'll download the 64-bit version and give that a go.

---

### Post by Skweek on 2007-10-19
@boomshaka - I thought the same thing you did, that Core 2 duo was 32 bit - but no it's 64.  I think it's a common misconception.

---

### Post by BoomShaka on 2007-10-30
So. I've been using gutsy for a few weeks now (since its release).
I no longer dual boot vista either, just a clean single gutsy install.

The only issue I am aware of that I have been unable to resolve so far is the black splash screen at startup and shutdown. I have tried suggestions but to no avail. From what I've read I'm led to believe a kernel downgrade will fix it... but I'm not that bothered.

I haven't checked my mic or my webcam yet, but I assume they will require some research to get working.

Anyway, was just wondering what issues other 1720 users are having, and if any of you know of possible solutions for my splash screen issue...

---

### Post by Skweek on 2007-10-30
After my previously disasterous install of Gutsy on my 1720, I downloaded the latest BIOS from Dell (A03), and attempted another clean install of Gutsy amd64 - This time things were much better.  I had sound issues, but these were solved very quickly, and I used the new Envy to install the latest drivers from nvidia. as far as I'm concerned I have no outstanding issues. (My 1720 doesn't come with a webcam).  I am a very happy 1720/Gutsy onwer!

The lack of a splash screen is no big deal really, is it?

---

### Post by BoomShaka on 2007-11-03
So far so good.

My latest issue is: I managed to find what packages I had to install to be able to rip CD > MP3. When I rip the actual CD, it makes quite a loud noise... this I can sort of understand.
But after the ripping is complete, and I have closed sound-juicer, it continues to make this noise. I have to take the CD out of the drive to stop it. Although even if I put it back in, it makes this noise again, only a reboot seems to really fix it...

anyone experiencing a similar issue?

EDIT: lol, it extracted to ogg files.. even though i selected the MP3 profile, and the extension is correct... sigh, why must it be so diffcult to simply rip some MP3s...
sigh.

---

### Post by mmslayer on 2008-01-04
For suspend/hibernation issues on a 1720:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure)

---

### Post by The Resident Expert on 2008-02-05
> **AndyQ said:**
> 
This was fairly obvious why this failed, the default NVidia drivers don't support the 8600M GT, so I changed my xorg.conf to use the vesa driver (change "nv" to "vesa"). This allowed X to start and I could then download and install the latest NVidia drivers which worked straight off.
I've installed wubi Ubuntu after having had read this, but how exactly do I change xorg.conf?  When X chokes to death I get a text window with some of the startup information on it, but whatever I type does nothing.
Do I need to do something before X starts?

> At this point, I wasn't totally confident that a straight install would be possible (although I think it would probably work fine afer more playing) so I decided to install using Wubi (installs a disk image within a Windows filesystem and boots from that - NOT a virtual machine). Wubi uses the aternate image and the install went fine and pretty much everything was detected fine and worked.
Thank you for mentioning this, I hadn't heard of Wubi before, and it really helped, I think.

---

### Post by BoomShaka on 2008-04-25
So... 8.04 is out.
I am keen to do a clean re-install in the next few days but had one or two questions:

1. Do I still need to do some trickery (modprobe malarkey) to do the install or have they sorted that issue out?
2. I have a 64bit architecture, but I am debating if I should rather go with i386, as I seem to recall having issues with java etc on the 64bit architecture.

Anyones comments with regards to hardy on the 1720 are welcomed.

P.S. I didn't want to start a new thread as I thought more 1720 users would see my post in here ;)

---

### Post by szandor on 2008-07-07
> **BoomShaka said:**
> Anyones comments with regards to hardy on the 1720 are welcomed.

i installed the 8.04 alternate iso after getting my second hd carrier from dell. i have 2 250gb drives in raid 0. all the hardware is workable. webcam works with v4l and v4l2 so i can use skype or stickam/tokbox. 3d, compiz, bluetooth, ir remote, etc, etc... pretty much the same results as the m1330. everything is working. one thing that was different was wine. when launching warcraft i had to add -opengl or i would get a memory access error. i was getting about 40+ fps with full settings just running around. not too shabby for a laptop. specs are:

# Ubuntu Alternate 8.04
# Intel Core 2 Duo Processor T7250 (2.0ghz)
# Intel Wireless WiFi Link 4965AGN (802.11a/g/n)
# 2GB PC2-5300 DDR2 SDRAM
# 500GB Total Space (250GB x 2)
# 8x DVD (+/-R double layer) drive
# 17.0" diagonal widescreen TrueLife TFT LCD display at 1920x1200 (WUXGA, Glossy)
# 256MB nVidia GeForce Go 8600M GT
# 2.0 megapixel webcam
# Bluetooth version 2.0 plus Enhanced Data Rate (EDR)
# ExpressCard slot w/Remote Control (ExpressCard/34 and Express Card/54)
# 5-in-1 media card reader

i picked it up during a dell sale last month for $1007, shipped. if you need the second bay carrier/interposer, the parts you need are:

C7586: HD Carrier No. 2 QTY 1
XK231: HD Interposer QTY 1
2864D: Carrier to HD screw QTY 4
63PDH: Carrier to bay screw QTY 3

the bonnie++ results i got are:

szandor,4G,52216,96,58901,21,26976,13,53483,92,61507,19,247.1,1,16,+++++	,++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++

i have the ubuntu satanic edition which looks pretty damn pimp with the display in 1900x1200. here's some basic shots.

[IMG]http://i314.photobucket.com/albums/ll405/szandor420/satanic%20edition/98cab96b.png?t=1215409823[/IMG]

[IMG]http://i314.photobucket.com/albums/ll405/szandor420/satanic%20edition/c7030ed1.png?t=1215409847[/IMG]

[IMG]http://i314.photobucket.com/albums/ll405/szandor420/satanic%20edition/edccf5fa.png?t=1215409590[/IMG]

---

### Post by szandor on 2008-07-07
one problem i have is when i have 2 or more laptops together they interfere with each other and they get disconnected from the access point. alone, they stay connected with no problems but i do leave at least 2 next to each other frequently and after 10 minutes, 2 days, 3 weeks, who knows, the connection may drop. the last image, bottom left shows a script i use with swatch to bring the connection back up if it drops. so now if i'm remote and my wireless drops, i can still get back in remotely.

---


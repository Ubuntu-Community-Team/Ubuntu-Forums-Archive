---
title: "Help! No Video Display with 10.04"
date: 2010-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jbissett on 2010-10-07
I had 7.04 installed on an old Dell Dimension XPS T450 computer. It ran fine. I just upgraded thru mini-ios to 10.04.1. The install went without problems, but after GRUB installed and it told me to remove the CD and reboot, the reboot happened but no monitor display took place. I rebooted several time more with no success. The blue Dell logo displays, then a blinking cursor in the upper left corner of the monitor for a few seconds, then the monitor goes blank. I know the Ubuntu is loading because of the HD activity light, etc.

I apologize that my first thread had a poor title.

---

### Post by P4man on 2010-10-07
Have you tried booting with the nomodeset flag ?

---

### Post by jbissett on 2010-10-07
Thanks for responding.  No, I am a new Ubuntu user trying to learn the system.  How would I do that without having a monitor?

Thanks in advance.

---

### Post by P4man on 2010-10-07
Do you get to see a grub menu or not? If not, hold down the shift key when the Dell bios logo shows. That will bring up grub. To test my solution, select the default boot line (first one) and press E to edit. 

YOu will see something similar to here:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

(note that is for grub1, you have grub2). 

Select the line that starts with "kernel" (it may be split over 2 lines so rather confusing) and press E to edit again. Press END to go to the end of the line that probably ends with "quiet splash" and add just add
```

nomodeset
```

IIRC, to boot with those options press control+X (or whatever it says at the bottom of the screen).

This will change the boot options for 1 boot only. If it solves the problem, Ill explain how to make it permanent.

---

### Post by jbissett on 2010-10-07
I got in by holding down the shift key.  The display looked nothing like you suggested, nor did I see the display on the web page you sent.  However, I did find a line ending with QUICK SPLASH and I added nomodeset.  The system then made me enter my user id and my password.  When the information was finally accepted after 5 tries, I received more command line stuff which at my learning level was not understood.

Not knowing what to do, I used CTRL-ALT-DEL to reboot in order to repeat your instructions.  However, holding down the shift key no longer brings up ?GRUB?.  It does nothing, so I guess I have really screwed things up.  I tried three more reboots, with no joy.

I appreciate your patience.  I never had this much trouble with my old TRS-80 Model I in 1979. :(   :(  :(

---

### Post by P4man on 2010-10-07
OKay, I guess I need some more information now. What exactly did you do to get where you are now? You had a working 7.04, and you upgraded it to "mini-ios" (whats that?) or to 10.04 ? AFAIK, there is no upgrade path that far back, so was this an upgrade or a fresh install? And did you install from a regular ubuntu 10.04(.1) CD/stick or something else? Is this a wubi install (inside windows)  by any chance?

If you installed from a CD, can you boot the CD and run ubuntu normally from the CD ?

BTW, I remember the trs-80. I remember having to hit the 8 inch floppy drive with my fist every hour when it started making a particular noise,  And rebooting (/resetting) resulting in gibberish on screen; if it was vertically stretched, it wouldnt boot and you had try again. And again. And yet again. Then try the rubber gum to clean out the contacts on the cables  until it booted ;)

---

### Post by jbissett on 2010-10-07
I had downloaded 10.04.1 686MB, but lost it when I tried to burn a CD.  A guru friend told me to download mini.ios, which is (as I understand things ) enough parts of 10.04 (or the the same for earlier versions) to allow it to begin the installation process, connect to the net, and then download the rest of the program in pieces as the installation requires.  Everything about the installation went perfectly.  At the end, whatever was necessary about GRUB was then installed, and I was told everything is fine, remove the CD and reboot.  From that point on, once 10.04 started to load, there was no monitor.  I know that it is loading and contacting the internet, based on the hard drive activity light and the lights on my satellite modem.  After a reasonable period, even though I can see nothing, I enter my User ID and Password, and the HD activity light flashes as it finishes up the boot.  My guru friends who are Ubuntu users (but far distant from me) suggested that there is a video card problem, which is when I submitted my help request.  I have the full versions on CD for 7.04 and 8.04, but I would rather not repeat the huge hit on my download limit that this install or full system download will take.

I suspect that I could just reinsert the mini.ios CD and it would eventually get me back to where the shift key will work again.  I would hope that it would recognize that the files are resident in the computer, and just fly through the "re-install".  

Any thoughts on that?

---

### Post by P4man on 2010-10-07
OKay, it was a "mini-iso". This here;
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Downside of that is that you cant just boot to try ubuntu or fix ubuntu like you can with a regular CD, and thats exactly what I would suggest you try now. 

I concur with your friend that your primary trouble was most likely videocard related, and the nomodeset trick I suggested might have solved that. But Im very confused as to not even getting a grub now, and your screen that looked so different as grub. Grub is grub.. ? Are you sure you booted from the harddisk and not from CD?

What to do.. well, you have a 8.04 cd. Can you boot that? With that, you should be able to access your harddrive, and perhaps we can find out what's going on, but reinstalling or fixing grub will be tricky, since 8.04 uses an older version of grub as 10.04 (grub 1 or legacy for 8.04 and grub 2 for the current release).  I think the best use for it now is making sure it boots at all, so we rule out a catastrophic hardware problem. 

Next use for it, is testing your harddrive, because if grub isnt doing *anything*, I suspect there might be a problem there. Install the package "smartmontools" in 8.04 (livecd) and use it to check your harddrive:

```
smartctl -a /dev/sda
```

---

### Post by P4man on 2010-10-07
BTW, if you arent in a hurry, and you are bandwidt constrained, feel free to request a free cd;
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

But delivery can take a while...

---

### Post by jbissett on 2010-10-07
They won't send me a CD.  They claim I have received multiple already, but of course, I have not.  I'll have to have my wife order it.

I don't understand HOW to boot from my 7.04 or 8.04 CDS.  Won't the system just start a new INSTALL the minute it accesses the CD?

---

### Post by jbissett on 2010-10-07
My East Coast guru friend just sent me this from his droid:

Read this:

[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

I guess I'm not alone.  I honestly don't really understand these solutions well enough to try them without guidance.  Plus, the shift key still doesn't bring up GRUB

---

### Post by P4man on 2010-10-07
> **jbissett said:**
> I don't understand HOW to boot from my 7.04 or 8.04 CDS.  Won't the system just start a new INSTALL the minute it accesses the CD?

Not if its a regular livecd. It will boot from the CD in to a full ubuntu desktop without installing anything. Doesnt even require a harddisk. Just a bit slower.  "try ubuntu without installing', its the default option. 

If its an alternate CD or server CD, then that wont work. But it wont install anything without asking you a million questions ;)

As for that link; nothing particular about Dell.  When there are 1.5 million threads in the support forum, some of them are going to be from Dell users ;) Or did you give the wrong link?

---

### Post by jbissett on 2010-10-07
OK.  8.04 is up and running off the CD, and I have good internet connection thru my Hughes Net.

Before we start, would the mini.ios for 10.04 CD have the same functionality?  My guess is no.  Now I'm REALLY sorry I lost the full 686 MB version.  Well, I didn't actually lose it.  The windows CD burner extracted all the files and wrote them to the CD, so "maybe" there is a way......   ???

So what should I do next to get my video back for 10.04?

---

### Post by P4man on 2010-10-07
> **jbissett said:**
> OK.  8.04 is up and running off the CD, and I have good internet connection thru my Hughes Net.

thats a start. Can you access your harddrive? Ubuntu 10.04 uses Ext4 filesystem, Im not entirely sure 8.04 can read it, but I think it can.

> Before we start, would the mini.ios for 10.04 CD have the same functionality?  


no.

> My guess is no.  Now I'm REALLY sorry I lost the full 686 MB version.  Well, I didn't actually lose it.  The windows CD burner extracted all the files and wrote them to the CD, so "maybe" there is a way......   ???


Yeah maybe. If you extracted the ISO then I think all you lost is the bootloader. I could think of a few complicated ways to make it boot, but is it really worth it? 

Anyway, the short version of what I am thinking would be (re)installing grub (grub 2) to your harddisk from 8.04 CD, create a ~700 MB partition to which you copy the extracted 10.04 ISO and point grub to it to boot from it, as if where a CD. Then install from there to another partition. It might work, but it wouldnt be easy.

There might be an easier way to convert your extracted iso to bootable iso again, but I wouldnt know how. Not exactly something I get asked very often :)

> So what should I do next to get my video back for 10.04?

Without working bootloader thats kind of a moot point. Check your harddisk first. See if you can mount it from the livecd, and even if you cant, check for SMART status using smartmontools. Grub isnt perfect, but it doesnt just vanish either.

---

### Post by jbissett on 2010-10-07
I am more than ready to try what you suggest in your very last short paragraph.  However, I'm so new to Ubuntu that I don't have a clue what you are talking about.  Can you point me at a tutorial or something to show me the steps, and the commands that I need to use?

Again, thanks much for your patience with this old fart!!

---

### Post by P4man on 2010-10-08
I cant give you the commands just like that, Id have to do some research first. I think its possible =! knowing by heart. Ill have a look later today, for now you can already boot the 8.04 CD, open a terminal (applications > accessories > terminal) and to avoid typing errors and confusins L's with 1's, copy paste the following commands, and paste the output from the terminal here:

```
sudo fdisk -l
```

That will show all hdd partitions on your system.

```
sudo mount
```

Shows mountpoints. I dont remember if 8.04 auto mounts hdd partitions from the livecd

```
sudo apt-get install grub2
```

This will hopefully install grub2 package (not to your harddrive yet, just in your live environment, doesnt do anything really yet). I just want to see if the repositories for 8.04 are still up and provide grub2.

---

### Post by jbissett on 2010-10-08
Here are the results for the three command line entries you suggested.

sudo fdisk -1

fdisk: invalid option -- 1

Usage:	fdisk [-b SSZ] [-u] DISK	Change partition table
	fdisk -l [-b SSZ] [-u] DISK	List partition table(s)
	fdisk -s PARTITION		Give partition size(s) in blocks
	fdisk -v			Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

sudo mount

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-26-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-26-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

sudo apt-get install grub2

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package grub2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package grub2 has no installation candidate

---

### Post by P4man on 2010-10-08
thats fdisk -l (lowercase L), not 1 (one). I think I warned you for that :p
To paste a command in a terminal, use middle mouse button or press control + shift +v

---

### Post by jbissett on 2010-10-08
Well, I'm dealing with two physically separated computers, so cut and paste is not an option.  :-) :-)

But!!!  I should have seen the obvious problem from the response.  My BAD!!!!!

sudo fdisk -l (that is a small "l")  :-)

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033165

   Device Boot  Start    End    Blocks  Id  System
/dev/sda1   *       1   4728  37970944  83  Linux
/dev/sda2        4728   4866   1108993   5  Extended
/dev/sda5        4728   4866   1108992  82  Linux swap / Solaris

FYI:  This old boat anchor had the HD formatted a year or so ago specifically to experiment with, and to learn Linux 7.04.  I could never get on line thru my ATT Wireless connection, so it sat until now when I changed to Hughes Net.

---

### Post by P4man on 2010-10-08
I thought you could connect to the internet from the livecd? If so, just use firefox on the live session to post here.

Anyway, before starting complicated attempts to recreate the 10.04 livecd, lets try mounting your filesystem. Open a terminal again

```
mkdir /mnt/harddisk
mount /dev/sda1 /mnt/harddisk
```

If that gives no errors, you should be able to use a file manager and browse your harddisk by going to /mnt/harddisk. If so, we can try "chroot" to change root to the installed and now defunct 10.04 and try to revive grub first. Lets first see if the above works though

---

### Post by jbissett on 2010-10-08
I must have bad Karma.

I CAN connect to the Internet from the live CD on the old machine, but I don't yet have a router.  My XP machine is still on my ATT wireless, and I am using it.  I guess I "could" read this forum on the old machine and cut and paste, but up until now this seemed easier.  I am not afraid of the command line, as I grew up with the TRS-80, etc.  I just don't know the syntax of Linux, which is quite different than DOS.  Once I understand what I'm doing and why, I will get better at the command line. :-)

Anyway:

mkdir: cannot create directory '/mnt/harddisk': Permission denied

This is frustrating, no?  I don't understand why I am the only user, yet "Permission denied"

---

### Post by P4man on 2010-10-08
my bad. YOu have to put sudo in front of those commands to execute them as root (administrator). I thought on a livecd you where root anyway, but I was mistaken. You just dont need a password.

so

```
sudo mkdir /mnt/harddisk
sudo mount /dev/sda1 /mnt/harddisk
```

---

### Post by jbissett on 2010-10-08
Again, I SHOULD have known to try sudo.  I just forgot my old training. 

Anyway....

mount: unknown filesystem type 'ext4'

ARGH!!!!

---

### Post by P4man on 2010-10-08
I was afraid of that. Ext4 is the new filesystem, and 8.04 has no support for it. You can mount them as Ext3 if certain features of Ext4 arent used, but I just tried on my own system and failed. You can try, but it most likely wont work:

```
sudo mount -t ext3 /dev/sda1 /mnt/harddisk
```

I guess this is where I suggest you borrow someone else's internet connection to download a more recent ISO. If thats not an option, let me look in to rebuilding the ISO from the extracted files.

---

### Post by jbissett on 2010-10-08
OK.  As you suspected, it failed as well.

As a reminder:

I am now up, running and on line with a live CD of 8.04.

I have a good CD of mini.ios 10.04.1 which is installed on the computer, but the display doesn't come up.

I have a burned CD of the 686MB full version of 10.04.1, but it is not bootable due to my screw up when I burned it to CD.  There may be some way to install it, but I don't know how.  I also suspect that the same video problem would result even if I could install it, based on the other messages I'm seeing of other problems.

My East Coast friend who is unavailable today told me he 'thinks' that my Dell would have an nVidia graphics chip on the motherboard, and that this suggestion from the forum just might work.  Of course, I'm still sketchy on how to try it.  Take a look and let me know if you think it might be worth a try.  It addresses the 'nomodeset' and 'quiet splash' that you suggested in your first responses.

Solution1

I have a HP Pavilion SLimline s7727c

with lspci giving me

VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)

I was getting a blank screen (out of sync) on booting from the live cd.

I worked around the problem as follows:

* At install screen press F6 and select nomodeset and install Ubuntu as usual.
* On first boot after install, press e on getting the GRUB bootloader.
* Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
* Press Ctrl and X to boot
* You should now be able to login to your Ubuntu as usual

For those of you who do not know what to do next, in the taskbar click on System->Administration->Hardware drivers, and select and activate the nvidia current driver if you have an nvidia card like I do. The driver will be downloaded and activated automatically, and you will be prompted for a reboot.

---

### Post by P4man on 2010-10-08
gotta admit, this is an interesting challenge, so I did some more thinking and searching. I see at least 2 things you can try to avoid redownloading

First, use supergrub cd (or floppy) to try and boot your 10.04 again. Its only 1.4Mb and can be found here:

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

The other thing you can try is genisoimage to regenerate the iso.
Im assuming you created a CD that doesnt boot but has all files on it, because the windows app extracted the iso. You could try this magic:

```
sudo apt-get install genisoimage
``` (requires internet connection)

Change directory to where you have those files. Note that you can not eject the ubuntu cdrom if you are in a live session, so use an USB stick or copy it over the network, unless you have 2 cdroms.

```
cd /pathtocdrom_with_ubuntu_10.04_ISO_files
```

```
genisoimage -r -V "ubuntu10.04" -cache-inodes -J -l -b isolinux/isolinux -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o /tmp/cdcopy.iso .

```

Courtesy of :
[http://serverfault.com/questions/112296/regenerate-iso-file-from-running-livecd-dd-wont-run-reliably-and-genisoimage](http://serverfault.com/questions/112296/regenerate-iso-file-from-running-livecd-dd-wont-run-reliably-and-genisoimage)

---

### Post by jbissett on 2010-10-08
I am in catch 22.  I finally found a 1.44 floppy, but either the floppy drive on the old computer is dead, or I don't know how to access it in Ubuntu 8.04.  Shouldn't it be listed in 'Places' ???

My XP computer doesn't have a floppy drive.  I can download to a USB stick, which 8.04 displays in 'Places' and I can see the files on the stick.  If you say I can use the USB stick, then I will need instructions on what to do next.

---

### Post by P4man on 2010-10-08
> **jbissett said:**
> I am in catch 22.  I finally found a 1.44 floppy, but either the floppy drive on the old computer is dead, or I don't know how to access it in Ubuntu 8.04.  Shouldn't it be listed in 'Places' ???

Id think so. Havent used a floppy in nearly a decade though.

> My XP computer doesn't have a floppy drive.  I can download to a USB stick, which 8.04 displays in 'Places' and I can see the files on the stick.  If you say I can use the USB stick, then I will need instructions on what to do next.

Are you talking about supergrub here, or recreating the 10.04 ISO?

If the former, then you need to "burn" the supergrub iso to the USB stick, like you would (and didnt!) with an ubuntu CD. I dont know which version of windows you have, but this tool is universal:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Install it, run it, select "custom ISO" and use that to create the supergrub usb stick. Then configure your problem machine to boot from USB first.

If you wanted to recreate the iso, i dont know for sure where 8.04 mounts usb sticks by default. Probably a subfolder of  /mnt or /media. Just look in nautilus and cd to that directory.

---

### Post by jbissett on 2010-10-08
Thank you so much for your patience and your help.  I downloaded supergrub2 to my XP machine and then downloaded the burner program you suggested.  To me it looks nothing like any burner I've used, so I just punted and did "something" from the supergrub2 download on one stick, and it seems to have 'extracted' a host of files and written them on a second stick.

I have no clue if these extracted files are what I needed to create.

I'm beginning to realize this is probably too complicated for me to do long distance by e-mail, since I am wasting so much of your time.

In any event, I have a stick with 'something' involving supergrub2, but I have no clue what to do next, nor whether it will even work.

Joe

---

### Post by P4man on 2010-10-08
> **jbissett said:**
> Thank you so much for your patience and your help.  I downloaded supergrub2 to my XP machine and then downloaded the burner program you suggested.  To me it looks nothing like any burner I've used, so I just punted and did "something" from the supergrub2 download on one stick, and it seems to have 'extracted' a host of files and written them on a second stick.

I have no clue if these extracted files are what I needed to create.

I think you're making it too hard. In unetbootin, just select the "custom ISO" option (the other options are to generate linux bootable live USB sticks, but they will download those files first). Browse to the supergrub iso you downloaded earlier. At the bottom make sure type is set to USB and your USB stick is selected (or use a CD if you feel like wasting a blank CD for a 1.4 MB image).

> In any event, I have a stick with 'something' involving supergrub2, but I have no clue what to do next, nor whether it will even work.

If you made the stick with unetbootin (important, since just copying files wont work), then plug the stick in the ubuntu computer, and try to boot from it. You may need to configure your bios to boot from USB or press some function key to access a bios boot menu. On most Dells that is F12 I think.

And dont worry about taking anyone's time. No one is forcing me or anyone else to do this ;)
If it werent for others helping me before, I wouldnt be here now either.

---

### Post by jbissett on 2010-10-08
> **P4man said:**
> I think you're making it too hard. In unetbootin, just select the "custom ISO" option (the other options are to generate linux bootable live USB sticks, but they will download those files first). Browse to the supergrub iso you downloaded earlier. At the bottom make sure type is set to USB and your USB stick is selected (or use a CD if you feel like wasting a blank CD for a 1.4 MB image).

My unetbootin does not have a "custom ISO" option anywhere that I can find.  At the top there is a radio button "Distribution" that defaults to checked.  There are only two drop down menus, and "custom ISO" appears nowhere.  I have nowset it to Super Grub disk, which causes the second menu to default to Latest, which is the only option.

At the bottom is a radio button checked with a drop down that has only ISO or floppy, so I set it to ISO and opened the supergrub2 iso file name on stick E as what I believe to be the source.

as Type I selected USB Drive (the other option is Hard Drive) and selected my second stick G:

I now have 183 files extracted on stick G:  The UNetbootin program is telling me to REBOOT, but since I am on my XP computer, I'm simply removing the stick.

After you review this, if you agree, I will put the stick (G:) into the old computer running Ubuntu 8.04 live from the CD.

---

### Post by P4man on 2010-10-08
You're right, its disk image. Or you could use the distribution / supergrub (which will download it for you, I had no idea it was in the list).

Anyway, the idea is now to boot the other computer, but **without** CD. Boot from the USB stick (which contains a specially configured grub) to try and boot the ubuntu installed on your harddisk. If that "works" then we will probably still have at the very least the videocard problem to work out, but we'd be a step closer.

---

### Post by jbissett on 2010-10-08
OK, now I'm confused again.  I CAN boot 10.04.1.  I know it is booting from the HD activity light and the modem access lights.

So if supergrub2 will also only boot up without the display, I'm wondering what we will have accomplished.

Sorry for being a total Nerd, but.....

---

### Post by P4man on 2010-10-08
You didnt even get the grub menu before we used supergrub, so I cant see how ubuntu would have booted. Now we are back to post 1 which was better than post 5. 

I do wonder, did you see any supergrub menu? Are you sure it actually booted from the stick, or does it boot into a "black ubuntu" without stick as well again ? 

Regardless, we need grub menu to edit the boot options (nomodeset is still my best bet) or to try rescue mode.

---

### Post by jbissett on 2010-10-08
I think I am so confused that I am confusing you.  :-(  

Let me start over.  I originally (from a year ago) had 7.04 running on this machine WITH display.  I installed 10.04.1 from the mini.ios cd that I burned.  10.04.1 booted up, but the display failed immediately after the Dell logo.  Everything we have done since then has been to try and find out why the display fails, even though 10.04.1 is actually booting up.

I "think" your original theory about nomodeset, and the quiet splash line was probably right, based on the suggestion from another forum that I included in a previous response in this thread.  I think I just implemented your original instructions wrong because I don't know what I'm doing.

I think that what we ought to do now is for me to remove the live cd which is running 8.04 quite nicely, and reboot (without the grub stick at this attempt) and try setting the nomodeset that was discussed in that other suggestion.  I think the sequence or something was slightly different than what I did after your instructions.  It's been too long ago for my addled brain.

To do that, I would need your specific guidance on what I need to do after I do CTRL-ALT-DEL in order to be able to bring up a proper screen in order to change or modify or whatever to nomodeset and quiet splash.

Once the start up moves along into the actual 10.04.1 boot after the Dell logo disappears, I will have no display, so I guess I have to be quick if we try this.

Clear as mud?  Maybe you need to fire me.  :-(

---

### Post by P4man on 2010-10-08
Okay, so maybe I misunderstood this phrase: 'However, holding down the shift key no longer brings up ?GRUB?. It does nothing, so I guess I have really screwed things up. I tried three more reboots, with no joy."

I thought you couldnt get in to grub anymore, even pressing the shift key. What I let you do, editing the kernel parameters in grub and add the nomodeset, is only valid for a single boot. Upon rebooting it will revert back to default settings. So if subsequent boots, even when holding the shift key did not produce a grub menu, then something seriously get messed up. I take it now I misunderstood that, and you can still bring up grub without cd or stick, by holding down shift during and after the Dell bios logo?

If so, then try it again. If you dont get a grub screen that roughly matches the links I provided, then if you can, take a camera and make pics or describe the screens as good as you can. 

BTW, you're fired ;)

---

### Post by jbissett on 2010-10-08
OK.  Holding down the shift key brings up the BIOS menu which I can use to change the boot order.  This is DIFFERENT than what happened the very first time I did it following your initial suggestion.  That time the GRUB menu came up, but somehow I screwed things up and after that ONE time, the shift key produced NOTHING, until just now.  I also tried the F6 key, but it did nothing.

I am tempted to try a re-boot of mini.ios, and if that doesn't once again at least make the shift key do what it's supposed to do, then how about this?  I INSTALL 8.04, which should at least produce a working Ubuntu machine.  Perhaps from that point the shift key will bring up the GRUB menu and we can proceed.

And now I finally know who you are from your last sentence in your last response.  "You're fired".



p4man = Donald Trump

---

### Post by P4man on 2010-10-09
> **jbissett said:**
> OK.  Holding down the shift key brings up the BIOS menu which I can use to change the boot order. 

?? Ive never seen a machine were shift key enters the BIOS. Are you positive about this? If this is true then you will have to time your shift key really well, press it right after the bios logo dissappears.

Do it too early and you get in tot the bios, do it too late and grub will have finished. Maybe this is the real problem?

> I am tempted to try a re-boot of mini.ios, and if that doesn't once again at least make the shift key do what it's supposed to do, then how about this?  


Shift key shows a menu for grub. THat has nothing to do with the BIOS. Grub is the linux bootloader that sits on your harddrive. Its like NT loader for windows, showing a menu if you have more than one windows installed. Now if you boot off the mini iso, you wouldnt be loading grub, whatever shift key does or doesnt do will depend on the bootloader of that iso and doesnt matter. You dont want to installthe mini iso again, because it will download everything and still not give you a bootable 10.04 livecd. If you are going to download, download the 10.04 iso again.

> 
I INSTALL 8.04, which should at least produce a working Ubuntu machine.  Perhaps from that point the shift key will bring up the GRUB menu and we can proceed.

Well installing 8.04 sounds tempting, but here is the problem: its bootloader cant boot your 10.04 install. Ext4 remember? It wont help us more than booting the liveCD

You could install 8.04 and then upgrade it to 10.04, but this isnt recommended and pointless since it will download 600+ MB again. Might as well grab the iso

Anyway, at this point, Id make sure you are rpessing shift at the right moment. I suspect its just your timing thats preventing us from changing boot options. Wait until the right after the bios logo screen disappears. 

If you really cant get in to grub on the harddisk, then  try the supergrub stick again. I havent seen that you actually managed to boot from it. It should look this:
[http://www.supergrubdisk.org/w/images/7/78/SG2D_1.98s1_main_menu.png](http://www.supergrubdisk.org/w/images/7/78/SG2D_1.98s1_main_menu.png)

Quite similar to a normal grub menu but with very different options.

> p4man = Donald Trump

Na, aside from the wealth, Im nothing like him. 
;)

---

### Post by jbissett on 2010-10-09
> **P4man said:**
> Do it too early and you get in tot the bios, do it too late and grub will have finished. Maybe this is the real problem?

Timing is everything.  That worked!!!  I was holding down the shift key way too early.

> **P4man said:**
> If you really cant get in to grub on the harddisk, then  try the supergrub stick again. I havent seen that you actually managed to boot from it. It should look this:
[http://www.supergrubdisk.org/w/images/7/78/SG2D_1.98s1_main_menu.png](http://www.supergrubdisk.org/w/images/7/78/SG2D_1.98s1_main_menu.png)

Quite similar to a normal grub menu but with very different options.

While I was waiting for your next epistle, I tried the GRUB stick.  I changed the load sequence, but when I rebooted, nothing happened.  I'm sure since I was seeing a different menu in the burner that I did not burn it correctly.

Right now I am sitting here looking at:

GNU GRUB version 1.98-1ubuntu7

That "looks" to me like it is the GRUB from my ORIGINAL installation of 7.04.  That seems strange to me, because I distinctly remember seeing a GRUB installation right after 10.04 finished loading, and before I was informed that the installation was complete and that I needed to reboot.

What should I do next?



> **P4man said:**
> Na, aside from the wealth, Im nothing like him. 
;)

No hair, huh?

---

### Post by P4man on 2010-10-09
Slowly we are getting somewhere heh. Grub from ubuntu 7.04 doesnt look very different from grub in current releases. At the top you will probably see a more recent version, it should be 1.97 or something (edit, you already wrote its 1.98. That is, believe it or not, grub2 and part of ubuntu 10.04).

Among the options, do you see a recovery mode? If so, what happens when you select it. If recovery doesnt work, pick the first regular ubuntu kernel (most likely the top item in your list, if in doubt, type the kernel version here) and try the nomodeset trick again.

---

### Post by jbissett on 2010-10-09
SUCCESS !!!

I ran recovery, then rebooted, then went back in and deleted SPLASH QUIET and replace it with nomodeset.

Ubuntu 10.04.1 LTS ubuntu tty1

I had to log in, and it tells me my last login was Oct 7, which was when I installed 10.04.1.

I am now sitting at the command line prompt, and have no clue what to do next.

---

### Post by P4man on 2010-10-09
Thats hardly success, since you still dont have a GUI. 

Did you add the nomodeset to the recovery option, or to the regular kernel line? Im guessing you did it to the recovery option, and if so, now try with the regular kernel entry (top one I assume). 

BTW, to reboot, just type

> sudo reboot

BTW bis, I never said to remove "quiet and splash" but its not a bad idea to remove them so the boot becomes a little more verbose (no gui splash and lots of on screen messages during boot which may help if it still fails).

---

### Post by jbissett on 2010-10-09
No, I ran recovery, then rebooted, then selected the first option and made the edit.

I deleted the SPLASH QUIET because that's what it said to do in the tip specifically for 10.04.1 that I included in a reply to you a while ago.  When I first tried it with you, I didn't delete it, and it didn't work, so I said to myself "what the heck?" and I tried it.

I see what you mean about the commands showing on screen.  I guess I can always add it back.

I ran sudo reboot.  SIGH...  HEAVY SIGH.... still no GUI

---

### Post by jbissett on 2010-10-09
BTW, here's what the tip said to do to finish the job.  I left it off.  I don't know Linux, but this makes some sense to me, as it sure seems the proper driver is not loading.

For those of you who do not know what to do next, in the taskbar click on System->Administration->Hardware drivers, and select and activate the nvidia current driver  if you have an nvidia card like I do. The driver will be downloaded and activated automatically, and you will be prompted for a reboot.

---

### Post by P4man on 2010-10-09
Its weird that it would boot in to a terminal with no error message. You didnt accidentally install ubuntu server version did you?

Lets see what happens when you try to start the gui. Just type:

```
sudo startx
```

or

```
sudo service gdm start
```

If it says something about X already running, try hitting control+alt+F7 or control+alt+f8. If you get a different error, please report back.

---

### Post by jbissett on 2010-10-09
ARGH!!  Back to square one.

I rebooted CTRL-ALT-DEL in order to do the next step you suggested.

The computer hung up in the middle of a long list of command echos to the screen.  I had to do a hard power off to get past it. It was weird because the Caps Lock and Scroll Lock keyboard lights were blinking during the hang up.

In any event, after several tries, I got a reboot (without display of anything after the Dell logo), so we seem to be back where we started.

This is frustrating.

---

### Post by P4man on 2010-10-09
Blinking lights = kernel panic. And thats definitely not good. It could be a hardware problem. It could be an incompatibility between the kernel and your machine. Kernel panics are trouble :(

Also, rather than using control alt delete, use  "sudo reboot". If that fails, reboot the machine using REISUB:
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

That at least will not cause even more damage, whereas a hard reset can.

Anyway, im not quite sure where we are now. Remember the nomodeset only works for a single boot. You need to redo it every time you restart. Can you still boot to grub and in to a terminal now? If so, did sudo startx do anything?

---

### Post by jbissett on 2010-10-09
Did another recovery, then stumbled along and finally got to the 10.04.1 command line (after getting a Recovery Menu in color).

startx is currently not installed.  It tells me how to install it.  I'm guessing I SHOULD install it, then try it, right?

BTW, unless I go thru GRUB, I can never see enough to bring up a command line to do the other things you are suggesting.  For some reason the reset button on the computer does nothing, so it's either CTRL-ALT-DEL or a hard power down. 

And yes, since I am such a newbie, I forgot that I have to go into GRUB each time and re-enter nomodeset.  But why was the deletion of SPLASH QUIET permanent?  It was not there this time.

---

### Post by P4man on 2010-10-09
> **jbissett said:**
> Did another recovery, then stumbled along and finally got to the 10.04.1 command line (after getting a Recovery Menu in color).

startx is currently not installed.  It tells me how to install it.  I'm guessing I SHOULD install it, then try it, right? 

Not installed.. so you did a server install it seems. Yes you can install X and a GNOME desktop on top of that, but the download will be huge.

```
sudo apt-get install ubuntu-desktop
```

It will tell you how big the download is, up to you if you want to do it, or if you would rather download the ISO that you can use to both test and install and troubleshoot.
> 
BTW, unless I go thru GRUB, I can never see enough to bring up a command line to do the other things you are suggesting. 

Thats normal. If you want to make the nomodeset option permanent, try this:

```
sudo nano /etc/default/grub
```

That will bring up a configuration file in a Dos style editor. Near the top you will see this line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Should look familiar. Change it to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

Feel free to remove quiet and splash as well. Then save the file with control+X and Y and enter. 

Now update your grub:

```
sudo update-grub
```

And thats it. Nomodeset should be default now.


>  For some reason the reset button on the computer does nothing, so it's either CTRL-ALT-DEL or a hard power down. 

Do try the REISUB trick. It almost always works. Even if nothing seems to be happening.

>  And yes, since I am such a newbie, I forgot that I have to go into GRUB each time and re-enter nomodeset.  But why was the deletion of SPLASH QUIET permanent?  It was not there this time.

Shouldnt be permanent. But they are never there for the recovery mode I think.

---

### Post by jbissett on 2010-10-09
While I was waiting I went ahead and installed startx (75MB - you were right).  startx brings up a small white screen at the top left of the display, with a command line.  I can't seem to make anything work from this startx command line.  I can't reboot, etc.  CTRL-ALT-DEL doesn't even work, so hard shut down was my only option.  To be safe, I did a recovery, then re-did the nomodeset, and tried sudo service gdm start .  That wasn't allowed, or something like that.

Please explain a little better the REISUB.  Can I just enter it no matter where I am?  I tried it from the command line in the white startx screen, but nothing happened.

Nest I will install the GNOME desktop as you suggested.  What will that do for me?

Are we going to try to install the nVidia graphics driver like that other suggestion said?

---

### Post by P4man on 2010-10-09
> **jbissett said:**
> While I was waiting I went ahead and installed startx (75MB - you were right). 

I have no idea what startx would do without a desktop environment like gnome. You need a full desktop environmnent to have an actual gui. Install ubuntu-desktop package for gnome and all its dependencies. 

But again, I feel you are wasting bandwidth. It would be so much better to have the ISO so you can test the  distro on your hardware, install on several machines, reinstall, troubleshoot etc. But its your call.

> Please explain a little better the REISUB.  Can I just enter it no matter where I am?  I tried it from the command line in the white startx screen, but nothing happened.


Read the link carefully:
> Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB 
> 
Nest I will install the GNOME desktop as you suggested.  What will that do for me?

At least have a chance to get a GUI :)

> Are we going to try to install the nVidia graphics driver like that other suggestion said?

You dont need any drivers if you dont have a gui :) 
By default, 10.04 includes basic opensource drivers for both ati and nvidia. These are good enough for most. Of course feel free to install the proprietary drivers, but depending how old your hardware is, there may no longer be support for it from ati or nvidia, and thus there may not be any other drivers to install. What videocard do you have?

---

### Post by P4man on 2010-10-09
oh and one more thing. YOu seem to mistunderstand the recovery mode. It doesnt do anything other than boot into a root terminal (where a normal boot on a fully installed ubuntu will boot into a GUI). There is no point booting it if you arent going to do anything in that terminal. It doesnt fix anything by itself.

---

### Post by jbissett on 2010-10-09
Sorry, I've been out burning brush. This 400+MB Ubuntu Desktop just finished downloading, and it just started extracting, so I'm in for another wait.

Somehow I missed the part about holding down the ALT and SysRq keys while typing REISUB.  Sorry again for being such a nerd.

Yes I did misunderstand recovery mode.  I won't need to waste time with it again.

Are you thinking that once this ubuntu-desktop is fully installed that I will probably have a GUI?  If so, I wonder why it didn't download and install in the original effort.

I have no clue what graphics driver card I have.  I got this old Dell computer from my son-in-law, and only turned it on to play with and learn Ubuntu.  Perhaps when I next boot up I'll try looking at the BIOS stuff.  Maybe it will tell me.  If not, I have no clue how to find that out on a Linux machine.  Any instructions?

---

### Post by P4man on 2010-10-09
> **jbissett said:**
> Sorry, I've been out burning brush. This 400+MB Ubuntu Desktop just finished downloading, and it just started extracting, so I'm in for another wait.

I hope you wont regret that. 200MB more and you would have had a bootable and installable CD :S. Dont blame me if it turns out the machine is beyond redemption.


> Are you thinking that once this ubuntu-desktop is fully installed that I will probably have a GUI?  If so, I wonder why it didn't download and install in the original effort.

Iv never used the minimal iso. I dont know what it installs by default, but I suspect you accidentally installled ubuntu server. Which has no GUI.

> I have no clue what graphics driver card I have.  I got this old Dell computer from my son-in-law, and only turned it on to play with and learn Ubuntu.  Perhaps when I next boot up I'll try looking at the BIOS stuff.  Maybe it will tell me.  If not, I have no clue how to find that out on a Linux machine.  Any instructions?

```
lspci
```

Look for "VGA" in that list to see the videocard, or have ubuntu do it for you:

```
lspci | grep "VGA"
```

Thats a pipe symbol and remember everything is case sensitive.

edit: dont forget to insert the nomodeset in the grub config file. You will probably need it for the gui.

---

### Post by P4man on 2010-10-09
OH wait. I should have googled your machine type earlier. Thats to be frank, prehistoric. Forget about proprietary videodrivers, and Im really worried its just too old for any recent linux. Default specs include 64 MB ram. To run ubuntu you need about 10x that much. Lets hope it got upgraded. Ubuntu 10.04 *might* work with 256Mb. Maybe. Oh dear.

---

### Post by P4man on 2010-10-09
Ill be out for a while. Let me just tell you a few more things.
IN a terminal type

```
free
```

to see how much memory you have. Here is mine:
```

bob@bob-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       **4056200**    1653184    2403016          0     162364     708740
-/+ buffers/cache:     782080    3274120
Swap:      9136124          0    9136124
```

I have 4 gigs of RAM (4million bytes or is that kbytes lol). If you have less than 128000 there, then forget ubuntu 10.04. If you have 256000, then *maybe*. If you have 512000 or more, that is 512MB, you should be okay. If you dont have enough, you really need another computer or use lightweight distro like lubuntu:

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

or slitaz, puppylinux, .. but not a full blown ubuntu.
Im sorry :S

---

### Post by jbissett on 2010-10-09
> **P4man said:**
> I hope you wont regret that. 200MB more and you would have had a bootable and installable CD :S. Dont blame me if it turns out the machine is beyond redemption.

No problem.  This is a learning experience for me.  Over my last 72 years, this is not the first time I've screwed up. :-)  


Iv never used the minimal iso. I dont know what it installs by default, but I suspect you accidentally installled ubuntu server. Which has no GUI.

I'm really pretty sure that I did not install the server version.  I saw the different files for download, and even at my newbie status, I knew I didn't want the server version.  Now - it is always possible that when I clicked the link that I somehow moved the cursor and caught the server link.....  However, since many others seem to be having this 'no display' problem with 10.04.1, I suspect that I'm just another one of those folks.



```
lspci
```

Look for "VGA" in that list to see the videocard, or have ubuntu do it for you:

```
lspci | grep "VGA"
```

Thats a pipe symbol and remember everything is case sensitive.

edit: dont forget to insert the nomodeset in the grub config file. You will probably need it for the gui.

OK. The machine is still setting up the desktop.

---

### Post by jbissett on 2010-10-09
Hey P4man!!!

This reply is coming from my 10.04.1 machine with what appears to be a full up GUI.

Once again I really thank you for your patience, and for sticking with this old fart nerd through 50+ messages.

I guess I will now make nomodeset permanent per your instructions.

Since I can't seem to remember what you tell me very well, do you have any final suggestions?  (Watch it!!!  This is a family oriented forum!!  :-)  )

---

### Post by P4man on 2010-10-09
Wow, impressive. On a 1998 PC. Barely more modern than that TRS80 ;) Frankly I didnt have much hope. Looks like your son in law stuffed the old box with ram, so how much does it have? It cant be a very pleasant experience though. Just to give you an idea, installing a desktop environment takes about 1 minute on a modern machine. If that much.

Anyway, I dont have any "last words", Im sure you'll be back with more questions. You got it installed, its only now that it really begins ;)

---

### Post by jbissett on 2010-10-09
> **P4man said:**
> Wow, impressive. On a 1998 PC. Barely more modern than that TRS80 ;) Frankly I didnt have much hope. Looks like your son in law stuffed the old box with ram, so how much does it have? It cant be a very pleasant experience though. Just to give you an idea, installing a desktop environment takes about 1 minute on a modern machine. If that much.

Hey with two great minds working the problem, how could we fail?  The RAM is 384K.  The HD is 40 GB, and with everything loaded, I have 93% left.

Anyway, I dont have any "last words", Im sure you'll be back with more questions. You got it installed, its only now that it really begins ;)

Yep.  First annoyance.  Every time the computer decides to go to sleep and save my ancient monitor, I have to enter my password to get back in.  Since this machine won't be used for anything serious, I don't need the security like this.  Any idea how to turn it off?  Actually, there is no need to ever have to enter a password, as far as THIS machine is concerned.

Once I play around and learn a little bit, I will partition the HD on my Dell Inspiron (200+ GB) and install 10.04.1 on the new partition.

---

### Post by P4man on 2010-10-09
> **jbissett said:**
> Yep.  First annoyance.  Every time the computer decides to go to sleep and save my ancient monitor, I have to enter my password to get back in.  Since this machine won't be used for anything serious, I don't need the security like this.  Any idea how to turn it off? 

Sure, go to system > preferences > screensaver. Deselect the "lock screen" option.

>  Actually, there is no need to ever have to enter a password, as far as THIS machine is concerned.


Oh yes there is. You are not the only user using the computer. You are connected to a billion other internet users, not all of whom you want to trust. You do need basic security, that includes password. I dont want your machine to be turned in to another botnet computer sending spam to my email account. 

Now you may not want to have to enter a password to log in locally (using your keyboard and mouse, so not remotely over the internet), that you can change too. System > administration > log in window. Unlock the dialogue, and configure your user to log in automatically.

BTW, since you are doing this to learn, may I point you to the absolutely excellent ubuntu manual project:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by jonas ananda on 2010-10-15
> **jbissett said:**
> They won't send me a CD. They claim I have received multiple already, but of course, I have not. I'll have to have my wife order it.
 
I don't understand HOW to boot from my 7.04 or 8.04 CDS. Won't the system just start a new INSTALL the minute it accesses the CD?
No, it will give you the option to either try ubuntu without makig any changes to your system or to install it.

---


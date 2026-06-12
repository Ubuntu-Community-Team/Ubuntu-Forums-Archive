---
title: "Can not boot to windows without external hard drive attached"
date: 2009-05-31
forum: General Help
---

### Post by ladydonna on 2009-05-31
[SIZE=5]Hello, I was working with Reevine a while back on my problem. I have an Hp Pavillion DV 1000 series laptop with Windows XP Home on it with a  100gb hd in it. I also have a 650 gb external hard drive which plugs into one of my USB ports. If I don't have the external hard drive plugged in I get the following   "loading stage 1. stage 1.5 grub,  error 21.  if I plug the USB Hard Drive in and reboot, it goes to a grub menu showing ubuntu  3 diff entries then windows xp home at the bottom. If I select windows by scrolling down to it and press enter it will boot into windows properly. BUT the external hard drive must be connected. I want to be able to leave the external hard drive unconnected and boot into windows or Ubuntu, which I later installed on the hard drive in my laptop without the external hard drive connected, hoping this would correct the problem.  It didn't  I am posting below that shows up when I typed into the terminal the following, which I got from another post in the forum.   >gksudo gedit /boot/grub/menu.lst.   Then this is what opened up in menu.lst

default 0
timeout 10

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=31d86eaf-586d-4d6b-a6f4-ee17d37b48ca ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=31d86eaf-586d-4d6b-a6f4-ee17d37b48ca

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=31d86eaf-586d-4d6b-a6f4-ee17d37b48ca ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=31d86eaf-586d-4d6b-a6f4-ee17d37b48ca ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Home Edition
root (hd0,0)
chainloader +1
savedefault
makeactive

title Other operating systems:
root

Can anyone help me change a setting to the correct setting to boot to the grub loader that will appear if the error message is gone, which shows up after booting with the external hard drive connected which show windows xp and ubuntu that began appearing after I installed Ubuntu on my internal hard drive in hopes of correcting this problem the other day, which as I said did not correct the problem I am having.  Please, anyone who can interperate the above code and can advise me what to change or do to correct this load (boot up) problem would be greatly appreciated

[/SIZE]

---

### Post by logos34 on 2009-05-31
disconnect the external drive, and follow the instructions in the link below in my sig ("restore grub").

And use smaller font next--no need to "yell"

---

### Post by ladydonna on 2009-05-31
[SIZE=3]Sorry, I didn't know I was yelling.  Is this size ok for normal use? Please don't assume I know what you mean by go to below. I am very new at Ubuntu and have no Linux experience, that is how I got into this mess to begin with. I do appreciate help, any help from Ubuntu users. Those that can guide me through a problem. I happen to love Ubuntu, and wished I had known a long time ago about it, I would have dumped windows about a hundred crashes and problems long ago., but until I learn something I can not make an immediate change. I do learn fast, and am willing to follow any helpful instructions. If you can and want to help me I would appreciate it, but again do not assume I know what you are talking about,  I thank you for your response and for your telling me I was shouting, the print was to small so I increased it, but I increased it to much.  Thank you again, and any help will be greatly appreciated, by anyone.  :D[/SIZE]

---

### Post by merlinus on 2009-05-31
Here is the link for reinstalling grub after disconnecting your external drive:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Jameshardy88 on 2009-05-31
I have had the exact same issue before, the problem is that your grub menu is stored on your external hard drive which is what the computer looks for when it boots. Get yourself a live cd and follow the instructions given above to reinstall the grub menu onto your internal HD (don't worry its not as scary as it sounds)

Good luck,
James

---

### Post by ladydonna on 2009-05-31
[SIZE=3]Hello James and Logos34,  Thank you for your response. I just got home from Church and coffee. Should I go to Windows and correct this problem or should I do it from Ubuntu in the external Hard drive? I did go to the terminal here in Ubuntu on my external hard drive and ran the code with the cable plugged in. It came up with the following. 

-laptop:~$ >sudo grub
Probing devices to guess BIOS drives. This may take a long time.
I then closed the terminal and opened it again and entered the grub and this is what I came up with,

grub> find /boot/grub/stage1
 (hd1,4)

grub> root (hd1,4)

grub> root (hd1.4)

Error 11: Unrecognized device string

grub> root (hd1,4)

grub> setup (hd1,4)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,4)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,4)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,4) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.



When I tried to do as it instructed  the terminal window read Drive does not exist. I have my Ubuntu desktop edition cd from Canonical. Is that the live cd or do I need to download it from somewhere? If I have the proper cd now, do I just insert it? will it go to the proper boot? I did install it to windows (Without changes to windows) but that did not work, as I said in my post above. It seems the only way I can get to Ubuntu terminal is in the external drive and when it is disconnected it disconnects me from the internet. Please advise. I will be up for a while yet tonight, but if no one responds I will wait until tomorrow then begin again. I do appreciate the help.:D.   [/SIZE]

---

### Post by logos34 on 2009-06-01
> **ladydonna said:**
> When I tried to do as it instructed  the terminal window read Drive does not exist. I have my Ubuntu desktop edition cd from Canonical. Is that the live cd or do I need to download it from somewhere? If I have the proper cd now, do I just insert it? will it go to the proper boot? I did install it to windows (Without changes to windows) but that did not work, as I said in my post above. It seems the only way I can get to Ubuntu terminal is in the external drive and when it is disconnected it disconnects me from the internet.

Sounds like you did a Wubi install the second time (runs ubuntu *inside* your XP partition), which is why the grub restore method didn't work.

Yes, the shipit CD from Canonical = live cd.

What I would suggest it this: since you appeared to (re)install grub successfully to the MBR of the external drive, reboot and go into your computer Bios at startup (press **F1** key I think), look for a boot menu and change the hard disk boot priority from the internal to the usb drive.  If it boots ubuntu, then all you have to do is restore XP bootloader to the internal disk, [like this]("http://ubuntuforums.org/showpost.php?p=4691608&postcount=2"). Or download the Super Grub Disk (--> **[Advanced]("http://www.supergrubdisk.org/wiki/UninstallGRUB")**).  From now on, all you have to do to boot windows is choose it from the grub menu.  If the usb drive is disconnected you'll boot straight into windows.  No more error message.

If by "did not work" above you meant that ubuntu did not even install in wubi mode, then there;s nothing more to do.  If it did appear to install but won't boot you'll obviously have to [remove]("http://wubi-installer.org/faq.php#use") it.

About the usb drive problem: when you install ubuntu on an external drive, the Grub bootloader is written by default to the MBR of the first detected drive, '(hd0)', which is always the laptop internal drive.  This means that even though the grub IPL (initial program loader) is on the internal, when you boot it looks for menu.lst (grub menu), which resides on the ubuntu root partition on the *external* drive.  So if it's disconnected, you get a grub error.  I don't know why the developers have never figured out a way to prevent this, because it causes a lot of confusion.  A lot of people now boot, or would like to boot, linux from a external usb disk...seems nearly everybody has one these days.

---

### Post by ladydonna on 2009-06-01
Thank You Logos34.  I appreciate you definitive post.  I will try that. But let me add, I think I understand what you are suggesting, but I do not need to go to the Bios to load the USB port, as,  If the external drive is plugged in I can boot to the external grub menu which gives me the choice of selecting Ubuntu or Windows. when I make the selection, another menu appears, letting me again choose Ubuntu or Windows. If the drive is unplugged, all I get is the Error 21 in black screen. If I understand you, you want me to unplug the USB external drive and then go to my Bios and set it to boot to the USB drive? I have not gone to the Bios yet today, but will as soon as I send this post. But in previous visits to the Bios, I think it only gives me the choice of my Hard drive, an A drive, Which this laptop does not have, or to the CD/Dvd drive. No option to boot from a USB port.  Again, I really appreciate you posting in such an easy to understand wording and instructions to me.  I think you are on the right track to solving my problem, yes I did install Ubuntu on my internal hard drive using the option to install inside Windows with no changes to my system. Should I uninstall it? It wont open anyway from inside windows or in the initial boot up, as it only goes to the Error code 21 if the external is unplugged, as I said.  I will await your reply and am now going to try as you suggest in your previous reply..  Thank You, Donna

---

### Post by ladydonna on 2009-06-01
Hi  I went to the bootloader, link you gave me. It says using live cd open a terminal. The only way I know to open the terminal in within the installed Ubuntu on the external hard drive, whic I simply follow the same instructions it gives in the link with the exception of using live cd. I guess I just don't know how to use the live cd, when I put it in, it asks for the language then gives me options like install it or chec the cd for erroes etc, how do I access the terminal from live cd?.  Thanks again Logos34,   Respectfully, Donna..:)

---

### Post by logos34 on 2009-06-01
To get to a terminal on the live cd you need to load the desktop.  Select the first option "Try ubuntu without any change to your computer". Then Applications>Accessories>terminal

As far as the Bios and usb goes, you're looking at the *device* boot priority (floppy, hdd, cdrom)...there's a separate *hard disk* boot menu (or submenu) which allows you to select another boot disk from among multiple hard drives.  Poke around (check 'boot' tab first).

The reason it seems to be automatically booting directly to the external is that, like I said above, grub is in two parts--one (tiny) part is on the MBR (first sector) of the internal disk, the other part (menu.lst, stage2 etc,) is on the root partition on the usb.  So when you start your machine the bios looks for a bootable drive, finds the internal drive sda, then grub looks for the menu.lst and stage1 on the / partition.  

I don't know why it's going through two menus, though.  

Leave the usb attached. (I originally suggested you unplug it to simplify restoring grub.  But that's before I knew you did a wubu install).

---

### Post by ladydonna on 2009-06-01
Hello again Logo34   Well, I tried what the link told me to do. This was the result.  

E Could not open lock file

/var/lib/apt/lists lock-open (12 permission denied

E  unable to lock the list directory.

bash -p command not found.  

I tried several ways typing it in with and without sudo with and without the ( > ) 
and so on.  I shut the computer down and then ran the live cd to install Ubuntu  without changes onto the internal hard drive, I left the USB  drive (E) plugged in and then opened the terminal and followed the instructions exactly as it ask in the link you provided  ( How to restore XP and Vista Bootloader & restoring GRUB.   Also, now I don't seem to be able to eject the Ubuntu live cd from my cd drive. It keeps poping up, there it is again. open the large Ubuntu files and when I close that window another one pops up telling me I just inserted a video dvd, which I did not. Just the Ubuntu cd which has been in the drive since I started this fix.  Please let me know what I need to do next and how to open the cd drive to get the cd out. That popup window is driving me crazy...Please Advise.  Thank you  Logos34.

---

### Post by logos34 on 2009-06-01
hope all this trouble doesn't turn you off ubuntu...a lot of it shouldn't be happening.

the cd: nautilus file browser>edit>preferences>media tab. Check '**Never prompt.**..' box.

You shouldn't need this, but just in case, install **eject**, which allows you to override the OS controls:

sudo apt-get install eject

To open cd:

eject

to close:

eject -t

Also, remember that if you've changed directory into /media/cdrom0 or whatever, the drive will remain locked until you exit.

If all else fails, straighten out a large paper clip and stick it in the tiny hole on the front of the cd/dvd drive to manually eject the disc

You shouldn't have had to reinstall ubuntu on the internal. Did you find out how to change the bios to boot the usb directly?

---

### Post by ladydonna on 2009-06-01
I was in Ubuntu live cd terminal and tried what was suggested. It did not work. I posted from within Ubuntu, but I don't see the post here.

---

### Post by ladydonna on 2009-06-01
I did get the cd out, but had to shut down the machine and restart. I am now back i windows. I tried everything I could following the instructions and what I posted was what happened. I can not get to a boot menu, as it immediately goes to Error 21 instead of the boot menu.  I am one that has patients and do not easily get discouraged. I appreciate your help and am not going to get turned off by this little problem. Yes, I know it seems like a big problem, but I am sure there is an answer to this and if you stay with me, I'll stay with you and together we will get this problem worked out. I am willing to do what it takes to get this solved. So if you will continue working with me I will try each step you suggest until we git it solved.  Thanks again Logos34.  Whats next??:D

---

### Post by logos34 on 2009-06-01
ok, I'm checking for your Bios manual at HP...be back

---

### Post by logos34 on 2009-06-01
so, in the Bios you checked under >**Advanced Menu**>Boot Order?  The DV 1000 manual says:

> "Enable/disable MultiBoot, which sets a startup sequence that can include most bootable devices and media in the system"

> "Configuring the Boot Order"
[http://h10025.www1.hp.com/ewfrf/wc/fastFaqLiteDocument?lc=en&cc=us&product=18703&dlc=en&docname=c00364979](http://h10025.www1.hp.com/ewfrf/wc/fastFaqLiteDocument?lc=en&cc=us&product=18703&dlc=en&docname=c00364979)

You are able to boot usb (otherwise you wouldn't be running ubuntu), so there's got to be a menu in there that allows you to specify a bootable hard disk or USB

If we can just configure it that way, then we can worry about windows boot on the internal (for the time being at least you can still boot into it from grub).

---

### Post by ladydonna on 2009-06-01
Ok  I,m going to reboot and change the boot order, but what do you want me to do then. Like you said I cah boot to the USB drive with the external connected, as I am now. I just select Ubuntu or Windows. I will change the boot order to the USB port then what should I do, If I go into Ubuntu I can still post to you from in htere and follow your instructions. Is that what you want me to do?  Chang boot to USB then if it boots without the menu, go from there?  I'll wait for your post then do the above. I think I see what you are trying to get at, that is to see if it will boot directly from the external without the first menu. ?? Am I right?

---

### Post by ladydonna on 2009-06-01
I went to the hp site and read where I should have an option to boot from USB (option 4) on their site for my laptop. I followed the advanced to boot sequence and there was no USB boot option shown, only 4 1. hard drives (shows both internal and external) 2. a drive, (none in this machine  3. cd/dvd drive and 4. boot from network.  I then selected boot from internal hard drive and it did not boot just came back to the menu. I tried it both with the external plugged in and with it unplugged. I think I am going to reenter the bios, advanced and change the boot to boot from external and see what it does.

---

### Post by logos34 on 2009-06-01
any success?

it's odd that usb is not listed as an option, but hopefully choosing 'external' hard disk like you said will work.  

See, it would be so easy if we could just get the Bios adjusted to boot the external usb directly...Grub is already on that drive's mbr from when you did the "restore grub' routine the first time...Otherwise you'll have to start thinking about putting a small boot partition on the internal so you can boot windows even when the usb is disconnected.

---

### Post by ladydonna on 2009-06-01
Ops, second hard drive has USB after the description, I imagine it took the place of the USB setting in boot selection menu.:p

---

### Post by ladydonna on 2009-06-01
Actually, That is what I would like to be able to do. Just be able to boot the internal without the external attached, then be able to deal with the external hard drive.

---

### Post by ladydonna on 2009-06-01
DO you want to try that?  I should still be able to plug in the USB external and boot through the grub on it then, shouldn't  I ?  Or will this stop me from being to access the external drive completely?

---

### Post by ladydonna on 2009-06-01
By the way Logos34  I am in Florida, USA, where are you located? I don't want a big time difference to cause you problems.   :)

---

### Post by logos34 on 2009-06-01
sorry to keep you waiting...no, it ok I'm in central time...just doing some misc. stuff  around the house, keep putting the machine on standby...

you say

> **ladydonna said:**
> Ops, second hard drive has USB after the description, I imagine it took the place of the USB setting in boot selection menu.:p

so tell me: *Can* you set it to "External' (USB) and boot ubuntu directly? This is the easiest way

If you can't do that, or you would really rather boot the internal drive, you will have to do one of two things so that you can both boot windows without the usb attached, AND boot ubuntu when it is attached. 1) use windows bootloader instead to chainload ubuntu, or 2) add a small grub boot partition at the end of the internal drive so that you will see the grub menu even when the usb is disconnected.

Of the latter, I recommend using windows bootloader (hope this doesn't lead to another set of problems!).  But you have to restore the windows bootloader (fixmbr) first, using either the 'ms-sys' method or Super Grub disk (or if you have the XP Home install CD, please say so).

---

### Post by ladydonna on 2009-06-02
Good afternoon Logos34,  Let me go over this now.  When I first turn on my laptop and have the USB hard drive attached it boots to it says loading stage 1.5 and load grub then it gives me 4 choices 3 Ubuntu with different nomenclatures, and the  windows xp home choice. If I do nothing it boots into Ububtu. If I choose Windows it boots into windows. This is with nothing in the cd drive, and boot successfully to the one of my choice.  

Also if I have booted to windows I can then unplug (safe to remove hardware) the USB external hard drive and continue working in windows until I shut down or reboot the computer again, when I do if the external USB drive is not attached I get the laoding stage 1.5 and the Error 21 code, if it is plugged in at start up it will boot the grub and give me the choices of using Ubuntu or windows. If I choose Ubuntu, the hExternal Hard drive must remain attached or Ubuntu and the laptop wont do anything, and I have to reboot the machine, using either method I explaine here. 

Now if the USB external drive is not attached when I turn the laptop on I get the following   loading stage 1.5  and Error 21.  If I put the Ubuntu live cd into the drive and boot up it gives me the install choices, of which I did go into the Ubuntu install we discussed yesterday and I tried doing all the link and code you gave me showed. and I posted the results which were not successful, as it said cwnnot find, or incorrect code, etc.  

I would love to be able to get my laptop to boot up without the external USB hard drive connected. I just don't want to anve the problem that I can not access the external USB hard drive when I do want to plug it in and use it.

So Logos34, Can we somehow get the laptop to boot to Windows from the internal hard drive?  If so would I be able to plug in the external USB hard drive and still get the choices of Ubuntu and Windows?  

I would have put the Ubuntu installation on my internal hard drive in the first place, but I thought I would put it on the external to sort of give it a test drive and not take up space on my main internal hdrd drive, and thought it would be a simple matter of uninstalling it from the external drive if I did not like it, which is not the case, I do in fact like it.  Now my goal would be to uninstall ubuntu from the external drive and install it notmally with multi boot option to either use windows or Ubuntu in the laptop and reclain the lost partition space that Ubuntu took which was 468 gb of the external hard drive and leaving the 160 + gb of data I have on the original section of the external hard drive. Now I have showing several partitions in the part manager. and I was told I would have to completely wipe the partitions and start frwsh. The problem with doing this is I do not have enough space to transfer all the contents of the original portion of the external hard drive.

Ideally this is what I would like to achieve,  have the laptop boot independently to windows or Ubuntu at start up when I choose one or the other. Remove Ubuntu completely from the External USB hard drive and reclaim the Ubuntu space for use by me in both windows on eth internal hard drive or from Ubuntu in the internal hard drive. and have an equal amount of space for both windows and Ubuntu to be able to share on the external hard drive.  

I know this is long, but I wanted you to know the whole picture, so we are on the same page and it is clear to both of us. I know it is difficult to work back and forth with you only being given bits and pieces so goes the reason for this long post.  

I just wanted to bring you up to speed as to where we are and the overall picture of this situation.  I will be available here off and on the rest of the day and night.  I do very much appreciate your help with my problem here 

My deepest thenks.

:D

---

### Post by ladydonna on 2009-06-02
I just went to Microsoft support and found a post from their engineer support staff about something else, fixing the MBR and went into MSconfig from windows and to boot section and under the boot loader section the below is shown. I hope this helps you to see what is happening in the Windows Boot.

bootloader
timeout 15
default=multi(0)disk(0)Partition(1)Windows

Operating systems
multi(0)rdisk(0)Partition(1)Windows="Microsoft windows xp home edition"
/fastdetect/noexicute=Optin
C:\GRLDR="Start Grub
c:\wubild.mbr=Ubuntu

This is what is shown.  In msconfig   under  boot.ini tab

I hope this tells you something if not at least you know the things listed and the order of them in the boot.ini.

---

### Post by logos34 on 2009-06-02
Ok, I get the picture.  

Just for the record: you never answered me on this:

> > **ladydonna said:**
> Ops, second hard drive has USB after the description, I imagine it took the place of the USB setting in boot selection menu.:p

**so tell me: *Can* you set it to "External' (USB) and boot ubuntu directly? This is the easiest way**

What happens when you select 'external'/usb in the Bios boot order?

Anyway, if you want ubuntu on the internal, uninstall Wubi first:

> [http://wubi-installer.org/faq.php#use](http://wubi-installer.org/faq.php#use)

How do I uninstall it?

You uninstall it as any other applications. In Windows go to the control panel and select "Add or Remove Programs", then select Wubi/Ubuntu and uninstall it. You can also use the uninstaller that you find in the installation folder.

Backup your XP "My Documents" (i.e. your personal files) to 160 Gb partition on your usb drive.  

Defragment your C: drive, as [shown here]("http://www.linuxdevcenter.com/lpt/a/6554"):

> "Before you can resize the NTFS partition, you must move all files to the "front" of the disk. You can see the locations of files on your disk by running the Windows Defragmenter utility. Go to Start->All Programs->Accessories->System Tools->Disk Defragmenter to launch the defragmenter. Figure 1 illustrates my disk usage after the defragmentation cycle completed."

Reboot.  Select windows from grub menu.  The boot choice for wubi should be gone. Your files are nice and compact at the front of the disk. 

Now boot the Ubuntu CD and begin installation to the internal disk.  When you get to the "Prepare disk space" screen, select the first option, "**Install them side-by-side**..." This will shrink XP to make room for ubuntu.  

[IMG]http://news.softpedia.com/images/extra/LINUX/large/ubuntu904installation-large_007a.jpg[/IMG]

When the installation has finished, reboot and you should have a new ubuntu partition  on your internal drive, after windows xp, with grub menu giving you a choice of either OS.  (Let's hope there are no problems, like grub still pointing to the usb ubuntu installation!).

Go into ubuntu, open a terminal and post the output of this:
> 
sudo fdisk -l

Note: I'll be online today as long as it takes to finish this job! I'll give you my undivided attention!

---

### Post by logos34 on 2009-06-02
any progress?

---

### Post by ladydonna on 2009-06-02
Hi I just got home from grocery shopping.  First I am going to reboot into the setup and check again so I can be sure of what I tell you this time. When I checked it yesterday it did not show the USB option in the menu without the external hard drive attached. With it attached it did not show a seperate USB option, just under hard drive it showed the internal hard drive and the external hard drive describing the drive and then (USB) listed like this.  I will be right back. I am going to reboot with the external unhooked to see what it reads both ways.

---

### Post by logos34 on 2009-06-02
> **ladydonna said:**
> I am going to reboot with the external unhooked to see what it reads both ways.

The point is to check it *with the usb **attached***, then try to change the Bios to boot that drive directly (select 'external', 'usb', or however it's listed).

---

### Post by ladydonna on 2009-06-02
This is what I found.

Restarted laptop without USB External hard drive attache went into setup, advanced, boot, and found the following

Floppy Disk Drive
APAti CD Rom
*Hard Drive
     ST9100822A-(PM)
Network Adaptor

I then shut doen and rebooted into setup with the external drive attached the following is what was there this time.

Floppy Disk Drive
APAti CD Rom
*Hard Drive
     ST9100822A-(PM)
     WD6400AAC External (USB)
Network Adaptor

I can not boot to external without the following appearing

Without external attached

Loading Stage 1.5

Grub  Error 21

With the external attached

Loading Stage 1.5

Grub

Next Screen

Ubuntu  8.10 kernel 2.6.27-11 general
  "    "      "      "         "    "    Recovery Mode
  "    "      "       "    Memtest86*
Microsoft Windows XP Home Edition
Other Operating System


I select one and it goes to

Grub

Ubuntu
Windows XP Home Edition
Other Operating System

I selected windows on this boot and am sending this to you for evaluation. 

I think to answer your question No I cannot boot directly to the USB external with it attached without the two menus and options to select.

---

### Post by ladydonna on 2009-06-02
Everything I want to save on the 650 GB external hard drive  is already in the first partition section of the partition.

---

### Post by ladydonna on 2009-06-02
I did that    Briefly,  power on with the 650 gb drive selected in boot  power up and the 2 menus I described above is what come up, select one of the options and the second comes up and select one of them and the laptiop boots into it. (there is no USB External selection available except under hard drives and then USB only reads in the description of the external hard drive under the boot selection.  I hope I am saying this right.  By the way I will be here the rest of the evening except for cooking dinner but even then I will be back and forth here to work this out with you, again Logos34 thank you.

---

### Post by logos34 on 2009-06-02
> **ladydonna said:**
> 
Floppy Disk Drive
APAti CD Rom
*Hard Drive
ST9100822A-(PM)
[COLOR="Red"]WD6400AAC External (USB)[/COLOR]
Network Adaptor

Ok, so that's how your Western Digital usb drive shows up, 'WD6400AAC External (USB)'...I knew it had to be there...But you're still booting to the internal drive...Notice the list is in order top to bottom, first to last...The Bios is looking for a bootable floppy first, then a cd (if present in the drive it will boot that), then the internal hdd '*Hard Drive', next your external USB drive, and finally network boot.

So using the **arrow keys** on your keyboard can you **highlight the USB** and move it up **above the the *Hard Drive ST9100822A-(PM)**?  That way the Bios will boot it ahead of the internal disk.  You installed grub on the external so it should work...So it looks like this:

> 
Floppy Disk Drive
APAti CD Rom
[COLOR="Red"]WD6400AAC External (USB)[/COLOR]
*Hard Drive
ST9100822A-(PM)
Network Adaptor

If you're still having problems, then we'll start the ubuntu install to the internal next.

---

### Post by ladydonna on 2009-06-02
I will try that, but you will need to tell me how I can get it to move up.  Presently it is inside the Boot  hard drives list  as shown. I can highlight it, which I did before this restart, but I don't know how to move it out of the hard drive choice and up above it. Can you tell me how to do that?

---

### Post by logos34 on 2009-06-02
> **ladydonna said:**
> I will try that, but you will need to tell me how I can get it to move up. 

I told you above.  Use the ARROW KEYS on the keyboard.  Navigating in the BIOS is handled for the most part by Arrow keys, Enter, TAB keys

---

### Post by raymondh on 2009-06-02
> **ladydonna said:**
> I will try that, but you will need to tell me how I can get it to move up.  Presently it is inside the Boot  hard drives list  as shown. I can highlight it, which I did before this restart, but I don't know how to move it out of the hard drive choice and up above it. Can you tell me how to do that?

Once you highlight the USB drive, see if clicking the + (plus) button works in moving the highlighted option up.  If it does, then you know that the - (minus) button will move it down.

At least, that's how it is in mine.  Hope it helps ... good luck.

---

### Post by ladydonna on 2009-06-02
I did that and moved it up above the other hard drive, it would move no further up. I rebooted and it just kep rebooting and rebooting without the grub or stage1.5 showing no error 21 either, just kept rebooting. I had to go back into setup and move it back below the internal  hard drive  so I could get it to book up again. That obviously is not going to work

---

### Post by logos34 on 2009-06-02
> **ladydonna said:**
> I rebooted and it just kep rebooting and rebooting without the grub or stage1.5 showing no error 21 either, just kept rebooting. 

I think I found the problem.   

Seems when you restored grub the first time, you wrote it to the bootsector of the ubuntu / partition (you used 'hd1,4' instead of just 'hd1'.  It should have gone on the MBR.  

So move the external USB disk back **above** the hard disk.

Put in the Ubuntu Live CD in and boot it.  Open a terminal and type in the following lines, pressing Enter after each one:
> 
sudo grub 

root (hd1,4)

**[COLOR="Red"]setup (hd1)[/COLOR]**

exit


Now reboot, revove the cd and see if that gets you into ubuntu on the external usb

---

### Post by ladydonna on 2009-06-02
Ok, I'll give it a try. I'll Be back to you in a while.  You are great to help me this way Logos34:D

---

### Post by ladydonna on 2009-06-02
I followed your instructions, booted from cd and opened terminal

typed the commands and pressed enter after each line, when I typed in setup (hd1) on it's own line it came up with  Unrecognized Device String.
I tried typing the line  Root (hd1,4) Setup (hd1) on one line and it seemed to take, then a menu appeared in the same window asking me which I wanted to boot from giving me the choices the initial boot menu on start up. I highlighted and pressed the windows option and it crashed with a statement   Segmentation Fault    Core Dump  I closed the window and restarted the computer and am back where I was. I have not checked the setup yet to see if the external hard drive is still above the internal hard drive. but when I did restart the first start gave me the error 21 twice. Then I unplugged and plugged back in the external hard drive restarted and it booted the grub and the choices.

---

### Post by logos34 on 2009-06-02
argh...You do have the USB connected when you do that, right?  Try it once more like you did originally (commas, not periods between #'s):

> 
**sudo grub**

**find /boot/grub/stage1**

(it should ouput 'root (hd1,4)')

**root (hd1[COLOR="Red"],[/COLOR]4)**

**setup (hd1)**
[B]
quit[/B]


I wish I knew why it's giving you such difficulty

[COLOR="Blue"]EDIT: the only other thing I can think of is when you boot the live cd after moving the usb ahead of the internal hdd in the Bios, it sees the usb as drive (hd**0**) instead of (hd1).[/COLOR]

so if for  

> find /boot/grub/stage1

it returns 'root (hd0,4)', then do:
> 
root (hd**0**,4)

setup (hd**0**)

quit

---

### Post by ladydonna on 2009-06-02
I went back over everything again, and went back into the terminal carefully entered everything just asyou wrote it and this time it displayed the following

checking if */boot/grub/stage1 exists.. yes
checking if ?boot/grub/stage1.5 exists.... yes
running embed /boot/grub/e2fs_stage1_5 (hd1)  16 sectors are embedded
running  install /boot/grub/stage1 (hd1)  (hd1) 1+6 (hd1.4) /boot/grub/stage2/boot/grub/menulst  succeeded
done

I shut down and removed the Ubuntu cd and rebooted. The same results the grub then again both menu choices and I chose to boot into windows again. It still did not boot directly to the Ubuntu USB drive. I did have to go back into setup and change the external hard drive back to where it was, second position, 

this is what I get that keeps rebooting if I leave it in the first position. 

intel undi   pxe-20 build 082

for real tek pci fast eithernet controler
for real tek  pxe  e61
PXE - Mof. exiting  PXE Rom

So we are seemingly where we were,

Oh I tried unplugging the external to see what happens and I get the error 21 code and no boot.:(

---

### Post by ladydonna on 2009-06-02
I'm going to follow the last instructions now.  Yes the drive was USB connected.

---

### Post by logos34 on 2009-06-02
Did I say ARGH! ?

Jeez, I hate it when machines behave irrationally...It obviously supports USB boot, grub appears (again) to have succeeded in reinstalling to the MBR of the external, yet the Bios refuses to boot your drive directly (skips to network?)

Ok, then you want to skip next to the internal installation.  Follow the instructions I gave you...other than that the installation is the same as what you originally did.

I'll be around for a little while more tonight, and back tomorrow if you have any questions.

---

### Post by logos34 on 2009-06-02
> **ladydonna said:**
> I'm going to follow the last instructions now.  Yes the drive was USB connected.

no need to try it again...the output clearly shows grub succeeded in putting it on the right drive (it was 'hd1' after all)...

> checking if */boot/grub/stage1 exists.. yes
checking if ?boot/grub/stage1.5 exists.... yes
running embed /boot/grub/e2fs_stage1_5 **[COLOR="Red"](hd1) [/COLOR]**16 sectors are embedded
**running install /boot/grub/stage1 (hd1) (hd1) 1+6 (hd1.4) **/boot/grub/stage2/boot/grub/menulst succeeded
done

it's something wrong with the bios.  Forget it.. Just go ahead with installing on the internal.  If and when you ever succeed there, delete ubuntu on the usb and you'll be back in business.

good luck

---

### Post by ladydonna on 2009-06-02
Same results as above, I did it like I did before as you instructed and it returned the same results, but when I restart after quit. It booted up the same way to the grub then to the two menus .

---

### Post by ladydonna on 2009-06-02
Whoa, I understand the install upon the internal, no problem, but then I want to save what I have on the 650 gb external, (the 168 gb):p I have there from my windows files. I was told If I delete the partition that Ubuntu is on I will loose everything on the drive  Please show me how To get rid of Ubuntu on the external, and recover the space on the Partition, over 420 GB that Ubuntu took when I installed it.

---

### Post by logos34 on 2009-06-02
Once you complete the installation of ubuntu on the internal, you will boot into it and go to Top Panel>System>admin>partition editor) and delete just ubuntu sdb5 and sdb6, I believe (and the extended partition housing them).  

If unsure, post output of 

sudo fdisk -l

Gparted allows you to delete individual partitions, rather than the whole drive, leaving the windows backup/storage partition untouched.

---

### Post by ladydonna on 2009-06-02
Will the partitions revert back to the one big partition on the drive putting the taken space by Ubuntu back in the single first partition?

---

### Post by ladydonna on 2009-06-02
I am going to shut down, reboot to the ubuntu cd and do a full install on my internal hard drive.  You say I am to use the Ubuntu installation on the internal hard drive to delete the Ubuntu from the external hard drive. ??

---

### Post by logos34 on 2009-06-02
> **ladydonna said:**
> You say I am to use the Ubuntu installation on the internal hard drive to delete the Ubuntu from the external hard drive. ??

yes.  It must be unmounted beforehand (but Gparted will prompt you).  

See "Deleting a partition" [here]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") (--> read down to figure eighteen).  

Make sure to select the right hard disk in the drop-down menu upper right!

After that, you'll only need to remove the extra ubuntu boot entry from the bottom of /boot/grub/menu.lst

---

### Post by ladydonna on 2009-06-02
I tried to install Ubuntu to my internal hard drive, had to boot up with the external attached, as it is the only way I can boot this machine. The Ubuntu cd ran and started to install. cane to the partition window and it was trying to install on the external drive again. I unplugged the external and it then tried to install on the internal hard drive, but it wanted to use the whole hard drive 100gb and that would eliminate everything including windows and That I don't want. I need instructions on how to install it in about 10 Gb and leave the rest of the drive intact. Then I need to make sure of what I am doing before I delete Ubuntu and it's partitions so I don't eliminate my 168 gb of data on the 1st partition of the external hard drive.  I do appreciate all the time and effort you are putting in helping me through this. I wish I had had someone walk me through putting Ubuntu into the external drive properly at first so I would not have messed it up like this. Leave it to me.DUH..
So anyway. If you still want to work with me on this problem I will probagly be back online here about 1pm my time or so tomorrow.  Thanks again for your patients and precise instructions and help Logos34.  Have a Blessed Day.  Till later

Donna

---

### Post by logos34 on 2009-06-03
Here's a good step-by-step guide:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by ladydonna on 2009-06-03
WOW !!  You are amazing, the knowledge, the helpfulness.  I am very greatful. I just finished copying the first 49 pages of how to and here you give me even more info.  I am going to go over this tonight and tomorrow and hopefully will be able to do all that needs to be done, and correctly this time. I will let you know the outcome. That is if all goes well and I don't crash this whole thing, HAHA  Thank you again Logos34. and God Bless You..  Till tomorrow, Donna:p

---

### Post by logos34 on 2009-06-03
> **ladydonna said:**
> I just finished copying the first 49 pages of how to 

ha ha...maybe it feels that way with all the links I'm throwing at you, but rest assured they are the most succinct, precise explanations I can think of...they do a better job than I can to explain matters...

Hopefully the apcmag link will get you up and running a dual boot on the interna (it's techinally based on 8.04 Hardy, but the partition screen is almost exactly the same).  Then you can use gparted to delete the ubuntu on the external (but not windows ntfs partition!), edit menu.lst and have done with the matter.

---

### Post by ladydonna on 2009-06-03
Hello again Logos34. :)  I appreciate the links to both how to's. I printed out How to Dual Boot.  I then followed the instructions. When I got to Make roon for Ubuntu I had the same screen that I got yeaterday, showing a used space partition (before) and the after, both show 100% for Ubuntu and do not show my existing windows which is about 85% of the drive. If I read it right it is not seeing my current instalation and will delete or overwrite the current data on the internal hard drive. It did not give instructions on which option to choose, Guided,  or guided using the largest continuous free space  or Manual.  I was unsure what to choose and also in fear of wiping out my windows partition, which as I said, at this point it does not show. So I quit the installation and here I am, again, looking for your help.  Please let me know which to select and what I should enter if another window opens up for my choice. I will then shut this down and go back to live cd and try it again.  I love the how tos you sent. I copied the 49 pages and put them into my word program so I can print what I need to do to work on my external hard drive after I get Ubuntu successfully installed to my internal Drive.  Till I hear from you, Thanks again,  Donna:D

---

### Post by logos34 on 2009-06-03
hmm...

Boot back into the live cd desktop, but instead of clicking on the 'install' icon go to >System>admin>partition editor (Gparted).  

Does Gparted see the windows installation on sda?

---

### Post by raymondh on 2009-06-03
also, using the liveCD and showing the output of gparted, take a screen shot and post it. 

It'll help in visualizing the HD

---

### Post by ladydonna on 2009-06-03
Yes it does in both the upper rt corner, and it is the only one shown as I have the external drive unplugged. I can give you full details of what the middle large window that has 3 lines shows if you want. I wrote them down.:)

---

### Post by logos34 on 2009-06-03
ok, what does it say exactly?

---

### Post by ladydonna on 2009-06-03
While I am waiting, I will post the rest of what it says

Big square window

dev/sda1
92.95 gb


lines below

/dev/sda1     ntfs                 92.95 gb
unallocated   unallocated         7.84 mib
/dev/sda2     unknown         203.95  mib          

lower left corner

0  pending     operations

Hope this helps.:)

---

### Post by ladydonna on 2009-06-03
How do you take a screenshot?

---

### Post by ladydonna on 2009-06-03
Can I leave this windows open and run the live cd? also How do I post the screenshot to this post for you to see, That would help me greatly,  writers cramp you know

---

### Post by logos34 on 2009-06-03
> **ladydonna said:**
> How do you take a screenshot?

"PrintScrn" key..It's uploading it that's kind of tricky. Some other time.


> 
dev/sda1
92.95 gb


/dev/sda1 ntfs 92.95 gb
unallocated unallocated 7.84 mib
/dev/sda2 unknown 203.95 mib 

See if you can shrink sda1 by moving the right border leftward (grab it by clicking on it, hold down left mouse key and drag it over), leaving ~ 10 GB unallocated space after it.

You *did* defrag windows as explained in the link I gave earlier, right?  

Did you also remove/uninstall Wubi?

---

### Post by ladydonna on 2009-06-03
Yes I defragged, but have don a lot of other work in windows since, so I need to drftag again..


Can I put the live cd in and run it in windows and do the things I need to do back and forth between live cd and windows.

---

### Post by logos34 on 2009-06-03
no, can't switch between windows and live cd, unfortunately.  Need to reboot into the other.  But you CAN access your documents on the windows partition from the live cd, if that's what you're asking...Just go to Computer and click on the 92GB volume listed to mount it.

---

### Post by ladydonna on 2009-06-03
Ok, So if I boot into live cd, I should be able to go online in Ubuntu then open the browser and get back to this posting and continue working with you and with the changes I need to do. Just not boot to windows at all.  Am I correct?  Also I assume mount and unmount mean can and cannot make changes to, am I right or wrong.

---

### Post by ladydonna on 2009-06-03
I just finishe the defrag and am going to shut down and boot from live cd. I will try to get to this forum from there if I can, if not I will try to re size the drive. Hopefully I will be able to work with you from within live cd. If so I will let you know the results if not I will have to reboot to windows and contact you from there. I think I should be able to get with you from there though.

---

### Post by logos34 on 2009-06-03
> **ladydonna said:**
> Ok, So if I boot into live cd, I should be able to go online in Ubuntu then open the browser and get back to this posting and continue working with you and with the changes I need to do. Just not boot to windows at all.  Am I correct? 
yep

>  Also I assume mount and unmount mean can and cannot make changes to, am I right or wrong.

if you're referring to resizing the partition, yes it has to be unmounted.

---

### Post by ladydonna on 2009-06-03
[SIZE=2]Ok here we go. I am in Ubuntu livecd , on the internal hard drive only and ready to start.:D[/SIZE]

---

### Post by logos34 on 2009-06-03
ok, so try to shrink windows like I said.  Your stuff on windows is backed up to the external, right? standard precaution whenever resizing partitions

---

### Post by ladydonna on 2009-06-03
I tried to resize but it wont resize. Unmount is grayed out.. the arrows aare there but wont let me resize the size. It says free space before 0  free space after 8mib[IMG]file:///tmp/moz-screenshot-1.jpg[/IMG][IMG]file:///tmp/moz-screenshot.jpg[/IMG]

---

### Post by ladydonna on 2009-06-03
Tried to insert the screenshot but it did not do it.

---

### Post by ladydonna on 2009-06-03
Since Ubuntu took up all the free space so I cant back it up, unless you can tell me how to do it from here. and then recover it back to my internal drive. I would be in sad shape if I lost it all, very bad shape.

---

### Post by ladydonna on 2009-06-03
I leave here about 6 oclock  for ur time, but your help and expertise areChurch.  And get back here about 10:30. I really need to somehow be able to use my laptop without the external attached and to be able to also access the external as I said. I know I am taking up a lot of your time but I reall do need your help and expertise.. I hope you will continue working with me.

---

### Post by ladydonna on 2009-06-03
I am beginning to thin that I cannot do this from live cd, but only from the install full, and if thet is the case, I fear that I will lose everything on the laptop as things are now, especially since I don't know how to copy (backup) to the Ubuntu portion of the external drive as that is the only place I could possibly do it., Wait a minut, I just remembered, I cleared out a hundred gb of the portion of the external hard drive windows is on. Can you tell me how to backup the whole computer to that portion of the external drive, then I would not be as concerned about the Ubuntu install on the internal drive.  ????:p

---

### Post by logos34 on 2009-06-03
sorry for the delay...

open a terminalm run this:

> sudo fdisk -l

and

> mount

post output

---

### Post by ladydonna on 2009-06-03
I see an install on my Ubuntu desktop. Is that where I do the full install from within Ubuntu live cd? That is after I backup the Internal Hard Drive. and that is if you can show me how to do that.  Hope you are still there..

---

### Post by ladydonna on 2009-06-03
OK thats done. Do you need to know what it says?

---

### Post by logos34 on 2009-06-03
> **ladydonna said:**
> OK thats done. Do you need to know what it says?

yes, I said post the output

---

### Post by ladydonna on 2009-06-03
Well, Have to get ready and go to Church. I am going to leave this on and up so that when I get home tonight I hope to continue on, If you are going to be busy, just let me know. I have been living with this problem for quite a while and I guess I can keep on living with it until it is solved. I you are not available, believe me I will understand.  Till Later, God Bless,   Donna

---

### Post by ladydonna on 2009-06-03
Here is the results

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12134    97466323+   7  HPFS/NTFS
/dev/sda2           12136       12161      208845   88  Linux plaintext
ubuntu@ubuntu:~$ mount
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$

---

### Post by logos34 on 2009-06-03
> **ladydonna said:**
> I see an install on my Ubuntu desktop. Is that where I do the full install from within Ubuntu live cd? That is after I backup the Internal Hard Drive. and that is if you can show me how to do that.  Hope you are still there..

yes, you just click on the "Install" icon (after we get done resizing windows)...then when you get to the partitioning screen we'll choose "Guided--use largest continuous free space" option, or "manual" if necessary.

You can use Gparted to copy/backup to copy the whole windows partition if you have the space on the external.  Or just copy what's in My Documents

---

### Post by logos34 on 2009-06-03
> **ladydonna said:**
> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12134    97466323+   7  HPFS/NTFS
/dev/sda2           12136       12161      208845   88  Linux 


any idea what sda2 is?  It's only a few hundred mb big so I guess we can delete it...I think windows is mounting which may be why it's grayed out.. Right click on it and unmount.

Ok, maybe we can pick this up again later or tomorrow..

---

### Post by ladydonna on 2009-06-03
Hi I don't have any idea what the 200 mb partition is, I thought maybe it had something to do with Ubuntu.  If you would rather do this tomorrow just let me know. I'm usually available daily between noon and 1PM and on for the rest of the day and evening.  If you get this tonight, let ma know and if you tell me how to use Gparted to backup my complete laptop hard drive to my exterior windows partition, I will go ahead and do that at least.

---

### Post by logos34 on 2009-06-03
yeah, maybe tomorrow afternoon would be better...Weird about the 'unknown' ~200 MB partition...can't be wubi related because the point about wubi is that installls ubuntu *inside* windows partition...hmm

One final way to get a boot menu even without the USB connected: dual boot using the windows bootloader to chainload Grub instead of the other way around.  This must be getting confusing to you, but I mention it only because it would avoid having to touch the windows partition...It should work. Read the stuff in my next post and sleep on it. Make a decision tomorrow.

------------

---

### Post by ladydonna on 2009-06-03
Ok Logos34, I'll read it and do some more reading from the 1st link you sent me, try to get a little more data in my head. I also agree thet tomorrow would probably be better, On my side I'll be available all day and evening, baring interruptions.  What time is good for you tomorrow afternoon?   You are sure a Blessing to me.

---

### Post by logos34 on 2009-06-03
_Use windows bootloader to chainload linux (WinGrub) _

Follow this [step-by-step guide]("http://users.bigpond.net.au/hermanzone/p9.html").  Herman's webpages are fantastic.

(I personally tested it a while back and it works).

---

### Post by ladydonna on 2009-06-04
I'll check them out and maybe do a few experiments on my own with them. I'll get with you sometime tomorrow. Hope to make this a little easier on you.  Thanks Again, With appreciation,  Donna   Goodnight.

---

### Post by logos34 on 2009-06-04
> **ladydonna said:**
> What time is good for you tomorrow afternoon? 

after 1 your time is fine.

Again, I'm trying to keep this as simple as possible, not throw anything at you not absolutely necessary. We've tried directly booting the USB, which should have been the easiest, but you apparently have some Bios issue.  THe only other (relatively simple) way to dual boot independant of the attached USB is a) install ubuntu on the internal drive or b) restore windows bootloader to the internal and add a linux entry, in the hope that you can chainload grub on the external. (I only mention b) now because ubuntu can't see windows during installation, as well as the anxiety factor inherent in resizing)

Those are basically your options.  Talk to you tomorrow.

---

### Post by ladydonna on 2009-06-04
Hello again.   Today is the day we will accomplish this task. Just wanted to tell you Hello, and that I am here. I am going to reboot now and go to Gparted and attempt to backup my full internal hard drive ti the windows portion of it's partition using the copy/backup command. If I have problems I will post to you from within Ubuntu live cd.  I will check this post from within live cd first to see if you are there and if you have any advise first though, Back shortly.

---

### Post by ladydonna on 2009-06-04
[SIZE=2]I am currently backing up my whole internal hard drive. I hope I am doing it right, I think it is working. I opened both my internal hard drive folder and Iopened my external drive windows portion and am dragging and dropping the folders individually into the external drive folder on the windows portion. It has been copying into the folder I created in the windows portion of the external and it seems to be successfully doing it this way. Right at the moment it is copying the 67 gb of my Doccuments and settings folder, it is taking the longest it has about an hour to run, then I will copy the rest of the folders over. Then I will check the folders and make sure my things are in there, then I will feel more confident about doing the partition and installing Ubuntu on the internal hard drive and make the changes and deleting needed to be done to the external drive. Once we get the laptop to boot up without the external hard drive attached[/SIZE]. I am not comfortable doing much other work while copying my backup files.  Hope all is well with you today.

---

### Post by logos34 on 2009-06-04
hi

[ok, great, I see you're just manually copying over your folders...67 gb will take a while, but fine]

If only Partimage (included with ubuntu) supported NTFS, it would so easy...you could mae a very small, compressed image of windows and store it inside the one of the two main USB partitions...but, alas, it has only 'experimental' support for NTFS...

Do you have a Windows XP Home Installation CD? Or even a Recovery CD? I doubt your machine came with one...at most, laptops come with a recovery *partition* on the hard disk

---

### Post by logos34 on 2009-06-04
how's it coming along?

---

### Post by ladydonna on 2009-06-04
[SIZE=4]CRASH..[SIZE=2] [SIZE=3]I don't know what happened, but right in the middle of the backup Ubuntu crashed. I had to reboot. When I returned to live cd and opened the two folders[/SIZE][/SIZE][/SIZE][SIZE=3] some of the files were there. I tried to open a couple of them, but they said there was nothing in them. So that did not work. So lets try it the way you mentioned in your last post. [/SIZE]

---

### Post by ladydonna on 2009-06-04
Oh yes, I do have the proper recovery cd and dvd for this laptop. I sent for them some time back and have used them for some problems and even recovery repairs before.  Standing by.

---

### Post by ladydonna on 2009-06-04
Are you there Logos34?   I'll be standing by here for what to do next.

---

### Post by logos34 on 2009-06-04
yeah here, thought you were still copying, so went back to compiling some programs...give me a sec to read about the crash...

---

### Post by logos34 on 2009-06-04
let's nail down some info...I need to know exactly what the state of things are...too many things are failing here...not encouraging...

ok, so you have recovery cds, good...

Clear up one thing: when I suggested [this method]("http://ubuntuforums.org/showpost.php?p=4691608&postcount=2") earlier (post #7), did you try it, but it didn't work? Because we'll need to restore the windows bootloader to the mbr of the internal.  I'd rather try wingrub method first--all these problems are making me nervous about resizing main internal windows partition.

Boot into ubuntu on the external disk, not live cd session and run these in a terminal:
> 
sudo fdisk -l
> 
df -h

post output

---

### Post by ladydonna on 2009-06-04
To answer the question on post #7  I think this is what happened. 

E Could not open lock file

/var/lib/apt/lists lock-open (12 permission denied

E  unable to lock the list directory.

bash -p command not found.  

I think I know more about using the terminal now and would be glad to try that again.  The crash was wierd. It said something about video resources the weird screens then little screens and finally I had to restart live cd. I will read the rest of your post and answer that in a sec.

---

### Post by ladydonna on 2009-06-04
Ok I'm going to boot into the Ubuntu external. Get to you from within there.

---

### Post by ladydonna on 2009-06-04
Hi again, Logos34,  I'm in Ubuntu external,  Here are the results of

sudo fdisk -l

and df -h

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12134    97466323+   7  HPFS/NTFS
/dev/sda2           12136       12161      208845   88  Linux plaintext

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       21954   176345473+   c  W95 FAT32 (LBA)
/dev/sdb2           21955       77825   448783807+   5  Extended
/dev/sdb5           21955       77081   442807596   83  Linux
/dev/sdb6           77082       77825     5976148+  82  Linux swap / Solaris
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             416G  3.1G  392G   1% /
tmpfs                 996M     0  996M   0% /lib/init/rw
varrun                996M  104K  996M   1% /var/run
varlock               996M     0  996M   0% /var/lock
udev                  996M  2.8M  994M   1% /dev
tmpfs                 996M  628K  996M   1% /dev/shm
lrm                   996M  2.0M  994M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             169G  113G   56G  67% /media/My Book


Again if you like I will go back to post 7 and try that again from the beginning and post the details to you. What do you want me to do now?  I will be happy to do anything you tell me to do here 1 step at a time. Just let me know.

---

### Post by ladydonna on 2009-06-04
Did that help?  Also, do you want me to go back to post 7 and run that in treminal? While you work on other things?

---

### Post by logos34 on 2009-06-04
Ahah! the reason it crashed during copy is you're using **FAT32** filesystem for sdb1 (standard factory format for USB)--duh, should have occured to me...Likely it encountered a file larger than 2 GB (max for fat32)...No big deal (except wasted time)

The lock stuff "E Could not open lock file..." is it was just complainignabout synaptic being open at the same time


Let's try something simple first: let's mount sda1, copy over the bootloader code, restore windows bootloader to the internal, and see if we can get this show on the road...Type these commands in, hit Enter after each one:
> 
sudo mkdir /media/windows

sudo mount -t ntfs-3g /dev/sda1 /media/windows

sudo grub-install /dev/sdb5

dd if=/dev/sdb5 of=/media/windows/ubuntu.bin bs=512 count=1

tell me how it went

---

### Post by ladydonna on 2009-06-04
Ok now I'm getting excited.  By the way, even though this has taken us in a lot of diff directions, I am learning a lot from you, so this has not been a waste of my time, but I know it has been for you. I want you to know that you are really appreciated.  REALLY.  Ok I am going to open the terminal and run it and I'll let you know the results. I will post them for you to see. Back soon..

---

### Post by ladydonna on 2009-06-04
[SIZE=3]Here are the results. 

[/SIZE]sudo mount -t ntfs-3g /dev/sda1 /media/windows
sudo grub-install /dev/sdb5
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sdb5 as (hd1,4)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

dd if=/devsdb5 of=/media/windows/ubuntu.bin bs-512 count=1
dd: unrecognized operand `bs-512'
Try `dd --help' for more information.
dd if=/dev/sdb5 of=/media/windows/ubuntu.bin bs=512 count=1
dd: opening `/dev/sdb5': Permission denied


Can we increase the size of the writing, it is hard to see the code, at least the code portion so I can make sure I am piutting in the correct code and exactly. It is hard to see the periods, spaces dashes, etc.  Thanks. Please check to see if I typed the code exactly.

---

### Post by logos34 on 2009-06-04
[SIZE="3"]> dd: opening `/dev/sdb5': Permission denied

oops, left out sudo. try
> 
**sudo **dd if=/dev/sdb5 of=/media/windows/ubuntu.bin bs=512 count=1[/SIZE]

---

### Post by ladydonna on 2009-06-04
[SIZE=3]That worked I think, at least it put this out

 sudo dd if=/dev/sdb5 of=/media/windows/ubuntu.bin bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000278248 s, 1.8 MB/s

Now, Do I have to run the whole thing over all at the same time?
[/SIZE]

---

### Post by logos34 on 2009-06-04
[SIZE="3"][SIZE="2"][SIZE="2"]no, I think that's fine...

Now we have add it to a windows file, boot.ini

[SIZE="3"]gedit /media/windows/boot.ini[/SIZE]

(or if necessary 'sudo gedit /media/windows/boot.ini')

add this line to bottom:

> [SIZE="3"]C:\ubuntu.bin="Ubuntu Linux"[/SIZE]

(after you paste it, backspace if necessary to remove any trailing empty space like

> C:\ubuntu.bin="Ubuntu Linux"[COLOR="Red"]**___**[/COLOR]

(windows is finicky about format).

Save and close.

Let me know how it went[/SIZE][/SIZE][/SIZE]

Post boot.ini so I can see how it looks

---

### Post by ladydonna on 2009-06-04
[SIZE=3]I'm confused here.  Am I still working in the terminal? Or do I need to shut down and do something in windows? If so what do I need to do now?[/SIZE]

---

### Post by logos34 on 2009-06-04
no, keep working in the terminal...gedit will call up text editor -- add the line, then close it...we can do a lot of this stuff from within linux

if you can manage to edit boot.ini we'll do ms-sys next to restore windows bootloader

(when I said 'save and close' earlier, I meant just gedit text editor, not the system)

---

### Post by ladydonna on 2009-06-04
This is what popped up after the first line of code was entered

---

### Post by ladydonna on 2009-06-04
DUH   

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin 
C:\GRLDR="Start Grub"

---

### Post by ladydonna on 2009-06-04
Ok I saved and quit.

---

### Post by logos34 on 2009-06-04
add the line in blue like this:

> [boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Home Edition" /fastdetect /noexecute=optin
[COLOR="Blue"]C:\ubuntu.bin="Ubuntu Linux"[/COLOR]

Show me the results

Then Save and close gedit and go back to terminal

I used smaller font this time to avoid any confusion!

---

### Post by ladydonna on 2009-06-04
I might have done it wrong. I opened a new terminal in each window and an the text editor so I could copy and paste to you. I saved each one, but I am wondering if that was the right thing to do. Maybe I should redo all that code in one terminal.  Is ther a way we can quickly check to see if I did it right?

---

### Post by logos34 on 2009-06-04
when you get done editing boot.ini, close it. Then close all the terminal windows.  Reopen afresh terminal window and type 

gedit /media/windows/boot.ini

to recheck it

---

### Post by ladydonna on 2009-06-04
This is what came up

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin 
C:\GRLDR="Start Grub"

---

### Post by ladydonna on 2009-06-04
What do we do now?:)

---

### Post by logos34 on 2009-06-04
> **ladydonna said:**
> What do we do now?:)

WHat do you mean?  Replace the existing line with the one in blue!

If necessary open as

> **sudo **gedit /media/windows/boot.ini

does it throw an error when you try to save changes?

---

### Post by ladydonna on 2009-06-04
Ok, this is what came up and no errors upon closing either the text editor or the terminal.  

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin 
C:\ubuntu.bin="Ubuntu Linux" 

 Hope this is right and what you want.  
standing by.:)

---

### Post by logos34 on 2009-06-04
ok, good. I hope that will work.

Now, test it by rebooting and choosing windows in the grub menu, then "Ubuntu linux".  If it hangs, reboot back into Ubuntu.

---

### Post by ladydonna on 2009-06-04
Should I boot with the external disconnected?

---

### Post by logos34 on 2009-06-04
keep it connected

Quickly: What does this command show:

> ls -l /media/windows

---

### Post by ladydonna on 2009-06-04
Ok here I go I'm Rebooting, and will let you know the results.  Right back.  I prey we made progress....:D

---

### Post by logos34 on 2009-06-04
> **ladydonna said:**
> Ok here I go I'm Rebooting, and will let you know the results.  Right back.  I prey we made progress....:D

yeah, right, 'prey'...(guess you missed the ls -l request)

---

### Post by ladydonna on 2009-06-04
Pray, spelled it wrong.  Nope, It did just the same as before. 
Grub Loading Stage 1.5

Loading Grub 

then the menu with the 3 Ubuntu options and the windows and other operating system choices. I chose Ubuntu and then the second menu giving Ubuntu or Windows as the choices. 

Now you say I left out the -l?  what do you want me to do to correct that?

---

### Post by ladydonna on 2009-06-04
Is this where I left it out?

			 		   		 		 		Hi again, Logos34,  I'm in Ubuntu external,  Here are the results of

sudo fdisk -l

and df -h

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12134    97466323+   7  HPFS/NTFS
/dev/sda2           12136       12161      208845   88  Linux plaintext

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       21954   176345473+   c  W95 FAT32 (LBA)
/dev/sdb2           21955       77825   448783807+   5  Extended
/dev/sdb5           21955       77081   442807596   83  Linux
/dev/sdb6           77082       77825     5976148+  82  Linux swap / Solaris
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             416G  3.1G  392G   1% /
tmpfs                 996M     0  996M   0% /lib/init/rw
varrun                996M  104K  996M   1% /var/run
varlock               996M     0  996M   0% /var/lock
udev                  996M  2.8M  994M   1% /dev
tmpfs                 996M  628K  996M   1% /dev/shm
lrm                   996M  2.0M  994M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             169G  113G   56G  67% /media/My Book


Again if you like I will go back to post 7 and try that again from the beginning and post the details to you. What do you want me to do now? I will be happy to do anything you tell me to do here 1 step at a time. Just let me know.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7401213") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7401213")

---

### Post by logos34 on 2009-06-04
Let me get this straight: the first time you chose ubuntu or windows?

On the first grub men screen you should have selected windows.

Then that should have browught up windows bootloader.  There you should have selected "Ubuntu linux".

ie:

windows>"ubuntu linux">ubuntu

Clarify please

---

### Post by ladydonna on 2009-06-04
Oh I thought I should have stayed in Ubuntu. I'll restart.

---

### Post by ladydonna on 2009-06-04
Here I am.  Yes in the second menu it said it just like that.

Now here is the boot up process

Grub  LoadingStage 1.5

Grug Loading 

that was the first black screen

Ubuntu Ubuntu

Ubuntu recovery

Ubuntu  mem

Windows

Other Operating sys

That is the second black screen


Windows XP home

Ubuntu - Linux

This is the final black screen then it boots to your choice, and this is with the external connected.

I  hope this is precise so you can get an idea of what is happening.

---

### Post by ladydonna on 2009-06-04
I chose windows in bot menus and am in windows now.:D

---

### Post by logos34 on 2009-06-04
> **ladydonna said:**
> I chose windows in bot menus and am in windows now.:D

No, for the final time: 1) select **Windows** 2) **[SIZE="3"][COLOR="Red"]"Ubuntu Linux"[/COLOR][/SIZE]** 3) **ubuntu**

> Grub LoadingStage 1.5

Grug Loading

that was the first black screen

Ubuntu Ubuntu

Ubuntu recovery

Ubuntu mem

**Windows** [<--select]

Other Operating sys

That is the second black screen


Windows XP home

**[COLOR="Red"][SIZE="3"]Ubuntu - Linux[/SIZE][/COLOR]** [<--select]

This is the final black screen then it boots to your choice, and this is with the external connected.

3) ubuntu

Think you can handle that?

---

### Post by ladydonna on 2009-06-04
It comes up with a blank black screen   with the word   GRUB _   and a blinking cursor.

Sounds like you are getting upset with me.  I appreciated your help and I know this has taken up a lot of your time. I will try somewhere else for more assistance with this problem.  This is all new to me, adn I am very impressed with Ubuntu, and am going to overcome this problem, and will also learn the ins and outs of this operating system.  Rome was not built in a day, and I can only do so mych. I make mistakes  and have adifficult time seeing some of the instructions with the print so small, but I have paients and time, I again really appreciate your help.   God Bless and Keep you.

Respectfully

Donna
71 years old and still learning.  :popcorn::p

---

### Post by logos34 on 2009-06-04
no, not upset with you at all.  I assumed as much. 

But unless I missed something, you will have to restore the windows bootloader and somehow use that the chainload linux, which normally is not very hard to do.  I would recommend you try the Wingrub method that I gave you earlier. Follow it step by step

best of luck

---

### Post by VMC on 2009-06-04
> **ladydonna said:**
> ...
Sounds like you are getting upset with me. ...  Rome was not built in a day, and I can only do so mych. I make mistakes  and have adifficult time seeing some of the instructions with the print so small, but I have paients and time, I again really appreciate your help.   God Bless and Keep you.

Respectfully

Donna
71 years old and still learning.  :popcorn::p

[SIZE="4"]Donna,

I have been following this topic from the beginning. When I saw your first post, I wondered if you might have problems reading the small print. I'm sure logos34 is not put off by all this. And do not go some where else. You found the right forum and the right person to help you.

I have stayed in the background so as not to compound the situation.

It's a real blessing that you started this at 71! Great for you. Stay with us. Your helping not only yourself but others who come by. You have great patience and fortitude. Keep it up!

Vern[/SIZE]

---

### Post by factorgaming on 2009-06-12
I think the information we provided here is really worth looking at. Thanks so much.

---


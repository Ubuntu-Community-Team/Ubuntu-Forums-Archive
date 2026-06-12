---
title: "how do i completely erase ubuntu?"
date: 2009-02-21
forum: General Help
---

### Post by dorado29 on 2009-02-21
i installed ubuntu on my freshly built computer and now, after realizing that almost every program i intended to use the new build for is incompatible with ubuntu, i need it erased. there is literally nothing except ubuntu on the hard drive; is there a program that i can d/l that will just wipe it? 

i have an ISO image of the OS i intend to put on it installed on a disc (which works, i tested it on a different computer running XP). When this is in the cd drive and i reboot there is no "boot from disc" option and nothing shows up to suggest ubuntu recognizes said disc on the desktop when i log on. im guessing ubuntu changed things around so it can no longer boot from disc? 

im confused :confused: :confused:, i just want a blank hard drive at this point

---

### Post by jimmy666 on 2009-02-21
i am on the same ship and no ones seems to have a clear answer.

not too hard. i also want to go from completely ubuntu machine to another and we need some help!

---

### Post by DGortze380 on 2009-02-21
It doesn't really depend on Ubuntu ... we need to know what OS you intend to install.

I f you have a full day to two, and really want a BLANK hard disk, download and use killdisk

---

### Post by yther on 2009-02-21
If you don't want to keep *anything* that's on your drive right now, just tell the installer (some form of Windows, I assume) to erase the drive when you set it up.

As for getting your machine to boot from CD, um... you said you have the ISO on a CD.  Does that mean when you open the CD, you see an ISO file sitting there?  If so, you will absolutely not be able to boot to that.  You'd need to burn the image to the CD; on Windows I'd recommend ImgBurn for that.

If the CD is properly made, then you have to tell your computer's BIOS to boot from CD.  On Dell machines you'd push F12 when you see the Dell logo screen, on some others the keys are different.  Don't wait for the operating system to load or it's too late.  :)  It sounds like your computer is set to *not* offer the CD as a boot choice, or it doesn't wait very long for you to make a decision.

I hope that helps; if not, tell us what brand & model of PC you have and I'm sure you can get some more assistance!

---

### Post by dorado29 on 2009-02-21
i intend to install XP 64bit, but i cant get to the installer to install it. I changed the boot priority in bios to cdrom as #1 and hard drive+ floppy drive as 2 and 3. it still booted ubuntu with no hesitation

just to clear things up it's not just the one .iso file burned onto the disc, there are a couple folders and whatnot. It boots properly, just not on my ubuntu-running desktop.

is killdisk compatible with ubuntu? it can take up to 2 days :shocked: lol

---

### Post by gallaau on 2009-02-21
That is a BIOS function. I don't think ubuntu can stop the BIOS booting the CD.
On mine it makes me press a button to boot the cd. I have 1 second to press the enter button when the message is displayed "BOOT FROM CD"

---

### Post by gallaau on 2009-02-21
Change all of them, 1 2 and 3 to boot from CD and see if you get a can't find OS message.

---

### Post by linuxisevolution on 2009-02-21
> **dorado29 said:**
> i intend to install XP 64bit, but i cant get to the installer to install it. I changed the boot priority in bios to cdrom as #1 and hard drive+ floppy drive as 2 and 3. it still booted ubuntu with no hesitation

just to clear things up it's not just the one .iso file burned onto the disc, there are a couple folders and whatnot. It boots properly, just not on my ubuntu-running desktop.

is killdisk compatible with ubuntu? it can take up to 2 days :shocked: lol

Ubuntu comes with 16,000 programs preinstalled and thousands more in the respitory, plus you can use wine to emulate your windows programs, so what programs won't run? And yes, killdisk is compatible. Ubuntu has higher compatibility with other operating systems than Windows does, believe it or not.

---

### Post by yther on 2009-02-21
OK, it sounds like you did the right thing with your BIOS.  :)  Although... you said "with no hesitation."  Normally I would expect some prompt from the system there.  Either a menu, or even "Press any key to boot from CD."  However, this can be turned off in some computers' settings, in which case it just boots whatever was detected, in order.

At this time, I do not believe the problem is in any way related to the contents of your hard drive.  Some basic troubleshooting is in order here.

Have you tested *other* CDs to see if your machine will boot to them?

You did say you tried it on another machine, so that lets us know the disc is recognizable&#8212;by *some* machines, but apparently not by yours.

Have you tried burning this CD at a lower speed, or on a different drive?  When burning a CD I intend to boot from, I always use the lowest speed possible; this has to do with the physical recording process, so slower speeds result in easier-to-read discs.  With some drives this can make a big difference.

Ah, one more idea.  It's unlikely, but possible, so I'll ask anyway.  Is this a CD or a DVD?  Some drives will boot to a CD but not a DVD; generally this is with older hardware, though, and since you have a 64-bit system I doubt your drive would be that old.  Still, you never know.

---

### Post by dorado29 on 2009-02-21
i couldnt change all 3 to cdrom so i disabled the other two. i got a black screen that said

"reboot and select proper boot device
or insert boot media in selected boot device and press any key"

the message stating "press [certain button] to boot from cd" doesnt show up on startup

this is with a 700mb cd. should i just d/l mandriva or something and write it to cd then try to boot it to see how it works?

edit: hold'em manager, full tilt poker, poker stars, poker tracker 3 are just some of the softwarez that i need to run, including some hotkey scripts, but i havent looked into any of those yet. i play online poker lol

---

### Post by yther on 2009-02-21
Yeah, it definitely doesn't like that CD.  :(

Try this:  [http://www.memtest.org/](http://www.memtest.org/)

The ISO for that is only a few megabytes.  A side benefit of that is you get to test your memory if you let it run for a few minutes.  ;)

---

### Post by linuxisevolution on 2009-02-21
> **dorado29 said:**
> i couldnt change all 3 to cdrom so i disabled the other two. i got a black screen that said

"reboot and select proper boot device
or insert boot media in selected boot device and press any key"

the message stating "press [certain button] to boot from cd" doesnt show up on startup

this is with a 700mb cd. should i just d/l mandriva or something and write it to cd then try to boot it to see how it works?

edit: hold'em manager, full tilt poker, poker stars, poker tracker 3 are just some of the softwarez that i need to run, including some hotkey scripts, but i havent looked into any of those yet. i play online poker lol

Do you have flash installed? If those are online apps, you could just run Firefox in wine, or Windows Xp 64bit in vmware...

---

### Post by dorado29 on 2009-02-21
do i d/l the "bootable iso" one?

---

### Post by yther on 2009-02-21
> **dorado29 said:**
> do i d/l the "bootable iso" one?

Yes.  Get either of those, probably the ZIP one if you're downloading on Windows, uncompress it, and burn it as a disc image to a CD.  Check it on a couple of machines including yours.  It should boot and immediately go to a blue screen with a lot of numbers.  ;)

---

### Post by dorado29 on 2009-02-21
strange. i wrote it to disc but it isn't recognized upon booting

---

### Post by jimmy666 on 2009-02-21
I boot from an iso burnt to a disc properly, the loader starts up and says "Press any key to boot from disc..."

I click, the blue screen with a text line at bottom indicates there is windows stuff being loaded, then after a few minutes i get an error saying it has encountered an error and needs to must quit.

this has been done with a iso of windows xp sp3 and also a boot disc from a purchased computer that had xp sp 2 and did the same.

also gives....

error code:

0x0000007b
0xf78d2524
0xc0000034
0x00000000
0x00000000

---

### Post by Hobgoblin on 2009-02-21
> **dorado29 said:**
> strange. i wrote it to disc but it isn't recognized upon booting

How did you write it do disk?

If you put the disk in a PC with an operating system running then look at the contents of the disk what do you see?

---

### Post by Hobgoblin on 2009-02-21
> **jimmy666 said:**
> I boot from an iso burnt to a disc properly, the loader starts up and says "Press any key to boot from disc..."

I click, the blue screen with a text line at bottom indicates there is windows stuff being loaded, then after a few minutes i get an error saying it has encountered an error and needs to must quit.

this has been done with a iso of windows xp sp3 and also a boot disc from a purchased computer that had xp sp 2 and did the same.

also gives....

error code:

0x0000007b
0xf78d2524
0xc0000034
0x00000000
0x00000000

Sounds like a memory error.  Try the memtest CD linked above, let it run a few hours.  See if you get errors.

---

### Post by dorado29 on 2009-02-21
> **dorado29 said:**
> strange. i wrote it to disc but it isn't recognized upon booting (on the ubuntu desktop)

this disc works fine in all my other computers. i think it's safe to say that the problem lies somewhere in the cdrom area amirite?

---

### Post by yther on 2009-02-21
yeaiguesurite  :rolleyes:

It's starting to look like that machine can't boot from *any* CD-ROM.

Do you have any commercial CDs you could try?

Not to change the subject, because I know you're trying to get rid of Ubuntu, but it is sometimes possible to "jump-start" a CD boot using GRUB.  Basically GRUB starts up and then you tell it to load the CD.  This can help if the computer itself can't start up from the CD; by starting GRUB first, we overcome that limitation.

When Ubuntu first begins to load, do you see a line like "Press Esc for a menu"?

---

### Post by dorado29 on 2009-02-21
yeah i can choose between generic, recovery mode and nemstat86(?)

---

### Post by yther on 2009-02-21
OK, then you have the option of doing a little work to extend the menu, which will add a choice of booting from CD.  It involves installing a package and editing your GRUB menu file.

I recommend you visit this thread and either print it, or do it while booted into Ubuntu so you can copy and paste:  [HowTo: Add a menu entry to grub to boot from CD](http://ubuntuforums.org/showthread.php?t=168693)

The procedure there needs to be done in a terminal window.

In step 4 you will need to edit a file as root.  Assuming you're using Gnome, push Alt+F2 and type "gksudo gedit /boot/grub/menu.lst", then continue the procedure.

If that works, you should now have a new line in your menu called "Smart Boot Manager," which should allow you to boot to any device it recognizes.

Good luck!

---

### Post by dorado29 on 2009-02-21
should i continue with the procedure all in the terminal if alt+F2 didn't do anything?

edit: i have no idea how to do step 4: "Add the following lines to the end of /boot/grub/menu.lst"

if someone wants to help me out for like 5 minutes on aim my sn is rwc221

---

### Post by yther on 2009-02-21
Step 4 is the part about editing the file.  Gedit is a text editor, but doing it as a normal user you wouldn't have permission to save it, so you have to do it with advanced permissions.  (It's like "Run as Administrator" in Windows.)

Try just doing this in the terminal when you get to that step:

```
gksudo gedit /boot/grub/menu.lst
```

After making the changes, save the changes and quit the editor.

---

### Post by dorado29 on 2009-02-22
crappy

so i just wrote this in

________________________________________________________
title           Smart Boot Manager
root            (**hd0,1**)
kernel          /boot/memdisk
initrd          /boot/sbm.bin
boot
________________________________________________________

apparently i have to get the root to be the place i boot from. This shouldnt be a problem because i tried to do a memtest and it shows up in the gedit thing but the root of that memtest doesnt show up,

________________________________________________________
title          ubuntu 8.10, memtest86+
uuid           6a122a96-5464-44ad-9d22-3dcbe014f6a2
kernel         /boot/memtest86+.bin
quiet
________________________________________________________

i dont have a root to my cd drive that i can copy from the memtest i *tried* to do

---

### Post by yther on 2009-02-22
Right.  In a GRUB setup, "root" refers to the drive it looks at to start booting.  So if you have everything on your only hard drive, most likely all your menu entries have "root (hd0,1)"... **but if they don't say that, change it to what they do say**.  If they all have this "uuid" then copy that.

You are not telling GRUB to load the CD directly.  You're telling it to load **memdisk**, and telling memdisk to load that sbm.bin file.  Then SBM (Smart Boot Manager) will start up, and you can point it to your CD and boot that.

Following the guide, try this for yours:

```
title Smart Boot Manager
uuid 6a122a96-5464-44ad-9d22-3dcbe014f6a2
kernel /boot/memdisk
initrd /boot/sbm.bin
boot
```

Sorry for the confusion there.  I didn't realize Ubuntu's config files were using all UUIDs now.  :shock:

Double-check that both **sbm.bin** and **memdisk** are in the /boot folder.  (Remember, sbm.bin came from the install CD.)  If they are both in there, that menu item should get you going.

---

### Post by dorado29 on 2009-02-22
Thank you for all the help yther :D :D (may i ask what/ where the name yther comes from? Hah im curious

I'll try to finish everything up tomorrow after i get some sleep, hopefully i dont have to bog down the forum with too many more questions

---

### Post by yther on 2009-02-22
Yeah, get some rest and things may seem clearer after that!

As for the name, a long time ago on IRC, I randomly wanted the nickname "aether" but it was taken, so I made up this one.  

Now I'm going to bed, too.  I hope this gets you sorted out.  :)

---

### Post by dorado29 on 2009-02-22
nice now i just have to get sbm.bin and memdisk in the /boot folder

.....which i dont know where the boot folder is. i also dont have the disc that i used to install ubuntu

during startup it said "loading grub from (hd0,0) ext3," perhaps that is the root i should be using?

---

### Post by dorado29 on 2009-02-22
nvm after it said the (hd0,0) one it had the long uuid code so i guess the long code is the right root now i just need to get the two things into the boot folder

---

### Post by yther on 2009-02-23
OK, I believe I have a solution for you.

Go [here]("http://ubuntuforums.org/showthread.php?p=2237979#post2237979") and download the "sbm.tar" linked in the first post.  Make sure you know where you saved it, for example in /home/yourname or /home/yourname/Desktop or whatever.

That file contains **sbm.bin** and **memdisk**.  Now you need to put those files in **/boot**.  So do this:

```
cd /boot
sudo tar xvf /home/yourname/sbm.tar
```

That folder may not be writeable by normal users, so we used "sudo" to extract the files as root.

Now you should have the two needed files in /boot, so the new GRUB menu item should work.

---

### Post by dorado29 on 2009-02-23
okay i d/l'ed the sbm.tar file and moved it to my ubuntu machine's desktop via a flash drive and drag dropping. after  entering the above commands in a terminal it said "cannot open, no such file or directory. error is not recoverabl: exiting now"

---

### Post by dorado29 on 2009-02-23
anyone? im not sure why the files can't be opened because theyre sitting on my desktop atm hah

---

### Post by gallaau on 2009-02-23
If they are on your desktop you should do... 
cd /boot
sudo tar xvf /home/yourname/desktop/sbm.tar

Make sure you use the path exactly right, unix is case sensitive. I think it is a capital D in Desktop ... my machine is not up at the moment or I would look.

---

### Post by laffinet on 2009-02-23
It is capital D for Desktop. And make sure you replace "yourname" with your actual user name.

---

### Post by dorado29 on 2009-02-24
i got the 2 files into the correct folder but it still isn't booting from the disc. It is seeing files, meaning i can browse whats on a disc through ubuntu desktop, but it still isn't booting from them. Strange because my laptop booted up from disc right away and this is the same disc...

---

### Post by yther on 2009-02-25
So does GRUB let you activate Smart Boot Manager or not?  The new entry in GRUB should let you arrow down to SBM, hit Enter, then you get a screen (see [here]("http://sourceforge.net/project/screenshots.php?group_id=4185")) which lets you select available devices and try to boot them.

With the CD in the drive, you pick the CD drive and hit Tab for a menu, and I believe you just have to choose "Boot device" from there.  (I've used it before, but it's been a while.)

So do you get to SBM now?

---

### Post by dorado29 on 2009-02-25
Yeah i can get to smart boot manager but the option to boot from disc isnt there with either disc drive installed. Is there a way to boot from a flash drive through SBM?

---

### Post by Old *ix Geek on 2009-02-25
> **dorado29 said:**
> hold'em manager, full tilt poker, poker stars, poker tracker 3 are just some of the softwarez that i need to run, including some hotkey scripts, but i havent looked into any of those yet. i play online poker lolI recently downloaded and installed PokerStars so I could test it for another person on this forum, and it runs FLAWLESSLY on 8.10 [under wine, of course]. Did you even try? :confused:

---

### Post by dorado29 on 2009-02-25
no i haven't tried it..

trying it would involve getting certain stuff to work (my PCI card to be exact) which would involve reading stuff from discs (drivers) which doesn't work atm

---

### Post by yther on 2009-02-25
> ... the option to boot from disc isnt there with either disc drive installed.

I'm not sure I understand.  Do you have two CD drives?  :?

Does SBM even show the CD drive as an option?

Have you made sure the drive actually works?  When you put a disc in and close the tray, do you hear it spin up?

I understand that it obviously worked at some time, because that's how you installed Ubuntu, but I'm wondering... have you done anything inside the case?  Maybe the CD drive got unplugged or loosened?

I hate to fall back to "it's a hardware problem" but at this point it sounds like that could be the case.

---

### Post by dorado29 on 2009-02-25
the discs spin up in the drive(s). I tried the one that's mounted in the machine and then i tried another drive that i took out of my parents' desktop and just plugged in. one was sata and one was IDE.

afaik they both work normally, this just showed if the mounted one was broken. CDROM is missing from the SBM menu

---

### Post by sgosnell on 2009-02-25
The online poker will work fine under wine.  Just 'sudo apt-get install wine', then use firefox to download the Windows executables, and run them.  Wine will take care of the install.

---

### Post by dorado29 on 2009-02-26
> **sgosnell said:**
> The online poker will work fine under wine.  Just 'sudo apt-get install wine', then use firefox to download the Windows executables, and run them.  Wine will take care of the install.

i suppose i could do that, but that wouldn't solve the "i can't boot from a disc" problem ;)

---

### Post by sgosnell on 2009-03-01
When the boot process starts, you should get a prompt to press F2, Del, or some other key to enter setup.  Press that key, and you will get the BIOS setup menu.  Go to the Boot tab and make sure the CDROM is set to be the first drive to boot.  Press F10 to save the settings, and you should be able to boot from the CD.  When changing operating systems, it's often necessary to change BIOS settings.

---

### Post by linux_tech on 2009-03-01
> **dorado29 said:**
> i suppose i could do that, but that wouldn't solve the "i can't boot from a disc" problem ;)

Pressing F12 during boot also works on some computers to bring up boot menu
to be able to select cdrom

---

### Post by bogiestl on 2009-04-18
Not to completely flog a dead horse, butI ran into a spot where I couldn't get a CD to boot, and if I recall correctly, I solved it by switching from a USB keyboard to a "traditional plug" keyboard... I needed to use the keyboard to monkey with stuff, but the keyboard didn't yet know it was a keyboard, so...
 
Maybe worth trying or remembering?

---

### Post by causeitsme on 2009-04-18
> **dorado29 said:**
> It is seeing files, meaning i can browse whats on a disc through ubuntu desktop, but it still isn't booting from them. Strange because my laptop booted up from disc right away and this is the same disc...

I believe what you are saying is you can browse the files which are stored on the CD in Ubuntu's file browser.

If that is true then the .iso on the CD needs to burned as an image. You'll need to save it to the hard drive somewhere, I recommend you just drag it to the desktop.

To burn the .iso you just dragged to the desktop:

In Ubuntu 8.10 place a blank CD in the drive, when the box pops up asking you what you want to do click 'cancel', navigate to the .iso and right click it, choose the *_top_* 'Write to Disk' option, then in the pop up box click 'Burn'. 

This will burn an image file which is bootable.

---

### Post by DGortze380 on 2009-04-18
> **causeitsme said:**
> I believe what you are saying is you can browse the files which are stored on the CD in Ubuntu's file browser.

If that is true then the .iso on the CD needs to burned as an image. You'll need to save it to the hard drive somewhere, I recommend you just drag it to the desktop.


Ummm... no.

If it was burnt correctly he SHOULD see files (plural) on the disk.

---


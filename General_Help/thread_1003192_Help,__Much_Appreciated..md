---
title: "Help,  Much Appreciated."
date: 2008-12-05
forum: General Help
---

### Post by SBDxAric on 2008-12-05
Hi guys, i have just signed up to be a member and i look forward to enjoying my time here. Anyways, today, when i was installing Ubuntu 8.10 the EASY way one of my friends messed with it while it was installing while i was in the bathroom :oops: 
Blah blah.. didnt install whatever. I restarted my desktop (Which is a Windows XP Media Center Edition), and tried to reinstall, but when i did, it said: "Ubuntu is already installed. Would you like to uninstall it?" So i went ahead and uninstalled it. When i tried to reinstall, i got an error message:
"Error opening file for writing: C:\ubuntu\install\*********"
It gave me the option to Abort, Retry, or Skip. I retried, it failed again. Then i chose skip. And the same error came again, only with a different file in side "ubuntu\install"
I have no idea what to do. Thank you in advance, im sorry if the answer to this was already posted somewhere, but i couldnt find any through the "Search" bar.

---

### Post by SBDxAric on 2008-12-05
Also i am rrunning Windows XP SP# Media Center Edition. I am using the guide found [here](http://seogadget.co.uk/the-ubuntu-installation-guide/).

---

### Post by Partyboi2 on 2008-12-05
Try deleting the C:\ubuntu folder and running the installer again.

---

### Post by SBDxAric on 2008-12-05
I try, but every time i try and open it it says access denied (whenever i try and open C:\ubuntu)

---

### Post by balaknair on 2008-12-05
You'll need administrator privileges, I guess, to delete C:\Ubuntu. Can you log in as Administrator on your Windows machine?

I'm not sure what else could cause this issue(I haven't played around with Wubi much).

An alternative option is to boot from the Live CD(the Ubuntu CD), and delete the Ubuntu installation that way, and then boot into Windows again and use the Wubi installer. 

 Of course you can always install Ubuntu in its own partition by booting from the Live CD, though then removing it later becomes harder if you don't like Ubuntu.

---

### Post by SBDxAric on 2008-12-05
thnks for the help! I will try it and get back to you guys tommorrow after I try. 

I don't want to try the livecd though...

---

### Post by sheishkabob on 2008-12-05
> **SBDxAric said:**
> I try, but every time i try and open it it says access denied (whenever i try and open C:\ubuntu)

One annoying thing I've found that XP does is tag a file as "in use" when it isn't. I've shut down all but critical programs, and it still won't let me edit a folder. It says either "access denied" or "file in use" or something along those lines.

If using Administrator priveledges as mentioned before does not work, try starting in safe mode. It should let you delete it then.

---

### Post by magmon on 2008-12-05
> **SBDxAric said:**
> thnks for the help! I will try it and get back to you guys tommorrow after I try. 

I don't want to try the livecd though...

The live CD works very well for partitions, and deleting partitions is easy enough.. Not wubi easy, but easy. I would recommend a partition anyway, because wubi has been reportedly unstable.

---

### Post by Jammanuser on 2008-12-05
> **magmon said:**
> I would recommend a partition anyway, because wubi has been reportedly unstable.

Agreed...i would **definitely** recommend installing Ubuntu 8.10 on a separate partition, as well!!! That way it wont be in contact at ALL with anything Microsoft has made... :D

Cheers! ;)

-jammanuser

:D

---

### Post by balaknair on 2008-12-05
OK, will check back tomorrow.

You should keep in mind that Wubi installs are generally slower than native installs of Ubuntu, though the drop in performance isn't noticeable if you have a decent spec machine.
The other reason I advise trying to boot from the LiveCD is that you can try out Ubuntu without making any changes to your PC, and you can therefore check to see if Ubuntu is indeed compatible with your hardware. Some motherboards etc have non-standard BIOS tweaked to make Windows XP compliant with ACPI, and though I've never encountered problems with Ubuntu 8.10, I know that the Ubuntu 8.04 LTS wouldn't boot up on my aging desktop machine. Another potential problem area is if you use certain ATI graphics cards, meaning you won't be able to directly able to use the GUI(you have to boot into 'Safe Graphics Mode', install Ubuntu, and then update to the latest ATI drivers).
So using the LiveCD to try out Ubuntu before making any changes to your PC is actually advisable.

As for your specific problem, I just wonder... Try this- restart XP in safe mode, and then delete the /Ubuntu folder. Restart and boot into XP normally, and reinstall Ubuntu via Wubi. Before you do that though, I again urge you to try Ubuntu from the LiveCD, just to get an idea about hardware compatibility(if you can run it from the CD without problems, great. If you do experience any issues, there are workarounds for most problems, but in my mind, it's always better to be prepared).

All the best.

---

### Post by Jammanuser on 2008-12-06
> **balaknair said:**
> OK, will check back tomorrow.

You should keep in mind that Wubi installs are generally slower than native installs of Ubuntu, though the drop in performance isn't noticeable if you have a decent spec machine.


A "drop in performance" wasn't **exactly ** what i had in mind when i made my above post! ^ ;) TRY a "crc error" that **completely** shuts down ur Wubi install of Ubuntu, and doesn't allow u to boot into it anymore...EVER!!! :D

Cheers! :)

-jammanuser

:D

---

### Post by balaknair on 2008-12-06
> **Jammanuser said:**
> A "drop in performance" wasn't **exactly ** what i had in mind when i made my above post! ^ ;) TRY a "crc error" that **completely** shuts down ur Wubi install of Ubuntu, and doesn't allow u to boot into it anymore...EVER!!! :D

Cheers! :)

-jammanuser

:D

Yes I can see how that could ruin your day. :(
I was referring to the performance drop from installing Linux on NTFS though(which I'm sure you understood).

As I said before, I haven't used Wubi much, only once in fact, when my sister-in-law got a new laptop I just wanted to try the Wubi installer(right after 8.04 was released). It seemed OK when I tried it, though I didn't use that set up for long. I formatted the drive after that to install XP + Ubuntu 8.04 64-bit as a dual boot configuration with a shared /Home folder(in ext3, and fs-driver in Windows to enable access from both OS) since she didn't want Vista. And Ubuntu was noticeably faster with its own ext3 partition, plus Suspend/Resume worked flawlessly(it didn't work with the Wubi-on-Vista install).

Anyway, from your comment about crc error(and yes I read your 'Booting from commands' thread while searching for info for help with this thread) it could be what messed up our friend's installation too. I also heard that Wubi in Ibex seems to be prone to failures, but then again, it's just hearsay.

By the way, I hope you find a fix for the crc error you had. I'll look around and if I come across something I'll post in your thread. Wishing you luck.

Cheers :D

---

### Post by SBDxAric on 2008-12-06
> **Jammanuser said:**
> A "drop in performance" wasn't **exactly ** what i had in mind when i made my above post! ^ ;) TRY a "crc error" that **completely** shuts down ur Wubi install of Ubuntu, and doesn't allow u to boot into it anymore...EVER!!! :D

Cheers! :)

-jammanuser

:D
:shock:
Alrite i will try the liveCD right now to delete the folders, then go safe mode if that dont work..

---

### Post by Jammanuser on 2008-12-06
> **balaknair said:**
> Yes I can see how that could ruin your day. :(
I was referring to the performance drop from installing Linux on NTFS though(which I'm sure you understood).


yah...i understood what u meant...i just wanted to make sure that the original poster understood the risks of using Wubi, instead of installing Ubuntu 8.10 on a separate partition, which would naturally work better, not only because ur less likely to have a "crc error" like me, but also because, like u said, the drop in performance when Linux in installed on NTFS filesystem, instead of ext3! ;)

> **balaknair said:**
> 
As I said before, I haven't used Wubi much, only once in fact, when my sister-in-law got a new laptop I just wanted to try the Wubi installer(right after 8.04 was released). It seemed OK when I tried it, though I didn't use that set up for long. I formatted the drive after that to install XP + Ubuntu 8.04 64-bit as a dual boot configuration with a shared /Home folder(in ext3, and fs-driver in Windows to enable access from both OS) since she didn't want Vista. And Ubuntu was noticeably faster with its own ext3 partition, plus Suspend/Resume worked flawlessly(it didn't work with the Wubi-on-Vista install).

Anyway, from your comment about crc error(and yes I read your 'Booting from commands' thread while searching for info for help with this thread) it could be what messed up our friend's installation too. I also heard that Wubi in Ibex seems to be prone to failures, but then again, it's just hearsay.

By the way, I hope you find a fix for the crc error you had. I'll look around and if I come across something I'll post in your thread. Wishing you luck.

Cheers :D

Thanks...I'm **also** still looking for a fix to the crc error (one of the posters on the "Booting with commands" thread suggested something that i **think** may work!). I haven't given up...**yet**! :) Anyway, i appreciate the support, and am glad that **some** people, at least, understand how much the "crc error" SUCKS, and realizes that **someone** needs to come up with a fix for it soon on Wubi! ;)

Cheers! :)

-jammanuser

:D

---

### Post by Jammanuser on 2008-12-06
> **SBDxAric said:**
> :shock:
Alrite i will try the liveCD right now to delete the folders, then go safe mode if that dont work..

So i **assume** deleting the folders with administrative privileges did not work for u then, correct?

If that is the case...then, yeah, i think u should try using the LiveCD to do it! ;)

Cheers! :)

-jammanuser

:D

---

### Post by SBDxAric on 2008-12-06
yah, it didnt work... umm about the seperate pertition.. is it hard to  do? How should i go about doing it?

---

### Post by Jammanuser on 2008-12-06
> **SBDxAric said:**
> yah, it didnt work... umm about the seperate pertition.. is it hard to  do? How should i go about doing it?

ok...how about the Live CD? and NO, installing Ubuntu 8.10 on a separate partition isn't hard to do...u just need a partitioning software (like Gparted, which can be found on the LiveCD, as well!) to create the partition, on which u later install Ubuntu on! 

Gparted can be found (after booting the LiveCD) under System>Admin>Partition editor. The process to create a partition using Gparted is pretty simple, and straightforward...u should be able to figure it out by yourself! ;)

Cheers! :)

-jammanuser

:D

---

### Post by balaknair on 2008-12-06
Actually, the LiveCD option is pretty simple.
Just a few steps.
Before you start, however, backup all important files on Windows and defragment your hard disk.

1) Put the CD in your CD drive and restart so that the PC will boot from the CD
2) It'll boot normally(provided your PC BIOS is set to enable 'Boot from CD', so ***if*** on restarting with the CD in the drive, it boots into Windows directly, you might need to change this setting in BIOS)
3) Once it boots into Ubuntu from the CD, you'll be asked to select a language, then you'll get a bunch of options, choose the first one(Try Ubuntu without Changes to your computer)--> Now Ubuntu will start up.
4) Once you get to the Live Session desktop, you'll see two icons on the desktop, one of which is labelled 'Install'. Double click on it to install. You can also choose to mess around with the LiveCD desktop environment a bit- browse with firefox, or play games etc.
5) Double clicking on the Installer starts the Install Application, which will guide you step by step through configuring and installing Ubuntu as dual boot(or any boot scheme you want), including partitioning the hard drive. It's pretty straightforward, and usually you'll be done with about 6-7 clicks.

If you're confident about doing a manual partition, you can also set up a custom partitioning scheme with a seperate /Home partition, /boot partition etc, all of which have their own advantages. It's all relatively straightforward and simple, but if you're not feeling adventurous, just go with default option Ubuntu gives you- 'Guided resize'

I strongly suggest you read this page here
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

before starting to install. It's very helpful, with screenshots of each step.

If you're interested in a custom partitioning scheme, you can also read up on how to plan partitions for a dual boot setup here
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

There's a lot of other interesting(and very noob-friendly and useful) information on that site. It's written by aysiu, one of the moderators and long time members here at ubuntuforums. I personally found it very useful when starting out with Ubuntu, and I still refer to it often.

Hope this was useful, have fun with Ubuntu.
All the best.

---

### Post by SBDxAric on 2008-12-06
> **balaknair said:**
> Actually, the LiveCD option is pretty simple.
Just a few steps.
Before you start, however, backup all important files on Windows and defragment your hard disk.

1) Put the CD in your CD drive and restart so that the PC will boot from the CD
2) It'll boot normally(provided your PC BIOS is set to enable 'Boot from CD', so ***if*** on restarting with the CD in the drive, it boots into Windows directly, you might need to change this setting in BIOS)
3) Once it boots into Ubuntu from the CD, you'll be asked to select a language, then you'll get a bunch of options, choose the first one(Try Ubuntu without Changes to your computer)--> Now Ubuntu will start up.
4) Once you get to the Live Session desktop, you'll see two icons on the desktop, one of which is labelled 'Install'. Double click on it to install. You can also choose to mess around with the LiveCD desktop environment a bit- browse with firefox, or play games etc.
5) Double clicking on the Installer starts the Install Application, which will guide you step by step through configuring and installing Ubuntu as dual boot(or any boot scheme you want), including partitioning the hard drive. It's pretty straightforward, and usually you'll be done with about 6-7 clicks.

If you're confident about doing a manual partition, you can also set up a custom partitioning scheme with a seperate /Home partition, /boot partition etc, all of which have their own advantages. It's all relatively straightforward and simple, but if you're not feeling adventurous, just go with default option Ubuntu gives you- 'Guided resize'

I strongly suggest you read this page here
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

before starting to install. It's very helpful, with screenshots of each step.

If you're interested in a custom partitioning scheme, you can also read up on how to plan partitions for a dual boot setup here
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

There's a lot of other interesting(and very **noob**-friendly and useful) information on that site. It's written by aysiu, one of the moderators and long time members here at ubuntuforums. I personally found it very useful when starting out with Ubuntu, and I still refer to it often.

Hope this was useful, have fun with Ubuntu.
All the best.

:evil:

Okay, so maybe i am... for now. Before, I was only doing this to get iPhone Linux, but now i want to learn more about Linux and its open-source features :)

---

### Post by Jammanuser on 2008-12-06
i have nothing to add to what balaknair wrote...save to say that the BIOS can be reached when booting ur computer by pushing F2 right before ur computer's manufactur's page (in my case, the Dell page!) finishes loading! This will send u to the BIOS menu, after which u can select Boot options (i think its called), and then selecting the CD/DVD drive, press "u" to move the entry up, and move it to the top...then save the changes u made by pushing Enter, and then Esc...and then "Save changes"! 

Hope this helps! ;)

Cheers! :)

-jammanuser

:D

---

### Post by SBDxAric on 2008-12-07
eeeeeek the ubuntu file dissapeared that i couldnt delete!!!!
should i delete ubuntu backup as well? too late, i already did...

---

### Post by SBDxAric on 2008-12-07
Thanks guys.. the ubuntu file i couldnt delete dissapeared. No idea how. And in its place a system file appeared called %SystemDrive%
My computer is acting a bit abnormally.....

---

### Post by balaknair on 2008-12-07
Are you still booting into Windows, and is that where you are seeing the %SystemDrive% file?
And did you defragment your drive or do a disk cleanup?

And BTW, I'm not sure what the Ubuntu backup you referred to is(probably doesn't matter anymore, since you've deleted it :D .

The file disappearing isn't a bad thing, it might have been deleted by the Wubi uninstaller on restart(the operation might have been pending and maybe happened only now because it was earlier denied permission to execute at Windows start up), or perhaps Windows might have found this file(unknown type, according to Windows), with bad registry keys(due to the broken uninstall process or a bad install process) and deciding it's junk might have moved it to a Found.000 folder.

I would suggest doing a disk defragmentation, then run a disk check and cleanup. If you have any tools to scan and fix your registry, do that too. This should clear up any debris or remnants of the failed Wubi Install/Uninstall process, especially since we don't know what exactly went wrong.

Once you've done all that, you can be more or less sure that your Windows install is as it was before you installed Wubi.

After that, you can decide what you want to do about Ubuntu- 
1) Install in seperate partition
2) Install with Wubi
3) Avoid installing Ubuntu.

My personal choice would be to install it in a seperate partition, but Wubi installs have the advantage that they are (usually) easier to remove if you don't like Ubuntu. That is provided the installation goes OK(in the rare cases when it doesn't, as it happened in your case, it's still usually possible to recover, but still troublesome).

If you're interested in giving Ubuntu a try, what I suggest is -

1) Use the Live CD and boot up with it, run the various apps like firefox(avoid sites with flash(like youtube) for now, though, you can install flash after installing Ubuntu), pidgin instant messenger, play some simple games, there'll be some sample files in the 'examples' folder, watch the video samples, listen to the sample audio files, open the open office files and slideshows, and hook up any additional hardware like digital cameras so you can get a feel of what the OS is like, and you can also make sure your hardware is supported. The LiveCD will be much slower than an actual install, but you can still try out the user interface and overall layout.
2) Read the material by aysiu at [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) including the intro and also this post by aysiu at [http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315) (Is Ubuntu for you?). If you know what Ubuntu is, you can make it work for you and enjoy it better.
3) After 1) and 2), now you can make a decsion whether you want to try it further with Wubi or if you're ready to take the plunge and partition your hard disk for a proper dual boot system(or even if you're ready to wipe Windows comletely off your drive and istall Ubuntu as sole OS).

Whatever decision you take, if you need any further help with Ubuntu(or with another distro, or even with Windows), you can always try ubuntuforums. 

Wishing you luck.

All the best.

---

### Post by SBDxAric on 2008-12-07
Thanks man, will do. Sorry for double post.
Im gonna go ahead and make a seperate partition, i think i can do this on my own :D
It is weird thogh as i dont have a clue what to do with %SystemDrive%
Ill figure it out.

---

### Post by balaknair on 2008-12-07
Be sure to defrag your hard drive before you start though.

---

### Post by Jammanuser on 2008-12-07
> **balaknair said:**
> Be sure to defrag your hard drive before you start though.

Yeah...otherwise u may end up losing data when it creates a partition! ;)

Cheers! :)

-jammanuser

:D

---

### Post by SBDxAric on 2008-12-07
hehehehe okay :P
Anyways lessay i wanna uninstall it. Is there anyway to delete the partition and GRUB without the use of an XP setup cd?

---

### Post by Jammanuser on 2008-12-07
> **SBDxAric said:**
> hehehehe okay :P
Anyways lessay i wanna uninstall it. Is there anyway to delete the partition and GRUB without the use of an XP setup cd?

yeah...u can use Gparted on the Ubuntu Desktop CD (System>Administration>Partition editor) to delete the partition...or u can use whatever software u used in the first place to **create** the partition! ;)

Cheers! ):P

-jammanuser

:D

---

### Post by SBDxAric on 2008-12-07
Thank You!!!!!!!
iPhone Linux, Here I Come!!!

---

### Post by balaknair on 2008-12-07
Hang on a second- :!:

Deleting the Ubuntu partition is easy(you can do so within Windows itself, Conrol Panel>System management>Disk Management), but restoring the MBR(the master boot record) after removing GRUB is slightly more complicated.

Basically the MBR is the first 512 bytes on your first hard drive, which points the computer to the places where the first file needed to open the boot menu(boot.ini in XP, GRUB.lst in Linux(I don't remember the exact filename)). Right now it points to the Windows boot.ini, but with Ubuntu installed on a separate partition, it will point to GRUB.lst. So after removing Ubuntu and GRUB, you want it to point at boot.ini again, or **your PC will not boot**

**Option 1:** The safest option imo, use the XP installation CD(you're using XP media center edition, right?). Steps to follow - Boot from the XP CD--> You get options like install, repair etc.--> Choose &#8220;Repair&#8221;--> You get to a command prompt--> type in the command 'fixmbr'--> Press enter when asked for Confirmation--> reboot

[**NOTE:** *You should know a few facts about your installation before you do this though. The fixmbr command creates a new MBR pointing to the beginning of the first partition(C:\) where in most cases the boot.ini file will be. In some **laptops** however, the first partition might be a 'recovery partition' put there by the manufacturer. So if you're using a laptop here, or a heavily customized PC and Windows is not on C:\ you must specify the partition. Also steps for Vista are slightly different. It's easy enough to find out the correct lines, but just things to keep in mind*]

**Option 2:** Use other tools to fix the MBR

a) Use a MBR backup utility to create a backup of your MBR ***before*** you install Ubuntu or partition the drive. Afterwards, you can use this to restore the saved MBR from a recovery floppy or Cd/DVD if you remove Ubuntu.

b) Use a Rescue CD which can fix the MBR.

Examples of such tools include HD Hacker and Super Grub Disk respectively. I haven't used HD Hacker, but some friends have and they claimed it's easy(I don't know how easy you'll find it, those people were big time geeks, but it seems simple enough).

If you want an illustrated guide on how to use SGB I recommend
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk)

(specific part of the guide you need: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows) )

All this comes into play only if you need to remove Ubuntu. I'm pretty confident that if you stick with Ubuntu for a while(2-4 weeks maybe) you'll probably be using Ubuntu as your main OS, because seriously, Ubuntu Rocks :guitar: 

I hope you find this useful.
Lots of luck- ):P

---

### Post by SBDxAric on 2008-12-07
I most probably will, but this is a HUGE risk for me.
My desktop seems weird these days... i have used spybot, mcafee, and a whole bunch of other BS to search for malware and viruses. Nothing. If something screws up here (and things are screwing up alot for me lately),
I will probably by a new Desktop, and i really dont want to. Im taking every precautionary step possible before installing GRUB and Ubuntu.

PS What if you do not have the XP CD? My desktop came preloaded with XP.
I think i mentioned this Before But it is:

Windows XP Media Center Edition SP3 64 bit(? im guessing)

---

### Post by Jammanuser on 2008-12-07
OH...right! :o balaknair is right...i forgot about fixing the MBR after deleting Ubuntu! yes! u will need to first create a backup of the MBR, like he said, **before** deleting Ubuntu! otherwise u will not be able to boot into Windows afterwards...of course all this is assuming (i THINK!) that u did not hide the Windows partition **first**, before u installed Ubuntu on a separate partition! I'm pretty sure that if u do, then u will not have that problem, and deleting Ubuntu wont mess up the MBR...simply because it will still be pointed to boot.ini, due to having used a program like [EasyBCD]("http://neosmart.net/dl.php?id=1") to add Ubuntu to the **Windows** bootloader, which will have eliminated the need to use the Grub bootloader! ;)

Cheers! :p

-jammanuser

:guitar:

EDIT: never mind...I have used EasyBCD since, and it seems it still requires Grub in order to boot a Linux partition. I guess I was assuming that it didn't require Grub...anyway, I was wrong, so just ignore that last part of this post. However, there is a way to install Grub to the partition's boot sector, instead of the MBR, and if you need any help with that, then let me know. Cheers! :D

---

### Post by Jammanuser on 2008-12-07
> **SBDxAric said:**
> I most probably will, but this is a HUGE risk for me.
My desktop seems weird these days... i have used spybot, mcafee, and a whole bunch of other BS to search for malware and viruses. Nothing. If something screws up here (and things are screwing up alot for me lately),
I will probably by a new Desktop, and i really dont want to. Im taking every precautionary step possible before installing GRUB and Ubuntu.

PS What if you do not have the XP CD? My desktop came preloaded with XP.
I think i mentioned this Before But it is:

Windows XP Media Center Edition SP3 64 bit(? im guessing)

That's good to know! :p that is, that ur going to take every precaution! 

as for what to do if u do not have the XP CD, i think i already answered that in my other posts! :guitar:

Cheers! ):P

-jammanuser

:popcorn:

EDIT: in case u didn't understand what i meant...I was speaking about first creating a partition, using whatever program u want, but **first** (BEFORE) creating the partition, **hiding** it using the Ubuntu Live CD (i.e. Gparted), and then when u want to delete Ubuntu, and its dedicated partition, then u simply just delete it using Gparted or whatever program u used to **create** it...and the MBR won't be messed up! Cheers! :D

---

### Post by balaknair on 2008-12-07
Hmmm...
AFAIK, WinXP MCE does not have a 64 bit version, so you're probably using the regular 32 bit version.
(to check for sure, Start Menu--> Run--> type 'winver'--> This opens a pop-up window with info about OS version. Alternatively in Run type 'winmsd'--> a sysinfo window opens--> In the right hand pane, look for 'Processor'--> If the description for Processor begins with x86, you have a 32 bit OS, if it begins with ia64 or AMD64, you have 64 bit Windows)

That aside, 'system weirdness' can be due to many reasons, including malware, registry errors, OS rot, disk fragmentation etc. Try doing a comprehensive system maintenance- 

1) Use the Add/Remove programs to remove all those crappy programs you don't use(which you installed just to try them out, or when you have multiple programs which do the same task, but you only one) or are buggy/outdated, and get rid of those IE/Firefox toolbars. Apps like iTunes/Quicktime, Winamp and Acrobat Reader also slow up WinXP start up by insisting on starting up with Windows. Use MSConfig or a Windows tweaking tool like Evonsoft Computer Repair or System Mechanic to fix this for those apps you don't use frequently.
(You can use a tool like Secunia PSI to find insecure and outdated programs [http://secunia.com/vulnerability_scanning/personal/](http://secunia.com/vulnerability_scanning/personal/) , it's a great program, highly recommended).
Fewer apps= cleaner system= better performance
2) Do a full system scan with your antivirus app till it reports zero infections. If you feel your current AV suite is missing malware, use an online scan as well to confirm(good online scans- TrendMicro Housecall and BitDefender Online Scan
[http://housecall.trendmicro.com/](http://housecall.trendmicro.com/)
[http://www.bitdefender.com/scan8/ie.html](http://www.bitdefender.com/scan8/ie.html) )
Also do a scan with Spybot S&D to remove pesky spyware.
3) Scan for junk files and clean up the PC (Use the Disk Clean Up tool in XP, or a free tool like C Cleaner or Evonsoft Computer Repair)
4) Scan the Registry for invalid entries, clean up and compact the registry(Evonsoft Computer Repair does all this, another good app for this System Mechanic)
5) Defragment the hard drives

At the end of all this(it'll take quite a while, especially if you have a large hard drive :popcorn: ), you will have eliminated most software causes for 'system weirdness' and ought to see a noticeable improvement in performance.

For hardware issues, well, that's another story. There're tons of hardware monitoring and diagnostic apps and gadgets, but it's probably safer to get an authorized service tech to check your computer unless you absolutely know what you're doing.

OK, quite a long post. Hopefully some of this will be helpful to you.

Have fun with Ubuntu now. ):P
All the best.

---

### Post by SBDxAric on 2008-12-08
> **Jammanuser said:**
> That's good to know! :p that is, that ur going to take every precaution! 

as for what to do if u do not have the XP CD, i think i already answered that in my other posts! :guitar:

Cheers! ):P

-jammanuser

:popcorn:

EDIT: in case u didn't understand what i meant...I was speaking about first creating a partition, using whatever program u want, but **first** (BEFORE) creating the partition, **hiding** it using the Ubuntu Live CD (i.e. Gparted), and then when u want to delete Ubuntu, and its dedicated partition, then u simply just delete it using Gparted or whatever program u used to **create** it...and the MBR won't be messed up! Cheers! :D

I really do not understand this method...

---

### Post by SBDxAric on 2008-12-08
This is SBDxAric posting with his new Linux machine....
I did not do the full installation, my grandmother has just passed away and i dont have time, i will do it when i get back. :(

---

### Post by balaknair on 2008-12-08
Sorry to hear that SBDxAric.

I'd just read your previous question and was typing out another long response, not important now. 

Please accept my condolences, may she rest in peace.

---

### Post by Jammanuser on 2008-12-08
> **SBDxAric said:**
> This is SBDxAric posting with his new Linux machine....
I did not do the full installation, my grandmother has just passed away and i dont have time, i will do it when i get back. :(

yeah...i also i am very sorry that she passed away! :( I offer my condolences as well...as soon as u get back, if u feel up to it, we can work more on ur Wubi problem! 

Cheers! ):P

-jammanuser

:cry:

---

### Post by SBDxAric on 2008-12-31
Well im back.
4 weeks was a bit longer than expected due to some problems...
I will look at EasyBCD right now and explore the world of ubuntu.
Hey ubuntu isnt that hard to use! I dont see why people complain about linux. Its actually pretty nice. So what makes Ubuntu different then other 'Linuxes' like Yellowdog and Arch linux?

---

### Post by SBDxAric on 2009-01-01
hmm problem. whenever i try to do a "rea" install (partitions and such), in the middle of making partitions it gives an error message saying "Partition already mounted"

---

### Post by balaknair on 2009-01-01
Hi.
Welcome back.

> **SBDxAric said:**
> hmm problem. whenever i try to do a "rea" install (partitions and such), in the middle of making partitions it gives an error message saying "Partition already mounted"

Sorry for the delay in replying. My internet connection died last night and got fixed just a short while back.

You cannot partition a drive if it is already mounted. So if you boot from the LiveCD and then access the hard drive, you should unmount it before attempting to partition it.

Open 'Computer', right click on the drive icon(in the screenshot the drives/partitions MISC DUMP and Filesystem are mounted, the other two are not) and select 'unmount'. You can also unmount the partition by clicking on the little 'Eject' icons in the left hand pane of the file browser(screenshot 3). Don't eject the CD though.

Or you can just boot into a new session on the LiveCD and don't access the hard drive, directly starting the installer. The installer will then scan the drive without mounting it.

---

### Post by SBDxAric on 2009-01-02
I will try that
igot ipod touch linux up and running.

---

### Post by SBDxAric on 2009-01-02
on second thought let me first explore the ubuntu enviroment, then ill do a full installation :D

---

### Post by balaknair on 2009-01-02
Whatever works for you.
You can try it out on Wubi for a while till you're sure you want to switch. Anytime you need help, there's always Ubuntuforums.

You can also try installing Ubuntu on a USB device(a thumb drive or external hard drive) or a spare hard drive, to avoid touching your Windows partition altogether. But remember to back up your MBR before you do that(in case you ever want to remove Ubuntu and restore Windows).

Have fun.
Lotsa luck. :D

---

### Post by SBDxAric on 2009-01-03
Hmmm im getting another error on the full installation....
it is Error setting up partition or something like that... ill try again and see what is the error

---

### Post by balaknair on 2009-01-06
> **SBDxAric said:**
> Hmmm im getting another error on the full installation....
it is Error setting up partition or something like that... ill try again and see what is the error

Hi

Was busy shifting to a new house, and had no internet connection since saturday.

Give the install another shot, and if you still have trouble, let's see if we can fix it.

All the best.

---

### Post by SBDxAric on 2009-01-06
okay then

---

### Post by SBDxAric on 2009-01-09
An error has occurred while writing the changes to the storage devices. Resize operation has been aborted.

dangit.

---

### Post by balaknair on 2009-01-11
> **SBDxAric said:**
> An error has occurred while writing the changes to the storage devices. Resize operation has been aborted.

dangit.

Hmmm...
I wonder what went wrong there.

Not something I've come across before.

I'll hunt around to see if I can find possible causes/solutions.

---

### Post by SBDxAric on 2009-01-12
i have no idea how to fix it... i have defragged, deleted files, and everything,

---

### Post by balaknair on 2009-01-12
OK I came across a bug in Launchpad-
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/279778](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/279778)

Other links I found-
[https://answers.launchpad.net/ubuntu/+question/40967](https://answers.launchpad.net/ubuntu/+question/40967)
[http://ubuntuforums.org/archive/index.php/t-955727.html](http://ubuntuforums.org/archive/index.php/t-955727.html)

From what I could make out, it seems to be because "the NTFS volume's dirty bit is set and so the resize refuses to take place in case it would corrupt that volume".

The solutions I found to install Ubuntu
1) Boot into Windows, shut down normally(this will normally clear any pagefile/cache epending operations) and then boot the CD
2) Resize the partition within Windows(Right Click 'My Computer'--> Manage--> in the left hand pane, select Disk management--> select the partition and resize it, but don't format the freed space---> Restart and boot into Ubuntu CD--> at the partitioning step, select 'Use largest contiguous space')

Dirty bits are basically bits in the pagefile or cache memory which were changed but not properly committed to the hard disk. Usually happens when Windows shuts down before the changes can be saved to disk. The other common cause is corrupted bits or bad sectors--> as a result of data corruption/improper deletion etc. or simply because the hard drive is damaged.

I suggest you run a disk check in Windows(Right click the drive icon-> Properties--> Tools--> Check disk for errors'). This ought to fix most errors(except for physical damage to the hard drive).

---

### Post by balaknair on 2009-01-12
Do you have Norton Antivirus installed by any chance? I've read that Norton's Recycle bin protection often leads to the dirty bit to be set 'On'.

---

### Post by SBDxAric on 2009-01-12
Thank you, its a yes to all! i do have norton installed, i do have dirty bits and such! i will try it tommorrow, i have alot of work today

---

### Post by SBDxAric on 2009-01-18
the forum was down for a while.

---

### Post by SBDxAric on 2009-01-18
whenever i use the largest contingious disk space option it shows ubuntu overwritng everything

---

### Post by balaknair on 2009-01-19
> **SBDxAric said:**
> whenever i use the largest contingious disk space option it shows ubuntu overwritng everything

Do you mean that Ubuntu selects the entire disk to install to?
Or does it select the entire freed space?

In order to resize the partition in XP you have to use an external program
like Partition Magic or EASEUS Partition Manager 3(the Home edition is free).
[http://www.pcworld.com/downloads/file/fid,72826-order,1-page,1/description.html](http://www.pcworld.com/downloads/file/fid,72826-order,1-page,1/description.html)

---

### Post by balaknair on 2009-01-19
This is what it would look like after a reboot.

Update: I just tried installing Ubuntu(Kubuntu actually) in the free space(using the largest contiguous space option). It went without a hitch.

Ubuntu assuming the entire hard drive is free isn't a good sign. Can you still boot into Windows?
Could you check to see the space of the C:\ drive(give me an idea how your hard drive is partitioned)

---

### Post by SBDxAric on 2009-01-24
im sorry bout long response, internet was down. I tried it and it worked with no problem! Thank you for your help. Ill be on this forum now maybe once everyday, thanks to you!
I heard linux is great for writing programs, is this true?

---

### Post by balaknair on 2009-01-24
That's great.

Linux has a number of very popular tools for writing programs, but I'm afraid I don't know a lot about them, programming is not my forte.

If you're interested in programming, I suggest going through the 'Programming Talk' category in Ubuntuforums.
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

Have fun.
Bye

---

### Post by SBDxAric on 2009-01-25
Thank you, see you again around the forums!

---


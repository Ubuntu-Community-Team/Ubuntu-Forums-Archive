---
title: "[SOLVED] inspiron 1420n with ubuntuu need help to dual boot with xp"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by blackhowling on 2007-09-01
Just got a new dell 1420n with ubuntu installed and wanted to dual boot it with xp so that I could play games.  I used gparted live cd to make a parition but when I try to load windows xp it doesn't see any drives guessing b/c the dell fills up the main 4 partitions.  
/dev/sda1 fat 16 with 80mb
/dev/sda2 fat 32 with 2gb (guessing rescue partition) 
/dev/sda3 ext3 os_part
/dev/sda4 extended
/dev/sda5 linux-swap
/dev/sda6 ext3
/dev/sda7 unpartition <--- set up with gpart

---

### Post by blackhowling on 2007-09-02
Partition 1 (primary) Utility Partition (UP) n/a 32 MB 
Partition 2 (primary) Reinstall Partition (CP) n/a 2 GB 
Partition 3 (primary) Linux /boot 200 MB 
Partition4 (extended) Extended n/a Swap + rest of disk 
Partition 5 (logical) Swap n/a (1.3 x RAM) + 10 MB 
Partition 6 (logical) Linux / Rest of disk 

Wondering what steps I would need to take to dual boot a 1420 N with pre-installed ubuntu and trying add on windows xp so that I can play games, use photoshop cs3, etc ... 

particularly I need to know where make the partition (tried to make a another partition 7 that was unallocated 20GB made with gpart live cd that was under the extended and made from the partition 6 "Rest of disk" but when i tried to load windows xp sp 2 cd it could not read the hd. Trying to save myself the trouble of wiping the drive & installing windows first than setting up ubuntu from scratch since I just got it fully working.

---

### Post by Kalli on 2007-09-02
It's a SATA drive so the Windows XP disc won't recognize it, it doesn't matter where the partition is. The installation disc expects you to have a floppy drive for some reason and without it you are lost... The only way to get around it (the only way I know of) is to add the SATA driver to the Windows XP installation cd. There are instructions for how to do that on various places on the internet, just google something like "install windows xp sata no floppy" and go from there.

---

### Post by blackhowling on 2007-09-02
Thanks for the info from there I'll be using the n-lite to make another xp cd with the proper sata drivers found on the dell website and will try again.  If it works I'll post what steps i took to dual boot ubuntu / windows xp for the occations I need to edit pics or play games.

---

### Post by blackhowling on 2007-09-03
Steps to dual boot 1420n with ubuntu pre-installed.
First get The GParted LiveCD ISO @ [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
then download your favorite linux live Cd such as 
[http://ubuntu.com/getubuntu/download](http://ubuntu.com/getubuntu/download)
Also keep windows xp, vista or whatever other OS's CD's you want to  install on hand as well. 

other software you might need include
nlite ([www.nliteos.com/](www.nliteos.com/)) to add those sata drives from [http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INS_PNT_PM_1420&hidos=UBLN&hidlang=en](http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INS_PNT_PM_1420&hidos=UBLN&hidlang=en)
to a bootable win xp 

Next step after you gather your tools 
restart click f12 than hit boot from cd
you will need to use Gpart Live CD to make a partition for your new OS this might take a while took me around 40mins->an hr to partition my xp partition.

Next 
If you haven't made a win xp cd with the sata drivers I'd suggest going and downloading nlite than loading the drives from dell just select multi drivers = folder where ever u extracted the files usually C:\dell\drivers\R154200 than with nlite add those drivers to the win xp and create a bootable image.

After that restart your labtop and hit f12 too boot your win xp cd and install it onto your unallocated partition.

after that
Reinstall GRUB to the MBR.
use the ubuntu live CD
Go into the GNOME Partition Editor 
and take off the boot from the windows partition
and make the linux os swap partition 3 as the boot partition again


Now we are going to reinstall the grub since windows over wrote it.
go into terminal 
type:
sudo grub
find /boot/grub/stage1
than depending on your output
type root and whatever the output is ex. (sd0,0)
root(sd0,2) 
setup (sd0)
This restores GRUB to the MBR. 
Type in QUIT and then EXIT
sudo gedit /boot/grub/menu.lst
this will allow you to edit the list 
such as adding in
title Windows XP
root (sd0,6)
makeactivechainloader +1 

now you should be able to dual boot
since I know this is kind of hard to follow below I'll post the links to better resources that give the gist of what to do but not everything.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp#comment-37851](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp#comment-37851)
[http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)
[http://www.pro-networks.org/forum/about78184.html#dualboot](http://www.pro-networks.org/forum/about78184.html#dualboot)

---

### Post by blackhowling on 2007-09-03
Last issue I have with setting up the winxp is finding the proper audio driver since its not on the dell driver page.  Also for graphics u need to go grab them from intel website and possibly where I still need to dig around to find the proper audio driver

---

### Post by notwen on 2007-09-03
I may give this a try when I get more time to play w/ it.  I've been running WinXP home in VirtualBox, but it's not capable of doing quite everything I need from Windows.  Please post back if you are able to resolve the lack of a sound driver.  Thanks for the info on how you went about accomplishing this. =]

---

### Post by blackhowling on 2007-09-03
yeah I even called dell and they basically said that an audio driver for xp does not exist for the 1420N.  Guess that means I might have to dual boot vista instead (which i will probably do anyways to test software later on or at least play games with sound -.-)

---

### Post by blackhowling on 2007-09-03
[http://www.davidreedonline.com/wordpress/2007/08/03/installing-windows-xp-on-the-dell-inspiron-1420/](http://www.davidreedonline.com/wordpress/2007/08/03/installing-windows-xp-on-the-dell-inspiron-1420/)

I finally found the audio driver in that article after quite a bit of digging and another good guide for the 1420 [http://ftp.us.dell.com/audio/R153908.EXE](http://ftp.us.dell.com/audio/R153908.EXE)

---

### Post by blackhowling on 2007-09-03
Well hopefully this info will help others like myself that want to dual boot and will learn from my newbie mistakes and hopefully this will have everything that you would need to dual boot xp/ubuntu

---

### Post by notwen on 2007-09-03
Just wondering, which LiveCD were you using?  Gutsy tribe X or gParted?

---

### Post by blackhowling on 2007-09-04
Gpart live cd

---

### Post by notwen on 2007-09-04
> **blackhowling said:**
> Gpart live cd

Thanks, I wasn't sure if Gutsy's LiveCD would error out the same as Feisty does on the 1420n. =]

---

### Post by blackhowling on 2007-09-04
yeah it errored so i just used the gpart cd again since the way I installed did not overwrite the grub file or windows boot i just had to change the boot sector back to the linux os partition and add in the the windows 
... windows I think was hd0,1 actually and linux was hd0,2 default for the 1420n pre-install ubuntu

---

### Post by notwen on 2007-09-04
Jeebus, resizing a 150GB+ partition takes forever.  For future reference do you know if there is anyway to move a partition using gParted without having to grow it?  After freeing up the wanted space for my future XP install, it's growing all 144gb to 144gb, which looks like it will take 4+ hours.  I may leave my laptop up & running on my way home from work.   It took no time to shrink my swap and move it, but does simply moving a partition generally take a long time and would it depends on the size of the partition?

---

### Post by blackhowling on 2007-09-04
I'll basically say that... gpart and 1420 will probably run u at least a few hours to adjust partitions. I usually just do it over night and forget it.

---

### Post by notwen on 2007-09-04
Lol, I'll post back this evening(perhaps tomorrow) to let you know how all turns out.  Thanks again for the how-to and all the additional info you've linked to. =]

---

### Post by blackhowling on 2007-09-04
Let me know how it goes ... I think i just have to get the grub or MBR to boot to each other so far if i boot into ubuntu i can go ubuntu or win xp but if i log xp it'll reboot and take back the boot record.  I just keep the gpart live cd till i figure it out.

---

### Post by chris8484 on 2007-09-05
When I install the sigmatel driver it seems to work fine and then i restart and when the installation is about to finish it gives me an error message, saying the system does not support the driver you are about to install anyone else get this message what can i do to fix it?

thanks 
chris

---

### Post by blackhowling on 2007-09-05
hrmm... that sounds familar I have heard other people still have issues with the sound driver I actually installed a version that did not fix my sound just the encodec than i installed the one i mention here and it worked like a charm (and digging through the audio section on ftp.dell.com is no fun either)  the encodec I used was for for some other laptop probably why it did not work (just a sigmatel encodec for windows xp  ) ... really kind of wished that intel would host the sound drivers as well but ... 1420n guess there is a reason that the audio is not listed on dell's website for xp ... u gotta do a ton of stuff to get it to work... (pretty sure I did not have to restart for the sound driver to work though) maybe try this ... [http://drivers.softpedia.com/get/SOUND-CARD/OTHER-SOUNDCARDS/HP-Pavilion-dv8395ea-Microsoft-UAA-Driver-100-A6.shtml](http://drivers.softpedia.com/get/SOUND-CARD/OTHER-SOUNDCARDS/HP-Pavilion-dv8395ea-Microsoft-UAA-Driver-100-A6.shtml)  Universal Audio Architecture ... but guessing u just need the sgimatel encodec for windows xp than install the sound driver than again just look at [http://search.dell.com/results.aspx?cat=sup&subcat=dyd&c=us&l=en&s=dhs&cs=19&k=SIGMATEL%20STAC%2092XX%20C-Major%20HD%20Audio](http://search.dell.com/results.aspx?cat=sup&subcat=dyd&c=us&l=en&s=dhs&cs=19&k=SIGMATEL%20STAC%2092XX%20C-Major%20HD%20Audio) go through and find one that supports xp but keep in mind the one i posted earlier is the one i use and it works for me

---

### Post by blackhowling on 2007-09-05
oh and before you install the sound drivers make sure you install the intel drivers for your motherboard, etc...

---

### Post by chris8484 on 2007-09-07
hmmm thanks for the help but still no luck, i have a pci device that is not installed also could that be the problem with it? having no sound really sucks 

thanks,
chris

---

### Post by blackhowling on 2007-09-07
pci hrmm... under sound options I got the SigmaTel High Definition Audio codec pretty sure for the 1420n the sound card is intergrated into the motherboard if u got a different sound card go to the maker of the card and download the drivers for it

---

### Post by chris8484 on 2007-09-09
I found the fix to my problem here

[http://forum.notebookreview.com/showthread.php?t=150033](http://forum.notebookreview.com/showthread.php?t=150033)

thanks chris

---

### Post by blackhowling on 2007-09-09
the more info the merrier

---

### Post by notwen on 2007-09-10
XP had the notion to install it's MBR on my 2GB FAT32 partition.  The one that Dell pre-installed as part of the recovery partitions. LOL.  How would I go about editing my menu.lst to target it to boot XP w/o issue.  And would it adding it's boot files to this partition cause any conflict w/ my recovery option should I need it in the future?

---EDIT---
> Let me know how it goes ... I think i just have to get the grub or MBR to boot to each other so far if i boot into ubuntu i can go ubuntu or win xp but if i log xp it'll reboot and take back the boot record. I just keep the gpart live cd till i figure it out.

Suffering from the same issue here.

---

### Post by blackhowling on 2007-09-10
its probably the reason windows installs first followed by ubuntu lol... i get a hal.dll error when i try to load ubuntu from windows MBR but going from ubuntu to windows xp is fine lol oh well ... i just keep gpart live cd when i want to go back to ubuntu after gaming

---

### Post by notwen on 2007-09-10
Anyone know if it's possible to move the MBR of Windows from one partition to another.  If I hide the FAT16 and FAT32 partiitons of my recovery partitions would that prevent a Windows XP installation from being able to write the MBR to the FAT32 partition?  I've tried all options from Super Grub w/o any luck.  Anyone have recommendations?

---

### Post by blackhowling on 2007-09-10
if you find out limmie know

---

### Post by notwen on 2007-09-10
This is a slight work-around.  I've found using gParted, hiding the 2gb FAT32 partition will prevent MBR from over-writing GRUB since WinXP cannot see the hidden partition which MBR is located on.  In GRUB I select my Windows XP option and I am brought to the Windows boot loader where I promptly choose Windows and once I log out and reboot I am once again greeted again by GRUB.  This isn't the proper way to do this I'm sure, but until someone with a bit more experience w/ GRUB can tell us otherwise, hiding the 2gb FAT32 partition should keep you from having to depend on your gParted LiveCD.  Screen attached. Hope this helps, atleast temporarily. =]

---EDIT---
I'm not sure if hiding sda2 would affect your recovery option form working or not being hidden, but in that case gParted would let you unhide it and it should work properly again.

---

### Post by blackhowling on 2007-09-11
nice work around I'll try it

---

### Post by blackhowling on 2007-09-11
no go for that setup I'll try hiding the recovery hd and move the boot to the ubuntu and try it since the other startup still goes to the MBR for me

---

### Post by notwen on 2007-09-11
> **blackhowling said:**
> no go for that setup I'll try hiding the recovery hd and move the boot to the ubuntu and try it since the other startup still goes to the MBR for me

Did you remove the boot flag from sda2 and add it to your /boot partiiton(sda3) using the gParted LiveCD?

---

### Post by notwen on 2007-09-11
I have made a thread in the Hardware/Laptops sub-forum to see if anyone there is more informed about dual-booting around recovery partitions.  Here is this [thread]("http://ubuntuforums.org/showthread.php?t=548365").

---

### Post by blackhowling on 2007-09-11
still no go lol as long as i boot into windows it stays in windows doesn't want to give up to Grub

---

### Post by notwen on 2007-09-11
Odd, I rebooted 5-6 times to make sure my system wasn't getting a fluke, once I get home and have access to my laptop I'll double check all my current settings to make sure I have not left anything out.  When I boot up I am greeted with GRUB.  The only time I see the Windows boot-loader is when I select my Windows OS form the GRUB menu, but after rebooting out of Windows I am again greeted w/ GRUB.

---

### Post by blackhowling on 2007-09-12
yeah it doesn't seem to work for me oh well

---

### Post by LinuxOn1420 on 2007-09-30
> **notwen said:**
> This is a slight work-around.  I've found using gParted, hiding the 2gb FAT32 partition will prevent MBR from over-writing GRUB since WinXP cannot see the hidden partition which MBR is located on.  In GRUB I select my Windows XP option and I am brought to the Windows boot loader where I promptly choose Windows and once I log out and reboot I am once again greeted again by GRUB.  This isn't the proper way to do this I'm sure, but until someone with a bit more experience w/ GRUB can tell us otherwise, hiding the 2gb FAT32 partition should keep you from having to depend on your gParted LiveCD.  Screen attached. Hope this helps, atleast temporarily. =]

---EDIT---
I'm not sure if hiding sda2 would affect your recovery option form working or not being hidden, but in that case gParted would let you unhide it and it should work properly again.

I wanted to hide all of the linux partitions so Windows would think it was installing on the only partition but gparted will only hide the first two partitions -- sda1 and sda2.  Clicking on Hide while focused on any of the other partitions is ignored.  Is it possible to hid all of the Linux partitions?

I then unhid the first two partitions but something is different because Windows XP now sees the first partion as C: whereas before it had -: and this worries me.  Is windows likelty to write on the first partion now?

---

### Post by notwen on 2007-10-01
Not sure with your situation, but we do have similar setups.  One of my Dell Utility Recovery partitions shows up as the C:\ in my WinXP install, while Program Files and Windows show up on the correct partition and the drive letter is H:\ .  I do not know of any other way to correct this since we are unable to hide all of the previous FAT partitions before the Windows install.  You just have to be careful prior to saving new files.

---

### Post by LinuxOn1420 on 2007-10-01
OK. Let's say I take the coward's way out and wipe the hard drive, install Windows XP into the first partition and then install ubantu -- from the CD that shipped with the machine -- can I recrate all of the partitions -- including the Dell recovery partition?

---

### Post by notwen on 2007-10-02
You may be better off asking this on the [Dell Linux Forums]("http://www.dellcommunity.com/supportforums/board?board.id=sw_linux").  I've considered it, but I don't care to off the recovery partitions if I cannot, it's too convenient to have a brand new, for the most part functioning laptop option in my GRUB menu.  I was hoping if experiences w/ the new Dell remastered Feisty image were good that I'd be able to somehow implement it as the recovery image to use, but I haven't heard anything concrete yet as of user's experience w/ the new Dell Feisty image.  Please post back if you learn something new that may be useful for us who want to dual-boot. =]

---

### Post by blackhowling on 2007-10-02
You could wipe the disk and than do Xp followed by the dell's ubuntu recovery disk I think its only missing the open office which you can download later and still retain all the partitions and stuff.  <--- haven't tried this but using these and other forums you should be fine.  Looks this thread is helping a few people hopefully.

---

### Post by doppis on 2007-12-26
Thanks for the heads up on the drivers, im currently trying to figure out how to get xp running on a external hd with my 1420n, still no luck because of the hal.dll problem. :(

---

### Post by soupwell on 2008-01-15
First, awesome work on this stuff.  I hashed out the basic partitioning and sata driver stuff before I found this thread, but I was beating my head against a brick wall about the audio driver.  That's a bit of a convoluted procedure, but hey, it works!

Has anyone encountered (and hopefully solved) a problem with the video controller under WinXP?  I've got the hi-res screen, and it works fine in Ubuntu (I think it's 1440x900), but it will only operate at 1024x768 in Windows.  In the device manager, I've got two listings under "Other Devices" with question marks next to them.  "Video Controller" and "Video Controller (VGA Compatible)".  I've scoured the Dell driver page for the 1420, and can't come up with anything there, and I can't find any references to the video controller specifically on this forum.

Any ideas?

---

### Post by soupwell on 2008-01-15
Ah, now I've got it.  I didn't know what graphics hardware I was running, and so was having a hard time locating a driver.  After I made that last post, I read the tag under the previous poster's signature, saying they are running an Intel X3100 integrated graphics card.  This sounded vaguely familiar... and sure enough, after googling the driver and installing it, everything works great.  

Everything works perfectly now. Hot Dang!

---


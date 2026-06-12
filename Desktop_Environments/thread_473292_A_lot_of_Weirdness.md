---
title: "A lot of Weirdness"
date: 2007-06-13
forum: Desktop Environments
---

### Post by jimbo99 on 2007-06-13
Having used computers for well over 20  years I've become attuned to being able to spot weird things.  Since I've been using Linux (for over 2 years now--close to 3) I've somewhat become accustomed to knowing how it is supposed to work.  Tie that to the 20 years in other OSes and you can readily spot some of the weird things that appear to be happening in the Linux (maybe only Ubuntu) world.

I'll just list a bunch of them in a random order and give only a disheveled description of the issue and maybe some of you can make sense of it and figure out some of your own issues and get them resolved.

I have a network with Linux and Windows workstations, and even a Mac.  I also have many computers, including notebooks.

In working with these I have shares set up.  In the past I had chosen to leave the file systems intact on drives that I was using as secondaries when I switched from XP to Ubuntu.  So, I might have several dual boot computers, or computers with Linux and NTFS file systems.  For instance, my main computer is mainly a Linux box.  I have an external SATA enclosure HDD.  I also have 2 internal SATA drives and I have one or two (depending on any given day) USB external exclosures.

What I'm finding is that, at what seems to be random times, after a boot here or there, my NTFS formatted drive might be missing from the desktop.  In case you don't know if you install ntfs-3g support, then create a folder under /media and then chmod 777 to it and then reboot, and make the appropriate entries in your /etc/fstab, anyone with an account on the server should be able to write to it.

If you use ntfs-3g and the configuration tool (both available from the Ubuntu repository) you can read/write to NTFS partitions.  But if the partition is not shut down properly ntfs-3g will refuse to mount it upon your next boot.  That means that you will be missing the icon on your desktop that represents that drive.

If you boot into XP and then safely remove the device (for any hot swappable type device such as SATA external or USB as long as it is not the boot device) it resets a flag in the system and then NTFS-3G can mount it.  If you fail to do this you *wont* be told that the drive was not mountable&#8212;what a wierd way to deal with the issue.

This doesn't explain why I have had similar problems with some of my EXT2/3 drives that are secondaries (for storage purposes).

For instance, I bought a 500 gig external USB drive and decided to stick it on my Linux box.  First I attached it to one of my XP machines.  When I looked at the drive I noted the drive was partitioned and formatted as NTFS.  They had pre-formatted it at the factory.  I then connected the new 500gig drive to my Linux box to see if it would be seen.  Nope.  No drive.

I ran the NTFS-3G config utility and gave it a mount point and told it to mount the device.  What do you know?  It still didn't work.  After some hassling with it I chose to just delete the partition and reformat it as ext2.  I was going to do ext3 but ext3 is just ext2 with journaling.  I figured the journaling would cause more space to be consumed so I chose to just do ext2.  The only problem was how?  I finally decided on gparted. Gparted is a tool for partitioning drives.  It has a graphical user interface and is very competent at doing what it does, even if it is confusing at points in the program.

Aside form some disorganized screens and commands, the only problem was in how this thing kept rescanning for drives.  Sometimes I wasn't sure what it was doing at any given time.  I've used lots of partitioning programs under other OSes (say Windows and OSX) and they just seem better organized and more informative.  Notice I didn't say more capable.  The gparted program is just as capable as any under Windows or OSX.  It is not as well organized.

After rebooting I noticed the drive was not mounted.   So, I went into /media and created a folder called stuff and did a chmod 777 on it.  I then modified the /etc/fstab file and added the reference to it.  Then I went and typed type "sudo mount -a".  I tried then to write to it.  No luck.

So here's the weird part.  I know I did all the steps correctly.  I then got the idea I would reboot the computer and try again.  Low and behold the icon was on the desktop and I could write to it from a regular user account.

On another occasion, not related to the 500gig USB HDD I came in to work one morning and noticed that my main computer was off.  So much for the UPS.  Anyway, I started it up and noticed that some of the drive icons were missing from my desktop.  So, I looked at my secondary Linux box and found that it too was off.  So, I powered on and booted that computer and found that the only drive icons on its desktop were the *network* drives I'd mapped using the /etc/fstab file.

This was weird as this secondary Linux box also has 3 SATA drives.  One for the OS and two for other stuff (1 for the XP install and one for storage).  The two extra local drives should have been mounted but only one of the network drives was mounted.  Of the three SATA drives, one of the drives was a NTFS drive and the other was an ext3 drive, the third was the boot drive for Linux.

I reviewed the fstab file and all seemed right.  I had a copy of the fstab on the desktop and double clicked on it to compare the two.  There were little or no differences that weren't expected.

I went through some rigamarole and finally came up with the drives on the desktop.  It was pretty frustrating.  At one time I ran an fsck on the ext3 drive that didn't mount.  (Note:  In each case on both machines I used fdisk -l to look at the drives to see if they were phyically there&#8212;they were.)  I even ran  kdiskfree and kwikdisk to see if those programs would see them.  They did, just no mounting was possible.  There were times when I saw the same device used for multiple drives.  This was both weird and wrong.  I managed to get them worked out.

In the end I got the secondary Linux box up and running with both the extra local drives showing as icons on the desktop (the NTFS and the EXT3) drives (both are SATA, and less than 6 months old).

I then had to reboot my main Linux box to ensure that I had all the remote drive icons showing on the desktop.  When I rebooted, I had the shared drive from the secondary Linux box showing again on my main box&#8212;and my normal local secondary drives (yes, 3 drives on each of my Linux boxes)--I always encourage giving Linux as much resources as you possibly can.  I am not of the philosophy that bends to the idea that you should make your old hardware usable longer with Linux.  I feel you should give Linux every bit of power it deserves.

All of this weirdness was happening to SATA, USB, EXT2, EXT3, and NTFS drives for one reason or another on multiple computers.  I guess it is time to actually have the Ubuntu folks take a serious look at some of these issues.

There have been times when just connecting one of the SATA drives to a different header on the motherboard would cause my system to not work properly.  Since I have 3-4 drives on the system it was obviously causing me problems because I don't have the mental facilities for remembering which drive was connected to which connector on which header&#8212;maybe it is just that I don't have the time to remember such stuff.

I also found that if I put the main SATA boot drive on one bank of headers and then put my other drives on the other headers my computer would not boot.  If I moved the boot to the same header it would boot or if I removed the drives from the other header it would boot.  Just more weirdness.  I'm not talking about grub errors.  I'm talking about going past all the BIOS diag screens and getting to the point where it should load the boot loader.  Anyway, it doesn't boot with the hardware configured this way.

This somewhat limits the number of drives I can attach to 4 (down from 8) but I'm sure someone in the Linux community will get these issues worked out before I need 5 or more SATA drives attached.  I think I split them up, in part, for organizational reasons and for possible optimization.  I figured it would be faster access if I was reading from one and writing to another and they were on seperate headers.  Never know.  Was just a try.

Before doing this while I was trying to figure out the problem stated above I noted that the motherboard on my main Linux box has 8 (2 sets of 4) headers for SATA.  I knew I wasn't willing to, nor trying to, run them as RAID, so I turned off the RAID functionality in the BIOS.  Initially I split the main boot drive and the other drives onto different headers to help me keep them organized and for performance potential (as stated above).  I don't believe that worked as the system would not boot.  The drives were seen in BIOS, etc but Linux just would not bootstrap.  So, I decided then to put them on a single header.

Periodically I had to take the main Linux box down and organize the components (move the rabble of cables, clean dust, move one drive up or down in the drive bay for better cable organization, etc.).  Another instance was when my CPU fan started letting out a "barely audible" high pitched (very annoying) noise so I felt it was time to replace it.  I decided that since I hadn't cleaned this box in a while I would disassemble it and clean up and then reassemble with the new CPU HSF.

I was pretty sure I had everything in order when I reassembled.  Upon booting I got the various Error 17, 13, 21, etc from grub.  I'd have to experiment until I figured out which drive connected to which connector on the header block.  Weirdness that required organization.  Then if I'm using grub to dual boot I have to ensure that all the other drives are on their respective connectors on the header.

(Note:  Keep in mind that some of this happened before the failure to post with drives on muliple headers blocks (meaning I had managed to get things working at one point with multiple sets of headers and the drives split between them), but that deconstructing the computer for various purposes, such as cleaning and reorganization caused lots of issues that I didn't want to keep experiencing.  Also keep in mind my series of problems also covered two machines with two sets of 3 SATA drives each on two different versions of the same distribution of Linux (Edgy and Feisty).  Suffice it to say that at one point two sets of header blocks worked but I had problems ensuring that the right drive was on the right header and that the ultimate solution to all of this with each set of drives was to put all the drives on one set of headers and left it at that &#8211; on both machines.  Much of this happened around the time that Feisty Fawn was officially released.)


On another issue&#8212;somewhat related: 

Some more weirdness cropped up not long ago.  There was a new version of the Kernel and the header files, and I blithely let the Ubuntu Update Manager download and install them.  Upon rebooting I couldn't get past the error 17, or was it 15, or 13 or 21--I don't recall the exact error number.  I think it started as an error 17 but later changed to 21 as I worked with the grub commands.  Anyway....

I decided to boot with the LiveCD only to find that it wouldn't boot from that CD.  So I grabbed another Ubuntu LiveCD and tried it.  No luck.  I booted with an XP CD and that worked.  I have always been able to make DVDs, copy Cds, etc on that DVD RW under Ubuntu,  so, hmmmmm&#8212;who knows.   The DVD RW DL drive was about a year old.  I tried multipile copies of the CD I'd made from the ISO that I had laying around&#8212;I keep extras because it has the memory test as part of the menu displayed upon boot of the CD, and I have customers that come into my store periodically that want a copy.  Even though this DVD RW drive isn't that old, I thought it might be the drives fault, so I unplugged it and grabbed the first drive I found (a 3 year old DVD ROM drive).  I set that up and booted with the CD.  It worked.  I was able to run the LiveCD.  I now only needed to remember how to get a list of drives and to remember how to modify the grub file that told it about which drive has the main boot files.  Sheesh.

Using another computer I looked on the web (as I said, I have lots of them), and found some reference to fdisk -l, and running the find command in grub, and the commands used to tell grub which drive to use for booting.

Running those commands generated no errors.  Even so, rebooting didn't resolve the issue.  The same problems.  So I rebooted into the LiveCD once again and tried to figure this out.  This time I opened a terminal, ran sudo fdisk -l, identified the HDD with my Linux install on it, and used the mount command to mount the drive, then edited the /boot/grub/menu.lst.  Examining it uncovered that the reference to the boot device was wrong.  It was showing hd1 instead of hd0--I had told grub, using its' commands to set up hd0, not hd1.

I manually edited the menu.lst file and rebooted.  This time I could boot into the OS but it bailed out on me when it attempted to load the desktop GUI.  This new problem happened to be caused by a lack of a driver installed for the new kernel that had been installed with the Ubuntu Update Manager.  Experience has told me that I should always keep a copy of the nVidia drivers in a folder under my home folder; so I ran and installed it and then rebooted.  This brought me back to my desktop.  Only this time some of the network drives that should have been mounted (through the fstab file) were missing and so were some of the local drives.  (I remembered some cryptic error messages that were diplayed during that last boot (which, BTW, normally never happens) and thought something was awry.)  Because I remembered those messages it triggered the idea that if I rebooted it might just work (as I'd had similar problems and rebooting resolved them&#8212;very similar problems), and luckily everything came back as normal.  If I recall correctly, the error messages were about some rule that wasn't processed, or was broken, etc.  Who knows for sure.  But one thing is certain.  Mom and Pop are not going to even consider those messages and so they should not be displayed, especially on a character based boot screen which doesn't stop to ask for their input.

I'm getting the feeling here that any sort of error caused when the system boots up and is running through the fstab file will cause one or more following lines in the file to not be processed.

Anyway, I got it working and I was happy for a while, a few days (maybe a week).  Then I noticed that there were more changes to the kernel and some supporting files.  So, I first went to nVidia's website and downloaded the latest and greatest drivers.  These were the 100 series drivers for Linux.

Using the Ubuntu Update Manager I downloaded the changes.  While this was happening I went and got that old DVD ROM drive because I was certain Ubuntu would mess up on the /boot/grub/menu.lst file changes again.

I was correct.  The next time I booted I got the error 17 (or one of those related to it).

I set up the DVD ROM drive rebooted with the LiveCD, mounted the drive and manually corrected the /boot/grub/menu.lst and rebooted.  The issue with the graphics driver cropped up but I was ready.  I then installed the 100 series drivers and all has been well for the past couple of days.

One problem that seems to have irritated me over the months is related to mounting a remote network share.  Gnome gives you the ability to drop a remote share, say onto your desktop, but it is really a &#8220;fake&#8221; mount.  You are opening a stream to the share instead of actually mounting it.  For instance, if you have a folder on some remote share that has your music, and you decide to use Amarok to listen to that music, if you use Gnome's method, it will create connection and when you drag a folder (preferably with music in it) onto Amarok it will list the music (albeit without the tag info).  When you select a song to play Amarok will open a stream to the file and read the mp3 tag information and update the list.  Unfortunately, it does it on a song by song basis.  If you want to sort on say the artist or the album it won't do it because that information hasn't been read for each file.

This is much different than say when you mount the remote share tying it to a directory/folder in your file system.  In that case when you tell Amarok to open the folder (by dragging and dropping it into the playlist) it will read the tag information of each song and you can then sort on any of the columns.  Suffice it to say the connection to the remote share with the gnome desktop facilities doing the connection is much different than if you use Samba commands directly by adding the references to the remote shares in the /etc/fstab file.

I have used Samba for some time and wanted to ensure that I could get access to some of the other drives on my network that were on XP boxes and I wanted to ensure that my local drives were shared so that those could be seen by the XP boxes.  Generally, in past distributions, such as Fedora, I'd use smb4k to do that.  It is a nifty program.  The only problem is whatever they did to it in Ubuntu sucks and it doesn't work right all the time.

Before Feisty Fawn (and on other distros) I was able to do this without many serious problems, but there were some times that that would drive me nuts.  I'd be unhappy because periodically I'd get these very long delays when accessing the remote drive (which would cause some windows to dim (Beryl will dim unresponsive windows)).  I didn't know what to attribute it to so I just let it go on happening.  

Even with many of these problems outstanding Ubuntu is still a fine OS distribution and I never felt like giving up, so I would continue to work like this for some time.  Then I noticed a couple other issues.  For instance, when I tried to open up a .pdf file the non-Adobe Acrobat Reader program would launch even though I had installed Adobe's version.  As nice as it is I just don't feel it is up to par so I just don't like using it.  Nothing I could do would make a simple double click launch Adobe's Acrobat Reader unless I told it each time which program to use.

I searched the forums and found some reference to right clicking -> properties -> open with, and then selecting the program to use.  This was supposed to establish which program you want to use associate with that type of file forever, at least until you decided to change it again.  The only problem was that I couldn't change it.  I could click on the radio button associated with the program I wanted to use but nothing would happen.

I decided let this go too as it wasn't a huge problem right then.  I figured Feisty Fawn was coming out soon so I'd just live with it till then.  When I did a completely new install of Feisty on the machine I was planning on making my main computer I'd try to ensure that problem was resolved.

When Feisty Fawn was released I set it up.  After a while I noticed the same thing.  I couldn't launch Acrobat Reader by double clicking on a .pdf file (through file association).  I could launch it by manually and then open the file, or right click and choose which one to  open with, but double clicking resulted in no joy.  I investigated the right click-> properties -> open with, but again it couldn't be changed.  To say the least, I was disappointed.

I also noted that on the prior install of Linux on another machine I also couldn't turn on, or off, certain menu items using alacarte.  I'd been working with a friend to get Ubuntu working on his machine and when he called me with questions about how to turn on or off menu items using alacarte I couldn't figure out how nor why it wasn't working.

So, considering I had the new Feisty Fawn installed and me and my friend were having the same (or similar) problems, I decided to go to the web and search for a solution.  Everyone posting about it stated that all you needed to do was to right click -> properties -> open with...no one had any answers as to why it couldn't be changed.  Obviously they didn't understand the real problem.  Others had asked the same question but no one replied.

One day I was reading a thread when someone mentioned the .local folder (located in your /home/username folder).  I tried to go into that folder and found that permission was denied.  I thought to myself that this was weird because I should have access to all the files in my home folder.  Certainly I should have access to the .local folder.

I then chmod it to give me permissions (sudo chmod 777 .local).  I was able to go in this time.  I then looked around in there and found numerous other folders.  Most of them were set to deny me access via permissions as well.  So I went through them and marked them to give me permission.

If I recall correctly the reason I even noticed the reference in that guys web post was because he had mentioned that the mimetypes info is maintained in a file in this folder.  So, after making those changes I decided to do the right click -> properties -> open with, in order to see if I could change it.  Sure enough that worked.  I then decided to check out the alacarte menu changes and sure enough that worked too.

How and why I was denied access to that critical folder in my own home folder is beyond me.  I believe it has to do with having done a sudo -i at some point and working with files in my home folder early on just after I had installed Feisty Fawn.  I'd had the same problem on my Edgy box so I went back and did the same thing there and corrected the issue.

Another annoying problem:

What has been bothering me recently is my screen saver.  It kicks in properly, but I am finding that even though I have told Ubuntu to *not* turn off the monitor after &#8220;some period of time&#8221; it appears to do that anyway.  I've double and tripple checked and quadruple confirmed that the power saving feature to turn off the monitor is set to &#8220;never&#8221;, and I have even stopped the power management daemon completely.  To no avail as it still turns off the signal to the display.

The display I have is a nice 24" WS HD LCD which has numerous inputs.  I'm using the DVI input for the main Linux box and the VGA input for two other computers and SVIDEO (as this thing has picture in picture).  What I have is a KVM switch that allows me to switch back and forth between two two computers on one input.  So, effectively I have 4 outputs going to various inputs into the monitor.  The DVI is the one that is not being shared and it is the one used primarily.  It is the one directly connected to the machine that keep turning off the signal to the monitor.

What happens is after a while the screen saver kicks in. Then a period of time goes by and the monitor turns off--or rather it then sees there's no input so it searches for the next available input that has a signal (which happens to be the SVIDEO.  If you have seen SVIDEO full screen on one of these monitors you know it looks like crap and having the display sit with a static image just isn't a positive thing and defeats the purpose of the screen saver.

I tested with XP and told it to not turn off the monitor.  It does not.  It will stay as is forever, even if I have a screen saver running.  But the Linux box seems to just ignore the fact that I told it to never turn off the signal to the monitor.

Back to my remote network shares:

After Feisty Fawn was released I installed it fresh (as I stated above).  I then did the updates, etc.  I then decided to mount some remote network shares from my XP boxes.  After setting this up and using the system configured like this after a while I encountered various issues.  The most annoying was where the desktop would become unresponsive.  I was not able to click on any icon on the desktop for some time.

After a lot of investigation I found that I had a problem with Samba.  If I had a share mounted into a folder on my desktop or even into the /media folder (which causes shares to show on the desktop as an icon), and a period of time would go by, and after that period of time expired I couldn't access anything on the desktop--though I could still access the panel and the Ubuntu gnome menu.  It was as if the Samba share had gone to sleep.  If I tested this in reverse (using XP to access my Linux shares) it would never become unresponsive.

I discovered it was the Samba because when I moved the shares (meaning I  had them mounted under some other folder not located in my home folder or Desktop folder) I never had the problem with an unresponsive desktop.  But, whatever folder they were mounted in had problems with responsiveness.  In fact, when I investigated further I found that the folder had a very generic icon instead of the folder icon.  If I tried to double click on it it would sit there for an extended period of time making my machine unusable.

So, to explain it a little better.  If I create a folder under /home/jimbo called &#8220;XPShare&#8221; and then use Samba (via entries in the fstab) and reboot I will get the share mounted.  In fact, I can go into that /home/jimbo/XPShare folder and see the contents.  If I let it go for a while and do other things, say browse the web or listen to music, after a while I'll notice unresponsive applications and unresponsive folders.  If I try to open a folder on the desktop, say just any old work folder that might be there it will take forever, but eventually open.  If I try to open my home folder it will take forever and maybe not open.  If on the chance it does open and I look at the XPShare folder icon under it, that folder icon will have the generic &#8220;gnome&#8221; icon and not a folder icon.  I won't be able to open that at all.

I looked into the forums and even went into IRC and asked questions.  Any time I would go to pose a question in the #samba group on IRC I'd see tons of names but no one talking.  Periodically I'd see one person say something but it seemed he was talking at random. I was using GAIM 2.0 beta 6 with the IRC plugin.  I switched to xchat and had much better luck.  Just another weird thing that happened.

I then posed my question but no one could answer why.  They only stated I should be using the latest version of Samba.  I told them I had the one provided by the folks at Ubuntu that came with Feisty Fawn.

I started to get periodic replies from a thread I'd posted in one of the Ubuntu forums but the suggestion was to use something else (something other than Samba)--I think, CIFS.  I tried this but had a lot of other odd problems with it.  Using CIFS resolved the unresponsive desktop and folders thing, but there were other side effects.  So, I just gave up sharing for a while.

After a few weeks went by I noticed that some of the Samba program files had been updated so I let the Ubuntu Update Manager install those.  I then modified my fstab file again and set everything back to the way I had it before--mounted shares in the /media folder.  Low and behold the unresponsive desktop thing has been resolved (at least for now), but who knows for how long.  I'm all cheery about that.

Today I was moving a large number of files around using Ubuntu.  I use gnome.  I opened two drives.  The source and the target.  I selected the folder to copy (which had a large number of files in it).  I then told it to copy those files from one drive to another.  It was going to take some time so I decided to go to dinner and I'd check it when I came back.  

When I arrived back from dinner I found the process appeared to be done.  Folders seemed to be present on both drives.  I decided to compare the number of folders on the target with the source and found there were not the same number.  There should have been about 80k in each drive.  The target had 50k and the source had 80k.  30k were missing.

During the process of investigation I decided to copy them over in smaller batches.  I'd copy 10 or so folders at a time until done.  I encountered one folder that had an excessive number of files so I decided to copy it by itself.  Upon doing so I was informed there were files already on the target with one or more of the names I was copying and it asked me what I wanted to do:  skip, replace, etc.

I first chose skip.  When I did the copy process ended fast.  I figured most of the files had been previously copied, but I decided to make sure.  I checked the number of files in the source and target and they were not anywhere near the same number.  I then decided to copy some of them in smaller groups and when I started copying I was prompted again.  This time I chose to overwrite them.  The process then stopped immediately.

I started looking at the target drive and chose to delete everything and recopy them again from scratch.  When I tried to copy I was denied access.  I looked at the permissions and it said root was the only one that had permission.  I then opened a terminal and did the sudo thing to delete the files.  I then copied the files again in small groups of folders.  This worked.  

An odd thing that I noted was that the *files* that were supposedly marked to deny me permission were really supposed to be folders.  It seemed they'd been created as files on the target drive.  I also noted that some of the files mimetype icon were misrepresented.  They should have had some icon for that mimetype but they had the generic gnome icon instead.

As I stated early on in this post I had just purchased an 500 gig USB external drive and that I had partitioned it as ext2 only the day before.  So, the issue wasn't due to it being an NTFS partition and File System, and it wasn't because the file system had become corrupt because it was newly formatted.

If I had just trusted that the copy process had happened successfully, and had deleted the source files, I would have been in big trouble here.  The reason I didn't trust it was because I'd had a similar problem about 6 months earlier under Edgy.  I'd never sue, but I'm sure someone that took this procedure for granted would have had that on their mind.  For me, luckily I chose to just copy instead of moving files.

That's about it for now.  I think the story of my little journey should be helpful to some.  I have had many other experiences like this over the past year.  Maybe after reading this some fine soul at Ubuntu can, and will, take the time to get this whole bit with drives worked out and cleaned up and made extremely reliable.  Right now it is pretty give and take and if you aren't careful you could loose a lot of valuable data.

Mom and Pop, Grandma and Grandpa, brother/sister are not going to fare well with these types of problems.  Most normal human beings would be at a great loss to explain what is happening and even more so at finding an solution within a reasonable amount of time to any single one of the issues I've written about in this post.

Cheers.

---

### Post by ~sparkles~ on 2007-06-14
First thing... thank you for the post...

Second thing... i'm getting the same feeling...

Third thing... i only have about 15 years experience with windows and about 4 days experience with kubuntu...

Fourth thing... i really want this new relationship to work.... i've been loving everything except the weirdness with external hard drives, formats and things appearing/not appearing on the desktop...

Fifth thing... keep on keepin' on

---

### Post by Kobalt on 2007-06-14
Geee, that is the longest post I've ever seen on these forums :)

---

### Post by xpod on 2007-06-14
Those first few months are the best ones eh:p

This "pop" did indeed spend his first few months pretty confused with most stuff,but i`m glad to say that I`ve been using Ubuntu for nearly a year now which is 3 times longer than i used  Windows.;).
Ubuntu was certainly no more confusing than what Windows was to start out and im sure that if Ubuntu came pre-installed for mom & pop then it would be no harder to figure out than what Windows once was i`m sure.

---

### Post by jimbo99 on 2007-06-14
In no way was I attempting to dump on Linux or even Ubuntu.  I just felt that if I spent some time journaling what I had been doing and the problems I had and even the resolutions I would help others to understand that they are not alone, that the problems can be overcome, and that others feel that the Ubuntu people could do better to recognize and follow their own philosophy--that Ubuntu is for the human beings in the world.

---

### Post by jimbo99 on 2007-06-14
> **~sparkles~ said:**
> First thing... thank you for the post...

Second thing... i'm getting the same feeling...

Third thing... i only have about 15 years experience with windows and about 4 days experience with kubuntu...

Fourth thing... i really want this new relationship to work.... i've been loving everything except the weirdness with external hard drives, formats and things appearing/not appearing on the desktop...

Fifth thing... keep on keepin' on

Thanks.  I know others are feeling some bad vibes from some of these issues.  Hopefully they'll get some insight into the cause and solution by reading my, haha, excessively long post.

---

### Post by JPorter on 2007-07-21
Ok, have pity on us... can you insert section headings in bold, and put some space between the different sections?  

Thanks!

---


---
title: "DELL Inspiron 1526"
date: 2008-03-05
forum: Dell  Ubuntu Support
---

### Post by Alberto.Jaume on 2008-03-05
Hello,

I just purchased a DELL Inspiron 1526 and I want to install Ubuntu on it. I haven't done it yet because I don't know fi all the drivers are available (touchpad, webcam, video and sound card, etc). Can anybody help me with some orientation here?

Cheers!

Alberto

---

### Post by dicecca112 on 2008-03-05
See here [http://ubuntuforums.org/showthread.php?t=577469](http://ubuntuforums.org/showthread.php?t=577469)

Most should work if not all

---

### Post by eeefresh on 2008-03-09
I bought that same laptop two weeks ago but have not had time to install Ubuntu on it.  However, I have seen many threads that seem to indicate that Ubuntu on a Dell 1526 might be tricky...but not impossible.  Here are a few threads I found that will hopefully help you:

**Installing Ubuntu on a Inspiron 1525 (which seems to be very similar to the 1526)**

[http://ubuntuforums.org/showthread.php?t=712255&highlight=dell+1525]("http://ubuntuforums.org/showthread.php?t=712255&highlight=dell+1525")

**Dell Now Offers Wireless Drivers for Ubuntu**

[http://ubuntuforums.org/showthread.php?t=712255&highlight=dell+1525]("http://ubuntuforums.org/showthread.php?t=712255&highlight=dell+1525")

As I said, I have not tried any of these yet, so I cannot testify that they work.  Since there are very few posts on the 1526, please post your experience on the forums so that we all may benefit!

---

### Post by glefty on 2008-03-10
Bought the same laptop last weekend as well.  The only real problem was wireless.  Just make sure you've got a wired connection available so that you can download the restricted drivers.

---

### Post by Turbobusa311Hp on 2008-03-10
> **glefty said:**
> Bought the same laptop last weekend as well.  The only real problem was wireless.  Just make sure you've got a wired connection available so that you can download the restricted drivers.

I'm not usually a source of negativity, but Vista is horrible on this thing.  When you installed Ubuntu, was it a straight forward install?  I mean could even someone with minimal experience install Ubuntu on the Inspiron 1526?  I need to know or else this thing is going back to Best Buy.  Thanks everyone!

---

### Post by glefty on 2008-03-10
The install was straight forward, even with dual booting.  Just follow the prompts.  Afterwards, if you have any problems, just come back here for help.

---

### Post by eeefresh on 2008-03-11
> **glefty said:**
> The install was straight forward, even with dual booting.  Just follow the prompts.  Afterwards, if you have any problems, just come back here for help.

When I fired up gparted it was showing some partitions that weren't showing up in Windows.  They were taking up almost 3 GB of space, too.  One was [DellUtility]("http://www.dellcommunity.com/supportforums/board/message?board.id=insp_harddrive&message.id=23911&c=us&l=en&cs=&s=gen"), the other was called [MediaDirect]("http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&dl=false&l=en&s=gen&docid=F065D776B2DC5763E030030ABD620CAD&doclang=en&cs=").

I don't think I will use either of these, and I* think* they can both be reinstalled if needed.  Did you keep both of those partitions or remove them?  Just wanted to see if anyone else successfully removed them without hurting anything.

---

### Post by glefty on 2008-03-12
> **eeefresh said:**
> When I fired up gparted it was showing some partitions that weren't showing up in Windows.  They were taking up almost 3 GB of space, too.  One was [DellUtility]("http://www.dellcommunity.com/supportforums/board/message?board.id=insp_harddrive&message.id=23911&c=us&l=en&cs=&s=gen"), the other was called [MediaDirect]("http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&dl=false&l=en&s=gen&docid=F065D776B2DC5763E030030ABD620CAD&doclang=en&cs=").

I don't think I will use either of these, and I* think* they can both be reinstalled if needed.  Did you keep both of those partitions or remove them?  Just wanted to see if anyone else successfully removed them without hurting anything.

I personally just left them alone, didn't want to wonk the Vista install (until I'm done playing with it anyway :twisted:).  With a 250gb drive, there's more than enough room, and I also use an NAS drive, so nothing stays on the laptop for long anyway.

I don't know if it would hurt anything by removing them, but if you really want to, maybe check the Dell Ubuntu forums on the Dell website.  I'm sure they could help you out.

---

### Post by eeefresh on 2008-03-12
Thanks!  I will probably leave them for now, too, but if I can get everything in Ubuntu working, I may just remove Vista altogether.  I can always remap that MediaDirect button to something else.

---

### Post by eeefresh on 2008-03-16
I finally had a free day to install Ubuntu, and after some consideration, I decided to also take the bold step of removing DellUtility, MediaDirect and Recovery partitions.  I also resized the Vista partition to create some room for a data partition. I am sharing my experiences here so that others can do the same if they choose.

As stated above, I used gparted and removed the extra partitions to free up several gigabytes of space.  It irks me that Dell advertises a 250 GB hard drive, then fills 3-4 GB with crap they think you need.  I wasn't thrilled with MediaDirect, and I am savvy enough to fix my own computer problems, so I decided to remove them.

However, if you think you will need your recovery partition, or if you think you will use MediaDirect (I won't), then **don't** remove these partitions. You may also screw up your Vista installation (see my notes below). I read that you can reinstall DellUtilities and MediaDirect at a later time, but if you think you will use them its safer to leave them be.

Anyway, after removing the extra partitions, I moved the Vista partition into the open space and resized it to about 100 GB.  My goal was to set up my hard drive like this:

hda1 - Vista (ntfs, 100 GB)
hda2 -Ubuntu 7.10 (ext3, 20 GB)
hda3 - Linux swap
hda4 - Shared data partition/home folder (ext3, ~100 GB)

However, after getting the partitions set up, Vista wouldn't boot!  I'm still not sure if this was because I removed the extra factory partitions or because I resized and moved the Windows partitions. When I powered on the computer, it would bring up the Vista logo and chime, but then went straight to a blue screen.  I tried fixing the problem using the "repair" option on the install disc, but no dice.  

The only solution was to reinstall Vista.  This actually wasn't so bad; it installed quickly and didn't copy over some of the extra junk Dell installed. I also didn't have anything important on it yet, so I didn't mind reformatting.  I also had to reinstall all the drivers using the Dell CDs, but that also went quickly.  

Once my partitions were set up and Vista was working again, I installed Ubuntu without trouble.

The touchpad worked fine right off the bat.  It's not very sensitive, but I noticed that in windows, too, so I think its a hardware problem and not a Linux problem.  The media control buttons in the upper right part of the computer also worked fine.

Sound and video worked fine.  I have noticed that I can't enable visual effects.  It's set to "None" and won't let me change the setting.  I am guessing it has something to do with the ATI Radeon Xpress 1270 integrated graphics.  There may be a fix for this, but I haven't searched the forums for it yet.  It's ATI, so I am not getting my hopes up!  :)

The webcam works, too.  I opened Ekiga and went through the setup process.  Be sure to select "V4L2" for the video settings.  Once configured, it worked flawlessly.  I'll probably never use this, but its nice to know its working.  

As glefty stated, you need to enable some restricted drivers to get the wifi to work.  I think it actually prompts you to do this when you boot for the first time, so there is no complicated setup. Just be sure to have your WEP/WPA key handy to log in to your home network.  For some reason my connection never rises above 70%, even when I am sitting right next to my router.  Not sure why, but at least its working.

My next project is to figure out how to remap the MediaDirect button  to make it bring up my home folder.  If you have any questions or suggestions, let me hear them!

**UPDATE:** Remapping the MediaDirect button was quite simple.  Just go to System -> Preferences -> Keyboard shortcuts.  Piece of cake!
[B]
UPDATE 2[/B] I was able to get the visual effects working fine by doing the following:
> 
sudo apt-get install xserver-xgl

---


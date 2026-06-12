---
title: "DELL OEM Reinstall DVD Is Now Available 4 Download."
date: 2008-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kevpan815 on 2008-08-15
The Dell OEM Ubuntu 8.04.1 LTS Reinstall DVD Is Now Available 4 Public Download On The Dell Ubuntu 8.04 LTS Wiki Home Page At [http://linux.dell.com/wiki](http://linux.dell.com/wiki), Just FYI.

---

### Post by TimDaniels on 2008-08-15
> **kevpan815 said:**
> The Dell OEM Ubuntu 8.04.1 LTS Reinstall DVD Is Now Available 4 Public Download On The Dell Ubuntu 8.04 LTS Wiki Home Page At [http://linux.dell.com/wiki](http://linux.dell.com/wiki), Just FYI.

Just FYI, do you know that it completely wipes the entire disk and creates 3 partitions for you, only one of which contains Ubuntu, and you have no control over how large those partitions are or where they're placed, or where Grub is placed, and that it truly needs a DVD to fit its more than 4GBs?  Unless that is what you want, you're better off downloading Ubuntu 8.04 from the Ubuntu site and burning its 700MB to a CD.

*TimDaniels*

---

### Post by kevpan815 on 2008-08-16
The Dell Disk Contains Extra Features That The Regular Ubuntu 8.04.1 CD Disk Does Not Have Such As AMD, Intel, And Nvidia Device Driver's Included In The Automatic Installation, And Adobe Flash, As Well As A Workaround 4 The S3 Suspend And Hibernate Mode Malfuntions, Just FYI. It Is Also Only A 2.1 Gigabyte Download 2 Disk (NOT 4 Giga Bytes), Because It Does Not Contain Ubuntu Server Edition, And/Or The Debian Command Line Installer Edition, Also Just FYI.

---

### Post by kevpan815 on 2008-08-16
P.S. I Should Also Mention That Hard Disk Drive Space Is Not An Issue 4 Me As I Have A 500 Giga Byte SATA NCQ 7200 RPM Hard Disk Drive, Just FYI.

---

### Post by kevpan815 on 2008-08-16
I Should Also Mention That The Reason Why I Originally Posted This Both Here And In Dell's Forum, Is That Several People In Dell's Forum Who's Computer's Came With Earlier Copies Of OEM Ubuntu (Such As 7.04 And/Or 7.10) (Mine Came With 7.04) Expressed An Interest In Downloading A Dell OEM Copy Of Ubuntu 8.04.1, So Now That it Is Available, I Have Posted This Both Here And In Dell's Forum, Just FYI.

I Should Also Mention That My 4X PLDS Blue-Ray DVD+RW Burns CD's In Ubuntu At A Very High Speed (So High That The CD Always Fails 2 Burn Correctly), However It Burns DVD's Just Fine At A DVD Speed Of 2.4X, Just FYI.

---

### Post by TimDaniels on 2008-08-16
> **kevpan815 said:**
> The Dell Disk Contains Extra Features That The Regular Ubuntu 8.04.1 CD Disk Does Not Have Such As AMD, Intel, And Nvidia Device Driver's 

The generic Ubuntu 8.04 download provided the proper nVidia driver for me.  Whether it was automatically downloaded by the package manager, I don't know, but all I had to do was to check it as being "enabled" once Ubuntu was running.


> It Is Also Only A 2.1 Gigabyte Download 2 Disk (NOT 4 Giga Bytes)

The **7.10** download .iso file is 4.3GB, not the 8.04 .iso file - which is 2.2GB.  My mistake.  The 8.04 download still requires a DVD's capacity, though.


*TimDaniels*

---

### Post by sultanoswing on 2008-08-16
Just FYI (since that seems to be the sarcastic reposte of choice in this thread), of more interest to me is the automatic partitioning - can anyone confirm that this install disc automatically partitions the drive with no ability to customise it? If so, it really is a restoration disc rather than a useful updater / recoverer, if it doesn't have the ability to leave the user's /home partition unformatted.

Oh - and no 64-bit edition as far as I can see.

Good to see Dell finally get this out, though.

---

### Post by superm1 on 2008-08-17
> **sultanoswing said:**
> Just FYI (since that seems to be the sarcastic reposte of choice in this thread), of more interest to me is the automatic partitioning - can anyone confirm that this install disc automatically partitions the drive with no ability to customise it? If so, it really is a restoration disc rather than a useful updater / recoverer, if it doesn't have the ability to leave the user's /home partition unformatted.

Oh - and no 64-bit edition as far as I can see.

Good to see Dell finally get this out, though.
Yes it is a restoration disk.  If your /home is on a different drive it won't touch that.  If you modify the preseed options you can adjust what the automated procedure does, but at that point you are probably better off using a normal Ubuntu CD/DVD if you need to customize.

---

### Post by TimDaniels on 2008-08-17
> **superm1 said:**
> Yes it is a restoration disk.  If your /home is on a different drive it won't touch that....

**Drive**?  Do you mean "separate partition" or "separate disk"?  I assume you mean "separate disk", i.e "separate hard drive", but see how the terms morph?  And in the Windows world, how many times have you seen "C: drive" instead of "C: partition"?  In this case, to remove ambiguity, your reply should have been "If your home is on a different hard drive, the restoration disk won't touch it".  And the corollary is "If your /home is mounted on the same hard drive as /, the restoration disk will totally obliterate it".  And how many laptops have a 2nd hard drive to mount /home?  In short, the "restoration disk" - after the first couple days of laptop ownership - could truly be called a "wipe-out disk".

Here's my humble suggestion to Dell's Ubuntu cabal:  **Offer a true re-installation** .iso file (with necessary drivers) like it did for 7.10, and provide a utilities CD like it does for pre-installed Vista machines.  That way, **everyone will be happy**.

*TimDaniels*

---

### Post by BigSilly on 2008-08-17
Well I've been waiting for this to put on the wife's 1525n Dell which came with 7.10. I thought it might be a proper re-install disc, but it doesn't seem to be looking that way. Why is it such a big download? 2.1Gb seems an awful lot. Even with the extra customisation, it shouldn't take up half a DVD should it?

I think I'll just stick in a normal Ubuntu CD and customise it myself. She just didn't want to lose her LinDVD playback software, which is why we waited. So yeah, we're a bit disappointed here too.

---

### Post by superm1 on 2008-08-17
> **BigSilly said:**
> Well I've been waiting for this to put on the wife's 1525n Dell which came with 7.10. I thought it might be a proper re-install disc, but it doesn't seem to be looking that way. Why is it such a big download? 2.1Gb seems an awful lot. Even with the extra customisation, it shouldn't take up half a DVD should it?

I think I'll just stick in a normal Ubuntu CD and customise it myself. She just didn't want to lose her LinDVD playback software, which is why we waited. So yeah, we're a bit disappointed here too.
It was made from an Ubuntu DVD Live filesystem (squashfs).  The DVD squashfs includes all language packages pre-installed.

---

### Post by superm1 on 2008-08-17
> **TimDaniels said:**
> **Drive**?  Do you mean "separate partition" or "separate disk"?  I assume you mean "separate disk", i.e "separate hard drive", but see how the terms morph?

No, frankly I don't  see how the terms morph.  I said drive, and I meant drive.  There are multiple laptops that Dell sells that include multiple drives.

> 
 And in the Windows world, how many times have you seen "C: drive" instead of "C: partition"?  In this case, to remove ambiguity, your reply should have been "If your home is on a different hard drive, the restoration disk won't touch it".  And the corollary is "If your /home is mounted on the same hard drive as /, the restoration disk will totally obliterate it".

The recovery DVD restores the drive to how it would have been out of the factory, so if you modify the partition tables at all to put /home on a separate partition, it won't be useful.

> 
 And how many laptops have a 2nd hard drive to mount /home?  In short, the "restoration disk" - after the first couple days of laptop ownership - could truly be called a "wipe-out disk".

Most of the 17" models have the option for multiple drives.  The second drive is not touched in the recovery process.  The purpose of the disk is to restore your system to a known functional state.  It is your own responsibility to back up data if you are to use it.

> 
Here's my humble suggestion to Dell's Ubuntu cabal:  **Offer a true re-installation** .iso file (with necessary drivers) like it did for 7.10, and provide a utilities CD like it does for pre-installed Vista machines.  That way, **everyone will be happy**.

*TimDaniels*
Utilities CDs are still included, and so is a normal Ubuntu DVD with all machines sold.  Even for Vista machines, the recovery DVD will remove all partitions and data.

Like I have said several times now, the factory process used for 8.04 is not conducive to an interactive installation.

---

### Post by phenest on 2008-08-17
> **kevpan815 said:**
> The Dell Disk Contains Extra Features...As Well As A Workaround 4 The S3 Suspend And Hibernate Mode Malfuntions...

If Dell know how to make hibernate and suspend work, can this be included on a standard Ubuntu install? Or is it already?

---

### Post by phenest on 2008-08-17
Does the Dell Ubuntu install include mp3 support? If so, how have they overcome the problem of royalties (seeing as it's a free download)?

---

### Post by superm1 on 2008-08-17
> **phenest said:**
> If Dell know how to make hibernate and suspend work, can this be included on a standard Ubuntu install? Or is it already?
See [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Failed_Studio_Suspend](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Failed_Studio_Suspend)

The exact root cause of the bug was not identified other than that it was caused by the USB driver.  For this reason, a Stable Release Update was never made.  A workaround is included for it.

> **phenest said:**
> Does the Dell Ubuntu install include mp3 support? If so, how have they overcome the problem of royalties (seeing as it's a free download)?
If you buy a system from Dell w/ Ubuntu preinstalled, you receive a DVD playback solution as well as legal codecs for Windows Media and MP3 files.  The licensing costs are covered w/ the price of the system.

---

### Post by gbrainin on 2008-08-17
> **superm1 said:**
> If you buy a system from Dell w/ Ubuntu preinstalled, you receive a DVD playback solution as well as legal codecs for Windows Media and MP3 files.  The licensing costs are covered w/ the price of the system.

Whatever happened to the plans to allow those of us who bought our Ubuntu-preinstalled Dells before DVD playback was offered to add this feature?

In truth, I'm less interested in DVD playback than in the Windows Media license, if that allows me to encode WMA files.  If that's not a feature of the licensed system, than this is just an academic question for me.

---

### Post by TimDaniels on 2008-08-18
> **superm1 said:**
> Even for Vista machines, the recovery DVD will remove all partitions and data.

**Wrong-go**!  My XPS-M1330, purchased early in February, 2008, came with a **genuine Vista installation DVD** that will not wipe out any partitions that it is not explicitly directed to wipe out.  In that respect, it is like Dell's downloadable Ubuntu 7.10 re-installation .iso file.  Why you guys switched to discharging the 8.04 piece of effluent has yet to be answered - I suspect for legal reasons.

> Most of the 17" models have the option for multiple drives.  The second drive is not touched in the recovery process.  The purpose of the disk is to restore your system to a known functional state.  It is your own responsibility to back up data if you are to use it.

So, to summarize:

1) The Dell 8.04 reinstallation DVD will **wipe out all** partitions on the primary disk.

2) The Dell 8.04 reinstallation DVD will create:

  a) a **Primary partition** complete with diagnostic utilities - which is entirely **superfluous** since a utilities CD is included with the PC,

  b) another **Primary partition** for as-delivered system recovery - also entirely **superfluous** because what one already has is, in effect, is a recovery partition,

  c) an **Extended partition** with a logical drive containing a swap partition of size 2GB or thereabouts.

  d) an Ubuntu **Primary partition** that takes up the rest of the disk.

3) The is **a change** from the Dell 7.10 reinstallation DVD which only installed Ubuntu to a partition that the user specified and would put Grub (the boot loader) either in the MBR or in the Ubuntu partition, and the size and placement of the swap partition was at the direction of the user, and which would not touch any other partitions.

4) If you want to keep /home on a partition that doesn't get wiped out by the reinstallation DVD, you have to have a laptop with a **17" screen** and the **optional 2nd internal hard drive**.

5) And none of this includes the LinDVD software.


Wow!  What value!

Now, the hard questin:

**Why doesn't Dell provide a true re-installation .iso file for Ubuntu 8.04 like it did for Ubuntu 7.10**?

*TimDaniels*

---

### Post by superm1 on 2008-08-18
> **TimDaniels said:**
> **Wrong-go**!  My XPS-M1330, purchased early in February, 2008, came with a **genuine Vista installation DVD** that will not wipe out any partitions that it is not explicitly directed to wipe out.  In that respect, it is like Dell's downloadable Ubuntu 7.10 re-installation .iso file.  Why you guys switched to discharging the 8.04 piece of effluent has yet to be answered - I suspect for legal reasons.

Yes, and these systems come with genuine Ubuntu 8.04 DVDs too.  The recovery DVD i'm referring to is what gets sent to you in the event that your hard drive goes bad.

> 
5) And none of this includes the LinDVD software.

This is paid for when you buy a system.  It can't just be distributed with the recovery media.

> 
**Why doesn't Dell provide a true re-installation .iso file for Ubuntu 8.04 like it did for Ubuntu 7.10**?

*TimDaniels*
Because it's not necessary.  For 7.10 drivers and backports didn't make it into the Ubuntu archive, it made more sense.  For 8.04, everything on that DVD is already available in Ubuntu.

---

### Post by TimDaniels on 2008-08-18
> **superm1 said:**
> For 8.04, everything on that DVD is already available in Ubuntu.

Wow!  What value!  It's not even worth the download(!) considering that Dell's "8.04" consists of 2.16GB and must be burned to a DVD and it obliterates everything, and Ubuntu's "8.04" fits on a CD and it does what the user tells it to.

*TimDaniels*

---

### Post by superm1 on 2008-08-18
> **TimDaniels said:**
> Wow!  What value!  It's not even worth the download(!) considering that Dell's "8.04" consists of 2.16GB and must be burned to a DVD and it obliterates everything, and Ubuntu's "8.04" fits on a CD and it does what the user tells it to.

*TimDaniels*
Tim:
As I've said several times now, some users prefer to have something that has a recovery framework integrated and no extra steps "for enabling" their drivers or "installing" their languages.

That's what this disk is.  If it's not of value to you, don't use it.  To some people it is.

---

### Post by anjilslaire on 2008-08-18
superm1:
Your diligence & patience is greatly appreciated with Timdaniels. However, for simplicity soimething like [linuxmint]("http://www.linuxmint.com/") may be more appropriate for Tim, who seems bent on arguing his point beyond all reasonable explanations.

I'm not usually one to point users to another (modified) distro, but this may be more towards something Tim may be looking for, with lots of extra codecs included in the ISO.

---

### Post by superm1 on 2008-08-18
> **gbrainin said:**
> Whatever happened to the plans to allow those of us who bought our Ubuntu-preinstalled Dells before DVD playback was offered to add this feature?

In truth, I'm less interested in DVD playback than in the Windows Media license, if that allows me to encode WMA files.  If that's not a feature of the licensed system, than this is just an academic question for me.
I don't believe anything to cover encoding is shipped.  You'll have to contact fluendo directly to look for a solution on that.

---

### Post by TimDaniels on 2008-08-18
> **superm1 said:**
> ...some users prefer to have something that has a recovery framework integrated and no extra steps "for enabling" their drivers or "installing" their languages.

That's what this disk is.

Yes, I see that you've quietly changed the title of the download from **Dell OS Reinstallation 8.04 DVD ISO** to [b]
Dell OS Factory Recovery 8.04.1 DVD ISO[/b] ([http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)).  I guess that acknowledges the truth of my complaint - that calling it a "reinstallation DVD" like that of 7.10 (which was an actual re-installation DVD .iso) **was misleading**.  But sadly, you forgot to re-name the .iso file itself - it's still named "**ubuntu-8.04.1-dell-reinstall.iso**"! 

*TimDaniels*

---

### Post by TimDaniels on 2008-08-18
> **anjilslaire said:**
> ...this may be more towards something Tim may be looking for, with lots of extra codecs included in the ISO.

Anji, if you've been reading this thread at all, you'd know that "what I've been looking for" is an installation .iso that includes all drivers and work-arounds for my Dell M1330 laptop like the "reinstallation DVD .iso" that was made available for download for 7.10.  _That_ .iso lived up to its name.  The 8.04 DVD.iso, until yesterday when its name was quietly changed, was also called a "reinstallation DVD .iso", but it was actually an "OEM recovery DVD .iso" that wiped the entire disk and set up partitions that most people don't even want or need.  That Dell has changed the name now to an **OEM recovery DVD .iso** - acknowledges that it was previously mis-named.

*TimDaniels*

---

### Post by TimDaniels on 2008-08-18
> **TimDaniels said:**
> it was previously mis-named.

Here's the name ("Dell OS **Reinstallation** 8.04.1 DVD ISO") up until about yesterday:
[http://209.85.141.104/search?q=cache:JF3gEqKvP6MJ:linux.dell.com/wiki/index.php/Ubuntu_8.04+dell+ubuntu+8.04+reinstallation+DVD&hl=en&ct=clnk&cd=3&gl=us](http://209.85.141.104/search?q=cache:JF3gEqKvP6MJ:linux.dell.com/wiki/index.php/Ubuntu_8.04+dell+ubuntu+8.04+reinstallation+DVD&hl=en&ct=clnk&cd=3&gl=us)

Here's the name ("Dell OS **Factory Recovery** 8.04.1 DVD ISO") today:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

Just a leeeetle change.  <hee, hee>

*TimDaniels*

---

### Post by anjilslaire on 2008-08-18
I *have* been reading your responses, Tim. The problem is, you've been arguing over the name of the ISO, which hasn't been an issue for the vast majority of users. Also, this ISO (regardless of it's name) isn't going to give you what you're looking for. 
It will not supply *all* the  codecs & drivers/workarounds that are shipped on the original drive. For example, none of the downloadable images will provide the LinDVD playback codecs that are installed on the original system. So effectively, you've been arguing over a filename, not the functionality provided. 

Yes, it wiped the drive. No, it will not reinstall *all* of the factory configured drivers/codecs.

---

### Post by superm1 on 2008-08-18
> **TimDaniels said:**
> Here's the name ("Dell OS **Reinstallation** 8.04.1 DVD ISO") up until about yesterday:
[http://209.85.141.104/search?q=cache:JF3gEqKvP6MJ:linux.dell.com/wiki/index.php/Ubuntu_8.04+dell+ubuntu+8.04+reinstallation+DVD&hl=en&ct=clnk&cd=3&gl=us](http://209.85.141.104/search?q=cache:JF3gEqKvP6MJ:linux.dell.com/wiki/index.php/Ubuntu_8.04+dell+ubuntu+8.04+reinstallation+DVD&hl=en&ct=clnk&cd=3&gl=us)

Here's the name ("Dell OS **Factory Recovery** 8.04.1 DVD ISO") today:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

Just a leeeetle change.  <hee, hee>

*TimDaniels*
Tim:
Yes I took your suggestion and changed the name.  My not "announcing" it in here immediately shouldn't be interpreted as a silent change.  I have other responsibilities too besides responding to posts on the forums.

---

### Post by Anditsu on 2008-08-18
"Here's my humble suggestion to Dell's Ubuntu cabal:  **Offer a true re-installation** .iso file (with necessary drivers) like it did for 7.10, and provide a utilities CD like it does for pre-installed Vista machines.  That way, **everyone will be happy**."

*TimDaniels*[/QUOTE]

This is a great point! Doing so saves some time driver hunting. I'm looking to buy a Dell inspiration 1525,and would like to know more about how they portion the drive. Being as that we are on the subject of recovery CDs;is there a program that allows you to ghost the drive or another way to back up the system updates with having to wait and catch up?

---

### Post by TimDaniels on 2008-08-19
> **anjilslaire said:**
> I *have* been reading your responses, Tim. The problem is, you've been arguing over the name of the ISO

You read the leaves and ignore the trees.  My complaint has been that the **recovery DVD file for 8.04** was presented exactly as was the **reinstallation DVD file for 7.10**.  Plus their names were misleading as well since they were both called "reinstallation files".  But even though the earlier file truly was a "reinstallation file", the "reinstallation file" for 8.04 was really a recovery file with a totally different and unpleasant outcome.  And to confirm that the names were misleading, the name of the 8.04 recovery file was quietly changed to "factory recovery" when I pointed it out yesterday in this forum.  So to be explicit just for you, the recovery file, which was presented in the same way as a previous reinstallation file had been and even called a reinstallation file, did not act like a reinstallation file in that it wiped out my entire disk contents.

And as for "SuperM"'s sneaky little name change, making that name change without any acknowldgement of a naming error was sneaky and dishonest.  All "SuperM" had to do was make a quick reply saying "OK, I'll change that.  Thanks.", but instead... he didn't, and he was caught by Google's archives.   

*TimDaniels*

---

### Post by phenest on 2008-08-19
So, to recap, Dell are offering a recovery disc. That makes sense. That's no different to having a Windows recovery disc. If you want a proper Windows install disc, you buy a genuine copy of MS Windows. If you want a proper Ubuntu install disc, you download Ubuntu from [www.ubuntu.com](www.ubuntu.com).

Maybe this thread can be closed now, just FYI (nobody's used that for a while :) ).

---

### Post by akniss on 2008-08-19
> **phenest said:**
> so, to recap, dell are offering a recovery disc. That makes sense. That's no different to having a windows recovery disc. If you want a proper windows install disc, you buy a genuine copy of ms windows. If you want a proper ubuntu install disc, you download ubuntu from [www.ubuntu.com](www.ubuntu.com).

Maybe this thread can be closed now, just fyi (nobody's used that for a while :) ).

FYI:
:lolflag:

---

### Post by sultanoswing on 2008-08-21
> **phenest said:**
> So, to recap, Dell are offering a recovery disc. That makes sense. That's no different to having a Windows recovery disc. If you want a proper Windows install disc, you buy a genuine copy of MS Windows. If you want a proper Ubuntu install disc, you download Ubuntu from [www.ubuntu.com](www.ubuntu.com).

Maybe this thread can be closed now, just FYI (nobody's used that for a while :) ).

What would be ideal from some of our POV (at least some of us, such as Tim) is a customised Ubuntu install disc which is Ubuntu, but with Dell's drivers compiled in and the options to do as you wish with the installation a la the regular Ubuntu install.

Having said that, the garden GNOME Ubuntu install runs damn near everything out-of-the-nox on my 1330, so I'm certainly not complaining. And even if Dell did put out a Dell Ubuntu Install disc with all the drivers and options, I can still see two groups of dissatisfied users:

1) Why does it contain all that extra bloat?

2) It's confusing to noobs who just want a "rest-to-factory" option.

---

### Post by phenest on 2008-08-21
Then how about if Dell were to supply packages for all their stuff? In a repository, maybe?

---

### Post by Zalmor on 2008-08-22
> **BigSilly said:**
> Well I've been waiting for this to put on the wife's 1525n Dell which came with 7.10. I thought it might be a proper re-install disc, but it doesn't seem to be looking that way. Why is it such a big download? 2.1Gb seems an awful lot. Even with the extra customisation, it shouldn't take up half a DVD should it?

I think I'll just stick in a normal Ubuntu CD and customise it myself. She just didn't want to lose her LinDVD playback software, which is why we waited. So yeah, we're a bit disappointed here too.

If you still have your original ISO image file from Dell, search for & copy the **lindvd_1.2.5.27.dell-ubuntu1_i386.deb** file from the Dell ISO image to a USB external flash drive.  Boot up the new Newer version of the **ubuntu-8.04.1-dell-reinstall.iso**, DON'T use INSTALL yet.

Try the 'Live mode' I think its called, and install the **lindvd_1.2.5.27.dell-ubuntu1_i386.deb** from _within_ the 'Live mode' from your USB flash drive.  It worked here as I tried it on my 'The Bourne Supremacy' and the DVD played with no problems.  Video and Sound have no problems playing .. so far!  :)

LinDVD is now running here on my M1330n series laptop which I bought a few months ago with Gutsy Gibbon preinstalled, and is now running the  Hardy Heron version of **ubuntu-8.04.1-dell-reinstall.iso** on the hard drive here. \\:D/

Your mileage may vary of course.  :mrgreen:

---

### Post by BigSilly on 2008-08-29
Thanks for your advice Zalmor. I don't know why I didn't think of that! I'll backup the file, and install Hardy as soon as the missus clears it. ;) 

I notice Dell have removed their ISO from the link in the first post here. I should be OK using a regular ol' Hardy ISO shouldn't I?

---

### Post by superm1 on 2008-08-29
> **BigSilly said:**
> Thanks for your advice Zalmor. I don't know why I didn't think of that! I'll backup the file, and install Hardy as soon as the missus clears it. ;) 

I notice Dell have removed their ISO from the link in the first post here. I should be OK using a regular ol' Hardy ISO shouldn't I?
ISO link still works? [http://linux.dell.com/files/ubuntu/hardy/iso-images/ubuntu-8.04.1-dell-reinstall.iso](http://linux.dell.com/files/ubuntu/hardy/iso-images/ubuntu-8.04.1-dell-reinstall.iso)

---

### Post by BigSilly on 2008-08-29
> **superm1 said:**
> ISO link still works? [http://linux.dell.com/files/ubuntu/hardy/iso-images/ubuntu-8.04.1-dell-reinstall.iso](http://linux.dell.com/files/ubuntu/hardy/iso-images/ubuntu-8.04.1-dell-reinstall.iso)

Oh I see. I just clicked the link in the first post and the page has changed completely. The link to download isn't there as it was before, so I just presumed it had been recalled or something. Thanks for that.

---

### Post by sTpny on 2008-09-03
Does anyone know if the dell re-install iso will install a dual boot system?  I'm downloading the iso now, but I'm not sure if it will do what I need it too. My client wants ubuntu but he also wants his broken Vista re-installed, yuck, what a pain. Click ok.. Ok.. Click ok.. ok.. reboot.. ok.. reboot.. ok.. 

I'd like to not have to go through the windows install again, so I'd like to get this ubuntu install right the first time. So does the ubuntu dell reinstall give a dual-boot option, or shoud I use the standard 8.01?

Also, what happens when you press the media direct button after installing a dual-boot system when you are logged into ubuntu.  Does it still cause any problems with the hd partitions?

Help muchly appreciated, especially if it comes tonight.  I've got an identical install to do on another machine tomorrow.

---

### Post by RetiredInMaine on 2008-09-03
Having read through all of the posts to here, I am totally confused. I thought I was very computer literate so maybe it's my advanced age.

My situation and resultant question.

I have a Dell Inspirion 1420 laptop that came with 7.04 pre installed. I upgraded to 7.10 from the ubuntu repository yesterday and my system will no longer run gdm. My working assumption is that I need Dell specific drivers. 

My question: If I want to go to 8.04 on my laptop can I use the iso from ubuntu even though it will wipe out the two dell specific partitions, will it have the proper drivers including wifi?,
OR
Should I go with the Dell reinstall ISO, ie is it really an install ISO with everything I need? I don't need / want the MS codecs, also I am not concerned about losing data as everything on my laptop is also on my desktop and very well backed up.

---

### Post by superm1 on 2008-09-03
> **sTpny said:**
> Does anyone know if the dell re-install iso will install a dual boot system?  I'm downloading the iso now, but I'm not sure if it will do what I need it too. My client wants ubuntu but he also wants his broken Vista re-installed, yuck, what a pain. Click ok.. Ok.. Click ok.. ok.. reboot.. ok.. reboot.. ok.. 

I'd like to not have to go through the windows install again, so I'd like to get this ubuntu install right the first time. So does the ubuntu dell reinstall give a dual-boot option, or shoud I use the standard 8.01?

No, if you want to perform a dual boot, you will need to set up Ubuntu after windows using a normal Ubuntu disk.  Your other option is to set up windows in a virtual machine for your client so that if it decides to go unstable again, the base OS (Ubuntu) is still OK.

> 
Also, what happens when you press the media direct button after installing a dual-boot system when you are logged into ubuntu.  Does it still cause any problems with the hd partitions?

I would recommend removing media direct if it gets installed from your Vista recovery media.  Newer factory versions of media direct are not troublesome anymore, but I'm not sure what machine you are referring to.

> 
Help muchly appreciated, especially if it comes tonight.  I've got an identical install to do on another machine tomorrow.
Good luck :)

---

### Post by chalewa on 2008-09-03
> **kevpan815 said:**
> I Should Also Mention That The Reason Why I Originally Posted This Both Here And In Dell's Forum, Is That Several People In Dell's Forum Who's Computer's Came With Earlier Copies Of OEM Ubuntu (Such As 7.04 And/Or 7.10) (Mine Came With 7.04) Expressed An Interest In Downloading A Dell OEM Copy Of Ubuntu 8.04.1, So Now That it Is Available, I Have Posted This Both Here And In Dell's Forum, Just FYI.

I Should Also Mention That My 4X PLDS Blue-Ray DVD+RW Burns CD's In Ubuntu At A Very High Speed (So High That The CD Always Fails 2 Burn Correctly), However It Burns DVD's Just Fine At A DVD Speed Of 2.4X, Just FYI.

why do you capitalize the first letter of every word?

---

### Post by superm1 on 2008-09-03
> **RetiredInMaine said:**
> Having read through all of the posts to here, I am totally confused. I thought I was very computer literate so maybe it's my advanced age.

My situation and resultant question.

I have a Dell Inspirion 1420 laptop that came with 7.04 pre installed. I upgraded to 7.10 from the ubuntu repository yesterday and my system will no longer run gdm. My working assumption is that I need Dell specific drivers. 

You shouldn't be needing any special drivers for starting X.  It's the same Intel/NVIDIA drivers as in the archive.  Perhaps worthwhile opening another thread to debug that issue at hand.

> 
My question: If I want to go to 8.04 on my laptop can I use the iso from ubuntu even though it will wipe out the two dell specific partitions, will it have the proper drivers including wifi?,

You can use the Dell ISO or the Ubuntu ISO.  The Dell ISO will recreate those two partitions for you.

> 
OR
Should I go with the Dell reinstall ISO, ie is it really an install ISO with everything I need? I don't need / want the MS codecs, also I am not concerned about losing data as everything on my laptop is also on my desktop and very well backed up.
It's a piece of recovery media that will restore the machine to a factory state as though it was shipped with that OS.  IE, it will wipe out everything on the machine before starting.

---

### Post by RetiredInMaine on 2008-09-03
superm1  Thank you for the clarifications.

I tried installing from the Dell ISO and got a bazillion error messages. Said the heck with it and installed from the normal ISO. Every thing works fine now. Maybe I had a bad burn on the Dell ISO, I used KB3 for both burns. Anyway it all works and I am happy. Thanks again. :)

---

### Post by putz3000 on 2008-09-03
I am glad to find this thread.  I understand Tim's complaint and at the very least was important for anyone thinking anything other than a complete wipe out of their drive would occur.  

That said I am disappointed in Dell over this.  Not because of a 2 gig DL, but because I bought my 1530 prior (about 3 month) to Ubuntu being offered.  I would love to get my hands on the official Dell version to see if there is better driver support issues and for the codecs/multi-media app.  But even though I can prove I bought and own my laptop, Dell will force me to purchase another laptop to get the full Dell Ubuntu install.  And DL'ing and installing this version will not give me everything I would get if I purchased a "Second" laptop (something I don't need or have the money for).

If the Dell version includes limited Ubuntu support which is sold with the cost of the Dell laptop or if there are costs for multi-media apps/files, then charge me for those benefits and let me buy a copy for my Dell laptop.  I am glad that Dell is offering more and more products with Linux but I would like to see something further done for folks who later want the dell Ubuntu install with all of its features.

---

### Post by anjilslaire on 2008-09-03
> **RetiredInMaine said:**
> Having read through all of the posts to here, I am totally confused. I thought I was very computer literate so maybe it's my advanced age.

My situation and resultant question.

I have a Dell Inspirion 1420 laptop that came with 7.04 pre installed. I upgraded to 7.10 from the ubuntu repository yesterday and my system will no longer run gdm. My working assumption is that I need Dell specific drivers. 

My question: If I want to go to 8.04 on my laptop can I use the iso from ubuntu even though it will wipe out the two dell specific partitions, will it have the proper drivers including wifi?,
OR
Should I go with the Dell reinstall ISO, ie is it really an install ISO with everything I need? I don't need / want the MS codecs, also I am not concerned about losing data as everything on my laptop is also on my desktop and very well backed up.

I've got a 1420 shipped with Vista that I zeroed the drive and installed the standard kubuntu 8.04 with no issues. I also have a 1420n (shipped with ubuntu 7.10) that I wiped and loaded kubuntu 8.04 on (I prefer a separate /home partition). No issues on either system driver-wise.

---

### Post by Zalmor on 2008-09-21
> **BigSilly said:**
> Thanks for your advice Zalmor. I don't know why I didn't think of that! I'll backup the file, and install Hardy as soon as the missus clears it. ;) 

Glad I could help out as I'm a total newbie to Ubuntu also.

---

### Post by dhurst on 2008-11-24
> **RetiredInMaine said:**
> superm1  Thank you for the clarifications.

I tried installing from the Dell ISO and got a bazillion error messages. Said the heck with it and installed from the normal ISO. Every thing works fine now. Maybe I had a bad burn on the Dell ISO, I used KB3 for both burns. Anyway it all works and I am happy. Thanks again. :)

I have the same problem.  There is an error in the oem post install scripts somewhere.  I haven't the time to figure it out.  Basically, you get no X and no networking.  The system is there but gdm, networking, and X aren't running.  Probably needs some checking by Dell engineers.  I tried this on a Dell Ubuntu 1420n laptop.
Dow

---

### Post by superm1 on 2008-11-25
Did you run the install with networking plugged in?

If so, please try unplugging it when you run the restore.

If you didn't, then please attach /var/log/installer/chroot.sh.log

---


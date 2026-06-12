---
title: "Misconfigured new PC (oem autologin)"
date: 2008-09-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by danemaslen on 2008-09-30
I recently bought an Inspiron 530 running Ubuntu Hardy Heron from Dell.  Either it was shipped to me before it had been properly configured or something went wrong in the initial boot (see later).

The most obvious symptom of the problem is that username oem is automatically logged in.  To use my own username, i.e. the one created by adduser during the initial boot, I have to log out the oem session and then log in again.  I know why the autologin of oem is occurring and hence I know which file needs editing to stop it.  Unfortunately that leads me on to the most severe symptom of the problem...

When it was created during the initial boot my own username was not added to the admin group.  The only member of the admin group is oem.  I, of course, do not know the oem password.  Therefore there is no way I can use sudo.

I thought I knew how to get out of this impasse.  I hit ESC at the appropriate stage of the boot so that grub would give me a list of boot options.  I selected

  Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)

in the belief that it would boot up in single-user mode.  Alas it appeared to do a normal boot.  I repeated this procedure and paid attention to the messages appearing on the screen.  I'm fairly sure I saw a reference to being unable to do 'init 1', together with an error number.  I repeated the procedure again, intending to record the exact details of the error message but got a different one, namely:

root=UUID=8369f4ef-bc20-4d3a-8912-f9e18d5a7a31 ro all_generic_ide quiet
kinit: name_to_dev_t(/dev/disk/by-uuid/66b05f48-e346-4baa-a0d2-2d871a9ac2fc) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/66b05f48-e346-4baa-a0d2-2d871a9ac2fc
kinit: No resume image, doing normal boot..

That is the error message that now occurs very time I try the recovery-mode boot.

I mentioned above that I suspected that either the PC was shipped to me before Dell had configured it properly or that something had gone wrong in the initial boot.  An error certainly was reported during the initial boot (the monitor had come with two cables and no indication of which one should be used; one cable was already connected to the monitor, so I used that one and it proved to be wrong).  Although the initial boot continued, e.g. prompting me for details of a username to be created, it occurs to me that maybe some of the script was unable to run because of the incorrect monitor configuration.

I've now exhausted my knowledge of how to gain control of my own PC.  I'm looking for the following:

 * Suggestions about what I can do to gain control.

 * Speculation about what else might be wrong, i.e. what else might not have been done by the initial boot.  Better yet, is the script that the initial boot ran likely to be around somewhere so that I can check it out?

Thanks in advance.

Dane Maslen

---

### Post by bcom on 2008-09-30
Just a couple of questions for you.

Did you call Dell to ask if they can give the password?  Perhaps Dell has a set of "standard" passwords they use with the OEM user name.

When you are logged on as OEM and go to System - Administration - Users and Groups and it asks you for a password to authenticate, did you try leaving it blank?

Did the computer come with a Recovery DVD?  Perhaps you could use that to reinstal.

If it did not come with a recovery DVD you could go here: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04), download and burn the Dell Recovery DVD and then reinstall Ubuntu.  However, beware, note this warning on web page.

"If you already have a Dell system with Ubuntu shipped on it, you should use that DVD to perform the recovery. The DVD playback software and media playback codecs are *NOT* included in this public image. Using this DVD will produce a system very similar to what you receive when ordering Ubuntu, but not identical."

---

### Post by danemaslen on 2008-10-02
> **bcom said:**
> Did you call Dell to ask if they can give the password?


I didn't.  I suspect that any call to Dell in the UK about a Ubuntu system would be met with bemusement.  Also I consider it extremely unlikely that they would be prepared to give out the password if it were standard.

> **bcom said:**
> When you are logged on as OEM and go to System - Administration - Users and Groups and it asks you for a password to authenticate, did you try leaving it blank?


Somewhat bizarrely System - Administration - Users and Groups doesn't prompt me for a password to authenticate, even though the help claims that it does.   Instead it simply greys out most options (i.e. all usernames other than oem and all groups).

> **bcom said:**
> Did the computer come with a Recovery DVD?  Perhaps you could use that to reinstal.



It came with the following three DVDS/CDs:
[LIST]
[*]Ubuntu 8.04 LTS DVD
[*]Dell 228WFP LCD Monitor
[*]Dell drivers and utilities for installing Dell Inspiron 530/530s n series computer software
[/LIST]
I have been wondering whether it's possible to boot using the Live DVD, mount the appropriate hard disk partition and manually edit the group file.

> **bcom said:**
> 
If it did not come with a recovery DVD you could go here: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04), download and burn the Dell Recovery DVD and then reinstall Ubuntu.  

That's not an option for me as I'm currently still in the dark ages when it comes to internet connections, i.e. I'm on dial-up (though I could perhaps enlist the help of a friend with broadband).  If the worst comes to the worst I would have to reinstall from the Ubuntu 8.04 LTS DVD that I have.  I'm assuming that that is a generic Ubuntu rather than one tailored by Dell (or am I mistaken?) and that I might have other issues were I to adopt that approach.

> **bcom said:**
> 
However, beware, note this warning on web page.

"If you already have a Dell system with Ubuntu shipped on it, you should use that DVD to perform the recovery. The DVD playback software and media playback codecs are *NOT* included in this public image. Using this DVD will produce a system very similar to what you receive when ordering Ubuntu, but not identical."

Thanks for pointing that out.

Dane Maslen

---

### Post by danemaslen on 2008-10-02
> **danemaslen said:**
> Somewhat bizarrely System - Administration - Users and Groups doesn't prompt me for a password to authenticate, even though the help claims that it does.   Instead it simply greys out most options (i.e. all usernames other than oem and all groups).


I eventually found the option in System - Administration - Users and Groups that would permit changing the oem password.  Only when I tried using this option was I prompted for a password to authenticate.  I can therefore now confirm that the oem password is not a null string.

> **danemaslen said:**
> I have been wondering whether it's possible to boot using the Live DVD, mount the appropriate hard disk partition and manually edit the group file.


Another possibility has occurred to me (assuming that the above is not possible).  I have a spare USB disk drive on another PC.  Could I plug it into the Inspiron 530, use the Live DVD to install Ubuntu on it, boot from the external disk drive, mount the appropriate internal disk partition and manually edit the group file?

Dane Maslen

---

### Post by gbrainin on 2008-10-02
> **danemaslen said:**
> I have been wondering whether it's possible to boot using the Live DVD, mount the appropriate hard disk partition and manually edit the group file.

This is precisely what I was going to suggest from your initial post.  This should be able to get your login to be able to use sudo, and from that point you can do anything you need.

By the same token, however, I couldn't even begin to guess what else might be "wrong" with your system because it is in this odd state.  It could be nothing, or it could be any number of things; it seems to me your bigger problem is not getting the ability to fix things (by being a member of the administrators group), but knowing what to fix.

I would suggest you try calling the Dell Linux support line, 866-622-1947.  As you guess, the regular support lines are fairly useless for this sort of thing ("You're running 'lin-uks'?  Okay, so what do you see when you click on the Start menu?"), but the Linux line has, in the past(*), been extremely helpful.

(*) There are rumors that the North American call center has been closed since I last called them, so things might have changed.  Still, you're better off calling people who ostensibly know about Linux versus ones who don't.

---

### Post by bcom on 2008-10-02
In regard to calling Dell to ask about a password, I didn't know if Dell, like the manufacturers of some hardware devices, makes use of default passwords that they leave to the end-user to change when he or she configures the hardware.

---

### Post by bcom on 2008-10-02
Here is another thought on booting into recovery mode.

Based on a suggestion found in the book, A Practical Guide To Ubuntu Linux:


To boot into Recovery mode from an installation CD.  I don't know if your DVD will present you with the same screens and options as described in the book.

 
This is what it says in the book:

"If you are booting from the live/install Desktop CD/DVD, when Ubuntu displays the Ubuntu logo and startup menu, press F6.  Ubuntu stops its countdown and displays the boot option line which looks similar to the following:

Boot Options :casper initrd=/casper/initrd.gz quiet splash --

Ubuntu displays only the end of the boot options line.  You can use RIGHT and LEFT ARROW keys to display other parts of the line.  With the cursor pointed to the right of the SPACE following the two hyphens at the right end of the line, type "single" and press return.

Ubuntu boots to recovery mode from the CD/DVD; it will not require a password."

If it works, you should be able to go to Use and Groups and make the necessary changes.

---

### Post by danemaslen on 2008-10-03
> **bcom said:**
> Based on a suggestion found in the book, A Practical Guide To Ubuntu Linux:


To boot into Recovery mode from an installation CD.  I don't know if your DVD will present you with the same screens and options as described in the book.

 
This is what it says in the book:

"If you are booting from the live/install Desktop CD/DVD, when Ubuntu displays the Ubuntu logo and startup menu, press F6.  Ubuntu stops its countdown and displays the boot option line which looks similar to the following:

Boot Options :casper initrd=/casper/initrd.gz quiet splash --

Ubuntu displays only the end of the boot options line.  You can use RIGHT and LEFT ARROW keys to display other parts of the line.  With the cursor pointed to the right of the SPACE following the two hyphens at the right end of the line, type "single" and press return.

Ubuntu boots to recovery mode from the CD/DVD; it will not require a password."

If it works, you should be able to go to Use and Groups and make the necessary changes.

Eureka!  This put me on to the easiest solution. I interrupted the boot from hard disk with ESC and then edited one of the boot options that grub was offering me by adding "single" at the end of the line. Then when I got given the option to drop out to the CLI, I did so and edited /etc/group with ed (having first taken a copy in case I goofed the edit!).

At long last I have a PC that I am in control of.  Now all I have to do is work out what else is wrong with it.

Dane Maslen

---

### Post by danemaslen on 2008-10-03
> **gbrainin said:**
> By the same token, however, I couldn't even begin to guess what else might be "wrong" with your system because it is in this odd state.  It could be nothing, or it could be any number of things; it seems to me your bigger problem is not getting the ability to fix things (by being a member of the administrators group), but knowing what to fix.

Indeed.  The knowledge that I wasn't able to fix anything (and the need to work out how to rectify that) was, however, holding me back from investigating what was wrong.  I'm fairly sure that whatever problems there are must stem from one of two causes:

[LIST]
[*]An error during the initial boot of the system
[/LIST]
The initial boot had to do various one-off tasks, e.g. prompting me for details of a username to be created.  If the script that did those tasks did not delete itself, then (assuming I can find it) I can in principle review what else it should have done and determine what needs fixing.
[LIST]
[*]Failure by Dell to prepare the system properly before shipping
[/LIST]
There's an application (it runs a script) on oem's desktop called "Prepare for shipping to end user".  It's not impossible that whoever 'prepared' my PC failed to run this.  Now that I've been able to change the oem password, I'm in a position to be able to run it, but first I want to work out what it's going to do!

Dane Maslen

---

### Post by gbrainin on 2008-10-03
> **danemaslen said:**
> There's an application (it runs a script) on oem's desktop called "Prepare for shipping to end user".  It's not impossible that whoever 'prepared' my PC failed to run this.  Now that I've been able to change the oem password, I'm in a position to be able to run it, but first I want to work out what it's going to do!

In my mind, this fact (the existence of the "Prepare for shipping to end user" script) makes it nearly certain that the problem is on Dell's end, and not a problem during your initial boot.  If it weren't for that, I would have suggested using the Dell hard drive re-imaging partition, but I have no idea if that'll work right (or at all) prior to the system being properly set up.

I suspect your problem is fairly unique, and won't be able to be authoritatively answered by anyone outside of Dell.  At this point, calling the Linux support line (866-622-1947) would be my first line of defense.

---

### Post by superm1 on 2008-10-03
Could you post the contents of the logs in /var/log/installer ?  We'll see if anything stands out as causing such a failure.

---

### Post by danemaslen on 2008-10-03
> **gbrainin said:**
> In my mind, this fact (the existence of the "Prepare for shipping to end user" script) makes it nearly certain that the problem is on Dell's end, and not a problem during your initial boot..

My initial rummagings lead me to suspect otherwise, though some of the scripts I've been looking at are pretty opaque so I'm not 100% sure I'm drawing the correct conclusions.

One thing that I am fairly sure of is that at least one of /usr/sbin/oem_config and /usr/sbin/oem_config_firstboot ran when I first booted the system.  I know because one of them (I forget which one) has some 'panic' code at the end that
[LIST]
[*]announces that the oem configuration has failed,
[*]warns that the system might therefore be unusable,
[*]instructs the user to use adduser and then reboot, 
[*]and then dumps the user at the CLI prompt.
[/LIST]This is indeed what happened to me six weeks ago when I first booted the system (though I'd forgotten the details in the intervening period that included two holidays that prevented me from investigating the problem more promptly).

Had it not detected an error oem_config would have undone the oem autologin by replacing /etc/gdm/gdm.conf.  oem_config_firstboot would have removed the oem username and its login directory.  The fact that these scripts ran when I first booted strongly suggests to me that the "Prepare for shipping to end user" script had indeed been run by Dell as something must have set up the 'first' boot to execute these scripts (obviously the real first boot was by Dell and did not execute them).

It also looked to me as though one or other of the two scripts (again I forget which one) would have created a new user and added it to the admin group if there had not been an error.  I now need to look at oem_config and oem_config_firstboot more carefully to see what else they were trying to do.

> **gbrainin said:**
> I suspect your problem is fairly unique, and won't be able to be authoritatively answered by anyone outside of Dell.  At this point, calling the Linux support line (866-622-1947) would be my first line of defense.

I think your assertions are correct, but I'm going to persevere with fixing the problem myself because:
[LIST]
[*]I think I would get frustrated trying to get sense out of Dell here in the UK (the US Linux support line would make for a very costly call!).
[*]I strongly suspect that I now have a system that is essentially ok (though I'm dubious about X-windows: I've seen some behaviour that suggests to me that the X-server won't start, but I've yet to investigate this).
[*]This is proving an interesting learning exercise.  I've already learnt some bits and pieces about gdm and grub configuration.  Who knows what else I might learn in the next week or so?
[/LIST]
If I stumble across some show-stopper several months down the line, you have my permission to say you told me so!

Dane

---

### Post by gbrainin on 2008-10-04
Well, you didn't say (or I didn't recall) the panic code part.  That does change my guess.

I also forgot that you are in the U.K., which does indeed make calling Dell linux support here an expensive proposition--and I agree, calling the regular (windows) support line would be a waste of everyone's time.

Barring finding a U.K. support line to call, I would suggest taking superm1's offer of help.  Try posting the contents of the /var/log/installer files, and they might help figure out (and perhaps even solve) the problem.

---

### Post by danemaslen on 2008-10-05
> **gbrainin said:**
> Well, you didn't say (or I didn't recall) the panic code part.

No, by the time I got round to posting my query, my recollection of the events had blurred sufficiently that I incorrectly remembered the initial boot "doing the adduser" rather than telling me to do it.  It was only when I started rummaging around in the scripts and saw the panic code that it refreshed my memory about what had really happened.

> **gbrainin said:**
> I would suggest taking superm1's offer of help.  Try posting the contents of the /var/log/installer files, and they might help figure out (and perhaps even solve) the problem.

I shall be doing that, though I have one or two things that I need to learn how to do before I can do it!  As I'm fairly busy for the next couple of days there might be a slight delay.

Dane

---

### Post by danemaslen on 2008-10-07
> **superm1 said:**
> Could you post the contents of the logs in /var/log/installer ?  We'll see if anything stands out as causing such a failure.

There were two log files in /var/log/installer.

I've attached casper.log as CASPER.LOG.txt.

The other, syslog, exceeds the forum limit for attachments of type text.  All the entries in syslog are date-stamped 13th August which is when the PC was being prepared by Dell (18th August was when I did my initial boot).

---

### Post by superm1 on 2008-10-07
The syslog (and chroot.sh.log if it's around) are more relevant than the casper log.  Can you post them to a pastebin?

---

### Post by danemaslen on 2008-10-08
> **superm1 said:**
> The syslog (and chroot.sh.log if it's around) are more relevant than the casper log.  Can you post them to a pastebin?

There's no chroot.sh.log.

If I done it right, syslog is now at [http://pastebin.ca/1222862](http://pastebin.ca/1222862)

Dane

---

### Post by superm1 on 2008-10-09
The combination of that log and the absence of chroot.sh.log make it seem like the system completed factory install no troubles.

When you first turned it on, did you have a DELL splash screen explaining your EULA before it started to boot to Ubuntu?

If all of this is true, what happened when you first booted?  

The quote I see from you is this:
> 

I mentioned above that I suspected that either the PC was shipped to me before Dell had configured it properly or that something had gone wrong in the initial boot. An error certainly was reported during the initial boot (the monitor had come with two cables and no indication of which one should be used; one cable was already connected to the monitor, so I used that one and it proved to be wrong). Although the initial boot continued, e.g. prompting me for details of a username to be created, it occurs to me that maybe some of the script was unable to run because of the incorrect monitor configuration.

Yes, a lot of stuff happens during this initial boot.  Rather than dissecting the actual issue that happened, you might just be better off hitting ESC at your GRUB menu, and recovering it to factory state from there.  There is an option to do so.

---

### Post by danemaslen on 2008-10-10
> **superm1 said:**
> The combination of that log and the absence of chroot.sh.log make it seem like the system completed factory install no troubles.

When you first turned it on, did you have a DELL splash screen explaining your EULA before it started to boot to Ubuntu?


My memory isn't reliable enough for me to say whether I did or not (it's not the sort of detail I would tend to remember).

> **superm1 said:**
> If all of this is true, what happened when you first booted?  


Again bear in mind the fallibility of my memory, but roughly:

Initially stuff scrolled through on the screen just as it would have on an old-style terminal.  All seemed to be going well.

Then there was an error message.  I certainly cannot remember the text of it, but at the the time it seemed clear enough to me that an attempt to use the monitor as a monitor (rather than as a scrolling terminal) had failed.  See below.

The monitor nonetheless went into a graphical mode with poor resolution.

I'm fairly sure that ultimately I was told to use adduser and warned that the system might be unusable.  I used adduser, shut down, corrected the presumed problem with the monitor (see below) and rebooted.  The system came up fine, but I eventually spotted that all was not as it should be.  As I've commented to some friends, if I'd been a completely naive user, I would not have noticed anything was amiss, whereas if I'd been an expert I'd have known how to investigate and fix it properly.  Alas I was neither.

The monitor came with two cables that could be used for connecting to the computer: a DVI cable and a VGA cable.  On delivery the VGA cable was already plugged in to the monitor so I used it to connect to the computer.  That was how the monitor was connected during the initial boot.  After the initial boot I removed the VGA cable and used the DVI one instead.  Given the error message that I saw during the initial boot (and the fact that the display has been fine ever since I switched to using the DVI cable), it has been my assumption that having the monitor connected using the VGA cable did not conform with what Linux was expecting or could cope with.

> **superm1 said:**
> Yes, a lot of stuff happens during this initial boot.  Rather than dissecting the actual issue that happened, you might just be better off hitting ESC at your GRUB menu, and recovering it to factory state from there.  There is an option to do so.

If it takes me back to the state in which the system left the Dell factory (i.e. rather than back to a generic Ubuntu installation - there are one or two CODECs or something missing from a publicly available installation, aren't there?), then I'm quite happy to do that as I have deliberately held back from doing any work on this PC while I have been seeking help on this issue (it's only today that I've finally got round to configuring a dialup connection to the internet - all my previous posts were from an aged PC running Windows 98).

Thanks for taking a look at the log files.

Dane

---

### Post by superm1 on 2008-10-10
> **danemaslen said:**
> 
If it takes me back to the state in which the system left the Dell factory (i.e. rather than back to a generic Ubuntu installation - there are one or two CODECs or something missing from a publicly available installation, aren't there?), then I'm quite happy to do that as I have deliberately held back from doing any work on this PC while I have been seeking help on this issue (it's only today that I've finally got round to configuring a dialup connection to the internet - all my previous posts were from an aged PC running Windows 98).

Thanks for taking a look at the log files.

Dane
Yeah, your options are as follows:
1) Reinstall from the recovery partition/grub menu.
2) Grab those files from the recovery partition ./debs/main/* and install them in a normal Ubuntu installation.

---

### Post by danemaslen on 2008-10-11
> **superm1 said:**
> Yeah, your options are as follows:
1) Reinstall from the recovery partition/grub menu.


That worked just fine and the initial boot behaved itself perfectly.  If only I'd realised earlier that there was a recovery partition (I'd been puzzled why there wasn't a recovery DVD), I'd have done this sooner.

If my speculation about why the problem originally occurred (i.e. monitor connected incorrectly) is correct, I'm vaguely surprised that other people haven't encountered this problem as the documentation sent with the PC gave no clue as to which of the two cables had to be used.

Thanks for the help.

Dane

---

### Post by gbrainin on 2008-10-12
My apologies for not mentioning the recovery partition myself.  The way you initially presented the problem, there were strong indications that something had gone wrong at the factory, not during your install, so I rejected the recovery option as pointless.  In retrospect, I suppose I should have mentioned it, since even if it didn't help, it is unlikely to do any harm (in your situation).

In any case, glad to hear you're up and running at last.

---

### Post by gbrainin on 2008-10-12
BTW, I have been using my computer with the VGA connection since I bought it, with no problem.

---

### Post by andybleaden on 2008-10-13
and also use this 

[http://linux.dell.com/wiki/](http://linux.dell.com/wiki/)

I always thought that dell uk were farmed off abroad anyway to a call centre. Interesting post. 

I have just bought the same deal (Dell 530 pre installed) ...it arrives tomorrow so hope the set up goes ok.

How have you found it generally now that you can access as sudo?

---

### Post by danemaslen on 2008-10-13
> **gbrainin said:**
> BTW, I have been using my computer with the VGA connection since I bought it, with no problem.

And I've just tried mine with the VGA connection again and it works just fine.  This leaves me very puzzled about what went wrong on the initial boot.  If I had the time to spare, I'd use the recovery partition again to revert to the factory setup and then try the initial boot again with the VGA connection to see if the problem reoccurred.

Dane

---

### Post by danemaslen on 2008-10-13
> **andybleaden said:**
> and also use this 

[http://linux.dell.com/wiki/](http://linux.dell.com/wiki/)


Yes, I did try taking a look there at one stage. 

> **andybleaden said:**
> I have just bought the same deal (Dell 530 pre installed) ...it arrives tomorrow so hope the set up goes ok.

How have you found it generally now that you can access as sudo?

Fine, though I'm going through a fairly steep learning curve (other than using Red Hat briefly about 5 years ago it's about 10 years since I last used Unix, and even then it was just a minor sideline as I was a VMS system manager).

I do wish though that Dell would leave an unused partition on the disk.  I'd like to have such a partition in case I ever take leave of my senses and want to install Vista alongside Ubuntu.  Trying to work out how one reduces the size of the partition that Ubuntu is installed on is not one of the easiest tasks for a newbie!

Dane

---

### Post by superm1 on 2008-10-14
> **danemaslen said:**
> Yes, I did try taking a look there at one stage. 



Fine, though I'm going through a fairly steep learning curve (other than using Red Hat briefly about 5 years ago it's about 10 years since I last used Unix, and even then it was just a minor sideline as I was a VMS system manager).

I do wish though that Dell would leave an unused partition on the disk.  I'd like to have such a partition in case I ever take leave of my senses and want to install Vista alongside Ubuntu.  Trying to work out how one reduces the size of the partition that Ubuntu is installed on is not one of the easiest tasks for a newbie!

Dane
There are technical limitations to the factory process that would prevent this from (easily) being done.  

My advice here would be to install Vista in a Virtual Machine such as VirtualBox and handle your windows tasks through that.

If you are insistent upon resizing partitions, I would recommend that you burn your backup DVD and nuke the recovery partition.  Place Vista there.  If you aren't happy with that allocation size, then boot up a live CD (NOTE: not your recovery DVD, a normal Live CD, your recovery DVD will erase things again) and resize partitions using the partition editor on the CD.

---

### Post by danemaslen on 2008-10-14
> **danemaslen said:**
> And I've just tried mine with the VGA connection again and it works just fine.  This leaves me very puzzled about what went wrong on the initial boot.  If I had the time to spare, I'd use the recovery partition again to revert to the factory setup and then try the initial boot again with the VGA connection to see if the problem reoccurred.

Dane

I've managed to find time to switch to the VGA connection, use the recovery partitition and go through the initial boot again.  It worked fine.  That does tend to suggest that there was something wrong with the system as shipped by Dell, but apparently not something that affected the recovery partition.

Dane

---

### Post by suntigen on 2009-02-11
the default password for user OEM (at least in the Dell 8.10 ISO) is "password" (omit the quotes).

---


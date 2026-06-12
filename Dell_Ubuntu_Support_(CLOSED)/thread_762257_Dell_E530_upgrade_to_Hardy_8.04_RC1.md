---
title: "Dell E530 upgrade to Hardy 8.04 RC1"
date: 2008-04-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nanog on 2008-04-21
Worked like a charm. LinDVD still works and the only problem was a known kernel bug that required switching to RAID (from SATA) in the BIOS.

---

### Post by davidpbrown on 2008-04-22
I've also just found this solution suggested on the bug reports.

Can you explain what it means to switch to RAID on a system that has existing partitions?

I want to upgrade not fresh install the entire system.

My very limited understanding has me thinking of RAID having multiple disks behaving as a single disk - I don't want to risk disrupting the partitioning I have atm.

I've added another disk from an old system, so don't just have the one disk. With just one disk I expect RAID might behave as single SATA..

---

### Post by freddybob on 2008-04-23
I'd also like to know the impact of this change.  It'd also be good to have simple step-by-step instructions on how to do it.

---

### Post by prinknash on 2008-04-23
> **freddybob said:**
> I'd also like to know the impact of this change.  It'd also be good to have simple step-by-step instructions on how to do it.

I don't really understand the implications of the change but suspect that if you've only got the one hard disk (as I have) the RAID setting doesn't have any effect beyond making it possible to boot the Inspiron 530, which I couldn't do in Hardy with SATA Mode set to the default IDE. (Never had this problem with previous versions of Ubuntu.)

To make the change, just boot the machine and, at the prompt, press F2 to enter System Setup. Go to the screen headed Integrated Peripherals, find the entry for SATA Mode, and change it from IDE to RAID. Save the new settings and reboot. That's all.

Obviously you do this at your own risk - but I gather quite a lot of people have done it (including me) and I'm unaware of any adverse effects.

p

---

### Post by ieldib on 2008-04-25
Hi,

Are you using the X3100 for video, or does your E530 have a videocard installed? Do you have video playback while compiz is enabled ? 

Thanks in advance.

---

### Post by prinknash on 2008-04-25
> **ieldib said:**
> Hi,

Are you using the X3100 for video, or does your E530 have a videocard installed? Do you have video playback while compiz is enabled ? 

Thanks in advance.

I suppose we're talking about the same machine - only I'm not sure where the "E" comes from. I'm using an Inspiron 530N desktop machine, which came with Ubuntu 7.04 (subsequently upgraded to 7.10 and now 8.04).

Anyway, it has a GeForce 8300GS video card and I don't have Compiz enabled, so can't tell you anything very useful, I'm afraid.

p

---

### Post by ditoa on 2008-04-25
Where did you find info on this kernel bug regarding the hard drive? I just tried to install 8.04 on my 0 day old 530 and was just presented with loads of errors :(

The Dell Wiki has nothing. Could you give me a link?

---

### Post by gbrainin on 2008-04-25
> **ditoa said:**
> Where did you find info on this kernel bug regarding the hard drive? I just tried to install 8.04 on my 0 day old 530 and was just presented with loads of errors :(

The Dell Wiki has nothing. Could you give me a link?

The Dell Wiki typically(*) doesn't have anything on a new release for some weeks, until the Dell techs have a chance to test things.

However, ths is a known bug, as shown at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702")

(*) Since there's only been one previous release since Dell started selling Ubuntu, "typically" just means "what happened last time."

---

### Post by davidpbrown on 2008-04-26
I found this yesterday
[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)
> Other known issues
DELL RAID firmware compatibility
Ubuntu 8.04 LTS fails to run on some DELL PowerEdge servers with RAID controllers, such as the 3/Di controller in the DELL PowerEdge 1650, due to a bug in the RAID firmware. To install or upgrade to Ubuntu 8.04 LTS on a system with the affected RAID controller, you will first need to upgrade your RAID firmware.

Unfortunately I then got nowhere looking around the repository trying to upgrade the BIOS
[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)
.. lots of rpm and seemingly less of the simple debian/Ubuntu compatible BIOS upgrading software. If anyone can make that work let us know how..

Of course that might be confusing two types of thing..

---

### Post by freddybob on 2008-04-26
Will changing to RAID wipe my disk?

---

### Post by Aearenda on 2008-04-26
Your disk will be fine. The change just affects how the kernel accesses the disks. But you can use the 'other' workaround if you want to play safe - use the all_generic_ide boot option. Take a look at bug 153702, towards the end ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702)). I use the RAID setting in the BIOS, it works just fine for me (I have two non-identical SATA drives, and made no changes on the extra outrageously ugly BIOS screen that pops up at boot time).

---

### Post by davidpbrown on 2008-04-26
I tried switching the RAID on in the BIOS and it didn't get further than simply recognising the disks were non-RAID atm. It asked if I wanted to set them as RAID.. which I didn't do because I expect that might make an irreversible change. I don't know if doing that would be equivalent to some type of formatting but expected it might at least undo the partition table.

I'm waiting for the Dell site to suggest their upgrade. I note the option is now in my update manager tempting the unwary to try.. I'm thinking it should really warn them to look at the releasenotes known issues first.

Just seen Aearenda's post and might try that grub change..

---

### Post by Aearenda on 2008-04-26
I just set mine back to IDE in the BIOS and tried the all_generic_ide setting, and everything is working as before :-)

Edit: But just maybe a little slower? Subjective feel only.

---

### Post by freddybob on 2008-04-26
For less-technically minded people that might be reading this (ok, for me) how do you go about adding the boot option to grub?

---

### Post by Aearenda on 2008-04-26
Here's how to add the option to GRUB temporarily, at boot time:

When you see the 'Press ESC to enter menu' message, press ESC.
At the Grub menu, press 'e'.
Use the cursor keys to move the highlighting down to the 'kernel' line shown, and press 'e' again.
Move to the end of the line, add a space if necessary, then add 'all_generic_ide' (without the quotes).
Press <ENTER> to complete the edit, and then press 'b' to boot.

The system should now boot up using that option.

To add it permanently, do this:
First, start a terminal session from Applications/accessories (it can be done from the GUI entirely, but you miss any error messages that way) then enter: 
```
cp /boot/grub/menu.lst ~/grub-menu-backup.lst
```
This makes a copy of the file in your home directory just in case :-)

Next:
```
gksudo gedit /boot/grub/menu.lst
```

Look for the line like this:
```
# kopt=root=UUID=8a4a255a-c61f-452b-ad60-927b8c48ba70 ro
```

Yours will have a different UUID part. 
After the 'ro' add 'all_generic_ide' so it looks like this:
```
# kopt=root=UUID=8a4a255a-c61f-452b-ad60-927b8c48ba70 ro all_generic_ide
```

Then save the file and quit gedit.

Next enter:
```
sudo update-grub
```
If it asks, choose the package maintainer's version unless you want to keep other customisations (in which case, you probably don't need to be told to add the all_generic_ide option to all the kernel lines yourself and skip this step).
Now type CTRL and 'd' to exit the terminal session and reboot.

Finally, if you would rather change to RAID mode than do the above, on my 530 the steps are (from memory):
1. Reboot
2. Press F2 at the DELL splash screen to enter 'setup'
3. Go to the Integrated Peripherals page
4. Move to the 'SATA Mode' line and press <ENTER>
5. Select RAID and accept the change
6. Press F10

When the extra ugly BIOS screen comes up (it should report the drive(s) are not in RAID mode), just let it time out and continue. All we have done in reality is to activate a different part of the BIOS for disk access.

Don't attempt any of this if you don't understand what is happening!

---

### Post by davidpbrown on 2008-04-26
That all went well - Thank you!
\\:D/

---

### Post by Aearenda on 2008-04-26
Glad to hear it! Well done.

---

### Post by prinknash on 2008-04-26
> **Aearenda said:**
> Glad to hear it! Well done.

Using the RAID setting rather than IDE for SATA, I don't think I get the "ugly BIOS screen" you mention. I certainly get a few lines of text that I didn't get with an IDE setting, which begin "AHCI Option BIOS ......" something or other; but it scrolls away so quickly to the screen where you choose what you want to load that I can't actually read any more of it. It sounds like you get something rather more extensive?

(I'm still on the original 1.0.3 BIOS version for my Inspiron 530N - mainly because I can't work out whether there's a later version available for the 530N (as opposed to 530 or 530S) and, if there is, an easy way of loading it given that I don't have Windows on that machine! Maybe you're using a later version?)

p

---

### Post by Aearenda on 2008-04-26
No, that's the one I mean - I haven't changed BIOS version, and won't unless there is a good reason. I've been hurt by failed BIOS re-flashes too often. "If it ain't broke, don't fix it!" is a very good rule for BIOS updates, I reckon!

OK, maybe it's not that ugly. But it's still ugly, 1980s-ish. 

BTW, I think Dell have a way to do BIOS updates without Windows that I came across on their site. I may be imagining it. But even then, if it isn't broken...

---

### Post by gbrainin on 2008-04-26
There are instructions for doing firmware flashes without Windows on the [Dell Linux Wiki]("http://linux.dell.com/wiki/index.php/Repository/firmware"), but they're community-support only.  If something goes wrong, Dell won't help.  Even if they would, I tend to agree with Aearenda: don't flash the BIOS unless you have to.  I'm still using version 1.0.0, myself.

---

### Post by freddybob on 2008-04-27
I just upgraded my Inspiron 530n using the all_generic_ide fix.  It worked perfectly - the whole upgrade process took around 30 minutes.

---

### Post by prinknash on 2008-04-27
> **freddybob said:**
> I just upgraded my Inspiron 530n using the all_generic_ide fix.  It worked perfectly - the whole upgrade process took around 30 minutes.

Glad to hear it, freddybob.

In my experience, either the fix you mention or switching SATA from IDE to RAID will do the trick. I'm not sure if there's any particular advantage to using one rather than the other, but I haven't seen anyone suggesting that either can do any harm.

p

---

### Post by gbrainin on 2008-04-27
> **prinknash said:**
> In my experience, either the fix you mention or switching SATA from IDE to RAID will do the trick. I'm not sure if there's any particular advantage to using one rather than the other, but I haven't seen anyone suggesting that either can do any harm.

Does anyone know of somewhere the IDE vs. RAID setting is explained?  This is a frequent question in these threads, and the answers tend to be a little sketchy.  I ask because:

So far I have downloaded but not installed Hardy.  I burned the CD, and could not even do the CD integrity check while the computer is in IDE mode (drops me to busybox).  I can get the live CD to start either in RAID mode or with the all_generic_ide switch, but if the BIOS is in RAID mode, my current setup (Gutsy) won't load properly: it gets to the GRUB menu, then instead of loading the OS it reboots itself.

From this I conclude that switching from IDE to RAID mode does make some difference to the way the OS interacts with the hard drive.  I'd like to know more about what that difference is.

(Using an Inspiron 530 with BIOS version 1.0.0, if that makes a difference.)

---

### Post by prinknash on 2008-04-27
> **gbrainin said:**
> Does anyone know of somewhere the IDE vs. RAID setting is explained?  This is a frequent question in these threads, and the answers tend to be a little sketchy.

I've seen something in one of these threads suggesting that AHCI, which gets switched on when you go from IDE to RAID mode, is a generally more advanced and better way of communicating with the kind of SATA controller we have in the Inspiron 530N. (It probably follows that forcing IDE with the other 'fix' mentioned here may not be using your system in the optimum way.)

A quick look at the Wikipedia entry on AHCI seems consistent with this but appears to suggest that there may be complications if you're running Windows as well as Ubuntu. My machine is Ubuntu only, so that doesn't bother me.

But - like you - I'd like to hear an explanation from someone who really understands this stuff. 

p

---

### Post by davidpbrown on 2008-04-27
I'm trying hard not to just do a 'me too!' post.. :)

I'd like a clearer explanation too, if only that now with it working I'm unlikely to then also install any .iso that Dell does produce in a few weeks. Useful as an .iso might be for a fresh installs, with the package list backed up I wonder a fresh image wouldn't get used.

---

### Post by freddybob on 2008-04-29
Me too!  :)

I'm very surprised this is not yet on Dell's list of 8.04 known issues.

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues)

---

### Post by jobcol on 2008-05-05
hi all
was having same issue after trying  8.04 and changed the SATA operation to RAID as suggested: system was booting fine.I now want to reinstall windows to set up a dual boot system, but since changing to RAID setting in BIOS i can no longer access the BIOS on my 530: F2 does not work and cant access boot menu via F12 either.

So i can no longer boot from a CD , or change boot order in BIOS to CD; just goes straight to HDD

any suggestions greatly appreciated

---

### Post by prinknash on 2008-05-05
> **jobcol said:**
> hi all
was having same issue after trying  8.04 and changed the SATA operation to RAID as suggested: system was booting fine.I now want to reinstall windows to set up a dual boot system, but since changing to RAID setting in BIOS i can no longer access the BIOS on my 530: F2 does not work and cant access boot menu via F12 either.


I don't understand that. On my Inspiron 530N, BIOS version 1.0.3, after changing the setting to RAID I went back and reset it to IDE so that I could try out the "all_generic_ide" solution (which did work) - and then went back and reset the SATA setting to RAID, which is where I left it. So I've been able to switch quite happily between the two; and the F2 and F12 keys work as they should.

Sorry - this doesn't help you.

p

---

### Post by Aearenda on 2008-05-05
> F2 does not work and cant access boot menu via F12 either.
I have changed back and forth several times. Have you tried moving the keyboard into a different USB socket?

---

### Post by ccacioppo on 2008-05-05
> **freddybob said:**
> Will changing to RAID wipe my disk?

YES !

---

### Post by RedRat on 2008-05-05
> **ccacioppo said:**
> YES !

I made the change and it does not wipe my disk! What are talking about?

---

### Post by Aearenda on 2008-05-05
Of course changing the BIOS setting to RAID will NOT wipe your disk. I have gone back and forth several times.

If you were to go the full hog and use the BIOS setup screen to establish RAID partitions on the disks, then yes, your disk will be affected. But we are not suggesting you do that.

Simply switching the BIOS setting to RAID modifies how the BIOS presents the drives to the kernel, fixes the problem, and leaves the drive contents unaffected. Along the way, it seems to go a little faster too.

---

### Post by Not Sure on 2008-05-20
Changing the SATA mode in the BIOS from IDE to RAID solved the upgrade problem for me too. The major problem was ubuntu would not start unless I edited the grub menu and put the parameter acpi=off after the parameter splash.  Turning off the advanced configuration and power interface then created shutdown problems with error messages.  Thanks for posting the BIOS change.  It solved the start-up problem and the shutdown problem.  Now, the upgrade from ubuntu 7.10 to ubuntu 10.4 was completely sucessful. I'm impressed with my Dell 530 and Hardy Heron.      

                                      
                                  :guitar:

---

### Post by freddybob on 2008-05-26
I have tried both RAID and IDE/all_generic_ide and know that both work well but I'd like to understand which is the better of the two.

I've read that Dell pre-configures the machines as IDE because Vista isn't compatible with RAID.  But I'm not dual-booting and have no intention of ever installing Windows on my computer.  Does that mean RAID is the better choice for me?

Is RAID faster than IDE?  More reliable?  What is the difference?

---

### Post by Aearenda on 2008-05-26
Setting the BIOS to RAID mode seems to make drive access a little faster subjectively, but it's not much. I haven't measured the difference. I may be imagining it. It ought to be faster, since it isn't pretending that a SATA drive is an IDE drive any more.

It isn't more reliable, since the drives themselves are still being used as single drives, not as an array of drives (RAID=Redundant Array of Inexpensive Drives). 

The difference is simply that the way the BIOS presents the drives to the kernel changes. It switches from an older way (IDE) to a newer way (natively SATA). Sort of. Something like that, any way :-)

---

### Post by fmaximo on 2008-06-08
Hello, Guys;

I Had updated the bios to the newest version on my Inspiron 530 (it was version 1.0.10 and now its 1.0.12 on my dell).

Ubuntu 8.04 is working fine, no aditional changes, just the default instalation!!! 


Go to Dell suport site and input your dell' s service tag (a group of sevem characters on machine's back) and follow the instructions.

Happy linuxing!!

Max

---

### Post by klein de usa on 2008-09-13
hi
i have a dell 4700 with two sata identical maxtor hard drives, when the second hard drive is pluged in, the bios sees the first sata-0 as maxitor and the second sata-2 as unknowen, and some times sees it as maxitor, when i first put the two hard drives in everything was good and after i started filling up the second hard drive it started coming up with errors, 87 errors
maxitor is replacing the drive, but i have never been convinced it was the drive. might this be part of the problem your having ?   i have no RAID setting in my bios.

---


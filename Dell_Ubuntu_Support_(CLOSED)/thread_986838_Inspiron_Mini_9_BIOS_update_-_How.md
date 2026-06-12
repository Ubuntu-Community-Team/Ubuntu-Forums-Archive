---
title: "Inspiron Mini 9 BIOS update - How?"
date: 2008-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Talon2 on 2008-11-19
I noticed that there is a A02 BIOS update for the Mini 9.  I've been researching how to do the update but have had little luck.  If one of you has updated your BIOS please share with us how you did it.

TIA

---

### Post by armandh on 2008-11-19
I have not done it on the mini 9 but I once had a computer that would not boot due to a bios check sum error. giving only access to the A:\ drive. the mini 9 can be swiched in the bios to boot first from a usb port.

I would load a bootable usb memory with compatable bios loader & updates. 
getting dos on to a usb memory stick may be a trick.
probably easier to use a usb cd drive to boot dos and do the rest

---

### Post by armandh on 2008-11-19
oops doubled posted some how

---

### Post by ytsejam1138 on 2008-11-19
Not my Utility, I found this on [My Dell Mini](http://www.mydellmini.com/forum/bios-upgrade-fails-p7011.html#p7011)

Created a simple utility program that will format a DOS bootable USB Flash Drive that you can then boot from in order to flash up to the latest I910 Mini / Vostro A90 flashBIOS.

Works well with USB Flash Drives up to 4GB in size, anything more just can't be formatted for DOS.

Successfully tested each BIOS included so I know it is working 100%.

Pick a location:

Torrent:  [http://thepiratebay.org/torrent/4513787](http://thepiratebay.org/torrent/4513787)

Hosted file:  [http://rapidshare.com/files/165242604/FlashBIOS_Mini9_-_from_USB_Drive.rar](http://rapidshare.com/files/165242604/FlashBIOS_Mini9_-_from_USB_Drive.rar)



BIOS A03 Leaked

Info on the leak:

[http://www.mydellmini.com/forum/view...6&p=7658#p7658](http://www.mydellmini.com/forum/view...6&p=7658#p7658)

Where you can download A03:

[http://www.mydellmini.com/forum/bios...s30.html#p7666](http://www.mydellmini.com/forum/bios...s30.html#p7666)

---

### Post by ytsejam1138 on 2008-11-19
Here is what Dell suggests:

snip

---

### Post by feranick on 2008-11-20
I am reposting this, hoping it's helpful:

**Disclaimer:** if something goes wrong with the bios update, you might brick your mini. *_**Do this at your own risk**_*

On a Windows capable PC (not the dell-mini)

**A. Create a USB bootable drive. For this you need:**

1a. if the PC is equipped with a floppy drive, make a bootable   floppy (using the format utility)

1b. If the PC is not equipped with a floppy, create a virtual one, using the the [free] "virtual floppy driver" from here:
[http://chitchat.at.infoseek.co.jp/vmware/vfd.html](http://chitchat.at.infoseek.co.jp/vmware/vfd.html)

2. Install the HP USB Disk Storage Format Tool Version 2.0.6
[http://www.bootdisk.com/plan40/hpflash1.zip](http://www.bootdisk.com/plan40/hpflash1.zip)

3. Run the HP USB Disk Storage Format Tool to format the USB drive. The program would need to use a DOS file image, so redirect it to the real or virtual floppy A:

4. The USB drive is now bootable.

**B. Prepare the new BIOS:**

1. Download and extract into a temporary folder "910_A00_BIOS" the older I910 BIOS with 16-bit DOS compatible flash utility:
[http://ftp.us.dell.com/bios/910_A00_BIOS.zip](http://ftp.us.dell.com/bios/910_A00_BIOS.zip)

2. Download 910_A02.exe BIOS from dell support
[http://support.dell.com](http://support.dell.com)

3. Run the 910_A02.exe file. MAKE SURE YOU SAY "DON'T CONTINUE" when the system detects a different PC.

4. Under C:\Windows\Temp\WINPHLASH grab the BIOS.ROM A02 BIOS

5. copy and paste it into the 910_A00_BIOS folder

6. You can either edit the FLASHB.BAT
Flash /x /MODE=3 KIZ00A00.wph
to
Flash /x /MODE=3 BIOS.wph

and rename the A02 BIOS from BIOS.ROM to BIOS.wph or
don't edit FLASHB.BAT and just rename BIOS.ROM to kiz00A00.wph

7. Copy the 910_A00_BIOS folder to a DOS bootable USB drive

**C. Install the new BIOS.** 

1. Reboot the mini, and make it to boot from the USB drive

2. When the DOS prompt appears, go to the BIOS directory in the USB drive and execute FLASHB.BAT in DOS.

3. The update should now take place.

4. When done the system should reboot automatically. Remove the USB drive

---

### Post by wx0112 on 2008-11-20
Download WinPE or WinPE-like and boot with it, you will enter a windows environment

and run the executable problem from dell and done.

---

### Post by Talon2 on 2008-11-20
> **ytsejam1138 said:**
> Here is what Dell suggests:

[http://support.dell.com/support/edocs/systems/ins910/en/sm/bios.htm#wp1110066](http://support.dell.com/support/edocs/systems/ins910/en/sm/bios.htm#wp1110066)

This doesn't work for me.  When I follow the directions I get a "Permission denied" message.

---

### Post by cmspider on 2008-11-20
I did something along the lines of what's in post #6, using but using fdisk, mkdosfs, and dosemu to make a small bootable dos partition on a usb stick.  

The bios flash worked just fine, but I haven't really noticed much different.

I created a thread on this issue at dell's linux forum here,:
[http://en.community.dell.com/forums/p/19242913/19375363.aspx](http://en.community.dell.com/forums/p/19242913/19375363.aspx)
and got a response that they will soon release a 'native' way to flash the bios.

---

### Post by anjilslaire on 2008-12-31
Worked great. Now I'm at A03. Thanks :)

---

### Post by magicfab on 2008-12-31
Please be aware any BIOS upgrades at this time are NOT recommended. You may void your original warranty if your Mini came with Ubuntu and you install a BIOS tested with Windows only.

Just FYI!

---

### Post by anjilslaire on 2008-12-31
I understand the business technicalities of what you're saying, but hardware-wise, that's not correct. The BIOS affects the hardware itself, not the software running on the hard drive.

I understand Dell/Canonical not recommending an upgrade because theres no released linux BIOS installer yet, but there's no reason that a BIOS upgrade would break the hardware if the BIOS is coded properly.

I installed the Dell-provided BIOS from a DOS environment. 

HOWEVER, before warranty threatening gets out of hand, Dell has provided a means to install from within Ubuntu, officially (posted on a dell.com page):

[Flashing the BIOS From the Solid-state Drive in Ubuntu®]("http://support.dell.com/support/edocs/systems/ins910/en/sm/bios.htm#wp1110066")

---

### Post by Talon2 on 2009-01-01
> **anjilslaire said:**
> 

HOWEVER, before warranty threatening gets out of hand, Dell has provided a means to install from within Ubuntu, officially (posted on a dell.com page):



I wouldn't get too excited about this official Dell posted method.

It doesn't work.

---

### Post by schimschone on 2009-01-01
Talon2 is correct.. Dell's method only ends up stating "No such file or directory".. so back to the drawing board.

---

### Post by magicfab on 2009-01-01
Please don't assume what the reasons are for my initial post. Just ask. These are not "technicalities".

> **anjilslaire said:**
> I understand the business technicalities of what you're saying, but hardware-wise, that's not correct. The BIOS affects the hardware itself, not the software running on the hard drive.

In fact it's quite the opposite. The operating system relies on a lot of information provided by the BIOS to function reliably. Last time I checked only A00 and A01 BIOS was shipping and was certified for Ubuntu.

Regarding the business implications of this, unless you post here officially for Dell or Canonical, please do not make such statements. I am asking our engineers specifically about A03 and will post about it here, however I stand by my first message in this thread.

> **anjilslaire said:**
> I understand Dell/Canonical not recommending an upgrade because theres no released linux BIOS installer yet, but there's no reason that a BIOS upgrade would break the hardware if the BIOS is coded properly.
The official, recommended way to update your BIOS from Ubuntu is documented here:
[https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)

If that method doesn't propose a new version, then there isn't one, as far as official software and hardware support is concerned. Granted, A00 systems will report they don't need an upgrade. I'll have confirmation about why no updates at all show up, but as I said last time I asked we had clear directions not to get any BIOS upgrades by other methods.

BIOS bugs do exist but in this case I am stating if you use a BIOS upgrade that wasn't tested on Ubuntu, you risk having software problems and yes, voiding your warranty. **ASK** first. Yes, Dell's downloads site is lacking in this respect.

> **anjilslaire said:**
> I installed the Dell-provided BIOS from a DOS environment. 
Keeping up with getting useful information on this thread, I'd like to know if this solved any specific issues for you ? There are no update notes on Dell's site, although someone reported getting more video memory. In support contexts ("keep the system working"), we advise not to fix something that's not broken, but I'd appreciate if you have more details about your reasons (other than keeping the BIOS up to date).

> **anjilslaire said:**
> HOWEVER, before warranty threatening gets out of hand, ...
Not threatening, just sharing what information I have. 

In fact this prompted me to triple-check the facts I have, I'll come back here with more when I can.

Cheers!

---

### Post by magicfab on 2009-01-01
Here's the post about A03 apparently enabling more VRAM:
[http://www.mydellmini.com/forum/i-think-a03-did-give-128mb-vram-max%C7%83-t2021.html](http://www.mydellmini.com/forum/i-think-a03-did-give-128mb-vram-max%C7%83-t2021.html)

---

### Post by Fredo on 2009-01-01
One reason why I consider upgrading ist the lack of F11 and F12 keys. Newer bioses are said to have them mapped to Fn+z and Fn+x. This would be a major improvement.

But I'll wait until an upgrade is officially supported. I just hope that actually people at Dell are working on this and lot letting Ubuntu users wait forever.

---

### Post by anjilslaire on 2009-01-01
Alright, let me clarify myself before things get out of hand (my apologies).
What I meant about the Dell/Canonical thing was, if they haven't provided an official linux-installer BIOS upgrade, then of course upgrading will be discouraged, as that could result in lots of unhappy users with bricked hardware. That's all I meant by 'business'.

Yes, I understand how the OS gets information about the hardware from the BIOS, etc. Of course I realize I'm anonymous user who you have no manner of verifying or understanding any credibility I may or may not have. As a result, per your request, I'll refrain from commenting further since I'm not employed by Dell or Canonical.

If your link is the official method of BIOS update, I do however suggest removing the  Dell.com sponsored link I found & posted. It's confusing.

I do have a question though:
Suppose I have a mini that's loaded with XP from Dell. I use the official download from 
[http://support.dell.com/support/downloads/driverslist.aspx?os=BIOSA&osl=EN&catid=-1&impid=-1&servicetag=HYPTWF1&SystemID=inspiron910&hidos=WW1&hidlang=en&TabIndex=](http://support.dell.com/support/downloads/driverslist.aspx?os=BIOSA&osl=EN&catid=-1&impid=-1&servicetag=HYPTWF1&SystemID=inspiron910&hidos=WW1&hidlang=en&TabIndex=)

and use my Service Tag to ensure I have the right product, and upgrade to A03. Fine and dandy, yes?
OK, I then decide to load my own Linux OS on it, and the hardware malfunctions  2 weeks later (nothing to do with the OS. SSD or keyboard or something fails). Is my hardware covered? Or is my warrantry void since I loaded software that's 'not compatible' with the firmware that was properly loaded on via approved OS?

Not trying to nitpick, just want to know whats going on.

Oh, as for performance, I've noticed quicker boot times, more vram, and the F11 & F12 keys.

Don't get me wrong. I'm not trying to spread any FUD or cause problems. I've had my mini for a few days, and I love it. No offense meant on my part. 

Please let me know if I've missed any points in my reply, or need clarification.

Thanks for your understanding & time :)

---

### Post by magicfab on 2009-01-01
> **anjilslaire said:**
> If your link is the official method of BIOS update, I do however suggest removing the  Dell.com sponsored link I found & posted. It's confusing.
Unfortunately I can't change anything on Dell's web resources.
:(

> **anjilslaire said:**
> I do have a question though:
Suppose I have a mini that's loaded with XP from Dell. I use the official download from 
[http://support.dell.com/support/downloads/driverslist.aspx?os=BIOSA&osl=EN&catid=-1&impid=-1&servicetag=HYPTWF1&SystemID=inspiron910&hidos=WW1&hidlang=en&TabIndex=](http://support.dell.com/support/downloads/driverslist.aspx?os=BIOSA&osl=EN&catid=-1&impid=-1&servicetag=HYPTWF1&SystemID=inspiron910&hidos=WW1&hidlang=en&TabIndex=)

and use my Service Tag to ensure I have the right product, and upgrade to A03. Fine and dandy, yes?
Sure.

> **anjilslaire said:**
> OK, I then decide to load my own Linux OS on it, and the hardware malfunctions  2 weeks later (nothing to do with the OS. SSD or keyboard or something fails).
Actually, you assume Dell Mini 9s with WinXP or with Ubuntu ship with the exact same hardware and BIOS, which is my initial point. 

> **anjilslaire said:**
> Is my hardware covered? Or is my warrantry void since I loaded software that's 'not compatible' with the firmware that was properly loaded on via approved OS?
Unfortunately, this is the wrong place to ask that. I can't answer for Dell, and they are the only ones able to answer that, that's why I suggested first ask Dell, then do as you please.

> **anjilslaire said:**
> Not trying to nitpick, just want to know whats going on.

Oh, as for performance, I've noticed quicker boot times, more vram, and the F11 & F12 keys.

Don't get me wrong. I'm not trying to spread any FUD or cause problems. I've had my mini for a few days, and I love it. No offense meant on my part. 

No problem, I think the tone is firendly and useful here :)

I can't remember the reference to boot times, but that's also something I can't repeat unless I have two exact same configurations in front of me, and I test and measure them. But that's because of my role, I may get into more trouble if I don't have proof of almost anything I say about Ubuntu :) 

VRAM and F keys are big motivators to upgrade BIOS, this being the holidays information flows a bit slower between everyone involved but I trust we'll have more details soon and will be able to share them.

Trust me, you don't want to brick you Mini over the holidays. Hold times are anything but short :)

---

### Post by anjilslaire on 2009-01-02
> **magicfab said:**
> 
Actually, you assume Dell Mini 9s with WinXP or with Ubuntu ship with the exact same hardware and BIOS, which is my initial point. 


Actually, thats not my assumption. I'm merely talking about installing non-shipped software on the hardware. 
If you say that the mini 9 with XP and the mini 9 with Linux (shipped) are not the same hardware, even when spec'd the same on Dell's website, I can only assume you are correct and (reasonably so) have insight into the hardware that we as consumers don't and therefore believe you. 

Since you brought it up, can you look into the issue for us and let us know what the hardware differences are between the "mini9XP" and "mini9Linux"? As some of us are hardware aficionados, it would be very interesting to know what we're purchasing. I imagine the only real difference would likely be in the motherboard, but please clarify.

---

### Post by magicfab on 2009-01-05
> **anjilslaire said:**
> Since you brought it up, can you look into the issue for us and let us know what the hardware differences are between the "mini9XP" and "mini9Linux"? As some of us are hardware aficionados, it would be very interesting to know what we're purchasing. I imagine the only real difference would likely be in the motherboard, but please clarify.

I would welcome a question about that on the Launchpad Answers system, here:
[https://answers.launchpad.net/dell-mini/+addquestion](https://answers.launchpad.net/dell-mini/+addquestion)

Unfortunately I can only volunteer a few hours (or even minutes) a week here, and on that questions tracker and I can't keep up with all public forums. 

I don't have any Dell Mini that shipped with Windows so I can't compare them side by side. More on that when/if you ask that on Launchpad where I can track and triage questions much easier than here.

Regarding the Dell BIOS upgrades safety, I just had confirmation that the only recommended version is A01 at this time. There are regressions for A03. We are not sure when A02 and A03 will ship from production or why they are on the Dell site without proper warnings. In my personal opinion, It's probably the legacy of a web site that has been Windows-centric for a long time, that is not changed quickly. 

The BIOS update published on the wiki at [https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS) doesn't work (and won't ever with Mini 9), as Compal and Dell chose to use a different BIOS and update mechanism. We (at Canonical) are still working with Phoenix to publish a Linux based tool that correctly updates this particular BIOS. 

I hope this clarifies the situation a bit, if there are any questions specifically related to BIOS I don't mind monitoring this one thread, however for other questions I'd appreciate going to the Answers facility in Launchpad.

---

### Post by magicfab on 2009-01-05
Forgot to ask, if CMSpider can share the method he/she used to upgrade the BIOS (using only Ubuntu packages/software without third party downloads), I'd appreciate it and I can test that.

Otherwise I'll test creating a FreeDOS bootable USB stick and putting the appropriate files on it and report back here as time permits.

---

### Post by anjilslaire on 2009-01-08
> **magicfab said:**
> I would welcome a question about that on the Launchpad Answers system, here:
[https://answers.launchpad.net/dell-mini/+addquestion](https://answers.launchpad.net/dell-mini/+addquestion)


Done :)

BIOS download still there, btw:

[http://support.dell.com/support/downloads/driverslist.aspx?os=BIOSA&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRON910&hidos=WW1&hidlang=en&TabIndex=](http://support.dell.com/support/downloads/driverslist.aspx?os=BIOSA&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRON910&hidos=WW1&hidlang=en&TabIndex=)

---

### Post by anjilslaire on 2009-01-14
OK, i now see BIOS A04, with instructions for both Windows & non-Windows environments. Whats the stance on A04? Is it still not recommended for Ubuntu versions?

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R207436&SystemID=INSPIRON910&servicetag=&os=BIOSA&osl=en&deviceid=18840&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=290595](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R207436&SystemID=INSPIRON910&servicetag=&os=BIOSA&osl=en&deviceid=18840&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=290595)
> 
Run the BIOS update utility from DOS environment (Non-Windows users)


NOTE: You will need to provide a bootable DOS diskette. This executable file does not create the DOS system files.


   1. Copy the file 910_A04.exe to a bootable floppy.


   2. Boot from the floppy to the DOS prompt.


   3. Run the file by typing Y:\910_A04.exe (where y is the drive letter where the executable is located).


---

### Post by magicfab on 2009-01-16
@anjislaire: that method doesn't provide any details on how to make a DOS  floppy bootable from Ubuntu.

See "Upgrading the BIOS using biosdisk and a floppy disk" at [https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS) for a method that will work from Ubuntu, although it requires a floppy drive.

---

### Post by anjilslaire on 2009-01-16
Understood. Is A04 still not recommended for Ubuntu?. It looks like not...

---

### Post by Talon2 on 2009-01-16
> **anjilslaire said:**
> OK, i now see BIOS A04, with instructions for both Windows & non-Windows environments. Whats the stance on A04? Is it still not recommended for Ubuntu versions?

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R207436&SystemID=INSPIRON910&servicetag=&os=BIOSA&osl=en&deviceid=18840&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=290595](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R207436&SystemID=INSPIRON910&servicetag=&os=BIOSA&osl=en&deviceid=18840&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=290595)

I don't get it.  I have a USB floppy drive and I have a DOS boot floppy.  I even have 910_A04.exe.  What I don't get is how a person is supposed to put file that is 2.1 mb in size (which is the size of 910_A04.exe) on a 1.4 mb floppy disk.

Anyone care to explain?

---

### Post by Mig Daddy on 2009-01-21
My Ubuntu Mini shipped with A01.  vRAM and the F11 & F12 keys aren't big issues for me.  I can also live with the boot time.  Do the newer BIOS updates provide anything else?  I have also been reading about how the A04 has detrimental effects on the keyboard layout, especially for non-US versions.

---

### Post by Ram0ne on 2009-01-21
This looks to be simple enough, just wish I could find the A04 download for Ubuntu not just the instructions [[COLOR="Blue"]Printed below[/COLOR]]("http://support.dell.com/support/edocs/systems/ins910/en/sm/bios.htm#wp1084976")


Flashing the BIOS From the Solid-state Drive in Ubuntu®

   1. Ensure that the AC adapter is plugged in and the main battery is properly installed.

   2. Turn on the computer.

	NOTE: Your computer may or may not ship with an external optical drive. Use an external optical drive or any external storage device for the procedures that involve discs.

   3. Click ® Places® Documents.

   4. Create a new folder and name it BIOS.

   5. Locate the latest BIOS update file for your computer at support.dell.com.

   6. Click Download Now to download the file.

   7. If the Export Compliance Disclaimer window appears, click Yes, I Accept this Agreement.

The File Download window appears.

   8. Click Save this program to disk and then click OK.

The Save In window appears.

   9. Click the down arrow to view the Save In menu, select Documents® BIOS, and then click Save.

  10. Click Close if the Download Complete window appears.

  11. Open the terminal command line application and proceed as follows:

         1. Type sudo -s

         2. Type your password

         3. Type cd Documents

         4. Type cd BIOS

         5. Type ./910A00

flash start... string appears.

The computer will restart automatically once the BIOS flash is complete.

---

### Post by anjilslaire on 2009-01-21
There is no official A04 for ubuntu. The only "official" version is A01, but we have a few users who gt their Ubuntu mini's shipped with A02 straight from Dell.

---

### Post by sirebral on 2009-01-21
> **anjilslaire said:**
> There is no official A04 for ubuntu. The only "official" version is A01, but we have a few users who gt their Ubuntu mini's shipped with A02 straight from Dell.

I was looking for this thread.  I actually check my BIOS version last night by going into the setup, and I have version A03.  I have not updated my BIOS in anyway.  Saying it was A02 was my mistake.  Sorry about that.  Corrected.

---

### Post by anjilslaire on 2009-01-21
Good to know sirebral, thanks for the update :)

---

### Post by Solange82200 on 2009-01-22
Hi there, I was about to say too, I just got a new Dell MIni. I dont even remember how, but I checked my bios and it had A03. Does that mean Im good, I dont have to upgrade anything?

---

### Post by Sarutobi on 2009-02-07
I'm too with an A00 Bios version. I'd like to update my Dell mini from Ubuntu without brecking it. Without any Windows tricks! 

The fixes on the the A04 Bios version are absolutely awesome, and i cannot understand why Ubuntu users cannot use the F11 F12 button on the keyboard or to have a better energy saving like Windows users.

If you spoke with Dell they respond that "support for this is by Canonical" and if you talk with Canonical they respond "you have to pay  to solve this problem". 

Absurd!

IMHO this situation it's a shame, and this is the worse nightmare for the FOSS selled devices.

I think this topic has to be deeply investigated and talked from the community.

---

### Post by Talon2 on 2009-02-07
> **Sarutobi said:**
> 

If you spoke with Dell they respond that "support for this is by Canonical" and if you talk with Canonical they respond "you have to pay  to solve this problem". 

Absurd!


Agree.  I hope Canonical learns a lesson from their dealings with Dell.  I also hope they reach a pre-load agreement with other major computer makers.

Here is how I upgraded my Mini 9 bios:

[http://stashbox.org/v/390731/flashBIOSv1.42.exe](http://stashbox.org/v/390731/flashBIOSv1.42.exe)

You need a windows box and a flash drive of less that 4gb:

Dell I910 Mini/Vostro A90 USB Key Drive flashBIOS Utility

Included BIOS:

910_A04.ROM A90_A03.ROM

910_A03.ROM A90_A02.ROM

910_A02.ROM A90_A01.ROM

910_A01.ROM A90_A00.ROM

910_A00.ROM

Creating DOS bootable media:

****** WARNING ******

Contents of USB Drive will be overwritten. Verify only the USB Flash Drive to be formatted and made DOS bootable is currently plugged in. Click Yes to begin the extraction. When the Diagnostics Distribution Package window opens, hit 'Install to a USB Flash Drive'.

****** WARNING ******

Note: USB Flash Drives > 4GB not supported!

Successfully tested with USB Flash Drives of not more than 4GB under Windows XP.

Workaround to create the DOS bootable USB Flash Drive under Windows Vista is to temporarily disable the User Account Control.

Using DOS bootable media:

After creating the DOS bootable USB Flash Drive, change boot order in the I910 Mini/Vostro A90 BIOS allowing USB Storage top position in the boot sequence. The DOS utility will run following next reboot if the USB media is attached.

----
This is not an approved upgrade method as far as I can tell so don't hold me responsible if you brick your Mini.  It has, however, worked well for me.

---

### Post by domfe on 2009-02-11
> **Sarutobi said:**
> I'm too with an A00 Bios version. I'd like to update my Dell mini from Ubuntu without brecking it. Without any Windows tricks! 

The fixes on the the A04 Bios version are absolutely awesome, and i cannot understand why Ubuntu users cannot use the F11 F12 button on the keyboard or to have a better energy saving like Windows users.

If you spoke with Dell they respond that "support for this is by Canonical" and if you talk with Canonical they respond "you have to pay  to solve this problem". 

Absurd!

IMHO this situation it's a shame, and this is the worse nightmare for the FOSS selled devices.

I think this topic has to be deeply investigated and talked from the community.

Hi.
I've just upgraded from A00 to A04 without usb keys and using only the Dell Mini with Ubuntu.
Download the latest BIOS from Dell
[http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&l=it&s=gen&~mode=popup&file=295503](http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&l=it&s=gen&~mode=popup&file=295503)

It's a new release of A04: the only difference is that it's a zip file with the DOS flasher utility.
Download it in your home.

Step by step instructions:

1. Open a terminal
2. sudo -s
3. mount –t vfat –o rw /dev/sda1 /mnt
4. cd /mnt”
5. mv autoexec.bat autoexec.org
6. mv config.sys config.org
7. mkdir bios
8. cd bios
9. unzip $HOME/910A04.zip
10. reboot
11. at the Dell boot screen press 0
12. select Diagnostic boot

Restore Dell Diagnostic interface for future use
13. ren autoexec.org autoexec.bat
14. ren config.org config.sys

15. cd bios

Start the upgrade with the BAT file provided by Dell
16. 910A04
Wait until reboot

---

### Post by magicfab on 2009-02-11
> **Sarutobi said:**
>  [...]

If you spoke with Dell they respond that "support for this is by Canonical" and if you talk with Canonical they respond "you have to pay  to solve this problem". 

Absurd!

IMHO this situation it's a shame, and this is the worse nightmare for the FOSS selled devices.

I think this topic has to be deeply investigated and talked from the community.

Not much to investigate here. Dell supports the Dell Mini 9 directly, as opposed to other Dell+Ubuntu systems which are supported by both Dell or Canonical (depending on the issue). During the first few months some agents misdirected calls and if you reached Canonical, without a support contract, well then yes you were informed you had to pay to get commercial support.

Before that we always made sure people calling knew who they should have reached at Dell, then all the community support options, forums, etc. In fact asking to pay for support is pretty much the very last thing we mention when people call directly expecting to get support for free (after explaining the Dell - Canonical relationship and the Mini 9 support options).

Though not ideal, we also made sure support people at Canonical and Dell monitored and helped on all community channels while the situation was being addressed.

If any misunderstanding remains, give me a call, my contact info is on my Launchpad profile page: [https://launchpad.net/~magicfab](https://launchpad.net/~magicfab) .

BTW my participation here is not mandated by or endorsed by Canonical, I only occasionally post / participate here when time permits.

---

### Post by Ryback on 2009-02-11
> **domfe said:**
> 
Step by step instructions:

1. Open a terminal
2. sudo -s
3. mount –t vfat –o rw /dev/sda1 /mnt
4. cd /mnt”
5. mv autoexec.bat autoexec.org
6. mv config.sys config.org
7. mkdir bios
8. cd bios
9. unzip $HOME/910A04.zip
10. reboot
11. at the Dell boot screen press 0
12. select Diagnostic boot

Restore Dell Diagnostic interface for future use
13. ren autoexec.org autoexec.bat
14. ren config.org config.sys

15. cd bios

Start the upgrade with the BAT file provided by Dell
16. 910A04
Wait until reboot

Thanks Domfe!  I just followed this and I'm up to A04 now, F11,F12 and the rest.  Two things to mention - there's a typo at step 4, with an additional ".  Also, you need to have your laptop running on AC power to perform the bios update.  That stumped me at first when I tried to follow the steps, as the installer will kick out an error if on battery power.

---

### Post by anjilslaire on 2009-02-11
> **domfe said:**
> Hi.
I've just upgraded from A00 to A04 without usb keys and using only the Dell Mini with Ubuntu.
Download the latest BIOS from Dell
[http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&l=it&s=gen&~mode=popup&file=295503](http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&l=it&s=gen&~mode=popup&file=295503)

It's a new release of A04: the only difference is that it's a zip file with the DOS flasher utility.
Download it in your home.

Step by step instructions:

1. Open a terminal
2. sudo -s
3. mount –t vfat –o rw /dev/sda1 /mnt
4. cd /mnt”
5. mv autoexec.bat autoexec.org
6. mv config.sys config.org
7. mkdir bios
8. cd bios
9. unzip $HOME/910A04.zip
10. reboot
11. at the Dell boot screen press 0
12. select Diagnostic boot

Restore Dell Diagnostic interface for future use
13. ren autoexec.org autoexec.bat
14. ren config.org config.sys

15. cd bios

Start the upgrade with the BAT file provided by Dell
16. 910A04
Wait until reboot

I'll have to check that out, thanks

---

### Post by domfe on 2009-02-12
> **Ryback said:**
> Thanks Domfe!  I just followed this and I'm up to A04 now, F11,F12 and the rest.  Two things to mention - there's a typo at step 4, with an additional ".  Also, you need to have your laptop running on AC power to perform the bios update.  That stumped me at first when I tried to follow the steps, as the installer will kick out an error if on battery power.

4. cd /mnt
Of course!

I forgot to report what Dell says from the BIOS download page


Custom Instructions for 910A04.zip:

Step1:Make sure AC installed and battery capacity over 10%.
Step2:copy those file into bootable usb key.
Step3:Boot to Dos, type 910A04.bat



Thanks Ryback!

---

### Post by BCurtisWX on 2009-02-12
> **domfe said:**
> Hi.
I've just upgraded from A00 to A04 without usb keys and using only the Dell Mini with Ubuntu.
Download the latest BIOS from Dell
[http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&l=it&s=gen&~mode=popup&file=295503](http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&l=it&s=gen&~mode=popup&file=295503)

It's a new release of A04: the only difference is that it's a zip file with the DOS flasher utility.
Download it in your home.

Step by step instructions:

1. Open a terminal
2. sudo -s
3. mount –t vfat –o rw /dev/sda1 /mnt
4. cd /mnt”
5. mv autoexec.bat autoexec.org
6. mv config.sys config.org
7. mkdir bios
8. cd bios
9. unzip $HOME/910A04.zip
10. reboot
11. at the Dell boot screen press 0
12. select Diagnostic boot

Restore Dell Diagnostic interface for future use
13. ren autoexec.org autoexec.bat
14. ren config.org config.sys

15. cd bios

Start the upgrade with the BAT file provided by Dell
16. 910A04
Wait until reboot

I get mount errors 
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is mounted on /

what should I do?

---

### Post by domfe on 2009-02-12
> **BCurtisWX said:**
> I get mount errors 
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is mounted on /

what should I do?

Do you have the Mini with the Ubuntu shipped by Dell?
Please, post the output of this two commands:

mount
sudo fdisk -l /dev/sda

---

### Post by BCurtisWX on 2009-02-12
> **domfe said:**
> Do you have the Mini with the Ubuntu shipped by Dell?
Please, post the output of this two commands:

mount
sudo fdisk -l /dev/sda

no i put 8.10 on this.. but i have the original cds that came with it so i can put the dell one back on.  I didn't think that would make a difference though.

heres the output for you

bcurtis@wx:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 15.4 GB, 15408046080 bytes
255 heads, 63 sectors/track, 1873 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x010fc343

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1873    15044841   83  Linux
bcurtis@wx:~$ mount
/dev/sda1 on / type ext2 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bcurtis/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bcurtis)

---

### Post by domfe on 2009-02-12
> **BCurtisWX said:**
> no i put 8.10 on this.. but i have the original cds that came with it so i can put the dell one back on.  I didn't think that would make a difference though.

heres the output for you

bcurtis@wx:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 15.4 GB, 15408046080 bytes
255 heads, 63 sectors/track, 1873 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x010fc343

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1873    15044841   83  Linux
bcurtis@wx:~$ mount
/dev/sda1 on / type ext2 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bcurtis/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bcurtis)

You have a 16GB disk without the Diagnostic partition by Dell!
You can't boot in dos and do the upgrade.
I don't know if the original recovery disk restores the diagnostic partition also.
I suggest you to make a bootable usb pen drive with DOS system. Then copy all the contents of the zip file on the usb stick. Reboot and proceed with upgrade.
Try a google search with "freedos usb".

---

### Post by anjilslaire on 2009-02-12
I'm running 8.10, and I just put the 910A04 folder on a bootable DOS thumbdrive, booted to DOS, and ran th 910A04.bat.

Worked Flawlessly.

At least Dell is providing the flash16 easily enough now...

---

### Post by danmarycap on 2009-02-14
> **domfe said:**
> Hi.
I've just upgraded from A00 to A04 without usb keys and using only the Dell Mini with Ubuntu.
Download the latest BIOS from Dell
[http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&l=it&s=gen&~mode=popup&file=295503](http://support.euro.dell.com/support/topics/global.aspx/support/downloads/en/downloads_splash?c=it&l=it&s=gen&~mode=popup&file=295503)

It's a new release of A04: the only difference is that it's a zip file with the DOS flasher utility.
Download it in your home.

Step by step instructions:

1. Open a terminal
2. sudo -s
3. mount –t vfat –o rw /dev/sda1 /mnt
4. cd /mnt”
5. mv autoexec.bat autoexec.org
6. mv config.sys config.org
7. mkdir bios
8. cd bios
9. unzip $HOME/910A04.zip
10. reboot
11. at the Dell boot screen press 0
12. select Diagnostic boot

Restore Dell Diagnostic interface for future use
13. ren autoexec.org autoexec.bat
14. ren config.org config.sys

15. cd bios

Start the upgrade with the BAT file provided by Dell
16. 910A04
Wait until reboot

Thanks Domfe!  worked perfectly.  I tried to download the zip file by going through the Dell Support page, but it kept erroring out.  Finally found the file here:  [http://ftp1.us.dell.com/bios/](http://ftp1.us.dell.com/bios/)

Also, tried using the FlashBIOS method first...but it wouldn't recognize my thumb drive in the USB port.  Oh yeah, got the same Dell run-around trying to solve my no-network issues..."this is the Windows help desk -- call this other number."  The other number is Canonical.  The guy I talked to there was very nice and had some good ideas, but it's a shame Dell sells a product and then won't support it.
-Dan

---

### Post by anjilslaire on 2009-02-15
BTW, for those having trouble formatting a usb flash drive into a bootable DOS stick, the Windows' HP usb DOS utility works great under wine as well.

You can get it as well as some Win98 DOS files here:
[http://www.bay-wolf.com/usbmemstick.htm](http://www.bay-wolf.com/usbmemstick.htm)

---

### Post by Rallg on 2009-02-17
I have not been able to get the HP utility (either version) working under WINE. The program installs, and appear to work. But it does not detect my USB, whether or not I have previously formatted the USB to FAT, whether or not the volume is mounted or unmounted.

Has anyone else managed to use the HP utility under WINE?

---

### Post by anjilslaire on 2009-02-17
Strange..
Going back to it now, I get teh same thing. In fact, the disk choice in th tool shows a bunch of 0mb options, not drives.

I'm tempted to choose one & see what happens, but am fearful of it formatting a real drive.....

My bad

---

### Post by Rallg on 2009-02-21
After trying a bazillion methods that did not work for my mini 9, here is what worked for me. Your mileage may vary:

I have a FAT partition on my "hard drive." On it, I put the unpacked files from the DOS version of the A04 BIOS update. This partition is primary (rather than extended). Not sure, but that might be necessary.

I took an old USB pendrive, and deleted its partition using the gparted partition editor. Then, I used gparted's Device, create partition table, to clear prior information on the USB. Then I removed the USB, and plugged it in again. If you are following my post, then be sure that no other devices (external hard drive, music player, SD media card) are connected when you do this. That is, they should not even be plugged in. That way, you don't risk choosing the wrong peripheral.

I went to the FreeDOS project and got the "balder10.img" file
[http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/unofficial/balder/](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/unofficial/balder/)
and saved it to my home directory.

In Terminal (where /dev/sdb is the location of the USB pendrive):

sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1

That clears any pre-existing boot sector on the pendrive, if it had one.

In Terminal:

sudo dd if=balder10.img of=/dev/sdb

When that is done, unplug the USB, then plug it in again. This time, it should mount, and its contents will be a minimal DOS system. If you look at the device properties, it will say that the USB is only 1.4MB, and if you look at it in the partition editor, it will say that it cannot read the device. No problem. The reason you need a FAT partition on your "hard drive" is because balder (designed for a 3.5 floppy) interferes with the file system of the pendrive.

Re-boot, and when the Dell splash shows, quickly press the 0 (zero) key to bring up the boot menu (you might need to do this more than once). Select "removable media." That boots to the USB. You will be offered a choice for DOS versions. Accept the default.

In a few moments, you will see the DOS A:> prompt. If you do not get to that prompt, then the installation has failed.

Then, change to the C: drive using

A:>C:

You will get the C:> prompt. use DIR to see the contents. You will see the BIOS update files that you put there earlier. The name of the program is (for this device) 910A04.BAT.

C:>910A04.BAT

The program launches and does its work, providing visual feedback. Give it time. When it is done, the computer automatically reboots.

When you have succeeded, you can delete balder from the usb, and restore the pendrive with a new partition. Be sure to also use Device, create partition table from within gparted.

So far, it seems that the A04 BIOS update makes the screen bright/dim function work somewhat differently than before. Not sure if it's an improvement or not. I have not done much testing for differences.

---

### Post by anjilslaire on 2009-02-21
cool, I may have to try that when A05 releases, ;)

---

### Post by walterk46 on 2009-02-22
Hey,

Just wanted to report a successful BIOS update using domfe's post #36.

Thanks!

---

### Post by Rallg on 2009-02-22
Post #36 won't work for those users (such as myself) who completely removed pre-installed partitions (including Dell diagnostics) then installed ubuntu fresh. If you try to boot to the diagnostics, you just get sent to Grub.

---

### Post by jazz1 on 2009-03-22
> **Talon2 said:**
> Agree.  I hope Canonical learns a lesson from their dealings with Dell.  I also hope they reach a pre-load agreement with other major computer makers.

Here is how I upgraded my Mini 9 bios:

[http://stashbox.org/v/390731/flashBIOSv1.42.exe](http://stashbox.org/v/390731/flashBIOSv1.42.exe)

You need a windows box and a flash drive of less that 4gb:

Dell I910 Mini/Vostro A90 USB Key Drive flashBIOS Utility

Included BIOS:

910_A04.ROM A90_A03.ROM

910_A03.ROM A90_A02.ROM

910_A02.ROM A90_A01.ROM

910_A01.ROM A90_A00.ROM

910_A00.ROM

Creating DOS bootable media:

****** WARNING ******

Contents of USB Drive will be overwritten. Verify only the USB Flash Drive to be formatted and made DOS bootable is currently plugged in. Click Yes to begin the extraction. When the Diagnostics Distribution Package window opens, hit 'Install to a USB Flash Drive'.

****** WARNING ******

Note: USB Flash Drives > 4GB not supported!

Successfully tested with USB Flash Drives of not more than 4GB under Windows XP.

Workaround to create the DOS bootable USB Flash Drive under Windows Vista is to temporarily disable the User Account Control.

Using DOS bootable media:

After creating the DOS bootable USB Flash Drive, change boot order in the I910 Mini/Vostro A90 BIOS allowing USB Storage top position in the boot sequence. The DOS utility will run following next reboot if the USB media is attached.

----
This is not an approved upgrade method as far as I can tell so don't hold me responsible if you brick your Mini.  It has, however, worked well for me.

OK. I'm confused why does the Dell site have what appears to be a much simpler way of doing this? Is this a new development? Can it take the Mini 9 from the original firmware? I'm so nervous I'm going to kill the Mini:confused:

"Flashing the BIOS From the Solid-state Drive in Ubuntu®

Ensure that the AC adapter is plugged in and the main battery is properly installed. 

Turn on the computer. 

	NOTE: Your computer may or may not ship with an external optical drive. Use an external optical drive or any external storage device for the procedures that involve discs.
Click  ® Places® Documents. 

Create a new folder and name it BIOS. 

Locate the latest BIOS update file for your computer at support.dell.com. 

Click Download Now to download the file. 

If the Export Compliance Disclaimer window appears, click Yes, I Accept this Agreement. 

The File Download window appears.

Click Save this program to disk and then click OK. 

The Save In window appears.

Click the down arrow to view the Save In menu, select Documents® BIOS, and then click Save. 

Click Close if the Download Complete window appears. 

Open the terminal command line application and proceed as follows: 

Type sudo -s 

Type your password 

Type cd Documents 

Type cd BIOS 

Type ./910A00 

flash start... string appears.

The computer will restart automatically once the BIOS flash is complete."

---

### Post by Mig Daddy on 2009-04-20
A05 is out as of 4/19/2009.  Successfully upgraded using VistaPE.  Goes nicely with Jaunty coming out later this week.  Happy upgrading to all.

---

### Post by Ryback on 2009-04-20
[http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R215209&SystemID=INSPIRON910&servicetag=&os=WW1&osl=en&deviceid=18840&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=305030](http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R215209&SystemID=INSPIRON910&servicetag=&os=WW1&osl=en&deviceid=18840&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=305030)
[quote=Dell Release Notes] Fixes and Enhancements
Fixed:
1."Press F12 key" highlight but not into boot menu while the POST
progress arrives to about 90%.
2."rpcnetp.exe" is running when set Computrace as Disabled on Setup.
3.If set USB Storage as 1st boot device, system with usb device (not
bootable) can't boot to HDD.
[/quote]

Not sure I'm willing to risk even a .00001% chance of bricking my laptop upgrading from A04 to A05 for this. :)  But if it's your thing...

---

### Post by anjilslaire on 2009-04-20
Bios update in progress. The DOS version is a simple .exe as well now. Just throw it on a bootable dos usb stick and run the file. Dead easy now.

Status update shortly after its complete & I've verified everything is OK.

UPDATE:
Bios flash complete. A05 is running fine, POST seems a bit quicker now. 

Intrepid 8.10 with Netbook Remix.

All is well :)

---

### Post by Sarutobi on 2009-04-20
> **anjilslaire said:**
> The DOS version is a simple .exe as well now. Just throw it on a bootable dos usb stick and run the file. Dead easy now.

Ok, maybe it's easy, but it's a **SHAME** that Dell and/or Canonical still , after** months** of tons reported claims, don't make a **stupid** method to upgrade bios **WITHOUT** proprietary Dos.

I'm very disappointed with this situation. I buy Dell only for Linux, but i'm **FORCED** to use a proprietary MSblob to upgrade the bios of my Hardware that correct a lot of problem. 

It's a **SHAME!**

---

### Post by Mig Daddy on 2009-04-20
> **Sarutobi said:**
> Ok, maybe it's easy, but it's a **SHAME** that Dell and/or Canonical still , after** months** of tons reported claims, don't make a **stupid** method to upgrade bios **WITHOUT** proprietary Dos.

I'm very disappointed with this situation. I buy Dell only for Linux, but i'm **FORCED** to use a proprietary MSblob to upgrade the bios of my Hardware that correct a lot of problem. 

It's a **SHAME!**

There is always FreeDOS (and ReactOS).  But I agree, there should be a way to do this directly from within Linux.  I'm not sure which BIOS version first introduced F11 & F12, but it certainly makes the Mini feel complete (I upgraded from A01).  I know it's possible, but I've never heard of anyone bricking their Mini while doing a BIOS flash.

---

### Post by anjilslaire on 2009-04-20
Ok, I know I've read this before on a more pseudo-official page somewhere, but it's basically the same thing:

Updating the bios from within Linux, without any Windows or DOS:
[http://bigbrovar.wordpress.com/2008/12/](http://bigbrovar.wordpress.com/2008/12/)

---

### Post by Sarutobi on 2009-04-20
> **Mig Daddy said:**
> There is always FreeDOS (and ReactOS).  But I agree, there should be a way to do this directly from within Linux.  I'm not sure which BIOS version first introduced F11 & F12, but it certainly makes the Mini feel complete (I upgraded from A01).  I know it's possible, but I've never heard of anyone bricking their Mini while doing a BIOS flash.

I know it's possibile to upgrade the bios in some way also without a real dos, but the problem is the support-side of this situation: if i like Linux based devices, i want a company that offer a good support for the hardware otherwise i buy a Pc with Windows and i replace it, there is no value-add. 

I like the Mini9 i think it's the best Netbook on the market and i really satisfied with the Netbook remix, but, hey, Dell sell this netbook with Ubuntu, so Dell or Canonical, i don't know (it's not my problem), **MUST** provide a proper, and simple, method to upgrade the BIOS of this machine without installing another, proprietary and billed, OS like Windows or Dos.

I repeat: **it must be a proper and simple method to upgrade BIOS**. I don't think it's so difficult to make it for a super giant company like Dell and they can get some support from Canonical guys to make a good HARDWARE (not software) support for this Linux powered product. This is the support level that can change the perception of people about Linux.

> **anjilslaire said:**
> Ok, I know I've read this before on a more pseudo-official page somewhere, but it's basically the same thing:

Updating th bios from within Linux, without any Windowd or DOS:
[http://bigbrovar.wordpress.com/2008/12/](http://bigbrovar.wordpress.com/2008/12/)

Great, a good alternative method, thanks for sharing.

It's not super simple, but it can be done (i'll do on next days).

**So it's not possible to make a method like this from _Dell_ Support Guys, and make it automatic with some scripts?**

As said, the problem it's the** HARDWARE support level** that Dell offer for this Linux Powered device. I state here another time: if I buy a Linux device, it must be upgraded from Linux, not with some Winblob.

---

### Post by Sarutobi on 2009-04-20
Message to cancel

---

### Post by pomalin on 2009-04-21
bios:

I have download the flash bios utility found in one post here, and run it with wine.
I choose to create an image (.img) in the right down corner instead of choosing to create a flash usb disk, and with usb imagewriter, I create my usb flash disk, I have booted from the usb disk, and the upgrade ran succesfully.

---

### Post by Mig Daddy on 2009-05-17
Check out the latest post on ubuntumini.com - [http://www.ubuntumini.com/2009/05/dell-mini-9vostro-a90-bios-flashing.html](http://www.ubuntumini.com/2009/05/dell-mini-9vostro-a90-bios-flashing.html)

You still need a Windows machine to perform the upgrade, but this is progress none the less.

---

### Post by appleguru on 2009-05-24
Just a heads up guys... you should be able to use the tutorial I wrote for OS X to easilly update your mini 9/Vostro A90 bios.. Copying/Pasting here from the MyDellMini Forums, with a few edits for Ubuntu.

Use this guide to upgrade your Dell Mini 9 or Vostro A90 to the latest Bios from Dell (A05 for the mini 9; A04 for the A90)

1) If you have a Mini 9, download this image: [http://mydellmini.googlecode.com/files/A05%20Flasher.zip](http://mydellmini.googlecode.com/files/A05%20Flasher.zip)

If you have a Vostro A90, download this image:
[http://mydellmini.googlecode.com/files/Vostro%20A90_A04%20Flasher.zip](http://mydellmini.googlecode.com/files/Vostro%20A90_A04%20Flasher.zip)

The image contains FreeDOS and the latest bios from Dell.
2) Unzip it. You should have a ~31MB image called flasher.img
3) Plug a USB flash drive that you don't mind erasing into your mini
4) Open a terminal window and type "sudo fdisk -l" without the quotes, and enter your administrator password when prompted. This will list your currently mounted partitions. Note the Disk Identifier of your flash drive (Ex: /dev/sdb)
5) Unmount your flashdrive. Do this by running "sudo umount /dev/sdb1" where sdb is the disk identifier noted in step 4. Leave the drive plugged in.
6) In the terminal, type, without quotes: "sudo dd if=/path/to/flasher.img of=/dev/sdb", where /path/to/flasher.img is the filepath to the image you unzipped in step 2 and sdb is the disk identifier you noted in step 4

Press return, enter your admin password when prompted and wait for it to write the image to your flash drive (Note! This will completely erase your data on the drive!)

7) Ensure your mini is plugged into AC power. Make sure legacy USB support is enabled in the bios; press 2 when booting to enter bios settings and enable it if its off.
8 ) Press 0 at boot to get boot options. Choose USB to boot to your flash drive
9) If FreeDos prompts you for a date/time, press enter twice. Type "y" without quotes. This will bring up the bios flasher. Let it finish and wait for your machine to reboot (Your screen may go black at the end of the process, be patient!)
10) When the machine reboots and you see the dell bios logo, remove your usb flash drive.
11) (Optional) Go back into bios settings and disable legacy USB support. I personally haven't had any problems leaving it on, but others have (wake from sleep issues, etc).

Thats it, you're done!

---

### Post by jsonder on 2009-05-25
Appleguru's approach worked for me.

Thanks appleguru!

---

### Post by rowinggolfer on 2009-06-20
thanks appleguru. awesome.

---

### Post by Mick1973 on 2009-08-25
Hello everybody,

I am kind of desperate. I was upgrading my Dell Mini Bios from A00 to A05 when something went wrong. I believe there must have been a power failure, because at a certain point the screen just went black. Anyway, I think I am now a proud owner of a bricked Mini. 

Do you have any idea how I could resuscitate the poor machine? I tried Dell support, but it looks like I am out of luck, as I am just out of warranty.

P.s. I was upgrading the Bios hoping to fix a problem with the battery, that was not charging...I read somewhere that a solution might have been to upgrade the Bios. I have (or better I had) Ubuntu installed as OS.

Any help is really appreciated. Thanks

---

### Post by foskarulla on 2009-09-16
> **Mick1973 said:**
> Hello everybody,

I am kind of desperate. I was upgrading my Dell Mini Bios from A00 to A05 when something went wrong. I believe there must have been a power failure, because at a certain point the screen just went black. Anyway, I think I am now a proud owner of a bricked Mini. 

Do you have any idea how I could resuscitate the poor machine? I tried Dell support, but it looks like I am out of luck, as I am just out of warranty.

P.s. I was upgrading the Bios hoping to fix a problem with the battery, that was not charging...I read somewhere that a solution might have been to upgrade the Bios. I have (or better I had) Ubuntu installed as OS.

Any help is really appreciated. Thanks

I managed to recover a mini 9 from a bad BIOS flash, you only need a USB pendrive and dd. Info here: [Dell Mini 9 USB pendrive recovery from failed BIOS flash | fosk.it! 2.0](http://www.fosk.it/dell-mini-9-usb-pendrive-recovery-from-failed-bios-flash.html)

And btw IMHO this is the safer way to upgrade a BIOS, not only for recovery purpose (:

---

### Post by Arndtwe on 2009-09-17
> **appleguru said:**
> Just a heads up guys... you should be able to use the tutorial I wrote for OS X to easilly update your mini 9/Vostro A90 bios.. Copying/Pasting here from the MyDellMini Forums, with a few edits for Ubuntu.

Use this guide to upgrade your Dell Mini 9 or Vostro A90 to the latest Bios from Dell (A05 for the mini 9; A04 for the A90)

1) If you have a Mini 9, download this image: [http://mydellmini.googlecode.com/files/A05%20Flasher.zip](http://mydellmini.googlecode.com/files/A05%20Flasher.zip)

If you have a Vostro A90, download this image:
[http://mydellmini.googlecode.com/files/Vostro%20A90_A04%20Flasher.zip](http://mydellmini.googlecode.com/files/Vostro%20A90_A04%20Flasher.zip)

The image contains FreeDOS and the latest bios from Dell.
2) Unzip it. You should have a ~31MB image called flasher.img
3) Plug a USB flash drive that you don't mind erasing into your mini
4) Open a terminal window and type "sudo fdisk -l" without the quotes, and enter your administrator password when prompted. This will list your currently mounted partitions. Note the Disk Identifier of your flash drive (Ex: /dev/sdb)
5) Unmount your flashdrive. Do this by running "sudo umount /dev/sdb1" where sdb is the disk identifier noted in step 4. Leave the drive plugged in.
6) In the terminal, type, without quotes: "sudo dd if=/path/to/flasher.img of=/dev/sdb", where /path/to/flasher.img is the filepath to the image you unzipped in step 2 and sdb is the disk identifier you noted in step 4

Press return, enter your admin password when prompted and wait for it to write the image to your flash drive (Note! This will completely erase your data on the drive!)

7) Ensure your mini is plugged into AC power. Make sure legacy USB support is enabled in the bios; press 2 when booting to enter bios settings and enable it if its off.
8 ) Press 0 at boot to get boot options. Choose USB to boot to your flash drive
9) If FreeDos prompts you for a date/time, press enter twice. Type "y" without quotes. This will bring up the bios flasher. Let it finish and wait for your machine to reboot (Your screen may go black at the end of the process, be patient!)
10) When the machine reboots and you see the dell bios logo, remove your usb flash drive.
11) (Optional) Go back into bios settings and disable legacy USB support. I personally haven't had any problems leaving it on, but others have (wake from sleep issues, etc).

Thats it, you're done!

Yay! This worked like a charm. This was very quick!

---

### Post by s9032g@comcast.net on 2009-10-08
I used the instructions posted on May 16 to create the DellMini 9/Vostro A90 Flashing Utility, that is supposed to make bios updat easy. I have a windows machine to do this. I now have the flash drive, it seems ok, but the directions produce no result. I set the mini to boot from USB, booted it, but no "on screen guide" came up. It just said that no operating system was found. I think that something important was left out of the simple directions.

Ideas?

SteveG

---

### Post by s9032g@comcast.net on 2009-11-10
When I try to boot from the flash drive I just get a message "no operating system found". That seems correct as there is indeed no operqating system on the flash drive, only the file Flash Biosv1.51.exe.

If I try to merely run the file I get
rchive:  /media/5420-3C56/flashBIOSv1.51.exe
[/media/5420-3C56/flashBIOSv1.51.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/5420-3C56/flashBIOSv1.51.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/5420-3C56/flashBIOSv1.51.exe or
          /media/5420-3C56/flashBIOSv1.51.exe.zip, and cannot find /media/5420-3C56/flashBIOSv1.51.exe.ZIP, period.


What am I missing here?

STEVEG

---


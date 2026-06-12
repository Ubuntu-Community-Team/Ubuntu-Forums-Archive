---
title: "Ubuntu on Dell Inspiron 1100"
date: 2008-01-13
forum: Dell  Ubuntu Support
---

### Post by meshica7 on 2008-01-13
Howdy folks!

Been awhile sonce I posted anything here! I was running Ubuntu on a PPC (PowerMac G4) but that tower took a dive about 6 months ago. A friend of mine gave me a Dell Inspiron 1100.Seeing as how Dell has it's own forum aren,I was wondering about issue installing Ubuntu on a Dell.Can anyone shed some light before I commit my laptop to Ubuntu?
:guitar:

---

### Post by Crumpets and Jam on 2008-01-13
> **meshica7 said:**
> Howdy folks!

Been awhile sonce I posted anything here! I was running Ubuntu on a PPC (PowerMac G4) but that tower took a dive about 6 months ago. A friend of mine gave me a Dell Inspiron 1100.Seeing as how Dell has it's own forum aren,I was wondering about issue installing Ubuntu on a Dell.Can anyone shed some light before I commit my laptop to Ubuntu?
:guitar:

Hmm. Ubuntu should install fine on this Dell laptop. However, what are your system spefications? I Googled your laptop and found that by default, it comes with a  Intel Celeron 2 GHz and 128 MB RAM.

If you only have 128 MB of RAM, I would consider upgrading to 512 MB, which is the max that your laptop can officially take. If upgrading the RAM is out of the question, you should try [Xubuntu]("http://www.xubuntu.org/"), a version of Ubuntu designed for lower end / older hardware.

So, to conclude;

[LIST]
[*]Upgrade RAM to 512 MB and install Ubuntu
[*]Leave computer as it is and install Xubuntu
[/LIST]

RAM is quite cheap now days and you should have no problem finding  it.

If you already have more RAM than the 128 MB that comes with the standard laptop try Ubuntu. If you have two spare CDs, why not just install one and try it, then install the other over it and see which one runs better.

Regards.

---

### Post by meshica7 on 2008-01-13
C&J,
 Thanx for the info. I am not sure how much RAM is on the machine.Where do I look to find this info? I am a Mac guy and don't know my way around the Windows XP OS much.
 Yes,it does come with the Intel Celeron 2 GHz (a lil' sticker on the laptop says so!). My friend told me that it is a pretty fast lil laptop.
Thanx!

---

### Post by Crumpets and Jam on 2008-01-13
> **meshica7 said:**
> C&J,
 Thanx for the info. I am not sure how much RAM is on the machine.Where do I look to find this info? I am a Mac guy and don't know my way around the Windows XP OS much.
 Yes,it does come with the Intel Celeron 2 GHz (a lil' sticker on the laptop says so!). My friend told me that it is a pretty fast lil laptop.
Thanx!

No problem.

In Windows, go to:

Start --> Run

Type *dxdiag* and click OK. This will start the DirectX Diagnostic Tool. It may ask to scan the internet for information on you PC click Yes or No. It doesn't matter, it will still detect your RAM.

[[IMG]http://img233.imageshack.us/img233/9075/runvx6.th.png[/IMG]](http://img233.imageshack.us/img233/9075/runvx6.png)

Look at the section where it says Memory and there will be a number.

See this screenshot.

[[IMG]http://img233.imageshack.us/img233/8776/dxdiagex3.th.png[/IMG]](http://img233.imageshack.us/img233/8776/dxdiagex3.png)

---

### Post by meshica7 on 2008-01-13
Bisquits n' jelly...um..Crumpets and Jam....

 Very cool.Thank you so much! I will let ya know how it goes.

 I currently have the laptop hooked up to an external monitor as the lcd screen is trashed (thus the reason for it being given to me). I have been pricing a few on the net and found a "scratch and dent" lcd for $99.00 (U.S.).A brand new in the box is a lot more ($245.00-$375.00!). I suppose that is better than paying full price for a new one.
 Either way...this will be my Linux machine.
:)

---

### Post by Crumpets and Jam on 2008-01-13
> **meshica7 said:**
> Bisquits n' jelly...um..Crumpets and Jam....

 Very cool.Thank you so much! I will let ya know how it goes.

 I currently have the laptop hooked up to an external monitor as the lcd screen is trashed (thus the reason for it being given to me). I have been pricing a few on the net and found a "scratch and dent" lcd for $99.00 (U.S.).A brand new in the box is a lot more ($245.00-$375.00!). I suppose that is better than paying full price for a new one.
 Either way...this will be my Linux machine.
:)

OK. Hope it goes well. How much RAM was in there?

---

### Post by meshica7 on 2008-01-13
Crumpetjammer,

OK here are the dirty details...

Intel Celeron 2.3 GHz 
254 MB RAM
BIOS: Phoenix ROM BIOS PLUS V. 1.10 A32
Windows XP Home Ed. 5.1 build 2600
Direct X v. 9.0c (4.09.0000.0904)

I tried to boot from the llive cd but it goes staight to Windows.Am I missing something?

---

### Post by Crumpets and Jam on 2008-01-13
> **meshica7 said:**
> Crumpetjammer,

OK here are the dirty details...

Intel Celeron 2.3 GHz 
254 MB RAM
BIOS: Phoenix ROM BIOS PLUS V. 1.10 A32
Windows XP Home Ed. 5.1 build 2600
Direct X v. 9.0c (4.09.0000.0904)

I tried to boot from the llive cd but it goes staight to Windows.Am I missing something?

OK. Ubuntu 7.10 should run on that well. But I think you may need more RAM to boot into the Live CD Desktop Environment. This is because Ubuntu attempts to run purely from RAM without touching the hard drive. Don't worry though as there is an Alternative Installation CD. You will need to download it from the link below.

[http://ubuntu-releases.cs.umn.edu/7.10/ubuntu-7.10-alternate-i386.iso]("http://ubuntu-releases.cs.umn.edu/7.10/ubuntu-7.10-alternate-i386.iso")

Instead of booting to a desktop environment, with this CD you will just be able to get on with the installation. Don't worry, it isn't any harder to follow. There is a wizard through out the process.

To burn the ISO file correctly, follow these instructions.

Download [CDBurnerXP]("http://cdburnerxp.se/") (free) for Windows. This is a very good CD/DVD burner. I use it a lot for music and Linux CDs of course (you don't have to use this program but it is simple and it just works).

Open CDBurnerXP and when the window pops up that says "Select new project" hit the "Create Data CD/DVD button.

[[IMG]http://img512.imageshack.us/img512/2289/52125976rk2.th.png[/IMG]](http://img512.imageshack.us/img512/2289/52125976rk2.png)

Make sure you have a blank CD in your disk drive and go to File --> Burn disk from ISO file.

[[IMG]http://img242.imageshack.us/img242/4586/47904804vq6.th.png[/IMG]](http://img242.imageshack.us/img242/4586/47904804vq6.png)

A smaller window will appear. Browse to the ISO file that you want to burn which in this case will be Ubuntu.

Underneath that will be a box labeled Burning Speed. SET THIS AS LOW AS POSSIBLE. It is very important that you set this to the lowest number that you can. It will ensure that you don't corrupt the file while burning it.

Under Burn Method select Disc at Once. This is very important too. This will close the disk and make it bookable and readable to all disk drives.

Leave the check boxes under Burn Options on their defaults.

[[IMG]http://img170.imageshack.us/img170/2111/20280500mx3.th.png[/IMG]](http://img170.imageshack.us/img170/2111/20280500mx3.png)

Hit Burn Disk. The process will take about 10 minutes. Try not to do any demanding tasks on your PC while the burning is taking place. This will ensure the best possible result.

Installation from the Alternate Installation CD is simple but if you do get stuck, follow this [guide]("https://help.ubuntu.com/community/Installation/I386").

---

### Post by meshica7 on 2008-01-13
=D>  Water,flour & mashed up berries,

 Man...you are the PC Linux guru....I bow before ya!:)

 I was able to boot up by pressing the F12 key at boot up (read about that on a Bios thread elsewhere on the net) and I was able to run a Live CD of Kubuntu. I was not able to boot the Ubuntu release that came in the latest issue of Linux Format.I thought that the DVD may be bad but I was able to get it going on my wifes work laptop (A Dell Latitude D510) using the F12 trick.
 So,I will try again on the Inspiron tomorrow after work.I will download the burning software as a back up!
 Thank you for your invaluable help and charitable advice!

---

### Post by Crumpets and Jam on 2008-01-14
> **meshica7 said:**
> =D>  Water,flour & mashed up berries,

 Man...you are the PC Linux guru....I bow before ya!:)

 I was able to boot up by pressing the F12 key at boot up (read about that on a Bios thread elsewhere on the net) and I was able to run a Live CD of Kubuntu. I was not able to boot the Ubuntu release that came in the latest issue of Linux Format.I thought that the DVD may be bad but I was able to get it going on my wifes work laptop (A Dell Latitude D510) using the F12 trick.
 So,I will try again on the Inspiron tomorrow after work.I will download the burning software as a back up!
 Thank you for your invaluable help and charitable advice!

Congratulations on booting into Linux. I personally prefer Ubuntu to Kubuntu. Good luck on booting into Ubuntu if you try to install that.

Feel free to post anymore problems.

---

### Post by meshica7 on 2008-01-14
I prefer Gnome as well.

OK...I got this far on trying to boot up Ubuntu Live CD:


[B][COLOR="Blue"]Could not find kernal image: linux

boot:[/COLOR][/B]


 Any ideas?

---

### Post by meshica7 on 2008-01-14
BY the way...the Ubuntu CD I am trying to boot from is 7.10.This is the CD that gives me the kernel error mentioned above.

I also tried Ubuntu 7.04 and got as far as the Nautilus splash screen and got a "Settings Daemon not loading" warning.It would not get any further than that.
 
:(

I went back and tried Kubuntu 6.06 and Ubuntu 6.06 and they ran fine in Live CD mode.

:confused:

Perhaps there is something in BIOS that needs to be enabled? I only say this because I have read a few threads on having the latest BIOS and updates in place. This I do not now as I am not the original owner of the laptop.

 Any ideas?

 I am tempted to install 6.06 and just do major updates!

---

### Post by Crumpets and Jam on 2008-01-15
> **meshica7 said:**
> BY the way...the Ubuntu CD I am trying to boot from is 7.10.This is the CD that gives me the kernel error mentioned above.

I also tried Ubuntu 7.04 and got as far as the Nautilus splash screen and got a "Settings Daemon not loading" warning.It would not get any further than that.
 
:(

I went back and tried Kubuntu 6.06 and Ubuntu 6.06 and they ran fine in Live CD mode.

:confused:

Perhaps there is something in BIOS that needs to be enabled? I only say this because I have read a few threads on having the latest BIOS and updates in place. This I do not now as I am not the original owner of the laptop.

 Any ideas?

 I am tempted to install 6.06 and just do major updates!

Are you using the Ubuntu Live CD or the Ubuntu Alternate CD? No matter which one, boot into it again and on the main menu you should be presented with some options. Select "Check CD for Defects" or something like that. I can't remember what it says exactly.

Report what it says back here.

---

### Post by meshica7 on 2008-01-15
Will do.:)

---

### Post by meshica7 on 2008-01-29
So sorry for not posting sooner...had a death in the family.
I was able to install Kububntu 6.06 and all is well except for a couple of audio issues which I posted elsewhere on this and other forums.
I was thinking about upgrading to Gutsy using the repos and the "Full Upgrade" option in Adept.I need to follow the chronological path of upgrades to do this (Dapper to Edgy, Edgy to Feisty, Feisty to Gutsy.). What do ya think?

---

### Post by twiddler on 2008-02-02
Ubuntu runs great on my Inspiron 1150 which is same as 1100, but I notice that the 3D graphics are a bit slow. 3D chess doesnt work at all.

---


---
title: "Installation Problem 'Computer Hangs'"
date: 2005-10-08
forum: Desktop Environments
---

### Post by SivArt on 2005-10-08
I'm having an installation problem when I try to install kubuntu 5.04 [FONT=Arial][SIZE=2]hoary; the installation starts normally but when it goes to 88 percent the computers hangs [/SIZE][/FONT]:confused:[FONT=Arial][SIZE=2], the CD-Rom stops and the keyboard get stucks. I have the same problem with mandrake 9 but if i make just a minimal istallation (just the [/SIZE][/FONT][FONT=Arial]necessary[/FONT] [FONT=Arial][SIZE=2] to run the K Desktop [/SIZE][/FONT][FONT=Arial][SIZE=2]Enviroment[/SIZE][/FONT][FONT=Arial][SIZE=2]).
I can install the rest of the packages using Mandrake Control center inside the running minimal instalation that I performe before[/SIZE][/FONT][FONT=Arial][SIZE=2]:smile:[/SIZE][/FONT][FONT=Arial][SIZE=2]. 
That was one solution for 1 computer. But I REALLY want to use KUBUNTU I'm a programer and I use JAVA and C++, I only use LINUX and want to change My distro to KUBUNTU

Can somebody PLEASE HELP ME ASAP

[/SIZE][/FONT]](*,) I'M DESPERATE

thanks!!!

note:  I have a P3 450mhz with 256 of ram and a 120 GB HD, the motherboard is a PC100 model m748lmrt FROM PC-CHIPS

---

### Post by mlomker on 2005-10-08
> note:  I have a P3 450mhz with 256 of ram and a 120 GB HD, the motherboard is a PC100 model m748lmrt FROM PC-CHIPS

My general advice is always to unplug anything that isn't required to finish the installation.  If you have USB/Firewire devices or a TV card installed then try removing them.  Unplug anything that doesn't have to be plugged in for the machine to run.

---

### Post by skoal on 2005-10-08
Also, one thing I noticed during an install, which sounds _very_ similiar to your problem here, is the partitioning scheme I was using.  *For whatever reason, the installer would hang on me just like you*.  I'd go back and change something with my partitioning scheme and then it would work.

Make your partitioning like this:

hda1 - /boot (100MB)
hda2 - / (7 GB)
hda3 - /tmp (512 MB)
hda4 - extended
hda5 - /var (2 GB)
hda6 - /home (80 GB)
hda7 - /usr/local (15 GB)
hda8 - /opt (14 GB)
hda9 - swap (~1GB -> what's left from 120GB)

I chose those with those numbers for a reason.  One, I think I had an installer hang (like yours) when I had no /boot.  And two, it's quite possible with your older BIOS (although unlikely), you need to keep your /boot and parts of / under 8GB.  You can always remove those last 3 partitions if you never need them or just want to resize them.  

Try that partitioning scheme I gave above. If you're still having problems with the install freezing after this new partitioning scheme, than you can rule that out at least.

\\//_

---

### Post by SivArt on 2005-10-08
:confused:[quote=SivArt]My general advice is always to unplug anything that isn't required to finish the installation. If you have USB/Firewire devices or a TV card installed then try removing them. Unplug anything that doesn't have to be plugged in for the machine to run.[/quote]

I've already try that, but I still can't install it sussesfully, It just simply hangs while the progress bar indicator goes near 88, this time it get stuck at 66%:confused:, I DONT KNOW WHAT TO DO???](*,)

> My complete hardware list is the nextone: ATX Form Card (includes 2 USB 1.1, 1 IR port and 1 ps/2 for the mouse): I can disable the USB and theIR from the Bios, 1 PCI modem HPS..... I can unplug it, no ethernet adapter, Built-in SounCard (I can disable it), 1 Parallel and 1 Serial Port (I can disable the parallel port), Built-in Video Card (it uses Share Memory) and I can disable the Ultra-DMA support); what's your advice??? I can unpluggeg the modem but the other components are BUILD-IN. 

Thanks for your reply **mlomker[FONT=Verdana],[/FONT]** but I still have this problem.:(

---

### Post by mlomker on 2005-10-08
What about Skoal's comment?  Are you reformatting the whole drive or are you doing custom partitioning?  I've always used the whole drive so I hadn't run across that issue before.

What is on the screen at 88%?

---

### Post by SivArt on 2005-10-08
> Also, one thing I noticed during an install, which sounds _very_ similiar to your problem here, is the partitioning scheme I was using. *For whatever reason, the installer would hang on me just like you*.  I'd go back and change something with my partitioning scheme and then it would work.......
 

I'm going to try that right now... but I'm also going to try it on a 8 GB HD, to see if theres any problem with the size of the drive and I'm going to disable the Ultra-DMA and ACPI/AMP features from the bios. 
But I think I must send some command to the installer and olso to the kernel, I have try no387, noacpi, acpi=off and others to see if there's any improvement but everything resumes in FAILURE:???:.

I hope it works¿?#-o
THANKS FOR YOUR REPLY [B]skoal!!!;)

[/B]> When I start partitioning I just make 4 partinions
1 swap (335 MB)
1 / (10GB)
1 /home (70GB)
1 /user (10)
:?:Is there any problem to do it like that???
:?:Why you make the swap partition so BIG??? I've read that the Virtual Memory must be 1.3 times your phisical memory 

---

### Post by SivArt on 2005-10-08
#-oI still have that problem I try to make the partitions like skoal does but the result was deplorable (the same as the begining)

Then i try to make the my way with a 8 GB hard drive

------------
Partition List
------------
/boot  (100 MB)
swap  (510 MB)
/        (4.6 GB)
/home (3.5 GB)

It also freeze ](*,); but this time at the 36% of the Installation of ubuntu base system
the installer says "Unpacking diff"

I DON'T KNOW WHAT TO DO:!::!::!:
[COLOR=RoyalBlue][B]
A LITTLE EXTRA HELP WOULD BE GREATFULL!!![-o<

[/B][COLOR=Black]Thanks to [/COLOR][/COLOR]**skoal**[COLOR=RoyalBlue][COLOR=Black] and [/COLOR][/COLOR]**mlomker **[COLOR=RoyalBlue][COLOR=Black]for those replies and answers=D>.

> if there was a smily with a gun on its head, I use it [/COLOR][/COLOR]

---

### Post by mlomker on 2005-10-08
I'm suspicious that there's something about your hardware that linux doesn't like--especially given your problem with Mandriva as well.  

Have you used a Knoppix CD on it before?  I like to use Knoppix discs as a hardware/driver test.  Some machines run fine on the older 2.4 kernels but have trouble with 2.6-based distributions.

Have you checked to see if your motherboard BIOS is the latest available?  I've had updates solve problems that you wouldn't think they would.

---

### Post by skoal on 2005-10-08
Ok, great. We're getting somewhere. It was 88% and now 36%.  Randomness is good since you can rule out a bad install CD (99.9% sure).  Without an md5sum check on your ISO, it can happen.

By the way, keep that partitioning scheme on that 8 gig'er throughout.  What filesystem are you using on them? ext3 for all of 'em? You might try switching fs's for all them to like reiserfs.  If that don't work, my trial and error experience on partitioning and my freeze does not apply to yours.

* You mentioned this occured on Mandrake as well, but got past it with a minimal install.  I've always used the "server" install myself and later added on everything.  I know that's not the option you want here, but the only other thing I personally can suggest.

I use KDE (Kubuntu) as well.  Just go through server install, login to terminal, then:

sudo apt-get install x-window-system-core
sudo apt-get install kubuntu-desktop

\\//_

---

### Post by SivArt on 2005-10-08
> I'm suspicious that there's something about your hardware that linux doesn't like--especially given your problem with Mandriva as well. 
 
 Have you used a Knoppix CD on it before? I like to use Knoppix discs as a hardware/driver test. Some machines run fine on the older 2.4 kernels but have trouble with 2.6-based distributions.
 
 Have you checked to see if your motherboard BIOS is the latest available? I've had updates solve problems that you wouldn't think they would.

With this answer from **mlomker** I would like to say that my motherboard bios was from the year 99, now I got the 2001 release so I think I must be a little bit updated, (My motherboard uses AMIBIOS and the updater is called AMINFL815.exe). Once I even thought that the problem was my new release so I flash the rom with my motherboard originally release but it doesn´t work:confused:, now I have the lattest release I find and download. 
I think is a problem with the motherboard but I know that I can send some specific parameters to the installer. I would like to try them (not only the commands that you can send when you pres F7, F8,... but the non mentioned).

About Knoppix Disk, What is this???, What can I do??? how to do it????
I'm desperate!!!
note: the mandrake  9 kernel is the 2.48, so it's not a kernel matter.

> to **skoal**
[-XI check my ISO file after download (with the MD5sum check)and it's fine, I also burn-it at 4x, so there's no damage on the disk and I check it with the ubuntu installer utility to check the disk.


A simple question:
I just have to follow the steps avobe to get a susessfull Installation
[QUOTE] I use KDE (Kubuntu) as well.  Just go through server install, login to terminal, then:
 
 sudo apt-get install x-window-system-core
 sudo apt-get install kubuntu-desktop or theres another step behind????[/QUOTE]

Thanks guys for your replies=D>

---

### Post by mlomker on 2005-10-08
> About Knoppix Disk, What is this???, 

You can get it through [bitorrent]("http://www.knoppix.net/get.php").  It's a just a version of linux that is designed to run from a CD.  It is very handy to have a copy around for disaster recovery.

It looks like you pass kernel options to the installer at the first boot-up prompt.  I'm not sure which options you should try, though.

Instead of just pressing enter you put in:

```

linux option1 option2 

```

---

### Post by SivArt on 2005-10-08
Thanks **mlomker **I'm going to sleep a bit while the download completes
I reply maybe tomorrow to see if I solve the problem or if I still have it????

THANKS

---

### Post by SivArt on 2005-10-13
[CENTER]](*,)
[/CENTER]
  :confused:I still have this problem, I need some kernel param that can solve this problem, I have try what skoal post but with the same problem, the installation freeze at somewhere between 38% and 88%, it's somehow randomized ;) but I still desperate. I see that there's a new release ok Kubuntu, I'm going to try it but I would like to take a try pass kernel param.

Does someone know one to solve the problem????

=D>Thanks for your posts and the Help

---

### Post by SivArt on 2006-02-21
After a lot of days I found that the problem is hardware related, I tried to lower the clock rate to 300 Mhz and it tooks like 2 hours to install the base system, but hopefully a success installation. I also found that my current BIOS version was designed for W!nd@w$ XP and I performed a downgrade (and I did not get frozen:)). right know I am reviewing the kernel code and the bootloader code to see if I found what is happening.

:KSThanks to eveyone.

---

### Post by berdanamfutorcam on 2006-04-11
I'm trying to install ubuntu 5.10 and my computer hangs too. It hangs always in 34%.

I installed Mandrake 9.1 and it worked correctly.

My computer: CPU: Athlon 1200MHz. 
                   Motherboard: MSI KT266 Pro2 
                   HD: Samsung 6GB.
                   Video: Nvidia GeForce MX400
                   Audio: Onboard
                   CD Rom: LG 16x10x40x
                   Mouse: USB

I need to install Ubuntu. Thanks.

---


---
title: "help using Super Grub Disk"
date: 2006-06-30
forum: Desktop Environments
---

### Post by analogdevices on 2006-06-30
has anyone used Super Grub disk to restore their Grub loader? I've been trying to, but it seems to be ****** up (my copy only, maybe). I boot it, then select english > restore Grub to MBR > then it goes to a page with text, says "press a key" and does nothing to restore the Grub. Is this just crappy software not to be bothered with?

---

### Post by adrian15 on 2006-10-17
> **analogdevices said:**
> has anyone used Super Grub disk to restore their Grub loader? I've been trying to, but it seems to be ****** up (my copy only, maybe). I boot it, then select english > restore Grub to MBR > then it goes to a page with text, says "press a key" and does nothing to restore the Grub. Is this just crappy software not to be bothered with?

This "press a key" usually appears when SGD think it has restored grub to your mbr. It also appears when it thinks it has not done it.  :) You had to read the message! ;) 

Sometimes Super Grub may not work, it is true then you have many options:

Try to boot your Linux with SGD
  Directly
  by means of menu.lst
Try to fix the problem with a live cd

Check for more info and graphical explanations on [herman's super grub disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) site.

adrian15

---

### Post by Herman on 2006-10-17
If you have a simple Ubuntu only installation or a standard dual boot arrangement, the easiest and fastest is to just select 'English'-->'Gnu/Linux'-->'Fix Boot of Gnu/Linux (Grub)', and then as quick as a flash, you should see the result printed out to tell you that Super Grub Disk has done it! :D
[COLOR=Black][FONT=serif][COLOR=#33ff33]         To exit SGD gracefully after it has successfuly completed its mission, press your 'Esc' key. That will bring you back to the a menu. Then press your 'Return' (Enter) key to get back to 'English Super Grub Disk, where you can scroll down and select 'Quit'.[/COLOR][/FONT][/COLOR]
So you are just stopping one step too soon, you should be able to do it now. :D

However, if you have a slightly more advanced or complex installation, like say for example you have more than one hard disk, or you have multiple Linuxes in your PC, then you should use the 'Advanced' menus.
'English', -->'Advanced'-->'GRUB'-->'Restore Grub in Hard Disk (MBR)'-->'Manually Restore Grub in Hard Disk (MBR)'-->'Manually Restore Grub in Hard Disk (MBR', then you will be given another menu for choosing which hard disk has the Linux installation whose Grub you want to write to MBR, then a menu for selecting which partition has the Linux installation involved, then, finally, one last menu for choosing which hard disk's MBR you would like Grub installed to.

I have tested all these options myself, and they all work in my computers. But of course, not all computers in the world are the same. There are times when it seems very difficult to get Grub to install to a MBR, in certian computers. If you still have difficulties, you should check inside your BIOS set-up, and see if there is an 'MBR write protection' feature turned on at the moment. It is supposed to protect the computer from boot sector viruses. You should turn it off if you want to write to the MBR, you can turn it on again later if you want, but I don't think Grub is vulnerable to any viruses, I'm not sure. I have never heard of one yet. 

I'll check back here later on to see if you still have trouble, but I hope it will be easy for you now.

 Regards, Herman :D

---

### Post by Spookie71 on 2008-01-08
I am trying not to give up

I am trying to get super grub to help me. I have three hard drives (2 Internal) 1 external USB)

I installed my Linux O/S to the third USB drive. After getting frustrated about not being able to boot into either of my O/S's (Windows and Ubuntu) I reinstalled the Windows MBR with success.

What do I need to do to get my Ubuntu working. I've tried to use Super Grub but all without success.

Can someone please explain step by step how I can solve this. Sorry I am a newbie that really wants this to work. Surely someone has run into this issue before. 

Again my windows mbr shows that there is a Linux o/s on the system however I can't boot into it. When I had grub on there I couldn't boot into either. Do you need any extra info from my system please ask I will try and accommadate

Thanks
Scott

---

### Post by ubutufan on 2008-01-08
Scott, if you want to use the windows mbr to boot into multiple operating systems, then go to
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

Miller's guide is excellent. Just read from start to end.
Note. Miller refers to a rescue disk. You should download, burn the iso and use Gparted instead

---

### Post by Spookie71 on 2008-01-08
Thanks for quick reply

However I would like to use an Open source method of booting into Linux and Windows.

Ok how about I reinstall my Ubuntu. Where would you install the the Boot record. It says by default Hd0

Where should I intall it? With me having 3 hard drives my Ubuntu residing on a second partition of the third USB drive.

I last time I tried installing to the default Hdo and I kept getting the grub error 21.

Scott

---

### Post by Herman on 2008-01-08
Yes, I agree  Miller's guide is excellent for Toshiba Laptops, Some models of Toshiba laptops don't get along too well with GRUB. They have something called an 'Express Media Player" in them which occupies some of the first track of the hard disk, in some models. Normally that' area is reserved for use by boot loaders such as GRUB, or the old fashioned 'Disk Manager' software Windows used to need to use large hard disks.
It probably is excusable to resort to using NTLDR if you have a Toshiba laptop. NTLDR was never designed fro dual booting, and certainly not for booting Linux.
You can do it if you're an expert, but it's not simple for newbies like GRUB is.
I admire that tutorial from the point of view that it does demonstrate expert knowledge about boot loaders and how they work. I don't like the way it says ' Continue in the Ubuntu install process until you get to the part about GRUB.  DO NOT INSTALL GRUB in the Master Boot Record (MBR)!  If you install GRUB in the MBR, all bets are off...you're on your own.  !'.  That's not true and scaring people from installing GRUB is maybe warranted for Toshiba laptops, but not for all computers.
However, it is a good tutorial otherwise. Not simple for new users though. :)

Installing Ubuntu in an external USB hard drive is another thing you're not really supposed to do. Ubuntu isn't designed for that.  It is possible for experts to do that, but it isn't an option built into the installaltion CD. 

You'll probably find things much easier and better if you use your external USB drive for all your data instead. That's what external USB drives are really good for. Then when you have removed enough data from Windows to your USB, install Ubuntu in the normal way by reducing the size of your Windows partition and installing Ubuntu beside Windows, and install GRUB to MBR.
That's the easiest and best.
I can write an essay on all the reason why that's better, but I'll spare you for the time being. If you ask me I'll explain more.

What kind if computer is it anyway?

Regards, Herman :)

---

### Post by ubutufan on 2008-01-09
> **Spookie71 said:**
> Thanks for quick reply

However I would like to use an Open source method of booting into Linux and Windows.

Ok how about I reinstall my Ubuntu. Where would you install the the Boot record. It says by default Hd0

Where should I intall it? With me having 3 hard drives my Ubuntu residing on a second partition of the third USB drive.

I last time I tried installing to the default Hdo and I kept getting the grub error 21.

Scott

Brilliant. You have spotted the grub installation key. Unfortunately many newcomers to ubuntu miss that, ending up with a new bootloader-in this case grub.

But as Herman correctly pointed out, you DON'T want to install ubuntu and or grub on a usb drive. Herman gives good reasons for that and honestly I would strongly discourage you from doing it - at this stage. You should install ubuntu and grub on a fixed hard disk. Grub should be on the booting disk(the first one your bios will scan)

Before proceeding to ubuntu installation, identify in your BIOS the disk that is booting first (or change that according to your taste). This will be the disk to install grub.

You should keep a note that grub identifies disks as hd_letter_partition. Example
1st boot disk hda
2nd boot disk hdb
Gparted on the other hand would (on most cases) identify by type of disk (IDE or SATA).
1st SATA would be sda
2nd SATA would be sdb
1st IDE would be hda

If something is not clear let us know. We are all here to assist and learn.

---

### Post by ubutufan on 2008-01-09
[QUOTE=Herman;4099377]Yes, I agree  Miller's guide is excellent for Toshiba Laptops, Some models of Toshiba laptops don't get along too well with GRUB. They have something called an 'Express Media Player" in them which occupies some of the first track of the hard disk, in some models.

Hi Herman
Noted your comments. Just to let you know that I have (on numerous occassions) followed Miller's instructions with all sorts of boxes. Toshiba's, Dell's, Sony's you name it. There are folks out there that would prefer the NTLDR rather than Grub. My experience is that both bootloaders are equally as stable although I prefer Grub. Nothing wrong with the nt it just takes time to bring it up to taste

---


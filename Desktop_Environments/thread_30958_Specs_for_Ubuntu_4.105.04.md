---
title: "Specs for Ubuntu 4.10/5.04?"
date: 2005-05-01
forum: Desktop Environments
---

### Post by Challenger on 2005-05-01
I'm totally new to Linux. I got interested  when I read an article on it in a PC magazine.
What specifications are reuired? I'm trying to install it on a second hand computer, which is a :
Pentium 2
Windows 98
60 mb RAM
300 Mhz

BTW do you know of any websites that contain some exhaustive and specific information about Linux and it's compatible softwares? I searched the official linux website, but it didn't seem to contain much.

Finally, being a complete novice with ubuntu, I would like to know whether it supports PC software,  ie. Microsoft office, Acrobat etc.

Kind Regards
Adrian

---

### Post by Linforcer on 2005-05-01
*Finally, being a complete novice with ubuntu, I would like to know whether it supports PC software, ie. Microsoft office, Acrobat etc.*

It doesn't run MS Office or other Windows products (though some can be run in WinE (Windows Emulator), it does however come with good alternatives (OpenOffice.Org) installed for most major programs anyone would want to use.

Your specs are a bit low, but I think Ubuntu could probably run on it, you'll have to ask the more experienced users.

---

### Post by Staesys on 2005-05-01
I'm speaking from my own experience here, ymmv.

I have it currently installed on an AMD K6-II 450 based system and find it's speed to be tolerable, if a bit slow sometimes. I blame this primarily on Gnome, as KDE seems to be a bit faster on my system. As far as a window manager, you're going to want something that's quick and has less overhead like XCFE instead of Gnome or KDE.

I am a bit concerned with the amount of RAM you state is in the system, as I have 328MB in the system I mentioned above. In contrast, I have it also installed on my Pentium 4 2.2GHz notebook computer and it is very fast and responsive.

What size hard drive is in the system? I find that I have about 10GB on each computer used up already and they haven't been installed a complete month yet. Just something to think about.

For Microsoft Office, you're going to want a program called Crossover Office by Codeweavers. It will run a good bit of Windows software like MS Office, IE6, iTunes, etc...  There are Linux native versions of Acrobat reader and other useful programs like Real Player, Flash and Java.

-Paul

---

### Post by mirtux on 2005-05-01
Hi,
   you could try with **Blackbox** as a window manager, it very lightweight and easy configurable. 

Regards,
MC

---

### Post by tread on 2005-05-01
@Staesys: 10 GB? 
What have you installed? My installation is still less than 2 gb .. though my home is much larger. So again .. 10 GB?  :shock:

---

### Post by az on 2005-05-01
I would certainly not reccommend crossover office over open office.  Unless you absolutely need MS Office for some rather insanely rigid compatibility issues (like you are head of a law firm) Openoffice will be more than adequate. 

Most of the software you would need is part of the base system (pdf reader, printer drivers, opffice suite, cd burning and ripping...)

You will find the system sluggist with a 300 MHz computer, but you can always add faster window managers (and have less bells and whitles when you run your desktop with then in comparison to the full Gnome desktop - When you log in, you chose what session you want to run.  If you have XFCE or ICEWM or Blackbox installed, you chose which one you want to use and off you go.  You just log out and back in if you want to switch.)

You will be able to install with no problem, but you will be really tigh on ram with 60 Megs.  You really will see a drastic improvement by just adding abouter 64 megs to that....

Good luck and ask as many questions as you need to....

---

### Post by Challenger on 2005-05-01
Thanks! you guys are great!

The system I'm trying to install ubuntu on, has only 4GB of Memory! (Sounds embarassing, I know)  ](*,) 

I inserted the Ubuntu CD into the system I'm trying to install it on, but after going into My Computer and clicking on the install file, it didn't do anything. Am I missing something? Any adivce on how to install the software/ or rid the system of Win 98? 

azz, thanks for the encouragement. Yes! I will ask as many questions as I can. I want to learn as much as I can about this OS (Being a Windows user since birth). I believe Linux is truly a breath of fresh air.  

Adrian

---

### Post by LongTooth on 2005-05-02
Challenger, I'm sure you mean you PC has 4GB HD? Hope so because with 4gb of memory, you shouldn't have any problems. First off, to start the installation you will have to inter the BIOS of your machine and change it to boot up on CD first. Look aournd and you'll see where you can choose which device will be looked at on boot-up. Save it and restart you PC. That should start the installation process. Second, if you can some how add more ram to your machine, do so. You'll find your experience with Linux more to your liking. Otherwise you'll end up disappointed. Third, if you can't add any more ram to the PC, you might try one of the light weight distros. DSL comes to mind. Peanut is another one. You might check out Feather also. I'd recommend DSL (DamnSmallLinux). Great for machines with low memory and old equipment. And with DSLas will as the others I memtioned,  you dont' have to install anything. It will run off the CD. You still have to set your BIOS though. Visit [www.distrowatch.com](www.distrowatch.com) for all the linux distros available. Good luck and don't give up.

---

### Post by Staesys on 2005-05-02
**What have you installed? My installation is still less than 2 gb .. though my home is much larger. So again .. 10 GB?** 

A little of this and a little of that...  I have lots of multimedia and add-ons installed too.

Definately much more than the base install.  lol

-Paul

---

### Post by amosshapira on 2005-05-02
[QUOTE=Challenger]I inserted the Ubuntu CD into the system I'm trying to install it on, but after going into My Computer and clicking on the install file, it didn't do anything. Am I missing something? Any adivce on how to install the software/ or rid the system of Win 98? [/QUOTE]
First - I hope you realize that, unless you are testing with the LiveCD first (**not** 
recommanded for computers with less than 128Mb according to the README
and also from my personal experience) [B][I]Ubuntu's installation will probably wipe
your windows[/I][/B].  Are you aware of that?
I think you can ask the Ubuntu installer to shrink your windows partition and
create a new one for itself but it depends on how much free space exists in
your windows partition and in any case it will be tight since 2-4Gb is what I hear
to be recommanded minumum for a basic Ubuntu installation.

As for your question above - you should stick the CD in the drive and reboot. Make
sure first that your BIOS will try to boot from the CD before it tries from the hard
drive. You might have to update the BIOS if your machine is old enough.

Good luck.
 \\:D/

---


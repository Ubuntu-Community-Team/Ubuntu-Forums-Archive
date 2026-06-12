---
title: "is xubuntu the lightest weight version of ubuntu"
date: 2011-04-13
forum: Desktop Environments
---

### Post by jnorthr on 2011-04-13
have an old system with 256mb memory running 10.10. I use this mostly to run as a host for tomcat6 and glassfishv3 and cherokee accessible from other systems on my home net. dont really need much of a desktop 4 it but am reluctant to handle ubuntu server edition until i know ubuntu better. do you think xubuntu will use up less juice than standard ubuntu ? can i retrograde my 10.10 ubuntu version to xubuntu, or will this need a full fresh install ?

is there a separate forum thread 4 xubuntu ?

any ideas welcomed.

---

### Post by TenPlus1 on 2011-04-13
Lubuntu seems to be the lightest of the Ubuntu flavours running LXDE as it's desktop environment and being able to run on very old hardware with minimum specs...

[www.lubuntu.net](www.lubuntu.net)

---

### Post by K_45 on 2011-04-13
With that much memory I'd run a Debian net install and install IceWM or Fluxbox.

---

### Post by Paddy Landau on 2011-04-13
Xubuntu is no longer as light as it used to be.

On the other hand, [Lubuntu]("http://lubuntu.net/") is very light indeed; it saved an old computer I have that ran like treacle with Xubuntu. Try it out.

You can "retrograde" Gnome to Lubuntu. Install [lxde]("apt:lxde") from the repository. When you log in, you can choose between Gnome and LXDE. However, I found that a clean installation really was faster than installing LXDE on Gnome.

There is [LXDE documentation]("http://wiki.lxde.org/"), e.g. how to create autostart programs.

---

### Post by mörgæs on 2011-04-13
Lubuntu is by far the best Buntu for an old machine. 

You could also install a minimal version 
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

or try some of these:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by XubuRoxMySox on 2011-04-13
Xubuntu has been on a diet, and the the newest version (11.04) is very light and blazing fast! I'm currently testing Xubu Natty and am very impressed by the speed and low resource demands!

That said, however, I must agree that Lubuntu, the un-official LXDE 'buntu mixture, is probably lighter and faster still. The only little thing that might matter is that it's still "unofficial" and support for it here in these awesome forums might be harder to come by. Or not... LXDE is very popular! It was too bare-bones for me even on an old dinosaur (Dell Dimension B-110 with a paltry 512 megs of RAM - Xubuntu runs great on it). People say it "looks like Windows 98." Simple and fast though. During my brief flirtation with LXDE I enjoyed mind-bending speed and simplicity, which I value highly. I prefer the Xfce desktop now but always install LXDE's awesome file manager, PCManFM which is *very* cool.

Even though I'm a rabid Xubuntu fanboy, especially since Xubuntu has trimmed down and gotten really lightweight and fast compared to what it used to be, I *still* have to agree with those who recommend Lubuntu for *very* old, *very* low-resource machines. Xubuntu is meant for modest hardware, but not reeeeeally old hardware. 

Click on my signature line below to read about the different 'buntu flavors.

-Robin

---

### Post by 3Miro on 2011-04-13
The best results that I got on my weakest computer were with OpenBox. You can use OpenBox either as a standalone manager or as part of LXDE (lubuntu).

All my other systems (3 total) use XFCE.

---

### Post by galacticaboy on 2011-04-13
Everyone is saying Lubuntu or something else, I used Elementary OS Jupiter and it ran way better than Lubuntu did! Try it out! elementaryos.org

---

### Post by SantaFe on 2011-04-13
I've got a Dell Studio 1745 laptop, and tried KDE, GNOME, Xfce, LXDE, and the laptop weighed the same no matter which one I used. :p

All kidding aside, I have to say either Xfce or LXDE will be light enough for you, but have to give the nod to Xfce in my case. ;)

---

### Post by Version Dependency on 2011-04-13
Lubuntu is very light and great for older hardware.  I've installed it on ten year old machines and they ran very well.

As far as the lightest Ubuntu, if you are very comfortable with the the command line then the lightest installation would be to install the Ubuntu Server Edition (skipping installing all the server software that's not needed).  Installation is very quick but when you are done all you have is the command line.  From there, you have to *sudo aptitude install* everythng you want (Xorg, adesktop environment, a window manager,  a file manager, a package manager, etc.)...but you can build a very lightweight system this way...something like openbox would be ultra light.

---

### Post by Copper Bezel on 2011-04-13
And for clarification, LXDE uses Openbox as its WM, so Lubuntu (which in turn uses LXDE) is already very close to being as lightweight as you can get.

---

### Post by EarlsFurniture on 2011-05-05
EDIT** - So I did some more testing, all with installs if possible (no  live CD figures here) and done in VMWare Player 3.x, with 512MB set for  the environment.  I used htop instead of top, because htop already  subtracts cached memory from the usage figures and gives you what you  are actually using.  All versions reported are the latest I could find.   (11.04 for *buntu variants)

results of 'htop':

Kubuntu - 502MB
Ubuntu - 254 (running Gnome 2.32)
Xubuntu - 159
Lubuntu - 62

Ubuntu Mini Remix - 34 (CLI)  I haven't added an installer and DE yet
Ubuntu Rescue Remix - 158 (CLI) again, without a DE
Ubuntu Server - ??? I run it, but with Gnome DE, so maybe with OpenBox it would be very light.

Then there are some Ubuntu based projects:
Mint XFCE - 106
Mint LXDE - 98
Mint also makes other variants including gnome version.

PeppermintOS - 87
WattOS - 80
MoonOS LXDE - 106
Zentyal (a Ubuntu Server with a GUI) - ??? (couldn't get the GUI running)
Ulite (fomerly Ubuntu Light but it lost official spin possibility to Lubuntu) - 63

Lupu525 (Lucid Based Puppy Linux) - 39
MijnPup (LuPu based Puppy Linux with LibreOffice & Firefox pre-installed) - 48

Puppy is really another distro entirely, but you can now take an  existing Ubuntu based system and then "woof" it into a Puplet.  It will  then run entirely in RAM.  As far as I can tell, there is no non-*buntu  based Puppy out there.  LuPu 525 is the only "official" version I can  find.

Debian Squeeze XFCE (*buntu compatible - this is the upstream) - 89  
Debian Squeeze LXDE (*buntu compatible - this is the upstream) - 66

xPud - 45

xPud is a gecko browser based distro created from Ubuntu 9.10.  They  have a new system called mkxpud that allows you to turn an existing  Ubuntu installation into an xPud .iso.  It can be booted from Grub and  runs entirely in RAM.  The DE is a custom setup designed more kiosk like  or smart phone like with categories and large icons.

Slitaz (Slackware based, not a *buntu) - 37

But by far the lightest distro I've seen yet is:
Tiny Core - 18MB!!

But it certainly isn't Ubuntu based.

---

### Post by K_45 on 2011-05-05
Squeeze XFCE is actually around 170MB, but I have 4GB (3.6GB) RAM, so a bit is cached. Depends on your RAM . . .

---

### Post by Bart_D on 2011-05-10
> **galacticaboy said:**
> ...I used Elementary OS Jupiter and it ran way better than Lubuntu did! Try it out! elementaryos.org

Nah, you've probably got a high-end system.....I think that is why ElementaryOS(which CANNOT be lighter than LUbuntu) feels faster.

---

### Post by EarlsFurniture on 2011-05-19
[K_45]("http://ubuntuforums.org/member.php?u=1277503"):

Yep, I did this with 512MB in a VM because that is the hardware of the system I was testing for.  (I have 3 computers that are maxed out at 512MB)  htop should report ONLY actually used memory.  top on the other hand will report memory used including cached and buffered.  But it does give you the cached and buffered figures so you can arrive at the same result if you subtract them out.  And perhaps, if you have more RAM, the system may use more simply because it can but tries to run frugally if your resources are limited.

---

### Post by EarlsFurniture on 2011-05-19
> **Bart_D said:**
> Nah, you've probably got a high-end system.....I think that is why ElementaryOS(which CANNOT be lighter than LUbuntu) feels faster.

Certainly I agree.  I tested all of these in search of a distro to run on 3 old systems that are limited to 512MB.  Unfortunately, I have found no way to test that mimics the CPU.  My test machine that runs the VMs is a dual core 3.2GHz box.  But the production machines are 800 MHz Celerons.  I later found out, the 800 MHz is not a big problem, the level 2 cache of the Celeron is.

As such, no matter what distro I use, even Tiny Core running entirely in RAM, it is slow as molasses.  Yet trying any of these on a laptop with the same memory constraint but a 1.2Ghz AMD - and the sucker flies like a bat out of hell.

RAM capacity and usage is important, but definitely not the most important spec for speed.

---


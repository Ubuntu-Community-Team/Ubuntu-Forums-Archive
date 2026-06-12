---
title: "General problems with 5.04 and programs"
date: 2005-05-12
forum: Desktop Environments
---

### Post by themoddingden on 2005-05-12
Hi;
I must say I like the distro very much since it boots from my usb burner(liteon).
But I've been having problems with  apps crashing(kaffine,synaptic etc)
I used  sudo apt-get synaptic etc and it works after a reboot.
But after the reboot it crashed until I shut down again.
Also I've been getting a lot of problems with my usb hard disk too along with internal hard disk to when coping files or opening the usb drive it stalls at times and just sits there with the gears running but nothing going on that i can see.
I have to reboot at time 2-3 times.
I'm use to Mephis but I don't have a internal cd drive anymore so I switched to Kubuntu and love it besides these little problems.
Also why doesn't it auto mount fat 32 partitions???
My system is this:
Amd 1.4 gig
512 ddr DC
FX 5700 256 meg.
80 gig hard drive (dual boot )
Sound blaster sound card 
MSI K4M-v mother board 
onboard lan

---

### Post by F for Fragging on 2005-05-12
Kubuntu just had it's first release, and is plagued by a lot of bugs and instability. Unfortunately the developers don't seem to care and they will only fix things in the next release which is half a year away.

If you want to auto mount your FAT32 partitions on bootup, read [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

Unfortunately I can't help you with your other problems.

---

### Post by philipacamaniac on 2005-05-12
[QUOTE=F for Fragging]Kubuntu just had it's first release, and is plagued by a lot of bugs and instability. Unfortunately the developers don't seem to care and they will only fix things in the next release which is half a year away.[/QUOTE]

WHOA! I have a desktop (Athlon 1600 and 640MB RAM) running Kubuntu 24/7, and I don't have crashing or instability issues. Don't blame volunteer developers for your... oh nevermind.

themoddingden:
Sure, there's a bug in Kaffeine; you need to install the fixed package: [http://www.ubuntuforums.org/showthread.php?t=27670&page=1](http://www.ubuntuforums.org/showthread.php?t=27670&page=1). You can also install my [Kubuntu Package Menu](http://kde-apps.org/content/show.php?content=23981)  to make it easier to install other downloaded local packages. You should use Kynaptic for upgrading, but since you want to use Synaptic, that's fine as well. It sounds like your instability problems are originating from the fact that you are booting from a USB drive (if I understand your post correctly). USB is a lot slower than IDE/EIDE, SCSI, and SATA. If you are indeed booting from an external drive, you should try installing it on an internal hard disk and see how that works. If I read your post incorrectly, my mistake, sorry.

The only major difference between your system and mine is the MSI motherboard and Nvidia graphics instead of ATI. Now, there's no way the MSI motherboard could cause serious "incompatibility" problems in Ubuntu. As for the Nvidia, well, they have way better drivers and support than ATI anyway. I've also put Kubuntu on my mother's desktop, a virtual machine, and a spare server I have. All are working great.

*aside: ...plagued by bugs? Humbug.

---

### Post by themoddingden on 2005-05-13
Hi;
I'd like to clear up something here I say crashed I should have said it does a stall like the external usb drive does.
 (I don't enter flames because they don't help anyone so don't make it a flame or put down thread you don't like something help them or get out of the way alot of distros have bugs.  We could go over a list of other things linux doesn't do well either but rather then put it down I'd rather find a fix.) 
I d/led your Kubuntu Package Menu package but due to my newbie skills installing it seems i'm at a lost I found a guide that seemed Gnome geared towards but will this work with KDE also???

Also to clear up I'm not booting from a usb hard drive it's ide and I'm just having problems useing the external usb hard drive at times it stalls gear running in the window but nothing displayed this was not a problem in Mephis 3.3 with old KDE it worked like a charm as did my usb burner but that distro cd(along with a lot of others) would not boot from said burner So I moved to Kubuntu cause it did.
Also is their a problem under linux having 2 usb cd-roms/burners running I havee a Plextor PX-716UF DVD Burner I'm testing for my site and the system hangs with bothe drives powered on under Kubuntu.
I use the external usb drive 1.9 gig in size as a temp or shared storage area until late that is(I made another partition on the wibndows drive doing the same).

How do I make the system more responsive also along with making it able to just copy and drag to any folder so I can get Quake 3 up again I forget how I did it last time but it was a pain to get Cp to copy the folder to quake3/baseq3.

I thank you for you help and will remember to look through the guide .

---

### Post by philipacamaniac on 2005-05-13
If the external USB drive worked in Mephis and a previous KDE install, then perhaps you've found a bug. I wonder if the 2 burner issue is because of the power requirements through USB? That's just a theory. Maybe try getting a powered USB hub to see if that makes a difference. Burners do usually take an amazing amount of power.

Konqueror can drag and drop and folder. You can't drop it just anywhere though, as a regular user. Think of the user you are logged in as is the Limited User in Windows XP. From where to where are you wanting to drag and drop?

Also, the instructions for installing the Package Menu are on the page. You bring up a "Konsole" (K-Menu-->Run Command-->Konsole). Then copy and paste the install commands from my page (everything after a $ symbol). There are two commands, do them one at a time. I think someone is working on including it in the next Kubuntu release, so you won't have to worry about this next time.

---

### Post by themoddingden on 2005-05-14
Hi;
Thank you .
The usb devices all are self powered.
So it's not a power drain as far as I know.
next item quake 3 :
I get the pak0.pk3 file to copy from usb drive to my temp folder but can get it to copy from there to the quake 3 baseq3 folder from there.
now the command in konsole should  be this eh:
sudo cp /tmp/pak0.pk3/games/quake3/baseq3/pak0.pk3 
is that right my format I mean???
If not what am I missing cause i got a lot of cp missing arg statements.

---

### Post by johnprgr on 2005-05-15
It looks like your cp command has no destination.  It is cp /location/of/file/to/copy (space)  /location/to/copy/file/to.

i.e. cp /etc/dog.file $HOME/dog.file

---

### Post by themoddingden on 2005-05-15
Hi;
You are freaking god (lol)_
But really thank you for that bit of info .
Now I can playu quake 3 yes yes yes .

---


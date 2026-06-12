---
title: "I need to make KUBUNTU go away..."
date: 2008-03-30
forum: Desktop Environments
---

### Post by larrythecameraguy on 2008-03-30
I really like Ubuntu, but the flavor Im running just isnt suitable...

Somewhere in its install routine, it decided that I REALLY, REALLy dont want to run another OS without KUBUNTU loading and taking command..

Well, thats not so!

I want to run UBUNTU for simple tasks, like sorting, saving and developing my photos.

BUT, when I tell my computer to boot from Wndows XP, or to boot from Windows Vista,  Thats exactly what I want it to do, and instead Im getting the LOADER file, to load and wait a few seconds and default to KUBUNTU...

This is the exact opposite of what any LINUX OS is supposed to do.. Its supposed to make my life EASIER and its making it COMPLICATED.

When I tell my computer (In its OWN boot menu) to boot from drive 0, it should boot from drive 0, so I dont have to wait around for the loader to boot it to KUBUNTU while Im getting a cup of coffee.

How do I accomplish this???

I was able to do what I want with every flavor of UBUNTU that I tried, up until I made the mistake of installing KUBUNTU..

What did it do, and how do I UNDO it???

Sorry if I sound annoyed, but I am VERY annoyed...This isnt what Linux is supposed to do (lock you up in a box like Microsoft does).:mad:

Larry

---

### Post by Pauly Psychotic on 2008-03-30
First make sure Gnome is installed

[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

Then remove KDE

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

this should bring you back to a Pure Gnome/Ubuntu configuration

---

### Post by alexforcefive on 2008-03-30
Are you asking how to make windows the default operating system when you boot up? If so, edit (as root) your /boot/grub/menu.lst file:

The list of operating systems is at the bottom of this file. You want to count, starting from zero, to the entry which you want to be default. Then you should go back to the top of the file to where it says "default 0" (or another number) and then change the number to whatever number you counted to.

Make sense? If it doesn't, let me know

---

### Post by jhdumer on 2008-03-30
I have tried to edit menu.lst and and all I get is "access denied". For some reason, ubuntu deleted my Windows XP entry on the menu.lst. While I learn more about ubuntu, I would like Windows XP to be the default. At present I think ubuntu is just too slow to be my main operating system. I am running 7.10. It runs like I have a 486 instead of a P-4 3.0.

---

### Post by Cresho on 2008-03-30
here its easy.. ill post in a bit

here is just a bit of some notes i posted in another section


The first time I did an install of ubuntu, I played with my one disk. I completely unplugged windows xp hardrive. I made sure ubuntu hardrive was my main boot through bios and also absolutely made sure everytime I needed to reinstall, that the live cd would install grub onto ubuntu hardrive. In anycase, after installing the operating system, I simply turned pc off, and plugged in windows xp. Of course, the hardrive does not (sometimes) automount when it boots up so in the terminal, I....

Just to note and this is important, before installing windows xp, I was able to configure this. Because my system did not hang at boot, i was able to identify my blank ntfs partition.

sudo gedit /etc/fstab

then I added to where my windows xp is located like this. do a df in a new terminal to see drive names before labling like this.

note that i placed this at the end of the page. the hdb5 is an extra disk i have laying around.

/dev/sdb1 /media/WinXP auto defaults,user,rw 0 0
/dev/hdb5 /media/Pictures auto defaults,user,rw 0 0

this next step is important.

In the Terminal, I did a sudo nautilus and created Pictures and WinXP directories under media.

Now for bootup. I noticed my operating system hung. It would not boot and found out that windows xp loves to be ontop and not on the bottom so I did this.

forgive this part since this is just my notes.

sudo gedit /boot/grub/menu.lst
sudo fdisk -l to find drives. sata1 is hd2

then I added this part after end debian automagic because if you do it before, it will erase. this modification needs to be because windows loves to be ontop. It hates being number 2


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


my pc has 2 sata drives. and anything other would be hda or hdb
on my machine, sda1, sda2 sda3 is my first hardrive with root being 1 swap 2 and home 3. the second hardrive is sdb1 which is windows xp. of course these are sata drives. Now in grub, it sees sda1 as hd0 and sdb2 as hd1.

If you have your hardware correctly installed to begin with or identified, ubuntu will automatically do this for you but since we are doing it the hardway, this is needed.
____________

---

### Post by Cresho on 2008-03-30
ohh I forgot to mention!  to boot in a particular operating system, do this.
in the terminal, type this and hit enter.


sudo gedit /boot/grub/menu.lst



Now you have a list of alot of information.  Remember when you but up?  how many lines you have?

its something like this.

0. ubuntu
1. ubuntu recovery
2. memory test
3. other operating system
4. windows xp

I simplified it for you.

now in menu.lst look for

# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

and change thd default to the number list i put up for you.

then it will default to windows.  if you hate the timeout, look right under it and change 10 to 3.

---

### Post by Cresho on 2008-03-30
opps!  I just updated the top part.  zero is the first one and not one.

---

### Post by larrythecameraguy on 2008-04-03
Thanks to all that responded.

With this array of help, I should be able to get it the way I want it.

Larry

---

### Post by larrythecameraguy on 2008-04-04
Is there some "do an un-install and remove the loader" command that I can run???

I just want to get this computer back to the configuration I had BEFORE I installed KUBUNTU.

I had a "dual boot" system with Windows XP Pro and Windows Vista Ultimate.  Thats what I want to get back to.

I want to make KUBUNTU totally go away...

Then I can boot up Vista or XP, clean up my drives, re-distribute my hard drive space, and install UBUNTU or SUSI and start over.

The KUBUNTU I'm running is 7.10 64 bit, and its too slow, and too "glitchy" to run.

I've not even been able to "update" the original install, as it crashes halfway through the update.

Windows 2000  (and DOS 3.6)  was the last OS I was truly happy with, SUSI comes in a close second, UBUNTU (any flavor but KUBUNTU) 3rd, and everything else from Windows 98 through Vista Ultimate is DEAD LAST.

Its too bad none of my software will run in Windows 2000

Larry

---

### Post by anjilslaire on 2008-04-04
load up your Vista DVD, and from the Recovery console do a :
fixmbr
then
fixboot

When done, reboot and you should be back on the Vista bootloader. Boot into Xp or VIsta, and go into the disk manager and delete the linux partitions.

---

### Post by larrythecameraguy on 2008-04-06
I will save using Windows console as a "Last Ditch" effort.. (last time I used it to rescue this computer I ended up on the phone with MicroShaft, for an hour, because, according to widows, my system wasnt "Validated").

The IDEAL fix would be to get KUBUNTU to go through its first set of "up-dates" so I can find out if it really works for me.

When it attempts to up-date, it never gets much farther than me telling it it is ok to start... then it locks up, crashes, and doesnt tell me what caused the crash..

Sifting through every action only leads up to an entry of  Update beg.

Which Im sure means something like up-date begins.

---

### Post by TheFuzz4 on 2008-04-06
Hey there,
I just got done installing Kubuntu on my Dell Laptop.  This is my only OS on this laptop (I have XP and soon Vista running through virtualbox) anyways I was also having problems getting Kubuntu to update.  If you watch the details of the update about a min into the actual updates you will see a stack smashing error or something to that extent.  Turns out in all of my research on this I finally found the answer to this in a bug report for Kubuntu 8.04.  Here is what I had to do to get this to work.  This all came from [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/205079]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/205079")
Do all of this in a konsole or terminal
cd /var/cache/apt/archives
sudo dpkg -i libgcc1_* libc6_*
this might error just ignore and roll on
sudo dpkg -i debconf* liblocale-gettext-perl_* perl-base_*
this might error just ignore and roll on
apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

Let me know if that helps you.

---


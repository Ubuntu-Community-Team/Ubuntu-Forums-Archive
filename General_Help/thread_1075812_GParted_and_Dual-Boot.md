---
title: "GParted and Dual-Boot"
date: 2009-02-20
forum: General Help
---

### Post by Martin Marshalek on 2009-02-20
I'm a little paranoid about only having 15GB for Ubuntu and want to add 5 more to get a recommended 20 GB partition. The last time I tried to do this with Gparted on the Ubuntu LiveCD it worked but ended up doubling the used space on the partition due to an error. I dual boot with Vista and was wondering if it would be better to use the true Gparted cd however I heard there are issues with Vista. Is that just the MBR or will Vista be seriously screwed up? Are there any other utilities you can recommend or a way to cut away that extra space in Ubuntu if the error occurs again?

---

### Post by Martin Marshalek on 2009-02-20
I'm a little paranoid about only having 15GB set up for Ubuntu and I want to add another 5. I tried this once and, at the end, there was an error and Ubuntu had twice as much used space as before (using Gparted from the Ubuntu live cd). I was wondering if this would work with a pure Gparted livecd but I'm afraid it will mess with my Vista install (I will also need to shrink Vista from Gparted). Will it work because I dual boot? Should I try the Ubuntu Gparted and hope I don't have the same error? Are there other utilities.

---

### Post by Yellow Pasque on 2009-02-20
> I'm a little paranoid about only having 15GB set up for Ubuntu and I want to add another 5.
Do you have a lot of packages installed? Multiple desktop environments?
What is your usage of Ubuntu vs. Windows?

---

### Post by Martin Marshalek on 2009-02-20
I use Windows for most everything but my Ubuntu usage is increasing. Right now I have 42GB free in Vista and the biggest things I will install now are probably no more than five or six games. I still have 12GB free in Ubuntu but I want to get all my partitioning done now so I don't have to worry until next time I upgrade my hardware (sometime in the summer probably as I plan to install Windows 7 and I only have a 120GB hard drive which is quite small compared to the average 250GB on most laptops now).

---

### Post by yeats on 2009-02-20
The only real issue with Vista is that the "shrink volume" feature often doesn't provide enough space for your second OS.  You can use gParted, but you risk overwriting Vista's boot partition.  But even that is okay if you have the Vista CD/DVD, which will "repair" whatever damage you do :-).

This is an excellent link for you:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

Good luck!

---

### Post by Martin Marshalek on 2009-02-20
Thanks for the link, I tried everything but still couldn't get the extra space. I could try do delete the pagefile from Linux but I decided that, since everyone says 15GB is more than enough, I'll leave it at that. This is my current partition setup:

Vista---->87GB with 42GB free
Ubuntu---->16GB with 12GB free
Compaq Recovery---->7GB with 200MB free
Linux Swap---->1GB

Do I have enough in Ubuntu to use it as my default OS for everything but gaming (I store most documents and pictures on the Windows partition as well as all of my music)?

---

### Post by TimDaniels on 2009-02-22
> **Martin Marshalek said:**
> Thanks for the link, I tried everything but still couldn't get the extra space. I could try do delete the pagefile from Linux but I decided that, since everyone says 15GB is more than enough, I'll leave it at that. This is my current partition setup:

Vista---->87GB with 42GB free
Ubuntu---->16GB with 12GB free
Compaq Recovery---->7GB with 200MB free
Linux Swap---->1GB

Do I have enough in Ubuntu to use it as my default OS for everything but gaming (I store most documents and pictures on the Windows partition as well as all of my music)?

For extra space, why not delete the Compaq Recovery partition?  All that would do is restore your Vista partition (perhaps your entire hard drive) to the as-delivered state without all the installed apps and data and personalized settings.

As for Vista's new (and unique) partitioning scheme, Vista's utilities understand the "outer world's" partitioning scheme as well as its own, so you can use Gparted or any other "conventional" partition manager to create partitions that Vista will understand.

If you want to dual-boot Vista with Ubuntu and retain Vista's boot manager, here's a distillation of several articles that I used to set up my own laptop that had a pre-installed Vista.  It maintains Vista's MBR and its BCD boot manager to give Ubuntu's boot manager (Grub) as an option at startup and Vista as the default.  The installer for Ubuntu will automatically give Vista's boot manager as an option to loading Ubuntu, so you can go back and forth between the two in case you select the wrong option the first time.  I wanted to do this with tools that are already available in Vista, i.e. 'bcdedit', instead of using EasyBCD or other add-on app, just to be "pure".  :roll:  The important thing to observe is to NOT put Grub in the MBR, but to put in the Ubuntu parition.  You get to that point late in the installation setup by clicking on the "Advanced" button near the lower right of the setup GUI.  Have fun!

-----------------------------------------
DISTILLATION OF SEVERAL ARTICLES -
USING BCDEDIT TO ADD A LINUX ENTRY TO VISTA'S BCD STORE
-------------------------------------------------------

Install Grub to Linux partitiion (not to MBR)

in Ubuntu:

find device names of Vista(VV) and Linux(LL) partitions
  System/Preferences/Hardware Information/SCSI Adapter [CANNOT FIND]
or
  sudo fdisk -l

copy the boot sector of the Linux partition
  directly to the root of the Vista partition
(check the name of the Vista partition in /media)
  sudo dd if=/dev/sdLL  of=/media/sdVV/Ubootsect.bin  bs=512  count=1

Use Synaptic to load Gparted from installation DVD,
mark Vista partition "active" to load Vista's BCD
  [use Gparted's "Manage flags" to set the "boot" flag]

  System/Administration/Partition_Editor
or
  sudo gparted


in Vista:

rt-click command prompt icon, select "Run as administrator",
show the current boot menu entries
  bcdedit /enum

(if there is already an obsolete entry for Ubuntu,
 delete it with:  bcdedit /delete {obsoleteID}     )

in Vista's command prompt, make a new BCD entry
  bcdedit /create /d "Ubuntu" /application BOOTSECTOR

  [rt-click|Mark, highlight "{long hex no.}", rt-click]
  [refer to the returned long hex no. as "UbuntuID"]

declare the ID as a boot device
  [rt-click|Paste to fill in "{UbuntuID}" in cmd below]

  bcdedit /set {UbuntuID} device boot
  [including the braces]

specify the path to the copy of the Ubuntu boot sector
  bcdedit /set {UbuntuID} path \Ubootsect.bin

add Ubuntu entry to the boot time menu
  bcdedit /displayorder {UbuntuID} /addlast

set default OS timeout to be 10 seconds
  bcdedit /timeout 10

show the new boot menu entries
  bcdedit /enum

in Ubuntu, edit boot menu
  sudo gedit /boot/grub/menu.lst

-------------------------------------------

*TimDaniels*

---


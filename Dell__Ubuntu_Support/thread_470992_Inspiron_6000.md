---
title: "Inspiron 6000"
date: 2007-06-11
forum: Dell  Ubuntu Support
---

### Post by ghost_ryder35 on 2007-06-11
DELL INSPIRON 6000 configured the way I like it (Ubuntu 7.04 Feisty Fawn)

Before anything:
1.**make sure universal repositories is checked** (if your using wired internet connection)
2.**sudo apt-get update**
3.**sudo apt-get install build-essential**

Video card (Only needed if the Linux version your using doesnt recognize your video or you require S-Video to work properly **hint S-Video cable needs to be plugged in and computer restarted before it will work**):
sudo apt-get install 915resolution
****or the better option for Intel Chipset 945GM****
**sudo apt-get install xserver-xorg-video-intel**
sudo dpkg-reconfigure xserver-xorg

Wireless card using BCM43XX-FWCUTTER (requires wired internet connection, or a cd with the package on it)
**sudo apt-get install bcm43xx-fwcutter**
**sudo modprobe bcm43xx**
then restart computer and all is good
**iwconfig **to check

When using Feisty Fawn with Network Manager controlling your wireless it adds the WEP and WPA code to the keyring manager, in some cases this causes problems and is annoying since you want to be able to log into your computer and be connected automatically to the internet.  With the keyring manager you have to manually enter your keyring password every time before you are allowed to connect to the wireless network.  To remove this keyring password prompt,

**sudo apt-get install libpam-keyring**
**sudo gedit /etc/pam.d/gdm**
and add this line:
**@include common-pamkeyring** 
to the bottom of your /etc/pam.d/gdm file, Then reboot and enjoy.

HowTo: View boot progress
To make this solution permanent. Do this:
**sudo gedit /boot/grub/menu.lst**
and remove "**quiet**" from the **kernel line**. You can also remove splash here, but I like to leave splash on and remove quite, this way you get the best of both worlds.


JUST A NOTE on Totem Video Player:
I have found that if you install the ADOBE FLASH PLUGIN OR MACROMEDIA FLASH PLUGIN in Firefox before installing all codecs for the Totem video player the player will freeze and not start at all.  To avoid this problem, install all video codecs for Totem then restart computer.  After restarting you may install the Flash plugin with no adverse affects if everything went well ;).  

RECOMMENDED DOWNLOADS:
K9 Copy (copies dvd's like DVD Shrink for Windows)
BitTornado (Bit Torrent Client)
WiFi Radar (Sometimes Network Manager is a b$#ch to get to work so this is a good substitute)
VmWare Player or Server (Just in case you have files that will only run on Windows, or your in to Virtualization)
(To completely remove VmWare Server or Player you need to run the command **sudo apt-get remove --purge vmware-server vmware-player** if you installed from the repositories or **sudo vmware-uninstall.pl **if you installed from a .tar package.  You also need to run **sudo rm -r /etc/vmware** _two _times to make sure it removes the folder!)


SunJava (Needed for a lot of web content to display correctly)
FireStarter (Firewall)
Gnome Partition Manager (Manage partitions on internal and external drives)
Avast Anti-Virus (Great anti-virus program [www.avast.com](www.avast.com)) Avast code: W48310684H4000A1106-KKKD0KP6

Good links:
[http://www.easyvmx.com/](http://www.easyvmx.com/) (Create virtual machines for VmWare player or Server)
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source) (Learn how to install **anything**)
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto) (How to Install VmWare Server 1.0.3)
[http://ubuntuforums.org/showthread.php?t=449760&highlight=uninstall+vmware+player&page=2](http://ubuntuforums.org/showthread.php?t=449760&highlight=uninstall+vmware+player&page=2) (How to uninstall VmWare)
[http://ubuntuforums.org/showthread.php?t=449232&highlight=s+video](http://ubuntuforums.org/showthread.php?t=449232&highlight=s+video) (S Video Help for Intel 945GM chipset)
[http://ubuntuforums.org/showthread.php?t=468039](http://ubuntuforums.org/showthread.php?t=468039) (Display boot steps)
[http://ubuntuforums.org/showthread.php?p=2824642#post2824642](http://ubuntuforums.org/showthread.php?p=2824642#post2824642) (THIS document your reading right now)
[http://en.wikipedia.org/wiki/Alien_(software)]("http://en.wikipedia.org/wiki/Alien_(software)") (Convert RPM packages to DEB packages)

---

### Post by molly_001 on 2007-06-19
This post was incredibly useful to me as I happened to be setting up Linux on an Inspiron 6000 today.

Thank you for assembling your knowledge and experience.  You deserve a Gold Star !!

---

### Post by ghost_ryder35 on 2007-06-20
thats why I posted it to hopefully help someone in the same situation i was.  Glad I could help :)

---

### Post by ~sparkles~ on 2007-07-17
Thnks so much for this... You've saved me a million hours and inspired me in the community! :)

---

### Post by kou on 2007-07-17
Thanks for the great tutorial
I have a question about video: 
My Inspiron 6000 only have 8 mb in video card and I want something pretty to look

What is the best app: compiz or beryl for this machine? or maybe compiz-fusion?
I´m usig Kubuntu

thanks in advance

---

### Post by woyzeckswoe on 2007-08-06
hi,
i've got the problem you mentioned 'bout firefox's plugins that screw up totem.
you know how to resolve?

it would really be bad if i had to reinstall everything...just found the thread little too late.

thanks a lot for the good post.

greets
w'w

---

### Post by MyR on 2007-08-07
vmware is terrible; i dont know why people use it. virtualbox is amazingly better.
also, a lot of the things this tutorial "fixes" worked for me out of the box, like wireless.
i don't mind the progress bar while it's booting; it looks a lot better.
i don't believe you need to sudo dpkg-reconfigure xserver-xorg either.
antivirus seems like a waste too.

sorry for the criticism but i mean for it to be constructive.

---

### Post by ghost_ryder35 on 2007-10-13
> **MyR said:**
> vmware is terrible; i dont know why people use it. virtualbox is amazingly better.
also, a lot of the things this tutorial "fixes" worked for me out of the box, like wireless.
i don't mind the progress bar while it's booting; it looks a lot better.
i don't believe you need to sudo dpkg-reconfigure xserver-xorg either.
antivirus seems like a waste too.

sorry for the criticism but i mean for it to be constructive.
^^^^^^^^^^^^^^^:lolflag:^^^^^^^^^^^^^^^^^^^^^^
It says "The way I like it" If you dont like it tough %^$#

---

### Post by elgalloloco on 2007-10-13
Very helpful...

THANX!

---

### Post by wormser on 2008-03-23
Warning to fellow 6000 users.  When I upgraded from Feisty to Gusty my sound card blew.  My trouble shooting leads me to believe the external amplifier is the issue.  Whatever it is... I have no sound from my speakers but the headset still works.

[http://ubuntuforums.org/showthread.php?t=620618](http://ubuntuforums.org/showthread.php?t=620618)

---

### Post by MyR on 2008-03-23
> **wormser said:**
> Warning to fellow 6000 users.  When I upgraded from Feisty to Gusty my sound card blew.  My trouble shooting leads me to believe the external amplifier is the issue.  Whatever it is... I have no sound from my speakers but the headset still works.

[http://ubuntuforums.org/showthread.php?t=620618](http://ubuntuforums.org/showthread.php?t=620618)


I've been using gutsy for quite a while with no problems.

sorry about your sound card though. :[

peace

---

### Post by wormser on 2008-03-23
> **MyR said:**
> I've been using gutsy for quite a while with no problems.

sorry about your sound card though. :[

peace

I should have made it clearer.  Do a fresh install of Gusty.  The upgrade process blew my hardware.

---

### Post by XRayA4T on 2008-04-03
> **wormser said:**
> I should have made it clearer.  Do a fresh install of Gusty.  The upgrade process blew my hardware.

Sad news :( I would get it fixed as soon as possible as I heard when getting a new screen cover for my wife's laptop that Dell was stopping support for the Inspiron 6000 soon. This may just be in South Africa but I'd check if I was you.

I had my Insipron 6000 laptop main board blow when changing a battery which I think had not finished charging. Are you sure the upgrade caused the problem and it was not just a coincidence?

---

### Post by wormser on 2008-04-04
> **XRayA4T said:**
> Sad news :( I would get it fixed as soon as possible as I heard when getting a new screen cover for my wife's laptop that Dell was stopping support for the Inspiron 6000 soon. This may just be in South Africa but I'd check if I was you.

I had my Insipron 6000 laptop main board blow when changing a battery which I think had not finished charging. Are you sure the upgrade caused the problem and it was not just a coincidence?

Yeah it was the upgrade.  Somebody else had the same issue.  I can live with it.  Hopefully soon I will get a new laptop.

---


---
title: "iceWM: Missing &quot;Programs&quot; Menu"
date: 2005-04-07
forum: Desktop Environments
---

### Post by dfv3 on 2005-04-07
First, let me praise the Ubuntu community;  I've installed Ubuntu 4.10 with Windows XP on my 2-HDD-desktop (AMD Athlon, 1.46 GHz, 512MB-RAM; with 120GB-master HD for Ubuntu, and 80GB-slave HDD for Windows XP) --- Ubuntu is awesome!!.  Thank you Ubuntu people!

With my very-old PC (1999), I'm having a li'l problem:

I, too, followed through the "Ubuntu/Debian-Sarge Mini-RAM How To, by Ingo LANTSCHNER (ingo@binonabiso.com)", and I've got my Ubuntu (Version 4.10) working on my old PC (Pentium MMX 400MHz, 64MB-RAM, and 880MB-HDD) --- except that the programs that I've installed does not show-up in the iceWM menu!

Through "apt-get install ---" ,  I've installed AbiWord, gnumeric, bluefish, etc.  And I can only open these programs from the Terminal console (e.i.: typing "abiword" at the $ prompt, opens up a new abiword document).

Perhaps, I've missed something; or there's a conflicting program that I've installed.  I've "apt-get install" all the following:

xserver-xfree86
x-window-system-core
xdm
numlockx
xterm
mozilla-firefox
abiword
gnumeric
zip
unzip
gaim
openssh-server
gpdf
cdrecord
mkisofs
bluefish
weblint
rdesktop
tsclient
emelfm

Please note that I've 2 HDD; I'm dual booting with Ubuntu in the master disk (hd0) and Windows 98SE in the slave drive (hd1).  

The grub-boot loader handles the boot options nicely ; though I've to modify the menu.lst file  --- /boot/grub/menu.lst --- with big help from [http://www.bioxray.dk/~mok/dual-boot.html](http://www.bioxray.dk/~mok/dual-boot.html).  

Also, I've noticed that my iceWM "Logout" menu, when selected,  brings me back to the Debian User-Login promt.  I've tried modifying the file /etc/sudoers  (with #visudo) by adding this line:

[username]   ALL=NOPASSWD: //sbin/shutdown, /sbin/poweroff, /sbin/halt, /sbin/reboot, /bin/cdrecord

It didn't work!  Is there a better way to shutdown Ubuntu/iceWM aside from the computer switch?



Help please,
dfv3 :confused:

---

### Post by Jason-X on 2005-04-08
Regarding the Icewm menu. I use "Ice Menu Editor" (iceme). It's very easy to use. You can just add the apps to the menu this way.

**sudo apt-get install iceme**

I also use "Ice Pref" (icepref) for configuring other parts of Icewm.

**sudo apt-get install icepref**

Regarding shutdown, I have the same problem. The logout>shutdown menu does not work. I use the "sudo halt" command in the terminal. That does the job.

Hope this helps :-)

---

### Post by az on 2005-04-08
Do you have the menu package installed?

sudo apt-get install menu

---

### Post by dfv3 on 2005-04-08
Thank you AZZ and Jason-X!

"sudo apt-get install menu"  worked!  After the installation of "menu", iceWM's "Programs" menu was automatically populated with the programs that I had previously installed.

"sudo apt-get install iceme"  and "sudo apt-get install icepref" worked well in customizing the whole iceWM dropdown- menus.

Ubuntu really rocks!  

Thanks again folks!
dfv3

---

### Post by wilhelm on 2005-05-10
oh man , was this thread helpfull.

thanks ppl ;-)

---

### Post by Neobuntu on 2007-11-11
>  sudo dpkg-reconfigure menu

Worked for me!:KS

---

### Post by D-EJ915 on 2007-11-12
> **Neobuntu said:**
> Worked for me!:KS
actually all you have to do is sudo update-menus...or that should be all, heh


and bump from hell, lol...

---

### Post by Neobuntu on 2008-01-06
Ha! 

> sudo update-menus

Worked better for me.

I'm using Xubuntu for an old comp with only 128MB RAM and wanted more speed so I installed icewm and friends.

All the goodness of Ubuntu. All the speed of icewm (with the Silver XP theme). It's easy to copy over and edit the .icewm preferences file; to better resemble stock XP (for kicks). It's not that it looks like crappy Windows. It's that it's clean and just works.

---

### Post by Ripfox on 2008-01-07
Man was this helpful!! Thanks alot.

Now how do I get the sound going...I'm using Antix...

---

### Post by Neobuntu on 2008-01-12
> apt-get install alsa-base alsa-utils alsa-oss aumix-gtk 

Try that!

---

### Post by BLTicklemonster on 2008-07-23
How can I add a way to look at the other computers on my home network in the menu in Icewm?

---


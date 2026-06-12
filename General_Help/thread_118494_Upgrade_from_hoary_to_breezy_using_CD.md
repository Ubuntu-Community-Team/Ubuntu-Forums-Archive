---
title: "Upgrade from hoary to breezy using CD"
date: 2006-01-17
forum: General Help
---

### Post by arphe_el on 2006-01-17
hello!

any suggestions on step by step procedure on how to upgrade from hoary to breezy using CD?

in the sources.list I unmark all url and mark only CD from this... 

##deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013)]/ breezy main restricted

I try to apt-get update from the terminal and I get this message...

# sudo apt-get update
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013) breezy Release.gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013) breezy ReleaseIgn cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013) breezy/main Packages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013) breezy/restricted Packages
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013) breezy/main Packages
Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013) breezy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051013)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051013)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

any help?

---

### Post by nocturn on 2006-01-17
If I read this correctly, remove the CD-rom option from sources.list and check out the apt-cdrom command to add it.

CD's are handled differently because apt-get update cannot get updates from them (they are static and may not be inserted).

---

### Post by Ali_Baba on 2006-01-17
You should write that apt-cdrom on command line first.It seems according that error message that you have to make that new cd recognized.Just writing to sources.list isn't enough.Hope this help's you out :)

---

### Post by arphe_el on 2006-02-20
I already made some modifications with the /etc/apt/sources.list but something appear on the terminal that i need to modify the fstab and the apt.conf

here are the ff. message after i type in sudo apt-cdrom

apt 0.6.35ubuntu2 for linux i386 compiled on Apr  6 2005 20:37:35
Usage: apt-cdrom [options] command

apt-cdrom is a tool to add CDROM's to APT's source list. The
CDROM mount point and device information is taken from apt.conf
and /etc/fstab.

Commands:
   add - Add a CDROM
   ident - Report the identity of a CDROM

Options:
  -h   This help text
  -d   CD-ROM mount point
  -r   Rename a recognized CD-ROM
  -m   No mounting
  -f   Fast mode, don't check package files
  -a   Thorough scan mode
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp

any comments, suggestions and instructions to modify the fstab and the apt.conf any help are greatly appreciated. GODspeed!

---

### Post by dcstar on 2006-02-20
[QUOTE=arphe_el]hello!

any suggestions on step by step procedure on how to upgrade from hoary to breezy using CD?
.....[/QUOTE]
Or you could follow the clear instructions here and avoid all of these problems:

[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

---

### Post by arphe_el on 2006-02-24
thank you for the info. i already visit the recommended link

i'm now performing the upgrade from hoary to breezy but there is a pop up box appeared which to choose either the default or smart update. Any suggestions?

thank you dcstar. GODspeed!

---

### Post by arphe_el on 2006-02-24
i finally chose the default button and after that the upgrade installation was successful except that when i click on the open office it's empty. So what i did is to install it using synaptic but after i reboot it something wrong with the x server which actually appear on the screen.

"i cannot start the x server your graphical interface. it is not likely that it is not set up correctly would you like to view the x server output to diagnose the problem. <yes> <no>"

any solutions to my problem? I think i did a big mistake

your help is greatly appreciated. GODspeed!

---

### Post by lamego on 2006-02-24
Try using:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bonjun on 2006-02-24
maybe you can try this [wiki]("https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28video%29")

---

### Post by arphe_el on 2006-02-27
I already made it (thank God!) I install the nvdia package and edit the xorg.conf as suggested by poofyhairguy on this link:  

[http://www.ubuntuforums.org/showthread.php?t=131267&highlight=gdm](http://www.ubuntuforums.org/showthread.php?t=131267&highlight=gdm)

after that my default desktop just crush but don't worry just delete the following files to your terminal or gftp make sure your in a failsafe mode by logging out and relogin in again on failsafe mode:

delete the following files
.gconfd
.gnome
.gnome2_private
.gconf
.gnome2
.nautilus

log-in again and click default. by doing this all of your set-up in the panel will be reset to default and you have to reconfigure again then your back.

---


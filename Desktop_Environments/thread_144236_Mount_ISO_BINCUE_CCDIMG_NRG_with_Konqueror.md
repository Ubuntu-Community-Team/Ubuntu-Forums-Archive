---
title: "Mount ISO BIN/CUE CCD/IMG NRG with Konqueror"
date: 2006-03-13
forum: Desktop Environments
---

### Post by adamkane on 2006-03-13
You can use the MountISO KDE service menu in Konqueror to **mount ISO, BIN/CUE, IMG/CUE and NRG** images, **convert NRG, BIN, CCD to ISO **images, **create ISO or UDF** images, and there are also utilities to **identify an ISO type** and **calculate MD5 checksums**. Konqueror is the default file manager for KDE, but GNOME and XFCE users can use Konqueror as well. It would not be difficult to re-write the MountISO KDE service menu as a Nautilus-Script.

References:
[http://www.ubuntuforums.org/showthread.php?t=69530]("http://www.ubuntuforums.org/showthread.php?t=69530")
[http://forums.suselinuxsupport.de/index.php?showtopic=14668]("http://forums.suselinuxsupport.de/index.php?showtopic=14668")

** Add the universe repository**, if you haven't already:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")

** Install build-essential, checkinstall, automake1.6, libtool, gcc-3.4, bchunk, nrg2iso:**

```

sudo apt-get install build-essential checkinstall automake1.6 libtool gcc-3.4 bchunk nrg2iso

``` 
** Install Konqueror**, if you don't have it installed already:

```

sudo apt-get install konqueror

``` 
** Install the appropriate linux-headers** for your system. (Pick one):

```

sudo apt-get install linux-headers-686 # Celeron / Pentium Pro / II / III / 4 without Hyper-Threading
sudo apt-get install linux-headers-k7 # AMD
sudo apt-get install linux-headers-386 # Pentium (Basic Driver)
sudo apt-get install linux-headers-686-smp # Pentium 4 with Hyper-Threading (Multi-Processor)
sudo apt-get install linux-headers-k7-smp # AMD Multi-Processor

``` 
Reboot if necessary to take advantage of the linux-headers you've just installed. It's OK to remove linux-headers-386, if you don't need them anymore, but only after you've rebooted with your new headers.

** Download and install cdemu:**
[http://cdemu.sourceforge.net/]("http://cdemu.sourceforge.net/")

```

cd ~
wget http://robert.private.outertech.com/virtualcd/cdemu-0.7.tar.bz2
tar xjf cdemu-0.7.tar.bz2
cd cdemu-0.7
sudo ls -la /lib/modules/`uname -r`/build 
sudo make
sudo make install
sudo modprobe cdemu
sudo gedit /etc/modules

``` 

Add the following line to the /etc/modules file:

```

cdemu

``` 
Save the file, then close gedit.

Note: Use the ` symbol, not the ' symbol.
Note: sudo make install is used, because sudo checkinstall doesn't work here.

** Download ccd2iso to your Desktop and install:**
[http://sourceforge.net/projects/ccd2iso/]("http://sourceforge.net/projects/ccd2iso/")

```

cd ~/Desktop
tar xzf ccd2iso-0.2.tar.gz
cd ccd2iso
./configure
make
sudo checkinstall

``` 
Accept the defaults. When the menu comes up,
enter the **Description** as: convert ccd to iso
Enter the **Name** as: ccd2iso-0.2
Enter the **Version** as: 0.2 

** Download extract-xiso binaries to your desktop and install:**
[http://sourceforge.net/projects/extract-xiso]("http://sourceforge.net/projects/extract-xiso")

```

cd ~/Desktop
tar xzf extract-xiso_v2.5_linux_libc6.tgz
cd extract-xiso_v2.5_linux_libc6
sudo chmod 755 extract-xiso
sudo cp extract-xiso /usr/bin

``` 
** Download the MountISO KDE service menu to your desktop and install:**
[http://www.kde-apps.org/content/show.php?content=11577]("http://www.kde-apps.org/content/show.php?content=11577")

```

cd ~/Desktop
tar xjf 11577-mount-iso-0.9.1.tar.bz2
cd mount-iso-0.9.1
gedit install.sh

``` 
Replace lines 1011-1034 with the following:

```

  mountcb)
    BASE="${BSNAME%.*}"
    BINFILE="$SAVEDIR/"`head -n 1 "$1" | cut -f 2 -d " " | sed -e "s/^\"//" -e "s/\"$//"`
    NODE=$((`'$CDEMU' -s | cut -f 8 -d " " | grep 0 -n -m 1 | cut -c 1`-2))
        
    if (test -d "$MOUNTDIR") then
      check_mount "$MOUNTDIR" &&
      err 2 "$1"
    else
      mkdir -p "$MOUNTDIR"
    fi
    if ( test -d "$MOUNTDIR" )
    then
      '$CDEMU' $NODE "$1"
      kdesu -c "mount -t iso9660 /dev/cdemu/$NODE \"$MOUNTDIR\""
    fi
    if ( check_mount "$MOUNTDIR" ) then
      kfmclient openURL "$MOUNTDIR"
    else
      rmdir "$MOUNTDIR"
      err 6 "$MOUNTDIR"
    fi
    ;;

``` 
Save the file and close gedit. Then continue:

```

./install.sh

``` 
The install script will tell you which components you already have installed, and then offer you some options. 

**Select:**
**2 - Install Mount-ISO using kdesu**

The install script will create some service menu files.

Open Konqueror and right-click an image to mount it. Right-click the image again to unmount it.

Note: Installation Option 1 - Install Mount-ISO using sudo doesn't work, because Ubuntu deals with kdesu and sudo differently than other distributions. The install script needs to be modified in order to use sudo instead of kdesu.
Note: MountISO will mount the images to a new folder at ~/Desktop.
Note: MountISO doesn't warn you if the image file is corrupt. If nothing happens, when you try to mount a file, then something is probably wrong with your image, or the image file uses advanced options that aren't supported by the MountISO package.

Note: You can also download ccd2iso from here:
[http://rarewares.org/debian/packages/unstable/ccd2iso_0.2-0.1_i386.deb]("http://rarewares.org/debian/packages/unstable/ccd2iso_0.2-0.1_i386.deb")

Note: You can also download extract-xiso from here: 
[http://rimron.co.uk/weblog/category/ubuntu/]("http://rimron.co.uk/weblog/category/ubuntu/")
[http://www.rimron.co.uk/experimental/extract-xiso_2.5-1_i386.deb]("http://www.rimron.co.uk/experimental/extract-xiso_2.5-1_i386.deb")
[http://www.xbox-scene.com/tools/tools.php?page=isotools]("http://www.xbox-scene.com/tools/tools.php?page=isotools")

---

### Post by zwaardmeester on 2006-03-27
Wauw it works perfectly for me!!! Thanks a lot!

---

### Post by adamkane on 2006-03-27
You may also find kiso useful:
[http://www.ubuntuforums.org/showthread.php?t=150593](http://www.ubuntuforums.org/showthread.php?t=150593)

---

### Post by Karbonik on 2006-10-24
I had a slight issue with the ccd2iso install:

karbonik@biosolar-laptop:~/Desktop/ccd2iso$ make
cd . && /bin/sh /home/karbonik/Desktop/ccd2iso/missing --run aclocal-1.6
/home/karbonik/Desktop/ccd2iso/missing: line 46: aclocal-1.6: command not found
WARNING: `aclocal-1.6' is needed, and you do not seem to have it handy on your
         system.  You might have modified some files without having the
         proper tools for further handling them.  Check the `README' file,
         it often tells you about the needed prerequirements for installing
         this package.  You may also peek at any GNU archive site, in case
         some other package would contain this missing `aclocal-1.6' program.
make: *** [aclocal.m4] Error 1


The README was no help, and the only package that turned up from apt-cache search of "aclocal" was the package "libguile-dev", which I installed, but I still do not get the "make" to work.  



Any suggestions?

---

### Post by ImplicitProcrastination on 2006-10-26
II had the same problem as karbonik, but worked my way around it using the .deb file.

It seems to have installed but when i try to mount a file i get this:

ERROR: "/media/sda1/VTC - JAVA/Java 2 Certified Programmer/Java 2 Certified Programmer.iso" has data error! File might be of wrong type or corrupted.

When I installed it this was the output:

```


     - Mount-ISO v0.9.1 (using "kdesu") -

Creating a folder for servicemenus: [ SKIP ]
Installing mountiso.desktop:        [  OK  ]
Installing mountiso-dir.desktop:    [  OK  ]
Installing mountiso-cue.desktop:    [  OK  ]
Installing mountiso-ccd.desktop:    [  OK  ]
Installing mountiso-grb.desktop:    [  OK  ]
Installing mountiso-nrg.desktop:    [  OK  ]
Installing mountiso-emu.desktop:    [  OK  ]
Installing mountiso-xbx.desktop:    [  OK  ]
Creating a folder for associations: [ SKIP ]
Installing associations (*.NRG):    [  OK  ]
Installing associations (*.CCD):    [  OK  ]
Installing associations (*.CUE):    [  OK  ]
Installing mountiso.sh:             [  OK  ]


```

---

### Post by groggyboy on 2006-11-10
i'm attempting to install this in kubuntu edgy (6.10).

my current problem (for which i don't know a fix - help please!) is when i try to install mountISO.  typing './install.sh' in the mountISO folder returns this error:> ./install.sh: 146: function: not found

Couldn't find !
Type the full path here or press "Ctrl+C" to abort:  
typing the full path does nothing, pressing 'ctrl+c' quits it.



some other issues (and my workarounds):

automake1.6 isn't in the edgy repositories.  i just skipped it.

when installing the linux-headers, use this command (regardless of your processor) instead of choosing a specific set of headers:> sudo apt-get install linux-headers-generic

i had the same problem with ccd2iso - the .deb file works fine.

i'd love to get this working, so if anyone can help me with that error, i'd be much obliged!

---

### Post by sphere02 on 2006-11-11
./install.sh: 146: function: not found

Couldn't find !
Type the full path here or press "Ctrl+C" to abort:

kate install.sh and replace "/bin/sh" with "/bin/bash" will do

---

### Post by groggyboy on 2006-11-11
thanks sphere02! your fix solved it, and everything installed properly.

great howto, adamkane.

---

### Post by adamkane on 2006-11-11
Thanks for all the help.

It's time to do an update for Dapper. Be back soon!

---

### Post by mr_byte on 2006-11-12
In the fixing the function error above, editing /bin/sh to /bin/bash, there is also another location that needs editing. This is the script that gets installed, the line is 696 in my copy, looks like

echo '#!/bin/sh  

Also, you need to replace this:

      *)
        # Anything else
        rmdir "$MOUNTDIR
        ;;

With
	# Anything else
	MODE=",defaults"
	;;
at line 862 or so.

This will let me mount ISO files, but NRG (and I assume others) are still borked.

---

### Post by mr_byte on 2006-11-13
I have found that for some reason, on my system, the file identification code doesn't seem to work, it will always return 000000, no matter what kind of file is used.

Has anyone else had this issue, and what did you do to correct it?

Jeff

---

### Post by koosvannermerwe on 2006-12-14
> **Karbonik said:**
> I had a slight issue with the ccd2iso install:

karbonik@biosolar-laptop:~/Desktop/ccd2iso$ make
cd . && /bin/sh /home/karbonik/Desktop/ccd2iso/missing --run aclocal-1.6
/home/karbonik/Desktop/ccd2iso/missing: line 46: aclocal-1.6: command not found
WARNING: `aclocal-1.6' is needed, and you do not seem to have it handy on your
         system.  You might have modified some files without having the
         proper tools for further handling them.  Check the `README' file,
         it often tells you about the needed prerequirements for installing
         this package.  You may also peek at any GNU archive site, in case
         some other package would contain this missing `aclocal-1.6' program.
make: *** [aclocal.m4] Error 1


The README was no help, and the only package that turned up from apt-cache search of "aclocal" was the package "libguile-dev", which I installed, but I still do not get the "make" to work.  

Any suggestions?


I had the same problem... after installing libguile-dev, I just created 2 symlinks to aclocal and automake:
```

sudo apt-get install libguile-dev
cd /usr/bin
sudo ln -s aclocal aclocal-1.6
sudo ln -s automake automake-1.6

```

It seems that  aclocal-1.7 got installed instead of 1.6. After creating the links it worked fine.

HTH
koos

---

### Post by adamkane on 2006-12-14
I think that Dapper and Edgy use a different version of automake, and the howto hasn't been updated to reflect that.

---

### Post by ImSneakinAround on 2006-12-19
I realize that this hasn't been updated in a while but i'm having a problem. When installing ccd2iso I get a "Command Not Found" error:

```
asz@asz-desktop:~/Desktop/ccd2iso-0.3$ sudo checkinstall
Password:
sudo: checkinstall: command not found

```

I'm using Kubuntu 6.10 Edgy, if any other info might help, let me know. Any help would be appriciated :)

---

### Post by adamkane on 2006-12-19
I think you need to install checkinstall or install build-essential.

---

### Post by ImSneakinAround on 2006-12-20
Should have seen that one coming! Thanks adamkane! :)

---

### Post by adamkane on 2006-12-20
900 beans versus 2! I will crush you!

---

### Post by Oklin on 2006-12-29
Uuh I really need this, i have some .bin files i need to install..

but i allready get errors at the 1st thing with the "repositories", there are a lot of the sources it cant find:

```
Err http://packages.freecontrib.org breezy/free Packages
  404 Not Found
Hit http://us.archive.ubuntu.com breezy Release
Err http://packages.freecontrib.org breezy/non-free Packages
  404 Not Found
Err http://packages.freecontrib.org breezy/free Sources
  404 Not Found
Err http://packages.freecontrib.org breezy/non-free Sources
  404 Not Found
```

```
Fetched 5B in 2s (2B/s)
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/bin ary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free /binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/sou rce/Sources.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free /source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.
```

I am new to Ubuntu and Linux, so I don't know what to do

---

### Post by adamkane on 2006-12-29
The "I really need help right now" is poor form.

You have the PLF repositories enabled in your /etc/apt/sources.list file. There's plenty of info on the forums about how to enable/disable sources.

```

sudo gedit /etc/apt/sources.list

```

Comment out the PLF sources.

```

sudo apt-get update
sudo apt-get upgrade

```

If you have a bin file, all you really need to do is install kiso.

```

sudo apt-get install kiso

```

---

### Post by Oklin on 2006-12-30
> **adamkane said:**
> The "I really need help right now" is poor form.

You have the PLF repositories enabled in your /etc/apt/sources.list file. There's plenty of info on the forums about how to enable/disable sources.

```

sudo gedit /etc/apt/sources.list

```

Comment out the PLF sources.

```

sudo apt-get update
sudo apt-get upgrade

```

If you have a bin file, all you really need to do is install kiso.

```

sudo apt-get install kiso

```

ahh thank you.. i will try that in a minute..

---

### Post by Oklin on 2006-12-30
> **adamkane said:**
> The "I really need help right now" is poor form.

You have the PLF repositories enabled in your /etc/apt/sources.list file. There's plenty of info on the forums about how to enable/disable sources.

```

sudo gedit /etc/apt/sources.list

```

i get this error:
bash: /etc/apt/sources.list: Permission denied

> **adamkane said:**
> The "I really need help right now" is poor form.
If you have a bin file, all you really need to do is install kiso.

```

sudo apt-get install kiso

```

It won't install for me :S:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kiso

---

### Post by 0x29a on 2007-01-01
this is a really neat thing for non-iso images. If you're dealing with just iso images, a quick down-and-dirty command is:

# mount -o loop -t iso9660 /path/to/iso /mnt/dir

this can mount as many iso images in as many directories as you feel compelled to create (up to 8 apparently). Still it is cool that I can finally figure out what all those img and nrg images are that I can't remember (even though they're for winders...).

---

### Post by tworkemon on 2007-01-16
If you are doing this in Feisty or 2.6.20-5 I noticed that cdemu will not work properly. I noticed this when i upgraded to feisty. I had this working fine on previous releases.
You will probably get some error similar to this when doign ```
sudo make
```

The error 
```
WARNING: "generic_file_read" [/home/USER/cdemu-0.8/cdemu.ko] undefined!

```

What I did to fix this was to replace ```
generic_file_read
``` with ```
do_sync_read
``` in the ```
cdemu_core.c
``` file.

It should be fine after that. Remember this is what happened to me after i upgraded to feisty but im sure you will have to do this also if you are installing this from scratch. You might run into more problems im not sure. This is all I had to do to fix the issue I had after I updated to feisty.

---

### Post by RealG187 on 2007-04-15
how can i mount and burn nrg without converting all my images?

---

### Post by L0cKd0wN on 2007-04-23
Just wanted to post an update in case others run into this.  I'm using Feisty (7.0.4) and initially encountered trouble with getting cdemu to work.  I encountered this:

~/Desktop$ sudo modprobe cdemu
FATAL: Error inserting cdemu (/lib/modules/2.6.20-15-generic/misc/cdemu.ko): Unknown symbol in module, or unknown parameter (see dmesg)
[B][U]
THE FIX:[/U][/B]

**1.**  cd into ~/cdemu-0.8 wherever you have put it
**2. ** 'gedit cdemu_core.c' or 'nano -w cdemu_core.c'
**3. **find the code "generic_file_read" (lines 489 and 493) and change _both_ to "do_sync_read"
**4.** 'sudo make' again
**5.** 'sudo make install' again
**6. **make sure you have added 'cdemu' to /etc/modules

modprobe should now simply return with no errors!

Hope this helps a few of you!

~L0cK

---

### Post by kvonb on 2007-04-23
Does anyone know it there is an app to actually edit ISO images?  I'd like to be able to add/remove/update files.

I can't seem to find one.

Thanks :).

---

### Post by RealG187 on 2007-04-23
I have Nero Linux, can that mount NRG? What if I started a CD in Windows and wanna continue the multi session CD, can I?

---

### Post by naszi on 2007-10-28
Hi,

I installed this little program, but when i try to mount an iso i get an information dialog with the name of the file, thats it, no mounting.

Can anybody help me, whats going wrong?

---


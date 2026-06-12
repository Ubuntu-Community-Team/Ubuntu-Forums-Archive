---
title: "Need help installing Ngspice"
date: 2006-11-04
forum: Education &amp; Science
---

### Post by edisav on 2006-11-04
Hi folks,

I'm looking for easy ngspice (EE application for circuit analysis) install instructions for my (K)ubuntu box. I saw some posting about ngspice, but they didn't provide enough info to really help me - specially since I'm not a Linux expert.

Any help would be appreciated.

Thanks!

---

### Post by Steveire on 2006-11-04
> **edisav said:**
> Hi folks,

I'm looking for easy ngspice (EE application for circuit analysis) install instructions for my (K)ubuntu box. I saw some posting about ngspice, but they didn't provide enough info to really help me - specially since I'm not a Linux expert.

Any help would be appreciated.

Thanks!
Hey. Ksimus is a KDE application for this. Make sure you have universe repositories enabled, and 
```

sudo aptitude install ksimus

```

---

### Post by slimdog360 on 2006-11-04
I think ksimus only does logic (unless thats what your looking for).

its buggy and only version 0.3 but if your looking for something simple you may want to look at [http://ktechlab.org/]("http://ktechlab.org/").

for ngspice
you can go here [http://sourceforge.net/project/showfiles.php?group_id=38962&package_id=31152]("http://sourceforge.net/project/showfiles.php?group_id=38962&package_id=31152"), click on the bit which says '17.binary.32bit' to expand it. THere should be something which says 'ngspice_17.0.0-1_i386.deb', download that one.

to install it type into a terminal ```
sudo dpkg -i ngspice_17.0.0-1_i386.deb
```
and then pray that it installs. download this into your home directory which would look something like /home/edisav. If you download it somewhere else you'll have to change into that directory first, then use the code I gave you.

---

### Post by boz on 2006-11-07
I would install gEDA if you need analog simulations as well.  Actually, the gEDA project has everything, including PCB board design and verilog translations.  You can go to my post [http://www.ubuntuforums.org/showthread.php?t=283903]("http://www.ubuntuforums.org/showthread.php?t=283903") and find the link that I posted.  There's a CD .iso file image there.  Just download it, put in a CD-R (if you have a CD-R drive), right click on the .iso file and click write to disk.  After it installs, install your kernel headers, build-essential, and their are a couple of other dependencies that I don't remember at the moment.

I'll tell you what, I'll come back and give you a full step-by-step once my classes are out.  They start in 10 minutes and I still have to eat.  You can at least get started on reading up on the project and the help files online, if you're not working, too.  I have to warn you, though, any circuit CAD program that you install on Linux isn't going to be as intuitive or developed as PSPICE.  In gEDA, you have to use separate programs to perform all of the tasks.  One to draw the circuit, another to interpret the netlist, another to simulate the netlist, and yet another to do any plotting, etc.  And you have to get comfortable with the command line.  You might try tclspice.  I haven't tried that program yet, but it might be easier.  Anyway, let me know if you want a step-by-step.

Kelly

---

### Post by ChristophM on 2006-11-08
Hi Kelly, 

I'm a pretty green Linux newbie, but have a little experience with SPICE etc. 

I tried to install gEDA from a CD (onto which I had burned the ISO image) to ubuntu 6.10, but I seem to have shot some libraries and had to reinstall ubuntu. 

So if you could walk *me* through the installation, I would very much appreciate it.

Christoph

---

### Post by boz on 2006-11-09
Note:  It's always a good idea to do a little research yourself.  If you "trust" me and simply copy my code and it f*&#$s up your system, you can't legally sue me.  That's the catch with open-source.  You're responsible for yourself no matter what.  So, I'm giving you fair warning that this is my first how-to on any Linux forum and I'm doing it from memory.  I installed gEDA a couple of weeks ago, so I do encourage you to double-check everything.  That said, here it is:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

I'm not sure about this following line.  Edgy may be using a new version of gtk.  If you want to be sure, open System->Administration->Synaptic Package Manager and search for libgtk.  Find the ones you have selected.  The development files (which are the ones you want to install) should match the libgtk version you have installed and have *-dev* at the end.  You can check it and install it from Synaptic while you're there.

```
sudo apt-get install libgtk2.0-dev #don't do this if you've already installed a different version from Synaptic!
```

download the .iso image
burn it to disk
pop in the cd
click System->Administration->Disks and navigate to cdrom 
To the right, underneath Properties look three lines down.  It should look something like /dev/***; mine says /dev/hda, so that's what I use two lines down from here.

```
sudo mkdir /mnt/cdrom1/
mount -o exec -t iso9660 /dev/hda /mnt/cdrom1/ #The -o flag allows executables to be run off the CD
```

If you have not yet set up the root password, do so now:

```
sudo passwd root
```

You'll know what to do after that.  Now,

```
su
/mnt/cdrom/installer --log
```

And you're off to the races.  Everything after that should be easy.  The whole install took about an hour for me, most of it for ngspice.  So, kick back with a beer or six and enjoy the show.  Hopefully you won't run into any errors, but if you do, post them on here.  I'm somewhat of a newb myself, but there are plenty of brilliant minds on this forum to help us if we get stuck.

Eject the CD after you're done, because I basically told you to mount it twice.  Ubuntu automagically mounts Cdrom's for you, but without the executable flag.

---

### Post by boz on 2006-11-09
By the way, gEDA isn't as simple as Pspice to use.  You have to get comfortable with the command line, and I found gschem (the schematic editor) to be a little awkward at first.  If you're not prepared (have the time right now, etc) to do some research on learning how to use gEDA, you might want to stick with windows emulation for right now.  However, it might not hurt to get a leg up and install it now and at least try it out.  Edgy's not going anywhere for 18 months, so you won't have to worry about recompiling the source code for that long.

---

### Post by Adrian Nania on 2006-12-23
to install ngspice, first you need to install all dependencies for Ubuntu (Edgy) and only after that try to install anything at all.
For extended details about required packages, see [http://www.ubuntuforums.org/showthread.php?t=282040](http://www.ubuntuforums.org/showthread.php?t=282040) and look inside the attached script file gEDA-CVS-ubuntu.txt
For ngspice only, open a shell, log in as root wit:
```

su -
```
now check the following lines and replace "adi" with "YourUserName" and change the default install location "/home/programs/gEDA" with your desired one:
```

clear
echo from http://ngspice.sourceforge.net/nighttarball.html
echo
apt-get install -y axel
mkdir /home/adi/tmp
cd /home/adi/tmp
echo ngspice download started: please wait, this could take up to 9s, function of the download speed
# axel -a http://ngspice.sourceforge.net/files/ng-spice-rework_CVS.tar.gz
axel -a http://superb-west.dl.sourceforge.net/sourceforge/ngspice/ng-spice-rework-17.tar.gz
echo
echo ngspice download END
cp -dpr ./ng* /home/backups/src/electro/gEDA/CVS-sources/
tar -xzf ng*
clear
echo ngspice setup started: please wait, this could take up to 442s on an AMD64 1.8Gb processor
echo if impatient, check the log file: /home/adi/tmp/ngspice.log
cd ng*
time {
./autogen.sh
./configure --prefix=/home/programs/gEDA \
	--enable-nosqrt \
	--enable-nobypass \
	--enable-capzerobypass \
	--enable-predictor \
	--enable-newtrunc \
	--enable-intnoise \
	--enable-xspice \
	--enable-numparam \
	--enable-dot-global \
	--enable-xgraph \
	--with-editline=yes
#	--enable-maintainer-mode	this is for the CVS version
#	--enable-experimental	this one is generating errors
#	--enable-sense2		this one is generating errors
#	--enable-ekv		this one is generating errors
#	--enable-cider		this one is generating errors
#	--enable-cluster	this one is generating errors
make
make install
} >/home/adi/tmp/ngspice.log 2>&1
echo
echo ngspice setup END
echo check the following Error messages -if any- to ensure no critical errors occured:
echo
grep error /home/adi/tmp/ngspice.log
grep Error /home/adi/tmp/ngspice.log
```

---

### Post by sdaau on 2011-05-03
Sorry to bump an old thread - maybe this wiki entry will help: 

[From_PSpice_to_ngspice-gEDA - Ubuntu Wiki](https://wiki.ubuntu.com/From_PSpice_to_ngspice-gEDA)

---


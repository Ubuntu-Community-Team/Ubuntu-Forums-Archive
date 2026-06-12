---
title: "How-to: Installing LabVIEW 8.2 under Ubuntu 7.10"
date: 2008-03-16
forum: Education &amp; Science
---

### Post by Trafferth on 2008-03-16
Hello all,

I am sure there are scientists and engineers who would like to install LabVIEW on their Ubuntu box, but have been unable to do so because the binaries are supplied as .rpm files, not .deb.  The following is a short how-to that shows how I installed LabVIEW 8.2 on my Ubuntu 7.10 box.

The information I used originally came from the National Instruments forums:

[http://forums.ni.com/ni/board/message?board.id=170&message.id=284896&query.id=129697#M284896](http://forums.ni.com/ni/board/message?board.id=170&message.id=284896&query.id=129697#M284896)

Specifically, there is the following link in that thread that leads to a how-to guide:

[http://www.ilbazaar.netsons.org/2007/06/19/linux/come-installare-ni-labview-82-su-ubuntu-feisty-fawn-704/](http://www.ilbazaar.netsons.org/2007/06/19/linux/come-installare-ni-labview-82-su-ubuntu-feisty-fawn-704/)

As you can tell from the URL, however, the guide is in Italian.  Hopefully the following 'remastering' of the how-to will be of use to English-speakers. I have only tested this with LabVIEW 8.2 under Ubuntu 7.10, but the original thread suggests that the procedure outlined below should work with LabVIEW 8.0, 8.2, and 8.5 under Ubuntu 7.04 and 7.10. 

Once installed, I found that all the front panel objects were present, and the majority of the block diagram (programming) functionality of LabVIEW was also available.  Programming features were missing from 'Measurement I/O', 'Vision and Motion', 'Control Design and Simulation', and 'SignalExpress'.  Perhaps these can be added from the Windows disks, although I have not tried it yet.  I expect the functionality that can be achieved in the following guide will be sufficient for most people, however.

Good luck! :)

Trafferth

[B][U]
Installing LabVIEW 8.2 under Ubuntu 7.10[/U][/B]

The problem with installing LabVIEW 8.2 under Ubuntu is that it is distributed using .rpm (Red Hat Package Managment) files rather than Ubuntu's native .deb (Debian) format.  This can be overcome using alien, as described below.

1. Open a terminal (Applications > Accessories > Terminal)

2. Make a temporary directory in your home folder:

```
mkdir ~/LV8pkg
```

3. Copy all .rpm files from CD main directory to a directory on the hard disk, e.g.:

```

cp /media/cdrom0/*.rpm ~/LV8pkg
```

4. Update apt:

```
sudo apt-get update
```

5. Install alien, libdb1-compat, and libosmesa6:

```
sudo apt-get install alien libdb1-compat libosmesa6
```

6. Navigate to the .rpm files on your hard drive:

```
cd ~/LV8pkg
```

7. Use alien on the .rpm files (each line is a separate command - the terminal's paste hotkey is <CTRL><SHIFT><V>):

```
sudo alien -k labview82-appbuild_8.2-1_i386.rpm
sudo alien -k --scripts labview82-core-8.2-1.i386.rpm
sudo alien -k --scripts labview82-desktop-8.2-1.i386.rpm
sudo alien -k labview82-examples-8.2-1.i386.rpm
sudo alien -k labview82-help-8.2-1.i386.rpm
sudo alien -k labview82-pro-8.2-1.i386.rpm
sudo alien -k labview82-ref-8.2-1.i386.rpm
sudo alien -k --scripts labview82-rte-8.2-1.i386.rpm
sudo alien -k labview82-vxi-8.2-1.i386.rpm
sudo alien -k --scripts labview-rte-aal-1.1-1.i386.rpm
sudo alien -k --scripts niexfinder-base-1.0-7.i386.rpm
sudo alien -k --scripts niexfinder-labview82-1.0-7.i386.rpm
sudo alien -k --scripts niwebpipeline20_dep-2.0-5.i586.rpm
```

The conversion procedure will take a while. Note that one of the 'niexfinder' commands may give an error about not being able to find the 'finder' directory, but this does not seem to affect the conversion.

8. Install each of the generated .deb files separately (again, each line is a separate command - the order is irrelevant):

```
sudo dpkg -i labview82-appbuild_8.2-1_i386.deb
sudo dpkg -i labview82-core-8.2-1.i386.deb
sudo dpkg -i labview82-desktop-8.2-1.i386.deb
sudo dpkg -i labview82-examples-8.2-1.i386.deb
sudo dpkg -i labview82-help-8.2-1.i386.deb
sudo dpkg -i labview82-pro-8.2-1.i386.deb
sudo dpkg -i labview82-ref-8.2-1.i386.deb
sudo dpkg -i labview82-rte-8.2-1.i386.deb
sudo dpkg -i labview82-vxi-8.2-1.i386.deb
sudo dpkg -i labview-rte-aal-1.1-1.i386.deb
sudo dpkg -i niexfinder-base-1.0-7.i386.deb
sudo dpkg -i niexfinder-labview82-1.0-7.i386.deb
sudo dpkg -i niwebpipeline20_dep-2.0-5.i586.deb
```

9. You can now close the terminal:

```
exit
```

10. LabVIEW should now appear under Applications > Programming > LabVIEW 8.2

11. You may have to point LabVIEW at your web browser when attempting to find examples.  If you are using Firefox it will be located at /usr/bin/firefox

---

### Post by phyrko on 2008-04-14
Nice howto, thanks. I can comfirm that it works equally well with LabVIEW 8.5.

One thing is that the two packages in your list (niexfinder-base, niexfinder-labview) also give errors in the dpkg install step. The NI Example Finder seems to work fine though.

---

### Post by Trafferth on 2008-04-25
Hello all,

Just an update: the above how-to seems to work fine for under Hardy for LabVIEW 8.2 as well - see screenshot!

At the time of writing, there remains an odd problem with running LabVIEW under Ubuntu - when attempting to tile the front panel and the block diagram, the system will hang.  Perhaps this is linked to Compiz - I shall investigate.

Regards,

Trafferth

@ phyrko: I am glad the how-to was of use.  I only ever get errors at the conversion stage, however - the packages install without complaint.  The example finder works fine for me too.

Just out of interest, do you get the hanging behavior when attempting to tile the editor windows?

---

### Post by Trafferth on 2008-04-25
Hello all,

Regarding the hanging with the tile command - this seems to be a conflict between LabVIEW and Compiz, as suspected.  The fix is simply to disable visual effects and LabVIEW then works without a hitch. :)

I don't know if this is specific to Hardy or not - I have installed 8.04 over my previous 7.10 installation, so I am unable to check.  Perhaps someone else can try this and see?

- Trafferth

---

### Post by carpediem1337 on 2008-04-30
I'm wondering how to install LabVIEW on the x64 version of Hardy.  I already have the 32-bit deb files..I tried doing "sudo dpkg -i --force-architecture xxxx.deb" but I get an error.  Here is my terminal output:

```
sudo dpkg -i --force-architecture labview82-core_8.2-1_i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 123659 files and directories currently installed.)
Preparing to replace labview82-core 8.2-1 (using labview82-core_8.2-1_i386.deb) ...
Unpacking replacement labview82-core ...
Setting up labview82-core (8.2-1) ...
sort: open failed: +1: No such file or directory

```

Help would be greatly appreciated.

---

### Post by vaibshah on 2008-04-30
Hello all!
I recently started working on Ubutu and had to install Labview 8.2 on it. 

Just yesterday joined this forum and I am really happy to have installed Labview 8.2 on my Ubuntu 6.06 LTS. Yes, the steps described above, by Trafferth, work perfectly with 6.06 also.

However, I had to change some directory names in few commands. I have saved the commands which worked finally. 
So here is an updated version, for anyone who wish to install LabVIEW 8.2 on Ubuntu 6.06 LTS.

Once again, I am just repeating Trafferth's commands with updated directory names.


==========
mkdir ~/LV8pkg

cp /media/cdrom0/*.rpm ~/LV8pkg

sudo apt-get update

sudo apt-get install alien libdb1-compat libosmesa6

cd ~/LV8pkg

sudo alien -k labview82-appbuild-8.2.1-1.i386.rpm
sudo alien -k --scripts labview82-core-8.2.1-1.i386.rpm
sudo alien -k --scripts labview82-desktop-8.2.1-1.i386.rpm
sudo alien -k labview82-examples-8.2.1-1.i386.rpm
sudo alien -k labview82-help-8.2.1-1.i386.rpm
sudo alien -k labview82-pro-8.2.1-1.i386.rpm
sudo alien -k labview82-ref-8.2.1-1.i386.rpm
sudo alien -k --scripts labview82-rte-8.2.1-1.i386.rpm
sudo alien -k labview82-vxi-8.2.1-1.i386.rpm
sudo alien -k --scripts labview-rte-aal-1.1-1.i386.rpm
sudo alien -k --scripts niexfinder-base-1.0-7.i386.rpm
sudo alien -k --scripts niexfinder-labview82-1.0-7.i386.rpm
sudo alien -k --scripts niwebpipeline20_dep-2.0-5.i586.rpm

sudo dpkg -i labview82-appbuild_8.2.1-1_i386.deb
sudo dpkg -i labview82-core_8.2.1-1_i386.deb
sudo dpkg -i labview82-desktop_8.2.1-1_i386.deb
sudo dpkg -i labview82-examples_8.2.1-1_i386.deb
sudo dpkg -i labview82-help_8.2.1-1_i386.deb
sudo dpkg -i labview82-pro_8.2.1-1_i386.deb
sudo dpkg -i labview82-ref_8.2.1-1_i386.deb
sudo dpkg -i labview-rte-aal_1.1-1_i386.deb
sudo dpkg -i labview82-vxi_8.2.1-1_i386.deb
sudo dpkg -i labview-rte-aal_1.1-1_i386.deb
sudo dpkg -i niexfinder-base_1.0-7_i386.deb
sudo dpkg -i niexfinder-labview82_1.0-7_i386.deb
sudo dpkg -i niwebpipeline20-dep_2.0-5_i386.deb

exit
==============

Once again, SINCERE THANKS TO TRAFFERTH. I DO NOT HAVE ANY PROBLEMS WITH EXAMPLES. 


Best regards,
Vaibhav

---

### Post by anshuljain on 2008-05-07
Vaibhav,
Were you able to install NI-KAL, NI-VISA and DAQ too?

-Anshul

---

### Post by Trafferth on 2008-05-08
@ carpediem 1337:

I'm afraid I don't have any direct experience with trying to install LabVIEW on 64-bit linux systems.

According to the NI developer forum, it doesn't look like installation is possible on linux 64-bit in general, although a few people have attempted it - see:

[http://forums.ni.com/ni/search?board_id=170&submitted=true&q=linux+64-bit](http://forums.ni.com/ni/search?board_id=170&submitted=true&q=linux+64-bit)

The only thing I can think of is if you try the --force-all option at the dpkg stage, i.e.

```
 sudo dpkg -i --force-all package-name.deb 
```

Beyond that, I don't know what else to suggest.  Let us know how you get on, though!

Good luck! :)

Trafferth

---

### Post by pavleb on 2008-08-12
@carpediem1337

Hi I have the same problem on Ubuntu 8.04 with LabView 8.2 My system is 32 bit.

Does anyone has any idea what is missing?

---

### Post by frumple on 2008-10-01
I was facing the same problem to install LabVIEW 8.5 on my AMD64 Ubuntu 8.04, alien complained about architecture difference. 

After a whole night trying different methods I've came to a procedure that works. All you need are the LabVIEW RPM packages, rpm2cpio and cpio utils, here are the step-by-step instructions:

1 - mkdir ~/labview
2 - cd ~/labview
3 - cp LABVIEW_INSTALL_MEDIA_MOUNT_POINT/*.rpm
4 - for each of the RPMs run the following command:

rpm2cpio RPM_FILE | cpio -idv

Don't mind to try *.rpm in the above command, I doesn't work ;) Unfortunately it must be file by file or you can automate the process using a script.

The above command complete unpacks the RPM, after all the RPMs are processed there will be an ~/labview/usr/local/ folder containing all LabVIEW's files.

6 - sudo mv usr/local/* /usr/local/

7 - It's already installed! Just create a launcher that points to /usr/local/natinst/LabVIEW-8.5/labview 

OBS: If you need to remove LabVIEW just remove the /usr/local/natinst and the 5 libraries added to /usr/local/lib

The result shown in the attached jpg is promising :popcorn:

Eduardo

---

### Post by Greettat on 2008-10-01
it is better to fight for good than to fail at the ill.-------------------------[evening dresses](http://www.china-stylish.com/Evening-Gown.html), [evening gowns](http://www.china-stylish.com/Evening-Gown.html), [wedding dresses](http://www.china-stylish.com/Wedding-Dress.html), [bridal gowns](http://www.china-stylish.com/Wedding-Dress.html), [wedding gowns](http://www.china-stylish.com/Wedding-Dress.html)

---

### Post by Cheesecycle on 2008-10-04
Thanks frumple, install went smoothly and labview runs.  The real test will come when we have a lab that uses it. :)

---

### Post by greg_gm on 2008-10-13
This post was excellent.  It gave me the key knowledge to try and go one step further.  I have successfully installed labview 8.2 using Ubuntu 8.04.  Additionally I have been able to get various USB AD/DA hardware working.  Here is an outline of the additional steps.

First, I assume you have labview 8.2 installed using the approach described.  Next, you need installation files from these two packages: NI-DAQmx, and NI-Visa which are readily available at the NI website.  Get the newest packages because older versions are not compatible with the newer linux kernals.

Visa package - [http://joule.ni.com/nidu/cds/view/p/id/1074/lang/en](http://joule.ni.com/nidu/cds/view/p/id/1074/lang/en)
DAQmx package - [http://joule.ni.com/nidu/cds/view/p/id/1076/lang/en](http://joule.ni.com/nidu/cds/view/p/id/1076/lang/en)

All the rpm files in the DAQmx package should be converted to .deb files and installed.  Generically the method is as described above. Here are the basic steps.

1) Download the .iso CD image and put in a folder
2) right click on the .iso image and "Extract Here"
3) The visa files further compressed in .tz format.  You need the package "ncompress" to dig into those.  "sudo apt-get install ncompress" to install.  Then untar using: "tar xf xxxx.tz"
4) Now dig into the directory structure and pull out all the rpm files into one place
5) Convert the rpm files as described above:  sudo alien -k --scripts xxxx.deb
6) Then double click on the xxxx.deb file from the file browser 'nautilus' which will initiate the package installer.  
7) I installed all the Daq-mx distribution and only the following deb conversions from the VISA cd with filenames that start as shown below.  When given a choice of 32 bit or 64 bit versions I ignored anything that implied 64 bits.  I have the standard 32 bit version of Ubuntu 8.04:

labview82-rte...
nicvirte...
nivisa...
nivisa-config

I was sure this was not going to work but it did!

You will find some important utilities under /etc/natinst/nidaqmxbase/bin

* lsdaq is a key utility which runs in a terminal.  It tells you if you have a working USB device.  This the utility to try first.  If you have a working usb device it will show up here first.  If not, keep trying.

* FWUpdate is also useful it allows you to upgrade firmware.

* mxbaseconfig is the NI-DAQmx Base Task Configuration Utility

* nidatalogger is a simple oscilliscope application that is good for debugging a setup.  If you can make the lines wiggle here, your set!

Additiionally on my system the visa utilities where installed in the gnome application pull down menu.
 
It is certainly reasonable to think that some of the packages I skipped may be useful or important.  So if all else fails you can try installing everything.

---

### Post by Trafferth on 2008-10-23
I am glad this thread seems to have helped.  I shall have to try this extra stuff that greg_gm mentions.  I honestly did not think to try - I was just happy to get a base installation of LabVIEW working.  If the drivers and other things work, then this will be one step closer to being able to ditch the last Windows installation I have (on my trusty laptop*).  If only OriginPro7.5 would work satisfactorily under wine...

* Dual-boot, natch! :)

---

### Post by wakayu on 2008-10-31
thanks to everyone. now i'm successfully install LabVIEW 8.5 to my ubuntu linux. i think i have a big problem. before this I developed and run the Labview algorithm using Window xp pro.for your information, i used VISION and Database as well in my algorithm. since i want feel boring with window, then i try to install ubuntu linux. is anyone here have any idea how to install labview vision 8.5 and the database as well. where i can get the installer for linux OS?i will appreciate your help. thank you

---

### Post by neoflight on 2008-10-31
Has anyone tried installing it in anyother disrto other than Ubuntu?

---

### Post by odwyerda on 2009-06-11
Has anyone got Vision to work yet?

I can't even seem to get Vision working on my XP lab computer


Dave

---

### Post by BosseGregersson on 2009-11-10
Can confirm that following Trafferth's instructions i got Labview 8.2 working on Karmic Koala 9.10. Started it and played around with it a bit and everything I tried worked so far.

---

### Post by labeljohn on 2010-08-24
Thanks! Just got it working under 10.4 64bit

---

### Post by neurostu on 2010-10-27
Does anyone know how to install the C API under Ubuntu (preferably a newer distribution like 9.10 or 10.04)

Does the C API get installed with labview or does it have to be installed explicitly?

---

### Post by northd_tech on 2010-11-13
> **labeljohn said:**
> Thanks! Just got it working under 10.4 64bit

I just attempted both using alien to convert .RPM to .DEB and installing LabVIEW 8.5 under 64-bit Ubuntu Lucid Lynx 10.04 and neither method worked.  Here are the error messages from** sudo sh ./install**:
> NOTE: LabVIEW will install by default in /usr/local/natinst/LabVIEW-8.5,
or in the natinst/LabVIEW-8.5 subdirectory if you specify an alternate location.

Preparing for installation...
Please indicate whether you would like to install the following components:

/media/Bakup_/LINUX/new_math/LabVIEW8.5/bin/rpmq: error while loading shared libraries: libbz2.so.1: cannot open shared object file: No such file or directory
[Ynasq?] y
/media/Bakup_/LINUX/new_math/LabVIEW8.5/bin/rpmq: error while loading shared libraries: libbz2.so.1: cannot open shared object file: No such file or directory
It continues on like this for a while with my telling it "y" with no success.  I found libbz2.so.1 here and tried linking it to the directory with the RPM's:

**/lib/libbz2.so.1**

That didn't work either.

Using alien-- **sudo alien -k labview85-appbuild-8.5-1.i386.rpm **

> Can't locate object method "new" via package "Alien:: Package::Rpm" at /usr/bin/alien line 436.I know these are 32-bit RPM files, but I don't have 64-bit ones on the CD. :(

I will attempt the rpm2cpio method above and see if that works.

---

### Post by giaino78 on 2011-02-21
Hi guy,
i want to say only...great job....it works...I mean I can install labview 8.5 on my
ubuntu10.10 amd64,

thanks.

---

### Post by snlzkn on 2011-03-21
Even works with Natty 64 bit! Thanks guys I was going to install OpenSUSE just for this :D Since I have Natty compiz drives me mad sometimes when I right click but Natty is alpha what can you expect :D

---

### Post by flakifero on 2011-04-08
Hi, I was looking around internet but couldn't solve a problem linking labview with firefox.
When I try to open the Labview Help, labview tries to open .html files with nautilus and gives error "The location is not a folder." which is logical.
The thing is that I can't find the way to tell labview to use Firefox to open help files.
If anyone has an idea to fix it I'll apreciate it.
I think this is maybe related to step 11 of this How-to.

Using Ubuntu 10.04 and Labview 8.5.

Thanks and sorry for my english.

---

### Post by Trafferth on 2011-04-08
Wow - this thread is still active! It's been a while! :)

@flakifero: As far as I know, the help files are simply .html, so quite why Nautilus can't read them is a bit of a mystery.  The only other thing I can think of is that only a *partial* path is being handed onto Nautilus, and because it isn't aware of a default base path, it cannot find the files.  This would be what I would check first; you might then be able to include the base path to the help files in Nautilus.

If Nautilus is indeed being given full paths, then pehaps if you have a machine spare (or if you create a virtual machine), you can install LabVIEW on an OpenSUSE machine and see how this (supported) distro handles the help files - it might be a simple matter of installing the application that OpenSUSE uses to view them.

I hope that gives you some ideas at least; I have following a great deal of frustrations with the LabVIEW / Linux combination standardised to using Windows 7 when developing with LabVIEW - it saves a lot of headaches.  Maybe I shall try installing LabVIEW 2010 on an Ubuntu virtual machine later this week and see how it goes.  Hmm.... might need to start a new thread for that though.

Good luck, everyone! :)

---

### Post by rowemate on 2011-06-14
Hi, has anyone managed to install a working PyVISA system based on NI-VISA in any Ubuntu x86_64? 

>>> import pyvisa.vpp43 as vpp43
ok.
>>>vpp43.visa_library.load_library("/usr/local/vxipnp/linux/bin/libvisa.so.7")
OSError: /usr/local/vxipnp/linux/lib/libvisa.so.7: wrong ELF class: ELFCLASS32

---

### Post by tommpogg on 2011-07-18
> **flakifero said:**
> Hi, I was looking around internet but couldn't solve a problem linking labview with firefox.
When I try to open the Labview Help, labview tries to open .html files with nautilus and gives error "The location is not a folder." which is logical.
The thing is that I can't find the way to tell labview to use Firefox to open help files.
If anyone has an idea to fix it I'll apreciate it.
I think this is maybe related to step 11 of this How-to.

Using Ubuntu 10.04 and Labview 8.5.

Thanks and sorry for my english.

Have you tried to use firefox (or another browser) to open the help pages.
Take a look [here]("http://digital.ni.com/public.nsf/allkb/83B0BFE9A19D744386257046006B3808"), it explains how to set the browser for LabView.

Anyway, the button "Find Examples" does not work!
Any clue to fix it?

---


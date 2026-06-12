---
title: "Newbie Questions with 5.10"
date: 2005-12-08
forum: General Help
---

### Post by Spikey.Lozenge on 2005-12-08
Alright, I have done some searching, and have not come up with any answers that seem to match my problem. Also, my second question, I couldn't seem to find an answer that worked...  If I missed something, I apologize.

1.) Whenever I'm opening  the Synaptic Package Manager, I get a Warning Box with these two Errors:

```
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
```

This started Occuring after using EasyBreezy, and having it crash during its installation. I think it may have made a bad backup of something?

2.) I'm looking for a step by step procedure for installing programs... for an example, [http://www.daimonin.net/](http://www.daimonin.net/)

I have downloaded it... but I'm not having any luck getting it installed.  Its currently Extracted in my Home folder, in a folder labeled daimonin.

As I stated, if I missed something, would you mind posting a link to where I can get the information? Thanks!!

Also, First post! :razz: 

Thanks for all your help!

---

### Post by blueplazma on 2005-12-08
1) That error you're getting from Synaptic is due to Synaptic trying to read the Ubuntu CDROM that came with your system and it not being there. You can turn that source off in the repositories menu.

2) It looks like Daimonin is distributed as a source package. You'll need to compile it yourself. The normal steps for that are to enter the directory containing the files and execute the following three commands: 
```

./configure
make
make install

```

It is possible that Daimonin has a different procedure. When you compile a program, you have to ensure that you have all of the libraries it requires. If you don't, you'll get an error during the first step.

---

### Post by cstudent on 2005-12-08
First: There's an option with apt-get that you can use to restore the CD repository. I've used it once, but don't remember exactly the syntax of the command. You should be able to use "man apt-get" in terminal and find it.

Second: Look through the extracted files in your folder. There is probably a readme and install file. Open them in  a text editor. There may be info there about the correct procedure to install. You also probably need the build-essential files. Use "sudo apt-get install build-essential" in terminal to install those.

---

### Post by Spikey.Lozenge on 2005-12-08
Haven't tried the first solution yet, but that makes sense.  However, I am getting this error on the ./Configure Instruction
```

david@David-Linux:~/daimonin/client/make$ ls
linux  README.txt  win32
david@David-Linux:~/daimonin/client/make$ cd linux/
david@David-Linux:~/daimonin/client/make/linux$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
david@David-Linux:~/daimonin/client/make/linux$ make
bash: make: command not found
david@David-Linux:~/daimonin/client/make/linux$

```

Any other pointers?  Sorry If I'm a pest...

---

### Post by cstudent on 2005-12-08
You need to install the build-essential package;

sudo apt-get install build-essential

This gives you the libraries it is looking for.

---

### Post by Spikey.Lozenge on 2005-12-08
Alright, Read the manual, and got two commands.  Check, and update.  Neither worked.  Here is the Terminal:

```
david@David-Linux:~$ apt-get check
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
david@David-Linux:~$ sudo apt-get check
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
david@David-Linux:~$ sudo apt-get update
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release.gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy ReleaseIgn cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Hit http://archive.ubuntu.com breezy/universe Packages
Fetched 189B in 1s (140B/s)
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
david@David-Linux:~$

```

---

### Post by carlosqueso on 2005-12-08
I'm not sure if this is exactly right, since i'm not at home and can't check, but here goes:

Open a terminal.
Type ```
sudo gedit /etc/apt/sources.list
```
Somewhere in that file, there should be a line or two that has "cdrom://ubuntu 5.10..." and some other crap.  Either delete those lines, or if you're worried about damage put a "#" at the beginning of the line.  
Save the file.

Now, before you try to build that software again, type ```
sudo apt-get update
sudo apt-get install build-essential
```[SIZE="1"]EDIT: Fixed my terrible punctuation/capitalization[/SIZE]

---

### Post by Spikey.Lozenge on 2005-12-08
[QUOTE=carlosqueso]I'm not sure if this is exactly right, since i'm not at home and can't check, but here goes:

Open a terminal.
Type ```
sudo gedit /etc/apt/sources.list
```
Somewhere in that file, there should be a line or two that has "cdrom://ubuntu 5.10..." and some other crap.  Either delete those lines, or if you're worried about damage put a "#" at the beginning of the line.  
Save the file.

Now, before you try to build that software again, type ```
sudo apt-get update
sudo apt-get install build-essential
```[SIZE="1"]EDIT: Fixed my terrible punctuation/capitalization[/SIZE][/QUOTE]


I Tried those steps, and I got this result:
```
david@David-Linux:~/daimonin/client/make/linux$ sudo apt-get update
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Hit http://archive.ubuntu.com breezy/universe Packages
Fetched 1B in 0s (1B/s)
Reading package lists... Done
david@David-Linux:~/daimonin/client/make/linux$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
david@David-Linux:~/daimonin/client/make/linux$


```

Now, Before we go any further, This is my first time with Linux, and I didn't put anything Vital on this.  I have no problem Re-formatting and re-loading to get things back to the way they should be.  Should I take that route since things don't seem to be working right?

(Also, to everybody, Thank you very much for the quick, and detailed posts. I'm learning a lot!)

---

### Post by carlosqueso on 2005-12-08
Reinstalling may very well work (of course, you'll have to repeat a lot once you reinstall), but I don't think we're there yet.  If you wouldn't mind, type ```
sudo gedit /etc/apt/sources.list
``` once more and copy and paste the results here so we can see what's up with that.   I think that may be the problem.

---

### Post by Spikey.Lozenge on 2005-12-08
Here it is, With the First Line Commented out:

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe

```

I was just listing a reload as an option.  This is more fun! (I like breaking stuff... ^_^ )

---

### Post by carlosqueso on 2005-12-08
I wholeheartedly agree....I spent all last night compiling a file manager from source...now that's an adventure :-D.

Anyway....your problem is that all of your sources have "#" in front of them.  That tells apt to ignore them.  To enable the repositories (where the software comes from) you need to remove the "#" in front of it.  So delete the "#" in front of the lines beginning with "deb http://" and "deb-src" and you will be in business with all of the repositories.  You may need to delete that bottom line too, as it's a duplicate of one of the ones above.   I'd also remove the "us" at the beginning of the "us.archive.ubuntu.com" parts, as the US mirrors don't seem to work very well.  Once you do that, you should be in business.  By the way....thanks for helping me get to my 50th post lol.

---

### Post by Spikey.Lozenge on 2005-12-08
Here is the Changed one.  I saved a copy of the original as sources.list.old just in case.
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb http://archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://archive.ubuntu.com/ubuntu breezy universe
 deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe


```

---

### Post by Bachstelze on 2005-12-08
here is a good sources.list file (thanks to aysiu)

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

```

---

### Post by carlosqueso on 2005-12-08
Spikey> methinks your list should work, or the one in HymntoLife's post will work nicely as well. (I just didn't feel like looking it up, as it's not the one I've tested).  I'd try your apt-getting now and see what happens.

---

### Post by Spikey.Lozenge on 2005-12-08
[QUOTE=carlosqueso]Spikey> methinks your list should work, or the one in HymntoLife's post will work nicely as well. (I just didn't feel like looking it up, as it's not the one I've tested).  I'd try your apt-getting now and see what happens.[/QUOTE]

Thank you all for the Quick Answers!

I copied the one from above, and Used that. Then, a apt-get check, update, check later, its fixed! No more error.

I am however, getting an error making the Daimonian File, however, I believe that it is because I am missing needed libraries.


And, as Newbies go... I have a few more questions:
1.) Is there any page that lists how to install drivers for a Microsoft MN-520 Wireless Notebook Adaptor? (802.11 b)  It does not detect it by default, and I have NO idea where to go with that one.  

2.) I have put the 'CPU Frequency Scaling Monitor' in the Panel, but I have a question.  Yes, the computer is a Laptop, but when I have it plugged in, does it really need to scale the Speed down? It constantly runs the system at 500 Mhz, and its killing me.  When i'm trying to watch a movie/DVD, it stutters really bad.  I know that I can open the System Monitor, and kill the powernowd process to stop it, but is there a better way?

3.) Related to 2, I have installed the Power Preferences Utility, But it does not seem to have any CPU Scaling Utility to allow me to set it, or turn it off. I would preferably like To Max it when running on AC, and Only Scale it when I am running Batteries...  Any Recommondations?

4.) I am a pretty powerful Windows User, and I was just sick of it... I'm trying to learn Linux because... well, its free, open, and...fresh!  Is there any recommended reading for me? I have printed out the Ubuntu Starter Guide, and Its all well and good, but it describes how to do stuff without WHY you are doing it.  I want to know what a command does not just 'Do This, Type this, you are Teh Win!'

5.) (It's a lot, I know) Is there a way to step back a directory in Terminal? The only two options when I '--help' (The '/?' Windows-Eqivalent?) the cd Command, the two options have no explaination...

I'm sure I'll think of something... Thanks if anybody is still reading this!!:)

---

### Post by Spikey.Lozenge on 2005-12-08
Has anybody had a chance to read any of this? I suppose they die down after work ends eh? ;)

---

### Post by Gray. on 2005-12-09
1) Maybe go [here]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29") to see if your card is supported.
2) & 3) Don't have my laptop with me at the moment but I may be able to see what I can do when I get it back.
4) I'd love to see something like that too.
5) ```
cd ..
```

---

### Post by carlosqueso on 2005-12-09
[QUOTE=Spikey.Lozenge]Has anybody had a chance to read any of this? I suppose they die down after work ends eh? ;)[/QUOTE]

Yah, went home and had other things to do, you know how it is ;-)  I'm not sure about 2+3, I've not played with that on my lappy (which is plugged in almost all the time anyway).

1.  The MS card is probably not anything special...is it a PCIMA card or USB? If it is a PCIMA card, type ```
lspci
```  If it's a usb card, type ```
lsusb
``` and post the output of the commmand that you use.
4. I'd hang out in the forums, especially the Absolute Beginner Talk.   There are some good and informative threads out there.   I've only been on linux full time for about 2 months, and I've learned a lot just from being a part of the community.  Also people also often have interesting links in their sigs and posts, but be prepared for a little arrogance in some of those.

---

### Post by Spikey.Lozenge on 2005-12-09
[QUOTE=carlosqueso]Yah, went home and had other things to do, you know how it is ;-)  I'm not sure about 2+3, I've not played with that on my lappy (which is plugged in almost all the time anyway).

1.  The MS card is probably not anything special...is it a PCIMA card or USB? If it is a PCIMA card, type ```
lspci
```  If it's a usb card, type ```
lsusb
``` and post the output of the commmand that you use.
4. I'd hang out in the forums, especially the Absolute Beginner Talk.   There are some good and informative threads out there.   I've only been on linux full time for about 2 months, and I've learned a lot just from being a part of the community.  Also people also often have interesting links in their sigs and posts, but be prepared for a little arrogance in some of those.[/QUOTE]

It is a PCIMA Card. Lucky for me, I brought it in today. :) 

Here is the 'lspci' result:
```
david@David-Linux:~$ lspci
0000:00:00.0 Host bridge: ALi Corporation M1647 Northbridge [MAGiK 1 / MobileMAGiK 1] (rev 04)
0000:00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1420
0000:00:04.1 CardBus bridge: Texas Instruments PCI1420
0000:00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
0000:00:08.1 Communication controller: ESS Technology ESS Modem (rev 12)
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:10.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)

```

I know what you mean about work too... I basically spent the night figuring out how to install that 'Daimonin' Game, however after install, i'm not sure where it installed.  I tried to run it from the terminal... is there a specific command for running from a terminal? (ex, run?)

So, i'll consult those forums since its not directly ubuntu related.

---

### Post by carlosqueso on 2005-12-09
I'm assuming you have a wired ethernet controller too, which is the EN-1216.  That means we're not seeing it....try to take the wireless card out, insert it, and run lspci again.  If it doesn't show up then.. run ```
 dmesg
``` and hopefully, it'll tell someone who knows what they're doing will be able to make sense of that.

If you installed it properly, you should be able to just go to a terminal and type ```
daimonin
```, but if that doesn't work, type ```
whereis daimonin
``` and it should tell you the directory that you need to go to in order to run the program.  If neither of those is helpful, the Daimonin folks should be able to help at their forums.

---

### Post by Spikey.Lozenge on 2005-12-09
Found it.  I was in the right place, I just had to type ./daimonin , Not, just 'daimonin'.


Although, it does full screen crash my computer when run... I assume that is their problem though, so I'll take that up there.

I checked the card compatability list that was posted above, and the Microsoft Card didn't seem to have any compatability at all. It wasn't even listed! Just in case its make by a different company, Here is the Code...

lspci Command
```

david@David-Linux:~$ lspci
0000:00:00.0 Host bridge: ALi Corporation M1647 Northbridge [MAGiK 1 / MobileMAGiK 1] (rev 04)
0000:00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1420
0000:00:04.1 CardBus bridge: Texas Instruments PCI1420
0000:00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
0000:00:08.1 Communication controller: ESS Technology ESS Modem (rev 12)
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:10.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
```

dmesg Command:
```
david@David-Linux:~$ dmesg

[4294671.365000] Mount-cache hash table entries: 512
[4294671.365000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[4294671.365000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[4294671.365000] Enabling disabled K7/SSE Support.
[4294671.365000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294671.365000] CPU: L2 Cache: 64K (64 bytes/line)
[4294671.365000] CPU: After all inits, caps: 0383f9ff c1c7f9ff 00000000 00000020 00000000 00000000 00000000
[4294671.365000] CPU: AMD mobile AMD Duron(tm) Processor stepping 00
[4294671.365000] Enabling fast FPU save and restore... done.
[4294671.365000] Enabling unmasked SIMD FPU exception support... done.
[4294671.365000] Checking 'hlt' instruction... OK.
[4294671.369000] Checking for popad bug... OK.
[4294671.369000] checking if image is initramfs... it is
[4294672.250000] Freeing initrd memory: 5172k freed
[4294672.256000] ACPI: Looking for DSDT in initrd... not found!
[4294672.370000]  not found!
[4294672.384000] ACPI: setting ELCR to 0200 (from 0820)
[4294672.390000] NET: Registered protocol family 16
[4294672.390000] EISA bus registered
[4294672.390000] ACPI: bus type pci registered
[4294672.403000] PCI: PCI BIOS revision 2.10 entry at 0xfd8b0, last bus=1
[4294672.403000] PCI: Using configuration type 1
[4294672.403000] mtrr: v2.0 (20020519)
[4294672.404000] ACPI: Subsystem revision 20050729
[4294672.454000] ACPI: Interpreter enabled
[4294672.454000] ACPI: Using PIC for interrupt routing
[4294672.457000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294672.457000] PCI: Probing PCI hardware (bus 00)
[4294672.458000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294672.462000] Boot video device is 0000:01:00.0
[4294672.464000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294672.465000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294672.466000] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 10 *11)
[4294672.466000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 10 *11)
[4294672.467000] ACPI: PCI Interrupt Link [LNKC] (IRQs *5 7)
[4294672.467000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11) *0, disabled.
[4294672.468000] ACPI: PCI Interrupt Link [LNKU] (IRQs *9)
[4294672.472000] burst-mode-ec-10-Aug
[4294672.472000] ACPI: Embedded Controller [EC0] (gpe 25)
[4294672.473000] ACPI: Power Resource [PFAN] (off)
[4294672.473000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294672.473000] pnp: PnP ACPI init
[4294672.480000] pnp: PnP ACPI: found 11 devices
[4294672.480000] PnPBIOS: Disabled by ACPI PNP
[4294672.480000] PCI: Using ACPI for IRQ routing
[4294672.480000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294672.482000] pnp: 00:06: ioport range 0x3810-0x381f has been reserved
[4294672.482000] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[4294672.482000] pnp: 00:06: ioport range 0x8000-0x805f could not be reserved
[4294672.482000] pnp: 00:06: ioport range 0x4d6-0x4d6 has been reserved
[4294672.483000] Simple Boot Flag at 0x36 set to 0x1
[4294672.484000] audit: initializing netlink socket (disabled)
[4294672.484000] audit: initialized
[4294672.484000] VFS: Disk quotas dquot_6.5.1
[4294672.484000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294672.484000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294672.484000] devfs: boot_options: 0x0
[4294672.484000] Initializing Cryptographic API
[4294672.484000] Limiting direct PCI/PCI transfers.
[4294672.484000] Activating ISA DMA hang workarounds.
[4294672.484000] isapnp: Scanning for PnP cards...
[4294672.839000] isapnp: No Plug & Play device found
[4294672.892000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[4294672.904000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.905000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.905000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294672.906000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.910000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.911000] io scheduler noop registered
[4294672.911000] io scheduler anticipatory registered
[4294672.911000] io scheduler deadline registered
[4294672.911000] io scheduler cfq registered
[4294672.912000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.916000] EISA: Probing bus 0 at eisa.0
[4294672.916000] Cannot allocate resource for EISA slot 1
[4294672.916000] Cannot allocate resource for EISA slot 3
[4294672.916000] Cannot allocate resource for EISA slot 8
[4294672.916000] EISA: Detected 0 cards.
[4294672.916000] NET: Registered protocol family 2
[4294672.927000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294672.927000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294672.928000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.928000] TCP: Hash tables configured (established 16384 bind 16384)
[4294672.928000] NET: Registered protocol family 8
[4294672.928000] NET: Registered protocol family 20
[4294672.928000] ACPI wakeup devices:
[4294672.928000] SBTN  USB  LAN COM1
[4294672.928000] ACPI: (supports S0 S1 S3 S4 S5)
[4294672.929000] Freeing unused kernel memory: 224k freed
[4294672.951000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.988000] vga16fb: initializing
[4294672.988000] vga16fb: mapped to 0xc00a0000
[4294673.058000] Console: switching to colour frame buffer device 80x30
[4294673.058000] fb0: VGA16 VGA frame buffer device
[4294674.232000] Capability LSM initialized
[4294674.264000] NET: Registered protocol family 1
[4294674.310000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294674.310000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294674.310000] ACPI: bus type ide registered
[4294674.321000] ALI15X3: IDE controller at PCI slot 0000:00:0f.0
[4294674.321000] ACPI: PCI Interrupt 0000:00:0f.0[A]: no GSI
[4294674.321000] ALI15X3: chipset revision 196
[4294674.321000] ALI15X3: not 100% native mode: will probe irqs later
[4294674.321000]     ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:DMA, hdb:pio
[4294674.321000]     ide1: BM-DMA at 0x1008-0x100f, BIOS settings: hdc:DMA, hdd:pio
[4294674.321000] Probing IDE interface ide0...
[4294674.585000] hda: HTS424030M9AT00, ATA DISK drive
[4294675.197000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294675.197000] Probing IDE interface ide1...
[4294675.869000] hdc: TOSHIBA DVD-ROM SD-C2502, ATAPI CD/DVD-ROM drive
[4294676.481000] ide1 at 0x170-0x177,0x376 on irq 15
[4294676.481000] Probing IDE interface ide2...
[4294676.994000] Probing IDE interface ide3...
[4294677.507000] Probing IDE interface ide4...
[4294678.020000] Probing IDE interface ide5...
[4294678.543000] hda: max request size: 128KiB
[4294678.562000] hda: 58605120 sectors (30005 MB) w/1739KiB Cache, CHS=16383/255/63, UDMA(33)
[4294678.562000] hda: cache flushes supported
[4294678.562000]  /dev/ide/host0/bus0/target0/lun0: p1 p3
[4294678.674000] hdc: ATAPI 24X DVD-ROM drive, 128kB Cache
[4294678.674000] Uniform CD-ROM driver Revision: 3.20
[4294679.811000] Attempting manual resume
[4294679.837000] swsusp: Suspend partition has wrong signature?
[4294679.915000] usbcore: registered new driver usbfs
[4294679.915000] usbcore: registered new driver hub
[4294679.917000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294679.918000] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 9
[4294679.918000] PCI: setting IRQ 9 as level-triggered
[4294679.918000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKU] -> GSI 9 (level, low) -> IRQ 9
[4294679.918000] ohci_hcd 0000:00:02.0: ALi Corporation USB 1.1 Controller
[4294679.918000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[4294679.918000] ohci_hcd 0000:00:02.0: irq 9, io mem 0xfff70000
[4294679.971000] hub 1-0:1.0: USB hub found
[4294679.971000] hub 1-0:1.0: 2 ports detected
[4294680.123000] Linux Tulip driver version 1.1.13 (May 11, 2002)
[4294680.123000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294680.123000] PCI: setting IRQ 11 as level-triggered
[4294680.123000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294680.124000] tulip0:  MII transceiver #1 config 1000 status 786d advertising 01e1.
[4294680.129000] eth0: ADMtek Comet rev 17 at 00018c00, 00:D0:59:7B:5D:45, IRQ 11.
[4294680.160000] usb 1-2: new low speed USB device using ohci_hcd and address 2
[4294682.190000] usbcore: registered new driver hiddev
[4294682.199000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.0-2
[4294682.199000] usbcore: registered new driver usbhid
[4294682.199000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294683.427000] ACPI: Fan [FAN] (off)
[4294683.435000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294683.435000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294683.440000] ACPI: Thermal Zone [THRM] (65 C)
[4294683.758000] Attempting manual resume
[4294683.780000] swsusp: Suspend partition has wrong signature?
[4294683.838000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294683.838000] EXT3-fs: write access will be enabled during recovery.
[4294686.384000] kjournald starting.  Commit interval 5 seconds
[4294686.384000] EXT3-fs: hda1: orphan cleanup on readonly fs
[4294686.384000] ext3_orphan_cleanup: deleting unreferenced inode 1192269
[4294686.384000] ext3_orphan_cleanup: deleting unreferenced inode 1192263
[4294686.384000] EXT3-fs: hda1: 2 orphan inodes deleted
[4294686.384000] EXT3-fs: recovery complete.
[4294686.408000] EXT3-fs: mounted filesystem with ordered data mode.
[4294688.066000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294694.792000] Adding 578332k swap on /dev/hda3.  Priority:-1 extents:1
[4294695.206000] EXT3 FS on hda1, internal journal
[4294705.182000] parport: PnPBIOS parport detected.
[4294705.182000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294705.282000] lp0: using parport0 (interrupt-driven).
[4294705.363000] mice: PS/2 mouse device common for all mice
[4294706.394000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[4294706.411000] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[4294707.029000] ts: Compaq touchscreen protocol output
[4294710.559000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294711.940000] cdrom: open failed.
[4294715.266000] Linux agpgart interface v0.101 (c) Dave Jones
[4294715.291000] agpgart: Detected ALi M1647 chipset
[4294715.327000] agpgart: AGP aperture is 64M @ 0xf0000000
[4294715.823000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294715.858000] shpchp: shpc_init : shpc_cap_offset == 0
[4294715.858000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294716.230000] Linux Kernel Card Services
[4294716.230000]   options:  [pci] [cardbus] [pm]
[4294716.269000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294716.270000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294716.270000] Yenta: CardBus bridge found at 0000:00:04.0 [103c:0018]
[4294716.270000] Yenta: Enabling burst memory read transactions
[4294716.270000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294716.270000] Yenta: Routing CardBus interrupts to PCI
[4294716.270000] Yenta TI: socket 0000:00:04.0, mfunc 0x009c1b22, devctl 0x66
[4294716.491000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294716.491000] Socket status: 30000006
[4294716.538000] ACPI: PCI Interrupt 0000:00:04.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294716.538000] Yenta: CardBus bridge found at 0000:00:04.1 [103c:0018]
[4294716.538000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294716.538000] Yenta: Routing CardBus interrupts to PCI
[4294716.538000] Yenta TI: socket 0000:00:04.1, mfunc 0x009c1b22, devctl 0x66
[4294716.759000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294716.759000] Socket status: 30000006
[4294717.242000] ali15x3_smbus 0000:00:06.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[4294717.242000] ali15x3_smbus 0000:00:06.0: ALI15X3 not detected, module not inserted.
[4294717.890000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[4294717.890000] PCI: setting IRQ 5 as level-triggered
[4294717.890000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294721.850000] Real Time Clock Driver v1.12
[4294722.061000] input: PC Speaker
[4294722.573000] Floppy drive(s): fd0 is 1.44M
[4294722.587000] FDC 0 is a post-1991 82077
[4294725.650000] NET: Registered protocol family 10
[4294725.651000] Disabled Privacy Extensions on device c02eb280(lo)
[4294725.651000] IPv6 over IPv4 tunneling driver
[4294727.346000] 0000:00:10.0: tulip_stop_rxtx() failed
[4294727.346000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[4294727.811000] ACPI: AC Adapter [AC] (on-line)
[4294727.921000] ACPI: Battery Slot [BAT0] (battery present)
[4294727.973000] ACPI: Power Button (FF) [PWRF]
[4294727.973000] ACPI: Lid Switch [LID]
[4294727.973000] ACPI: Sleep Button (CM) [SBTN]
[4294728.265000] ibm_acpi: ec object not found
[4294728.574000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294735.937000] eth0: no IPv6 routers present
[4294743.862000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294743.862000] apm: overridden by ACPI.
[4294746.256000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x207 0x408-0x40f 0x480-0x48f
[4294746.260000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x207 0x408-0x40f 0x480-0x48f
[4294746.264000] cs: IO port probe 0xc00-0xcf7: clean.
[4294746.265000] cs: IO port probe 0xc00-0xcf7: clean.
[4294746.267000] cs: IO port probe 0xa00-0xaff: clean.
[4294746.268000] cs: IO port probe 0xa00-0xaff: clean.
[4294746.862000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[4294746.867000] Detected 900.252 MHz processor.
[4294746.879000] powernow: No PST tables match this cpuid (0x770)
[4294746.879000] powernow: This is indicative of a broken BIOS.
[4294746.879000] powernow: Trying ACPI perflib
[4294746.879000] powernow: Minimum speed 500 MHz. Maximum speed 900 MHz.
[4294747.693000] Bluetooth: Core ver 2.7
[4294747.693000] NET: Registered protocol family 31
[4294747.693000] Bluetooth: HCI device and connection manager initialized
[4294747.693000] Bluetooth: HCI socket layer initialized
[4294747.809000] Bluetooth: L2CAP ver 2.7
[4294747.809000] Bluetooth: L2CAP socket layer initialized
[4294747.878000] Bluetooth: RFCOMM ver 1.5
[4294747.878000] Bluetooth: RFCOMM socket layer initialized
[4294747.878000] Bluetooth: RFCOMM TTY layer initialized
[4295479.545000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[4295522.300000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295522.300000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295522.421000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295522.421000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295522.524000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295522.524000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295522.610000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295522.610000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
david@David-Linux:~$

```

And correct, I do have a wired Ethernet Adapter. Thats what i'm using now.

---

### Post by carlosqueso on 2005-12-09
hmmm....you're on your own with that one....maybe post your quesiton again in the Networking forum with the name of your card as the title, and the lspci and dmesg outputs in the post....it doesn't seem to even be recognizing when your card is put in.

---

### Post by Spikey.Lozenge on 2005-12-09
[QUOTE=carlosqueso]hmmm....you're on your own with that one....maybe post your quesiton again in the Networking forum with the name of your card as the title, and the lspci and dmesg outputs in the post....it doesn't seem to even be recognizing when your card is put in.[/QUOTE]

Eh, I got the card and Laptop(!!) For free, so I guess you can't complain about one of them not working. ^_^  Thanks for all the help!

---


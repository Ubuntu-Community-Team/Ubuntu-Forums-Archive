---
title: "Installation of software (not from repository)"
date: 2005-07-28
forum: Desktop Environments
---

### Post by Aijaz Akhtar on 2005-07-28
Sorry for this looooong post with lot many error pastings.

Well as I was advised here, I used dpkg to install Grass6.0 and XFCE (deb packages) but failed. I am pasting all error messages here, the dpkg gave this (TravelDrive is my USB stick, and the deb packages were available in the root folder itself) and later I tried after copying the deb files to HDD too in Home directory.

root@ubuntu:/media/TRAVELDRIVE # dpkg -i grass_6.0.0-1_i386.deb
dpkg: error processing grass_6.0.0-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 grass_6.0.0-1_i386.deb
(arg: 1)

Use `dpkg' to install and remove packages from your system, or
`dselect' for user-friendly package management.  Packages unpacked
using `dpkg-deb --extract' will be incorrectly installed !

So I tried dselect:

root@ubuntu:/media/TRAVELDRIVE # dselect install  grass_6.0.0-1_i386.deb
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Do you want to erase any previously downloaded .deb files? [Y/n]
dselect: unknown action string `grass_6.0.0-1_i386.deb'

And through some help screen, I got another option of using aptitude to install packages, then I got this:

root@ubuntu:/media/TRAVELDRIVE # aptitude -f install grass_6.0.0-1_i386.deb
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "grass_6.0.0-1_i386.deb"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

After copying the files from the USB drive to the home folder: And this is with XFCE

root@ubuntu:/home/aijaz # aptitude -f install xfce_3.8.18-2ubuntu1_i386.deb
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "xfce_3.8.18-2ubuntu1_i386.deb"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

So let me be guided again in details as to how to install these packages. Also what is the difference between dpkg, dselect and aptitude? Unfortunately â€“h for all commands in bash are inadequate and I feel that it is one of the most minus point for any Linux distro, the un-understandable, vague and un-user friendly help.

Double clicking shows the deb file content all right (to prove that the files are downloaded properly), if I copy the contents of different directories of the package to the mentioned directories (say etc content to my etc director), will it get installed?? And above all, even if there are no symbolic links (or short cuts in Win lingo) created, I know that typing grass60 in any console would start grass, but will XFCE work this way, that is will I be able to select XFCE as my desktop environment in my log in screen.
Similarly will I be able to add KDE or IceWM that I always prefer over gome. Though Ubuntu is really faster than all distros even with the slow gnome, I prefer KDE, XFCE and icewm.

---

### Post by codejunkie on 2005-07-28
[QUOTE=Aijaz Akhtar]Sorry for this looooong post with lot many error pastings.

Well as I was advised here, I used dpkg to install Grass6.0 and XFCE (deb packages) but failed. I am pasting all error messages here, the dpkg gave this (TravelDrive is my USB stick, and the deb packages were available in the root folder itself) and later I tried after copying the deb files to HDD too in Home directory.

root@ubuntu:/media/TRAVELDRIVE # dpkg -i grass_6.0.0-1_i386.deb
dpkg: error processing grass_6.0.0-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 grass_6.0.0-1_i386.deb
(arg: 1)

Use `dpkg' to install and remove packages from your system, or
`dselect' for user-friendly package management.  Packages unpacked
using `dpkg-deb --extract' will be incorrectly installed !

So I tried dselect:

root@ubuntu:/media/TRAVELDRIVE # dselect install  grass_6.0.0-1_i386.deb
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Do you want to erase any previously downloaded .deb files? [Y/n]
dselect: unknown action string `grass_6.0.0-1_i386.deb'

And through some help screen, I got another option of using aptitude to install packages, then I got this:

root@ubuntu:/media/TRAVELDRIVE # aptitude -f install grass_6.0.0-1_i386.deb
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "grass_6.0.0-1_i386.deb"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

After copying the files from the USB drive to the home folder: And this is with XFCE

root@ubuntu:/home/aijaz # aptitude -f install xfce_3.8.18-2ubuntu1_i386.deb
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "xfce_3.8.18-2ubuntu1_i386.deb"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

So let me be guided again in details as to how to install these packages. Also what is the difference between dpkg, dselect and aptitude? Unfortunately â€“h for all commands in bash are inadequate and I feel that it is one of the most minus point for any Linux distro, the un-understandable, vague and un-user friendly help.

Double clicking shows the deb file content all right (to prove that the files are downloaded properly), if I copy the contents of different directories of the package to the mentioned directories (say etc content to my etc director), will it get installed?? And above all, even if there are no symbolic links (or short cuts in Win lingo) created, I know that typing grass60 in any console would start grass, but will XFCE work this way, that is will I be able to select XFCE as my desktop environment in my log in screen.
Similarly will I be able to add KDE or IceWM that I always prefer over gome. Though Ubuntu is really faster than all distros even with the slow gnome, I prefer KDE, XFCE and icewm.[/QUOTE]

to install grass_6.0.0-1_i386.deb you just do this place it in your home dir then 
```
sudo dpkg -i grass_6.0.0-1_i386.deb
``` from the terminal aptitude is just another front end for apt-get and if the package is not in the repo it cant be installed with apt-get, aptitude, or synaptic so if you downloaded and want to install .deb files that are not in the repo  this should work but if you get any errors during the install just do ```
sudo apt-get -f upgrade
``` this will download and upgrade packages that it needs to complete the install.

---

### Post by heimo on 2005-07-28
Ok, I don't know your earlier posts, but is there a reason why you're installing using dpkg and not synaptic or apt-get? :) dpkg is low level package installer and apt-get is much friendlier command line frontend, dselect is text based frontend and synaptic is full graphical, very friendly system to install most of the software that's available in Ubuntu repositories.

To install xfce, I'd enter sudo apt-get install xfce4 (or what ever the package name is). You can also try the synaptic package manager which can be found in one of the menus in Gnome.

Installing single packages using dpkg is rarely what you want to do. Extracting the files from package and copying to directories is very, very rarely what you want to do - packages do much more than just carry the files - they configure and packaging system maintains information of the software that's installed on your system.

---

### Post by Aijaz Akhtar on 2005-07-28
I use internet on a mobile phone and hence am forced to use WinXP for internet. Thus under Linux, I cannot be connected to ubuntu server. Thats the need to download packages thru WinXP, and use CD/ USB to install in the Linux FS.

---

### Post by heimo on 2005-07-28
Ok. So - I assume you've already checked that these packages weren't on the Ubuntu install cd. To me, your dpkg syntax looks ok. You could try to copy the file from USB memory to hard disk (maybe dpkg doesn't like fat filesystem for some reason, unlikely), simple dpkg -i [packagename] should do, just as you tried.

You may need to get many more packages to satisfy dependencies (other packages needed by those two), so what I'd try first would be to get that mobile connection working (of course you know better if that's possible). I had gprs connection on my Linux laptop, worked very nicely over serial connection. (wasn't quite easy to setup, I think it was Debian Woody)

Where did you get those deb-packages? Was it Ubuntu-repository?

You can use this search to find dependencies beforehand.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Aijaz Akhtar on 2005-07-29
1. I will try sudo dpkg today and let you know. But to me sudo is just equivalent to super user log in, and I am lready logged in as super user (through Root console giving my password).
2. Does that mean that if there are some dependency problems, no software can be installed when I am off line??
And I had already copied the deb file (that I DID download from debian site link) from the USB to home folder.
And now I find that the only plus point for the Ubuntu is it that is is faster despite the gnome. As I do not join the people who go ga ga over the ease of installation of software. RPMs can be installed at least with shell scripts, and many can be just uncompressed or unzipped and might work, if I am right. That is the way I succeeded in installing Grass in Mandrake 10.1 with RPMs, and running rpm -i in console (or at times adding -force) or with tar.gz file and runing the shell script.

---

### Post by heimo on 2005-07-29
1. Yes - sudo is "super user do", you need to install packages as root (no difference how you achieve it)

2. You can install deb packages offline, just as you can install rpm packages offline. And you can still use .tar.gz packagad binaries (compiled for platform) or compile yourself from sources, if installing deb-packages fails for you

You can use force -flags to force installing deb -packages, but that doesn't change the fact that you still (probably) want to satisfy dependencies.

>(that I DID download from debian site link)

Debian site? How about Ubuntu-site? Some deb-packages packaged for Debian won't work in Ubuntu (which does use debian packaging, but those packages are made specifically for Ubuntu). This can be confusing - maybe I just misread what you mean with the text abowe, but I'm just trying to help you solve this problem, not argue.

You probably want to check this [font=Arial][size=2][color=Black]"[/color][/size][/font][font=Arial][size=2][color=Black]**Unofficial Ubuntu 5.04 Add-On CD"**[/color][/size][/font]
[http://ubuntuforums.org/showthread.php?t=30147](http://ubuntuforums.org/showthread.php?t=30147)

Cheers!

---

### Post by lol on 2005-07-29
> dpkg -i grass_6.0.0-1_i386.deb 
dpkg: error processing grass_6.0.0-1_i386.deb (--install): cannot access archive: No such file or directory 
Errors were encountered while processing: grass_6.0.0-1_i386.deb 

you use the command dpkg -i *filename* when you need to install a package that is not in the repository, and that you previously downloaded (filename MUST be a .deb file). For example, you would need to do this if you want to install Opera. First you download the .deb package from the web site, then use dpkg -i to install it.

>  dselect install grass_6.0.0-1_i386.deb 
Reading package lists... Done 
Building dependency tree... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Do you want to erase any previously downloaded .deb files? [Y/n] 
dselect: unknown action string `grass_6.0.0-1_i386.deb'

dselect is an apt frontend, just like synaptic, it's not a command. So if you want to use it (that my favorite btw), you just start it with the command dselect, without any arguments. Then to install a package, you go in "select", you search your package, mark it for installation with "+" and then use "install" to install it. You don't have to previously download the package (dselect is going to do it for you) but you can only install packages from the repository this way.

aptitude is more or less the same, I wouldn't recommand to use it the way you tried, but if you really want to, you need to give it the name of a package, not the name of a file. Be sure to make the distinction between:
grass_6.0.0-1_i386.deb => this is a filename
grass => this is the name of the corresponding package

When you install with dpkg -i, you give the name of the file (that you downloaded) containing the package, but if you want to remove the package using dpkg -r, you need to give the package name this time!

If you need more help with those tool, try reading the man pages... It seems "un-friendly", but it is usually a good way to start.

---

### Post by kagashe on 2005-07-29
[QUOTE=Aijaz Akhtar]I use internet on a mobile phone and hence am forced to use WinXP for internet. Thus under Linux, I cannot be connected to ubuntu server. Thats the need to download packages thru WinXP, and use CD/ USB to install in the Linux FS.[/QUOTE]
Who says you can't use  internet on a mobile phone on Linux?

What is the make of mobile phone and who is your ISP?

kagashe

---

### Post by johanvdw on 2005-07-29
I was able to install grass by using one of the debian repositories:

Edit /etc/apt/sources.list as root and append the following line:

```
deb http://ftp.be.debian.org/debian/ unstable main contrib non-free
```

afterwards, enter 
```
sudo apt-get update
```
in the console.

Now Grass Gis can be found in the package list from synaptic/kynaptic. Or you might as well enter

```
sudo apt-get install grass grass-doc
```

In both cases all dependencies are looked after automatically. 

You can try the same for xfce. I didn't try that myself. But the correct packagename is xfce4 .

After adding grass gis and eventually xfce4, it is best to edit your sources.list again and a dash in front of the debian repository and run ```
sudo apt-get update
``` again: otherwise it may be used instead of the ubuntu repository for some packages.

---

### Post by johanvdw on 2005-07-29
BTW: you need an internetconnection to use the method I outlined. But I really recommend doing it this way. Grass is too complex and has too many dependencies to be resolved to install directly using dpkg.

---

### Post by Aijaz Akhtar on 2005-08-01
My question itself is installation WITHOUT repo, through saving in a HDD or a CDROM (not Ubuntu CD). here is the latest from my side, again a loooong post with all pastings:

sudo dpkg seemed to work as it attempted to install Grass, but showed dependency problem and listed a no. of lib files not installed. I had rpms of all these files. But then it said, cannot install rpm packages. Use alien instead.
What is this alien? It said read readme debian file. etc etc.
Then I selected sudo apt-get -f upgrade
It now REMOVED Grass!! 
Here is the pasting:


Reading package lists... Done

Building dependency tree... Done

Correcting dependencies... Done

The following packages will be REMOVED:
  
grass

The following NEW packages will be installed:
 tcl8.3

0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or 

removed.

Need to get 0B/870kB of archives.

After unpacking 9830kB disk space will be freed.

Do you want to continue [Y/n]?

Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release 

i386 (20050407)'
in the drive '/cdrom/' and press enter


I placed the Ubuntu CD promptly , then ...............


Preconfiguring packages ...
(Reading database ... 59107 files and directories currently 

installed.)

Removing grass ...

Selecting previously deselected package tcl8.3.
(Reading database ... 58445 files and directories currently installed.)

Unpacking tcl8.3 (from .../tcl8.3/tcl8.3_8.3.5-4_i386.deb) 
...
Setting up tcl8.3 (8.3.5-4) ...



I then ran sudo apt-get again, here is what I got:

root@ubuntu:/home/aijaz # sudo apt-get -f 

upgrade


Reading package lists... 0%
Reading package lists... 0%
Reading package lists... 11%

Reading package lists... Done

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... Done


0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@ubuntu:/home/aijaz #


For XFCE, I got this:

Selecting previously deselected package xfce.
(Reading database ... 58562 files and 

directories currently installed.)

Unpacking xfce (from xfce_3.8.18-2ubuntu1_i386.deb) ...

dpkg: dependency problems prevent configuration of xfce:
 xfce depends on libgdk-pixbuf2 

(>= 0.22.0-4ubuntu2); however:
  Package libgdk-pixbuf2 is not installed.

 xfce depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 
xfce depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
 
xfce depends on xfce-common (>= 3.8.18-1); however:
  Package xfce-common is not 

installed.

dpkg: error processing xfce (--install):
 dependency problems - leaving unconfigured

Errors were encountered while processing:
 xfce

root@ubuntu:/home/aijaz #




So where I go from here?? I installed this Debian package as many people said that it is the easiest to install a software in a Debian package and specially so in Ubuntu. But I only succeeded in mandrake so far, and in no other distro, I couild install a SINGLE software!! In fact if you ask me, Ubuntu is the fastest yet worst distro. It even does not allow to rename a file, or copy the file name, Control C does nowhere work, and you have always to select the text (in console or file manager, file properties), and right clicking only copies. This is really a matter of shame that this one of the most popular short cut key is not implemented in 
Ubuntu.

Aijaz
PS
I saved this file in Gedit but there the pasting seemed all right, In WinXP, notepad, all para settings have changed. Had to edit, may be some lines could not get edited properly.

---

### Post by Aijaz Akhtar on 2005-08-02
I forgot to add that I am from India. My mobile phone is a CDMA, handset is LG 5130, and the service is by reliance Infocom. They do provide some Linux drivers for some handsets, that they say work on Redhat 8 and 9, but 5130 is not included in that and I failed. Even otherwise, the speed is generally so low that I never venture downloading any file more than 1 MB.

---

### Post by kagashe on 2005-08-02
[QUOTE=Aijaz Akhtar]I forgot to add that I am from India. My mobile phone is a CDMA, handset is LG 5130, and the service is by reliance Infocom. They do provide some Linux drivers for some handsets, that they say work on Redhat 8 and 9, but 5130 is not included in that and I failed. Even otherwise, the speed is generally so low that I never venture downloading any file more than 1 MB.[/QUOTE]If you are using Ubuntu 5.04 this will work for you:
> To Connect to Internet using Reliance Phone (any)
with Fedora core 3

Create a file in /etc/wvdial.conf

1.file:/etc/wvdial.conf

[Modem0]
Modem= /dev/ttyACM0
Baud= 115200
SetVolume=0
DialCommand= ATDT
FlowControl= Hardware(CRTSCTS)
[Dialer R]
Username= my phone number
Password= my phone number
Phone= #777
Stupid Mode= 1
Inherits= Modem0

2. edit following file as follow

file:/etc/resolv.conf

service named start
nameserver 202.138.103.100
nameserver 202.138.96.2
nameserver 127.0.0.1

3. change Mobile\settings\phone\datarate = 115200

4. now to dial to Internet we need to follow these things

5. Connect Mobile to system using a USB cable
6. login as root
7. type following command

modprobe uhci
modprobe usbserial
modprobe ftdi_sio
wvdial R

I have copied the above from the following post on rimweb.com
[http://www.rimweb.com/forums/index.php?showtopic=3656](http://www.rimweb.com/forums/index.php?showtopic=3656)

It is working for me in Ubuntu 5.04 on GTran GC4020 handset but I am sure it will work for your handset as well. I don't understand why the modprobe commands are required but I used them for the first time as per instructions. One command may also give an error message, ignore it. I used sudo for these commands as login as root was not possible for the first time only. Next time I just opened a terminal and typed "wvdial R" and it works fine. Speed is no problem. I checked it at:
[http://testmy.net/](http://testmy.net/) and found OK.

rimweb.com is a nice community for Reliance Infocom and please ignore whatever is written on Reliance Infocom web site.

kagashe

---

### Post by johanvdw on 2005-08-02
[QUOTE=Aijaz Akhtar]My question itself is installation WITHOUT repo, through saving in a HDD or a CDROM (not Ubuntu CD). here is the latest from my side, again a loooong post with all pastings:[/quote]
I'm sorry for my first reaction. I didn't know that it was so difficult to use internet in your situation.> 

sudo dpkg seemed to work as it attempted to install Grass, but showed dependency problem and listed a no. of lib files not installed. I had rpms of all these files. But then it said, cannot install rpm packages. Use alien instead.
You should get compatible packages for these files.
First of all, run "sudo dpkg -i dpkg -i grass_6.0.0-1_i386.deb"
It will give dependency problems for some packages.

Check this page:
[http://packages.ubuntu.com/breezy/science/grass](http://packages.ubuntu.com/breezy/science/grass)

here you can click on each of these packages and download the file on the page that will show up.

It is complicated, but it works.
---

But maybe before you do the whole effort of installing GRASS: what kind of GIS work are you planning to do? Vector GIS or Raster GIS? Do you really have to use Grass?

Grass GIS is a very powerful program, but is hard to use. If you just want to learn about GIS or want to do mostly raster-GIS operations Saga GIS may be a better option.
[http://www.saga-gis.uni-goettingen.de/html/index.php](http://www.saga-gis.uni-goettingen.de/html/index.php)
It has an excellent manual:
[link](http://www.saga-gis.uni-goettingen.de/html/modules.php?op=modload&name=Sections&file=index&req=viewarticle&artid=4&page=1)


An advantage may also be the size: you need to download only some 6MB. Downloading the additional packages for grass gis will be about 40 MB. 

I've created a ubuntu/debian archive for personal use that I can send to you if you are interested. I tested it on 2 pc's using Ubuntu hoary and it worked fine.

---

### Post by Aijaz Akhtar on 2005-08-07
To ask me frankly I'd say Ubuntu is the MOST USDER UNFRIENDLY distro I have encountered.
Now you (K Agashe, thanks friend) suggested RIM connectivity that worked with FEDORA. I've already tried MODPROBE getting some tip somewhere, AND THIS COMAND IS NOT IN UBUNTU. I tried again. I opened Gedit, created the file but it did not allow me to save since I cannot log in as root unless it is a console. And how the hell I can save a file in Console???? However, with totally no hope, I attempted to type gedit in console and SURPRISINGLY, Gedit opened, though it gace gnomeui authenntication error or some thing in console.  I saved wvdial.conf file this way.
Next I opened /etc/resolv.conf in gedit. The file was present but it was blank. I added the said lines and saved. 
Then you mentioned:
change Mobile\settings\phone\datarate = 115200
But where?????
And then came the dreaded modprobe and promptly it displayed:
FATAL: Module uhci not found.
Next I ran modprobe usbserial, and this did not give errors.
Next: modprobe ftdi_sio too seemed to work.
But the next wvdialR gave this error:
root@ubuntu:/home/aijaz # wvdialR
Said Command not found (as expected)
Repeating that with wvdial R, I found:

WvDial: Internet dialer version 1.54.0
Warning: section [Dialer R] does not exist in wvdial.conf.
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directory

Now coming to GRASS, no, I myself may not be using it directly. But I am ESTABLISHING a FOSS Lab and have to make Grass to work where people can work on maps of our department Geological Survey of India. The geological maps, hard copies are scanned, and these RASTER have to be digitised/vectorised and saved as Arc files, in fact now planned to be made available on GSI portal (through Oracle database and some map server) As the work load is heavy and only one or two Arc GIS licenses at each headquarters, we plan to use open source GIS, and I am supposed to be the person fiddling with Tux since 1998 off and on. At other headquarters Grass is working with Mandrake and PCQLinux (FC3), or they have succeeded with trial and error. When on many forums, I heard the raves about Ubuntu, I attempted this.

and QUOTE:

I've created a ubuntu/debian archive for personal use that I can send to you if you are interested. I tested it on 2 pc's using Ubuntu hoary and it worked fine.

What did that mean, I could not comprehend. By Archive, do you mean some sort of repository?? That is another hated word for me now.

I am sure going to remove the Ubuntu partition.  IT HAS GREATLY DISAPPOINTED ME.

---

### Post by johanvdw on 2005-08-07
[QUOTE=Aijaz Akhtar]To ask me frankly I'd say Ubuntu is the MOST USDER UNFRIENDLY distro I have encountered.
[/quote]

>  And how the hell I can save a file in Console???? However, with totally no hope, I attempted to type gedit in console and SURPRISINGLY, Gedit opened, though it gace gnomeui authenntication error or some thing in console.  I saved wvdial.conf file this way.
That's the way to go. Logging into X (graphical userinterface) as a root is always a bad idea. Open a console and you can launch apps as a root by typing "sudo appname".
eg 'sudo gedit'. Probably some error-like lines will come in the console. It may seem that there are errors, but this almost always happens when you launch an app using the console.

I will not comment on any of the problems you had to connect to the internet, because I don't know anything about it.
> 
Now coming to GRASS, no, I myself may not be using it directly. But I am ESTABLISHING a FOSS Lab and have to make Grass to work where people can work on maps of our department Geological Survey of India. The geological maps, hard copies are scanned, and these RASTER have to be digitised/vectorised and saved as Arc files, in fact now planned to be made available on GSI portal (through Oracle database and some map server) As the work load is heavy and only one or two Arc GIS licenses at each headquarters, we plan to use open source GIS, and I am supposed to be the person fiddling with Tux since 1998 off and on. At other headquarters Grass is working with Mandrake and PCQLinux (FC3), or they have succeeded with trial and error. 
In that case I guess Grass may be a good choice. The biggest problem with grass Gis is the steep learning curve. But if you have to do repetitive work, and someone from the other hq's can give instructions, it guess it should work well.

Just in case you really have too much problems installing the whole system: ILWIS is a non-free windows GIS system which has good support for digitizing maps. I used it a lot myself when making my MSc thesis (soil mapping in Ethiopia). It is relatively cheap for a GIS program (i guess about $100) and a free 30-day trial version can be found on their website. I don't have any idea what you budget/... is, but I just wanted to share the information.
[http://www.itc.nl/ilwis/default.asp](http://www.itc.nl/ilwis/default.asp)
information about digitizing indian topomaps in Ilwis:
[http://www.itc.nl/~rossiter/docs/GIS_India_7_3.pdf](http://www.itc.nl/~rossiter/docs/GIS_India_7_3.pdf)

Anyway, the SAGA-GIS program which I mentioned earlier is not that good for digitizing.
> 
I am sure going to remove the Ubuntu partition.  IT HAS GREATLY DISAPPOINTED ME.
Well, I feel sorry for you. Installing Grass GIS on Mandrake of Fedora will need the same steps as installing it in kubuntu. In both cases dependencies will have to be solved and you will need to download and install different packages.

Considering the internetconnection I cannot judge ofcourse. But when administrating linux with whichever distribution you will run into similar problems once. I wouldn't give up too quick.

Anyway, good luck!

---

### Post by kagashe on 2005-08-07
[QUOTE=Aijaz Akhtar]To ask me frankly I'd say Ubuntu is the MOST USDER UNFRIENDLY distro I have encountered.
Now you (K Agashe, thanks friend) suggested RIM connectivity that worked with FEDORA.[/quote]RIM connectivity is working in Ubuntu 5.04. I am using it every day. Incidentally, I had to reinstall Ubuntu 5.04 today once again and this is how I proceeded. I ignored all modprobe commands and only made my wvdial.conf file as follows:
> I typed following command in the terminal:
sudo gedit /etc/wvdial.conf
It produced an empty file and I pasted the following
[Modem0]
Modem= /dev/ttyACM0
Baud= 115200
SetVolume=0
DialCommand= ATDT
FlowControl= Hardware(CRTSCTS)
[Dialer R]
Username= my phone number
Password= my phone number
Phone= #777
Stupid Mode= 1
Inherits= Modem0
Then I connected the mobile to the USB port and typed the following in the terminal:> wvdial Rand it worked.
> Mobile\settings\phone\datarate = 115200This is Baud rate setting in the mobile instrument.
> WvDial: Internet dialer version 1.54.0
Warning: section [Dialer R] does not exist in wvdial.conf.
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directoryAfter properly saving wvdial.conf file Dialer R is automatically set up.

kagashe

---

### Post by Aijaz Akhtar on 2005-08-11
Will try again. Sorry. My landline connection too went off and whenever I accessed net outside, this forum site never loaded.

---

### Post by DW5 on 2005-09-05
Problem installing Grass 6
 
I want to bump this thread, and see if I can finish getting Grass 6 installed properly.     I'm a bit of a newbie still, so bear with me. 

Background (skip down to real problem)

 I decided to try out all the GNU GIS software available in my newly adopted operating system.  I installed qgis and grass 5x via synaptic and jgrass and saga from their websites. I piddled with them all.  Grass does indeed have a steep learning curve and so had linux, that's why I quit even looking at it 5 years ago. I had been using Manifold for my GIS in windows (price is an issue, hence not ArcX).  I thought QGIS had some promise, but I wanted to be able to import a geotiff, and couldn't figure that out.  Same with Saga.  So I thought, hmm what if QGIS run from w/n Grass could do this (as suggested on the grass website).  While reading about this on the Grass site, I noticed that the grass project has a new stable release Grass 6 and that it had a Debian package, but when I went to install it I noticed that that it wasn't available via synaptic and apt-get (still grass 5x).  

Problem

So, I downloaded the Grass 6 package and tried to install it via dpkg -i.  There's lots of output below for the curious, but the short of it is this: Dpkg -i failed saying that there were several dependencies that needed to be installed (as indicated in a post in this thread), so I apt-get installed them.  

All worked well until I needed to install libgrass.  It failed because it depends upon grass, and grass is not installed because it depends upon libgrass.  ](*,) 

I do understand that the purpose of synaptic installs is to avoid this kindof issue and make intallation easy.  But, alas, now I'm into it. How do I work around this problem?  Maybe its not a problem, maybe it's commonsense but my newness to linux makes it seem like a problem.   Thanks for the help.

Outputs below. 

```
dwilliam@DUUbuntu:~/Desktop$ dpkg -i grass_6.0.0-1_i386.deb
dpkg: requested operation requires superuser privilege
dwilliam@DUUbuntu:~/Desktop$ sudo dpkg -i grass_6.0.0-1_i386.deb
(Reading database ... 118458 files and directories currently installed.)
Preparing to replace grass 5.0.3-5.1 (using grass_6.0.0-1_i386.deb) ...
Unpacking replacement grass ...
dpkg: dependency problems prevent configuration of grass:
 grass depends on proj (>= 4.4.1-1); however:
  Package proj is not installed.
 grass depends on tcl8.3 (>= 8.3.5); however:
  Package tcl8.3 is not installed.
 grass depends on tk8.3 (>= 8.3.5); however:
  Package tk8.3 is not installed.
 grass depends on libgrass; however:
  Package libgrass is not installed.
dpkg: error processing grass (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grass
dwilliam@DUUbuntu:~/Desktop$ sudo apt-get install proj
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  grass: Depends: tcl8.3 (>= 8.3.5) but it is not going to be installed
         Depends: tk8.3 (>= 8.3.5) but it is not going to be installed
         Depends: libgrass but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dwilliam@DUUbuntu:~/Desktop$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  proj tcl8.3 tk8.3
Suggested packages:
  proj-ps-doc tclreadline
The following packages will be REMOVED:
  grass
The following NEW packages will be installed:
  proj tcl8.3 tk8.3
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 2039kB of archives.
After unpacking 5825kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 ftp://mirror.mcs.anl.gov hoary/main tcl8.3 8.3.5-4 [870kB]
Get:2 ftp://mirror.mcs.anl.gov hoary/main tk8.3 8.3.5-4 [788kB]
Get:3 ftp://mirror.mcs.anl.gov hoary/universe proj 4.4.9-1 [381kB]
Fetched 2039kB in 21s (94.5kB/s)

Preconfiguring packages ...
(Reading database ... 115404 files and directories currently installed.)
Removing grass ...
Selecting previously deselected package tcl8.3.
(Reading database ... 114742 files and directories currently installed.)
Unpacking tcl8.3 (from .../tcl8.3_8.3.5-4_i386.deb) ...
Selecting previously deselected package tk8.3.
Unpacking tk8.3 (from .../tk8.3_8.3.5-4_i386.deb) ...
Selecting previously deselected package proj.
Unpacking proj (from .../archives/proj_4.4.9-1_i386.deb) ...
Setting up tcl8.3 (8.3.5-4) ...

Setting up tk8.3 (8.3.5-4) ...

Setting up proj (4.4.9-1) ...

dwilliam@DUUbuntu:~/Desktop$ sudo dpkg -i grass_6.0.0-1_i386.deb
Selecting previously deselected package grass.
(Reading database ... 115016 files and directories currently installed.)
Unpacking grass (from grass_6.0.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of grass:
 grass depends on libgrass; however:
  Package libgrass is not installed.
dpkg: error processing grass (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grass
dwilliam@DUUbuntu:~/Desktop$ sudo apt-get -f install libgrass
Reading package lists... Done
Building dependency tree... Done
Package libgrass is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgrass has no installation candidate
```

So I found libgrass 6 and downloaded it.


```
dwilliam@DUUbuntu:~/Desktop$ sudo dpkg -i libgrass_6.0.0-1_i386.deb
Selecting previously deselected package libgrass.
(Reading database ... 115679 files and directories currently installed.)
Unpacking libgrass (from libgrass_6.0.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of libgrass:
 libgrass depends on grass; however:
  Package grass is not configured yet.
dpkg: error processing libgrass (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgrass

```

Now, how to get one to install, so that the other will (seems like maybe libgrass should install first, and then grass, but what do I know)?

DW

---

### Post by lol on 2005-09-06
dpkg -i --force-depends *package name* 

have a look at 'dpkg --help' and 'dpkg --force-help'

---

### Post by DW5 on 2005-09-06
That did it.  Thanks loads.  This is the great thing about a rich user community--great support, and I learn something new everyday.  Hopefully at some point, I'll be savvy enough to help back.

DW

---


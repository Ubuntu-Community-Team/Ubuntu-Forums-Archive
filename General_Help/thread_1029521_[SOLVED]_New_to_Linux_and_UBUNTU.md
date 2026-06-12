---
title: "[SOLVED] New to Linux and UBUNTU"
date: 2009-01-03
forum: General Help
---

### Post by AJExtreme on 2009-01-03
Hello fellow peoples.

I am new to the entire Linux experience.  I have always used Windows and finally trying to switch over from the Microsoft Monopoly.  I have used Windows based software and OS since 97. I thought I was pretty good until I got into Linux, and now I feel like it is the first time I have looked at computer.  Kind of like Neo in the 1st Matrix first using his eyes.

I have a PC system with AMD64 3200+ with Epson NX300 Printer. Thus far I really enjoy UBUNTU 8.10 64bit. So far I have not run into any real problems with the exception of getting my printer install.

As earlier stated I know nothing of Linux,  got through my first install cause it was basically automated.  I can get by on everything as is for now but, I really need to get my printer working as soon as possible.  

I don't know how to go about trying new drivers from websites. I don't even know where to begin cause I don't understand the terminology, the file system, or the programing for Linux.  I am fast at learning computers, so if someone could help I would really appreciate it.  At least enough to help me get my printer going for now.

Right now when I connect the printer it comes up recognises the printer as the Epson NX300, but then uses the driver for Epson DX8450.  But when I print a test page it doesn't print anything it just starts rolling paper through until it runs out of paper and when I print from open office nothing happens.

Again Thank you for any help in advance and sorry for the long first post. 

AJ

---

### Post by gettinoriginal on 2009-01-03
Here is a site to get you started, welcome to ubuntu, and enjoy.  :popcorn:

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by teaker1s on 2009-01-03
avasys which is epson list a driver for your printer
[URL="http://avasys.jp/hp/page000001300/hpg000001251.htm"]http:
//avasys.jp/hp/page000001300/hpg000001251.htm[/URL]
select allinone on left tab and nx300 is listed.
select ubuntu as os if you have 32 bit system, if 64bit your need some help and post back machine spec

---

### Post by albinootje on 2009-01-03
> **AJExtreme said:**
> 
Right now when I connect the printer it comes up recognises the printer as the Epson NX300, but then uses the driver for Epson DX8450.


Here it says it is supported :
[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300)

However in my Ubuntu 8.10 I don't see it under Epson Stylus NX300.
It's possible that you only need to find a ppd file for it, and import that.

---

### Post by gettinoriginal on 2009-01-03
And here is one that might help with your printer, it is for a different model, but hopefully it will help:

[http://ubuntuforums.org/showthread.php?t=599673](http://ubuntuforums.org/showthread.php?t=599673)

---

### Post by AJExtreme on 2009-01-03
Thanks Tweaker1s I downloaded all the files.  But am unsure what to do with them. They are on my desktop.  I also have a 64 bit system, Would that effect the use of those files?  I am ready to move to the next step of doing something with them I think...LOL..I Hope..

Thanks albinootje,  I saw that it says compatible,  I want to try to find the ppd file and import it but I have not idea on how to or even what a ppd file, I mean guess it is for managing the hardware, but how do I get it and import it. 

I am trying to understand about terminal, I am guessing it is basically like DOS, but I have not used DOS is a lot of years.  and it is hard when I don't really understand the file structure let a lone the commands.  I want to learn it all but right now I just need to get my printer...  I was going to dual boot, so I didn't lose function until I understood more, but I screwed my Windows in the process of installing Linux.

I really appreciate you all helping get me through this issue.

---

### Post by teaker1s on 2009-01-03
Okay we can try to install the 32 bit deb on 64bit open terminal
Applications>Accessories>terminal

```
sudo apt-get install libc6-i386 ia32-libs lib32asound2 util-linux
```

```
sudo dpkg -i &#8211;force-architecture nameofpackage.deb
```

Failing that I can extract ppd file for you

---

### Post by AJExtreme on 2009-01-03
Tweaker  I went to terminal, i put the first code in, and it is doing a lot of stuff.. Pertty cool.  I don't know for sure what is going on, but guessing it is installing something... that is cool! After it finishes doing this then do I still put the second code in..  do i copy and paste or do i put the name of package in?  What is name of package.

---

### Post by teaker1s on 2009-01-03
what I've done is told your computer to download and install 32bit compatibility libraries in first command.

You should find the package you downloaded from avasys on your desktop with extension .deb 

second command you need to replace nameofpackage.deb with the package name you downloaded and leave the .deb extension on end-we have told package manager to ignore the fact that it's 386 and we will try to use compatibility libaries to provide compatibility with 64bit

If this fails then tell me if your using hardy or ibex and I'll get the ppd for you to try.

---

### Post by AJExtreme on 2009-01-03
I tried putting that in but it will not take, it  I get the following message

Photo Image Print System Lite
This software is a filter program used with Common UNIX Printing System (CUPS) from the Linux. This can supply the high quality print with Seiko Epson Color Ink Jet Printers.
This product supports only Epson ESC/P-R printers. Its function is same as Photo Image Print System. Unlike Photo Image Print System, which requires different pakage for each printer model, only one pipslite package can be used for all Epson ESC/P-R printers.
For detail list of supported printer, please refer to our Web page: [http://avasys.jp/](http://avasys.jp/) 

This is a copy of my terminal reading for the last entree

aaron@aaron-desktop:~$ sudo dpkg -i &#8211;force-architecture pipslite_1.3.0-2_i386.deb
[sudo] password for aaron: 
dpkg: error processing &#8211;force-architecture (--install):
 cannot access archive: No such file or directory
dpkg: error processing pipslite_1.3.0-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 &#8211;force-architecture
 pipslite_1.3.0-2_i386.deb
aaron@aaron-desktop:~$

---

### Post by teaker1s on 2009-01-03
Okay just tried that myself and even when in correct directory it complains about miss match.
 we could try installing ppd file for it. 32 to 64bit forcing in this case won't play.



Attached the ppd from the deb package, download and double click, then select extract, you should have a ppd file appear on desktop, point printer wizard to the ppd file and hopefully the 32 bit ppd file will work

---

### Post by AJExtreme on 2009-01-03
I got i installed it and I got a missing driver message below

Printer 'Stylus-NX300' requires the 'pipslite-wrapper' program but it is not currently installed.  Please install it before using this printer.

What is this program, where do I get it?
At least it seems we are getting somewhere..

---

### Post by teaker1s on 2009-01-03
have tried to make the source from the avasys site, It will configure and make but fails on install. Therefore my best advice would be to see if you can use a similar model as a driver
[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300]("http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300")

you will need 64 bit and 3.2 I believe
[http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-amd64/openprinting-gutenprint_5.2.2-1lsb3.2_amd64.deb]("http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-amd64/openprinting-gutenprint_5.2.2-1lsb3.2_amd64.deb")
download double click on package and install. on printer wizard select gluten print as you driver

---

### Post by albinootje on 2009-01-03
> **AJExtreme said:**
>  I saw that it says compatible,  I want to try to find the ppd file and import it but I have not idea on how to or even what a ppd file, I mean guess it is for managing the hardware, but how do I get it and import it. 

I've downloaded from this webpage :
[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300](http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300)
this file :
[http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-gutenprint_5.2.2-1lsb3.2_i386.deb](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-i386/openprinting-gutenprint_5.2.2-1lsb3.2_i386.deb)
and from that file i've extracted two ppd files for the NX300.

I'll attach those two files here archived as a tar file.
Download that file, and open it, and extract the two ppd files.

In the printer administration interface it should be possible to choose them as drivers.

You can actually choose "new printer", and then "provide ppd file".
Can you try one of them with that method ?

---

### Post by AJExtreme on 2009-01-03
What is an rpd file?

Here is a link I have been trying to figure out what all it is tying to tell me to do.  I believe you would know more of what it is trying to say.

[http://www.linuxfoundation.org/en/OpenPrinting/Database/DriverPackages](http://www.linuxfoundation.org/en/OpenPrinting/Database/DriverPackages)
[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300)

Both of these are some of what I have been trying to make sense of.

---

### Post by teaker1s on 2009-01-03
rpm is a redhat install package that can be forced to install, problem is that it's 32bit also. Have found an alternative driver for the printer mentioned in my previous post

---

### Post by AJExtreme on 2009-01-03
I got a missing driver error on the ppd file below:

Printer 'Stylus-NX300' requires the '/opt/OpenPrinting-Gutenprint/cups/lib/filter/commandtoepson' program but it is not currently installed.  Please install it before using this printer.

When I clicked the link it downloaded something then I got this following message:

Gutenprint - Top Quality Printer Drivers
A very high quality package of printer drivers for Ghostscript and CUPS, mainly for Epson inkjet printers, but also for inkjets from Canon and HP, dye sublimation photo printers, and PCL laser printers.
(Converted from a rpm package by alien version 8.64.) 

I have downloaded some rpm packages but I don't know what to do with them and it won't let me open them.

---

### Post by teaker1s on 2009-01-03
Have tried to make the source from the avasys site, It will configure and make but fails on install. Therefore my best advice would be to see if you can use a open printing gluten print nx300 model as a driver

[http://www.openprinting.org/show_pri...n-Stylus_NX300]("http://www.openprinting.org/show_pri...n-Stylus_NX300")

you will need 64 bit and 3.2 I believe
[http://www.openprinting.org/download...b3.2_amd64.deb]("http://www.openprinting.org/download...b3.2_amd64.deb")
download double click on package and install. on printer wizard select gluten print as your driver

---

### Post by AJExtreme on 2009-01-03
Are any of the following files anything I may need, these are all the files I have downloaded.  Am I able to delete any or all of these files from my desktop once all is figured out or should i be putting these in a different location other than my desk top.

gutenprint-5.2.3.tar.bz2
gutenprint-5.0.1-1lsb3.1.x86_64.rpm
pipslite-1.3.0-2.i386.rpm
pipslite_1.3.0-2_i386.deb
pipslite_1.3.0-2.tar.gz
cups-1.3.9-source.tar.bz2
pipslite_1.3.0-2.dsc
pipslite_1.3.0-2_i386.changes
eklite.ppd.tar.gz
eklite.ppd
openprinting-splix-1.1.1-5lsb3.2.x86_64.rpm
NX300 has 2 ppd files in it.

---

### Post by AJExtreme on 2009-01-03
How do I install an rpm file or extract it?

When I click on them they say they are unsupported?  Do I need to install another program to gain access to that type of file.

---

### Post by teaker1s on 2009-01-03
[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300]("http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX300")

[http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-amd64/openprinting-gutenprint_5.2.2-1lsb3.2_amd64.deb]("http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/main/binary-amd64/openprinting-gutenprint_5.2.2-1lsb3.2_amd64.deb")

try now

---

### Post by AJExtreme on 2009-01-03
How do I utilize the rpm file?

It is installing the eb file now, I hope this works!!!

---

### Post by AJExtreme on 2009-01-03
WOW WHOOOO HOOOOOO Thanks you so much I finally have print capabilities....  AT Last You are all totally awesome... I can't thank you enough!!!

Can I delete all this stuff off my desktop or am I stuck with it there.  i am making backup copies of all this stuff before I delete anything though...  I don't know what that last link you posted was but I was then able to access the rpm files and get to the ppd files inside and at last my printer works... 

Thanks again to all three of you and you especially Tweaker1s.  I couldn't have got hear with out you.  

How do I report as solved?

Aaron

---

### Post by teaker1s on 2009-01-03
you can delete all the files from desktop as it should be installed, book mark the links for future reference. 

if you select thread tools you should be able to mark as solved

---

### Post by nukeqler on 2009-05-21
For what it's worth:

I went out and bought an Epson NX-300 based on the report here that it could be made to work.  For me, with 64-bit Jaunty, it worked without installing anything else (at least the printing part, haven't tested the scanning yet).  So hopefully anyone who is using Jaunty will read this thread to the end and not bother downloading anything before trying the printer.

Cheers, and thanks to the folks who got this working before.

---


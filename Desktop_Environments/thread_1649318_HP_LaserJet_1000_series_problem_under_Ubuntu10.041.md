---
title: "HP LaserJet 1000 series problem under Ubuntu10.04/10.10"
date: 2010-12-20
forum: Desktop Environments
---

### Post by anant_crp on 2010-12-20
[COLOR=blue][FONT=Arial]Posted by[/FONT][/COLOR]
[COLOR=blue][FONT=Arial]ANANTREDDY, Corporate IS & IT, ITI Ltd,Doorvaninagar Bangalore, INDIA,[/FONT][/COLOR]
[COLOR=blue][FONT=Arial]E-Mail: [EMAIL="anant_crp@itiltd.co.in"]anant_crp@itiltd.co.in[/EMAIL],[/FONT][/COLOR]
 
 
[FONT=Arial][COLOR=blue]**_[COLOR=#ff6600][FONT=Arial]Troubleshooting the HP LJ 1000 series printers under UBUNTU[/FONT][/COLOR]_**
 
**_[COLOR=fuchsia][FONT=Arial]Introduction:[/FONT][/COLOR]_**
[SIZE=3][COLOR=#000000][FONT=Arial]This guide is for [/FONT][FONT=Arial]configuring [/FONT][FONT=Arial]the HP LaserJet 1000[/FONT][FONT=Arial] series printers on Ubuntu[/FONT][FONT=Arial]. The printers I'm aware of th[/FONT][FONT=Arial]ose which [/FONT][FONT=Arial]are likely to [/FONT][FONT=Arial]give problems[/FONT][FONT=Arial] are the LaserJet 1000, 1005, 1018, 1020, P1005, P1006, P1007, P1008, and P1505.[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Arial]These printers have always been a bit problematic, and with recent CUPS versions have become even more problematic. I've been investigating the problem becau[/FONT][FONT=Arial]se some[/FONT][FONT=Arial] LaserJet 10[/FONT][FONT=Arial]0[/FONT][FONT=Arial]0 [/FONT][FONT=Arial]series printers have [/FONT][FONT=Arial]stopped working[/FONT][FONT=Arial] with Ubuntu[/FONT][FONT=Arial]. In the process I've found many people on the Internet reporting similar problems, so this [/FONT][FONT=Arial]document[/FONT][FONT=Arial] is intended to [/FONT][FONT=Arial]guide[/FONT][FONT=Arial] people [/FONT][FONT=Arial]who [/FONT][FONT=Arial]are likely to encounter[/FONT][FONT=Arial] such problems, with[/FONT][FONT=Arial] solutions.[/FONT][FONT=Arial] This[/FONT][FONT=Arial] covers [/FONT][FONT=Arial]installing [/FONT][FONT=Arial]firmware (plug-in)[/FONT][FONT=Arial] & [/FONT][FONT=Arial]foo2zjs drivers[/FONT][FONT=Arial] for printing with CUPS in Ubuntu[/FONT][FONT=Arial]. [/FONT][/COLOR][/SIZE]
**_[COLOR=fuchsia][FONT=Arial]Overview:[/FONT][/COLOR]_**
[SIZE=3][COLOR=#000000][FONT=Arial]There are three things that need to happen in order to print [/FONT][FONT=Arial]using [/FONT][FONT=Arial]one of these printers.[/FONT][/COLOR][/SIZE]
[COLOR=#000000][FONT=Arial][SIZE=3]1.[/SIZE] [/FONT][SIZE=3][FONT=Arial]The firmware [/FONT][FONT=Arial](plug-in) [/FONT][FONT=Arial]must be loaded onto the printer. In order to decrease the cost of the hardware, these printers don't include the memory to store the firmware while powered off, so every time they are powered on[/FONT][FONT=Arial],[/FONT][FONT=Arial] the firmware has to be copied over from your computer.[/FONT][/SIZE][/COLOR]
[COLOR=#000000][FONT=Arial][SIZE=3]2.[/SIZE] [/FONT][SIZE=3][FONT=Arial]CUPS must detect the printer. This may happen automatically, or you may use CUPS tools to detect available printers. If the printer isn't detected, something is wrong.[/FONT][/SIZE][/COLOR]
[COLOR=#000000][FONT=Arial][SIZE=3]3.[/SIZE] [/FONT][SIZE=3][FONT=Arial]A document has to be sent to the printer. I won't say anything more about this, because I've never encountered an issue with it. The problems are typically in the first two steps.[/FONT][/SIZE][/COLOR]
**_[COLOR=fuchsia][FONT=Arial]Solution:[/FONT][/COLOR]_**
[FONT=Arial][COLOR=#000000][SIZE=3]After various attempts to install HP LaserJet 1000 Series Printers under Ubuntu, printing does not happen. Installation seems OK; printer is added, but no communication is established with Ubuntu machine. Finally we succeeded after following the below procedures.[/SIZE][/COLOR][/FONT]
[COLOR=black][FONT=Arial][SIZE=3]1.[/SIZE] [/FONT][/COLOR][FONT=Arial][SIZE=3][COLOR=#000000]As soon as you **power ON** the above said series printer it will ask for a proprietary [/COLOR][COLOR=blue]HPLIP-3.v.v[/COLOR][COLOR=#000000] plug-in (firmware). HPLIP version depends on the printer model. The required plug-in can be downloaded to the system by opening a terminal & Executing the following.[/COLOR][/SIZE][/FONT]
[SIZE=3][FONT=Arial][COLOR=#000000]# [/COLOR][/FONT][/SIZE][FONT=Arial][COLOR=#000000][SIZE=2][COLOR=blue][FONT=Arial]wget [/FONT][/COLOR][FONT=Arial][COLOR=blue]http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/ hplip-3.10.6-plugin.run[/COLOR][/FONT][/SIZE][/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]Note: hplip-3.10.6 is the example. Version gets changed depending on the printer.There is No space after ( / ). [/COLOR][/FONT]
[COLOR=black][FONT=Arial][SIZE=3]2.[/SIZE] [/FONT][/COLOR][FONT=Arial][SIZE=3][COLOR=#000000]When the pop-up window asks for firmware (plug-in) just enter [/COLOR][COLOR=blue]&#8216;p&#8217;[/COLOR][COLOR=#000000] to specify the path of [/COLOR][COLOR=blue]HPLIP-3.v.v[/COLOR][COLOR=#000000] plug-in location. Normally it will be in [/COLOR][COLOR=blue]root. [/COLOR][COLOR=black]So enter [/COLOR][COLOR=blue]/root. [/COLOR][COLOR=black]The plug-in will be installed.[/COLOR][/SIZE][/FONT]
[COLOR=black][FONT=Arial][SIZE=3]3.[/SIZE] [/FONT][/COLOR][FONT=Arial][SIZE=3][COLOR=#000000]To build the essentials type the following: #[/COLOR][COLOR=blue] apt-get install build-essential.[/COLOR][/SIZE][/FONT]
[COLOR=black][FONT=Arial][SIZE=3]4.[/SIZE] [/FONT][/COLOR][SIZE=3][FONT=Arial][COLOR=#000000]Then get the foo2zjs drivers: [/COLOR][/FONT][/SIZE]
[SIZE=3][FONT=Arial][COLOR=#000000][COLOR=black]#[/COLOR][/COLOR][COLOR=blue] [SIZE=2]wget -O foo2zjs.tar.gz [/SIZE][/COLOR][/FONT][COLOR=blue][FONT=Arial][SIZE=2]http://foo2zjs.rkkda.com/foo2zjs.tar.gz[/SIZE][/FONT][/COLOR][/SIZE]
[COLOR=black][FONT=Arial][SIZE=3]5.[/SIZE] [/FONT][/COLOR][SIZE=3][COLOR=black][FONT=Arial]Unpack gunzip file #[/FONT][/COLOR][COLOR=blue][FONT=Arial] tar -zxvf foo2zjs.tar.gz[/FONT][/COLOR][/SIZE]
[COLOR=black][FONT=Arial][SIZE=3]6.[/SIZE] [/FONT][/COLOR][SIZE=3][COLOR=black][FONT=Arial]Go to the foo2zjs directory : # [/FONT][/COLOR][COLOR=blue][FONT=Arial]cd foo2zjs[/FONT][/COLOR][/SIZE]
[COLOR=black][FONT=Arial][SIZE=3]7.[/SIZE] [/FONT][/COLOR][SIZE=3][COLOR=black][FONT=Arial]The default Ubuntu drivers should be uninstalled: #[/FONT][/COLOR][COLOR=blue][FONT=Arial] make[/FONT][/COLOR][COLOR=blue][FONT=Arial]uninstall[/FONT][/COLOR][/SIZE]
[COLOR=black][FONT=Arial][SIZE=3]8.[/SIZE] [/FONT][/COLOR][SIZE=3][COLOR=black][FONT=Arial]Compile & Install drivers: #[/FONT][/COLOR][COLOR=blue][FONT=Arial] make[/FONT][/COLOR][COLOR=blue][FONT=Arial]install[/FONT][/COLOR][COLOR=black][FONT=Arial] # [/FONT][/COLOR][COLOR=blue][FONT=Arial]./getweb 1000 OR other printer, e.g. 1020[/FONT][/COLOR][/SIZE]
[COLOR=black][FONT=Arial][SIZE=3]9.[/SIZE] [/FONT][/COLOR][SIZE=3][COLOR=black][FONT=Arial]Install hot plug (for HP LJ 1000/1005/1018/1020/P100[5678]/P1505): # [/FONT][/COLOR][COLOR=blue][FONT=Arial]make install install-hotplug cups[/FONT][/COLOR][/SIZE]
[FONT=Arial][COLOR=#000000]Then re-install the printer from [/COLOR]***[COLOR=blue]System >> Administration >> Printing and then Printer >> Add Printer. [/COLOR]***[COLOR=#000000]You have to choose the drivers with appropriate[/COLOR]***[COLOR=blue] HPLIP version plug-in, [/COLOR]****[COLOR=black]b[/COLOR]*[COLOR=black]ecause[/COLOR]*[COLOR=black]d[/COLOR]*[COLOR=#000000]efault [/COLOR][COLOR=blue]foomatic driver[/COLOR][COLOR=#000000] won&#8217;t work sometime. If everything goes fine printer will work fine[/COLOR][/FONT][COLOR=#000000][FONT=Times New Roman][FONT=Thorndale AMT]. [/FONT][/FONT][/COLOR]
 
[/COLOR][/FONT]

---

### Post by dulinux on 2010-12-25
It did not work for my 10.04 installation.

This, instead, has worked just fine:

[http://ubuntuforums.org/showpost.php?p=7454475&postcount=6](http://ubuntuforums.org/showpost.php?p=7454475&postcount=6)

Thanks

---

### Post by anant_crp on 2011-01-01
> **dulinux said:**
> It did not work for my 10.04 installation.
 
Thanks
 
The same response I had from Christ University & asking me to give the brief method. I gave them mail with brief procedures, Here are the mail responses.. 
 
 
*[FONT=Arial]-------- Original Message --------[/FONT]*
*[FONT=Arial]Subject: hp laserjet1000 series[/FONT]*
*[FONT=Arial]Date: Wed, 29 Dec 2010 10:56:52 +0530[/FONT]*
*[FONT=Arial]From: joshy TL <tljoshy@christuniversity.in>[/FONT]*
*[FONT=Arial]To: [EMAIL="anant_crp@itiltd.co.in"]anant_crp@itiltd.co.in[/EMAIL][/FONT]*
 
*[FONT=Arial]Hello,[/FONT]*
 
*[FONT=Arial]I have seen your solution for the above said problem but it is not working from our side. Kindly give us solution in a very brief method[/FONT]*
 
*[FONT=Arial]with warm new year greetings[/FONT]*
 
*[FONT=Arial]joshy[/FONT]*
*[FONT=Arial]for christ university[/FONT]*
 
[FONT=Arial][SIZE=3]I had replied to the above mail by giving them brief steps to follow. Below is my reply.[/SIZE][/FONT]
 
*[FONT=Arial]-------- Original Message --------[/FONT]*
*[FONT=Arial]Subject: Re: hp laserjet1000 series[/FONT]*
*[FONT=Arial]Date: Wed, 29 Dec 2010 12:19:09 +0530[/FONT]*
*[FONT=Arial]From: Anantreddy <anant_crp@itiltd.co.in>[/FONT]*
*[FONT=Arial]Reply-To: [EMAIL="anant_crp@itiltd.co.in"]anant_crp@itiltd.co.in[/EMAIL][/FONT]*
*[FONT=Arial]Organization: ITI Ltd[/FONT]*
*[FONT=Arial]To: joshy TL <tljoshy@christuniversity.in>[/FONT]*
 
*[FONT=Arial]Hi ,[/FONT]*
*[FONT=Arial]As soon as you power ON the Printer usually these series printers will ask for Plug-ins (firmware). Firmware version depends on the Printer. Ex: 1000, 1020 etc., Version it will display for you. You can download the plug-in from the site what I have mentioned in the solution. After that you follow the procedure mentioned in the document. Foo2zjs driver should be downloaded & follow the procedure for compilation & installation.[/FONT]*
 
*[FONT=Arial]My solution what I have uploaded is experimented at our end & all hplj1000 series printers are working fine with Ubuntu 10.04/10.10.[/FONT]*
 
*[FONT=Arial]Thanks regards[/FONT]*
*[FONT=Arial]Anant[/FONT]*
[FONT=Arial][SIZE=3]-------------------------------------------------------------------------------------------------------------------[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]2nd mail from Christ University,[/SIZE][/FONT]
 
*[FONT=Arial]-------- Original Message --------[/FONT]*
*[FONT=Arial]Subject: 2011 greetings[/FONT]*
*[FONT=Arial]Date: Sat, 1 Jan 2011 10:07:15 +0530[/FONT]*
*[FONT=Arial]From: joshy TL <tljoshy@christuniversity.in>[/FONT]*
*[FONT=Arial]To: [EMAIL="anant_crp@itiltd.co.in"]anant_crp@itiltd.co.in[/EMAIL][/FONT]*
 
*[FONT=Arial]Hai ,[/FONT]*
*[FONT=Arial]Thanks for the mail and it worked.[/FONT]*
 
*[FONT=Arial]We all from Christ university wish u and [/FONT]**[FONT=Arial]ur[/FONT]**[FONT=Arial] team a very happy 2011[/FONT]*
 
*[FONT=Arial]With warm regards[/FONT]*
*[FONT=Arial]Joshy[/FONT]*
 
finally it wokred..
 
Anant

---

### Post by dukebytes on 2011-02-26
I just had to add this for anyone else who bought a cheap wallyworld HP printer for 29 bucks and thought it would work fine with their ubu box....

I have done the above and several other things...  nothing worked for me, urls didnt work, webget couldnt find things etc... I did not get my printer to print once.

So I added everything I could find foo related thru the package manager and tried one last time.  Once again nothing.

So I deleted the printer and readded it and used the HP Deskjet 990c hpijs, 3.10.2 driver instead of the 1000c and it works fine.  I have printed several docs and it looks OK.

So if you dont want to go thru a lot of "stuff" just add foo stuff thru PM and then pick the 990....  it might just work for ya.

Duke

---

### Post by anant_crp on 2011-02-28
*[FONT=Arial]Hi ,[/FONT]*
*[FONT=Arial]As soon as you power ON the Printer usually these series printers will ask for Plug-ins (firmware). Firmware version depends on the Printer. Ex: 1000, 1020 etc., Version it will display for you. You can download the plug-in from the site what I have mentioned in the solution. After that you follow the procedure mentioned in the document. Foo2zjs driver should be downloaded & follow the procedure for compilation & installation.[/FONT]*
 
*[FONT=Arial]My solution what I have uploaded is experimented at our end & all hplj1000 series printers are working fine with Ubuntu 10.04/10.10. Try the procedures once again & get back to me.[/FONT]*
*[FONT=Arial][/FONT]* 
*[FONT=Arial]Anant[/FONT]*
 
> **dukebytes said:**
> I just had to add this for anyone else who bought a cheap wallyworld HP printer for 29 bucks and thought it would work fine with their ubu box....
 
I have done the above and several other things... nothing worked for me, urls didnt work, webget couldnt find things etc... I did not get my printer to print once.
 
So I added everything I could find foo related thru the package manager and tried one last time. Once again nothing.
 
So I deleted the printer and readded it and used the HP Deskjet 990c hpijs, 3.10.2 driver instead of the 1000c and it works fine. I have printed several docs and it looks OK.
 
So if you dont want to go thru a lot of "stuff" just add foo stuff thru PM and then pick the 990.... it might just work for ya.
 
Duke

---

### Post by etitor on 2011-03-07
Hi anant_crp.

As many other people, I am experiencing repeated problems getting my HP 1018 working with Ubuntu 10.10.

Your guide is near perfection and I thank you very much for it.

However, would you be so kind as to consider rewriting it so as to clearly separate the one-time activity involved (e.g., driver compilation) from the each-time-you-turn-on-printer activity?

I mean, reading your guide gives the impression that every time you turn on the printer, you have to download from the web and compile drivers. I sincerely hope this is not the case, because that would make me simply return the printer and exchange it for another one.

Thanks in advance!

---

### Post by anant_crp on 2011-03-09
Dear Member,
You need not download the firmware each time when you restart the printer. This only requires at the first time. Becoz the 1000 series printers don't have much memory to load the firmware (plugin) softwares. So as soon as you switch ON (first fime) after plugging in it will display you the massage to load the firmwares. The related firmware what we load will be installed on UBUNTU System. The printer will take these firmwares from the system each time when you restart. So you need not download the firmware every time.
 
Thanks & regards
Anant
 
> **etitor said:**
> Hi anant_crp.
 
As many other people, I am experiencing repeated problems getting my HP 1018 working with Ubuntu 10.10.
 
Your guide is near perfection and I thank you very much for it.
 
However, would you be so kind as to consider rewriting it so as to clearly separate the one-time activity involved (e.g., driver compilation) from the each-time-you-turn-on-printer activity?
 
I mean, reading your guide gives the impression that every time you turn on the printer, you have to download from the web and compile drivers. I sincerely hope this is not the case, because that would make me simply return the printer and exchange it for another one.
 
Thanks in advance!

---

### Post by mardibai on 2011-03-26
dear anant_crp,

i have ubuntu 10.04 and i'm trying to install a hp laserjet 1020 printer as you described above. 
i'm installing the required plug-in with the program "hp device manager". 
but it doesn't work when i arrive to the step in which he asks me to download the plugin from the internet. so i downloaded before the plug-in and after tried to install it giving the program the path, but it seems to do not respond.
i tried installing the hplip 3.10.2 with the terminal but it doesn't worx as well ... 
may be there is a problem in the printer?

Thank you for helping, i'm an ubuntu beginner!

---


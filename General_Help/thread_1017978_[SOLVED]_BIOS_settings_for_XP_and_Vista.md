---
title: "[SOLVED] BIOS settings for XP and Vista"
date: 2008-12-21
forum: General Help
---

### Post by Jammanuser on 2008-12-21
Hello all. I know this isn't directly related to Ubuntu, and I apologize...but it seems i'm having trouble with the BIOS on a dual boot (well...technically, a **triple** boot, since I also have Ubuntu 8.10) of Vista and XP. Vista was pre-installed, and XP was installed later, as a dual boot with Vista. 

My problem is, when i want to boot into XP, if I was Vista last, I have to **first** change my SATA hard drive controller settings. I change the operating mode from AHCI (which works for Vista, but doesn't work for XP) to ATA (which in **turn** works for XP, but doesn't work for Vista!)...:) So you can see why this is annoying, because every single time I want to boot into the other OS, no matter which one it is, I have to change the BIOS each time, or i get a BSOD! :lolflag: **Also**, before I can change that setting, if I was in Vista last, I have to first disable my Flash Cache Module, and then boot into XP...and once I want to boot into Vista, I have to **re-enable** it, and then change the SATA controller setting again to be AHCI, instead of ATA...:rolleyes:

Does anyone know a workaround or fix for this?

Thanks in advance! :)

-Jam man

:guitar:

---

### Post by logos34 on 2008-12-21
Either reinstall XP and insert (F6) sata drivers on floppy, or else slipstream into a new XP install cd image:

[http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation](http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation)

You could also reinstall Vista in IDE compatibility/legacy/emulation sata mode.  The problem is Vista (and Ubuntu of course) has native support for sata storage drivers, Xp doesn't

---

### Post by Jammanuser on 2008-12-21
> **logos34 said:**
> Either reinstall XP and insert (F6) sata drivers on floppy, or else slipstream into a new XP install cd image:

[http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation](http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation)

You could also reinstall Vista in IDE compatibility/legacy/emulation sata mode.  The problem is Vista (and Ubuntu of course) has native support for sata storage drivers, Xp doesn't

Thanks for the reply. :) I don't want to reinstall either one, though...Vista OR XP, because of all the recent hassle that I have had, just getting it to correctly boot into XP! :lolflag:

But wouldn't it be possible to just get the SATA drivers, and install it on XP, without reinstalling the whole OS? And if so, where would I get them?

Thanks! ):P

-Jam man

:guitar:

---

### Post by logos34 on 2008-12-21
AFAIK you can't install the sata drivers from the desktop--they have to either be put in before the installation begins or be included in the cd iso. 

Check your HDD manufacturer for driver downloads

---

### Post by Jammanuser on 2008-12-21
> **logos34 said:**
> AFAIK you can't install the sata drivers from the desktop--they have to either be put in before the installation begins or be included in the cd iso. 

Check your HDD manufacturer for driver downloads

hmm...I'll have to test it then, to see I can install the SATA drivers from my XP desktop! :) Because I **really** do not want to have to reinstall XP...:lolflag:

Thanks! :popcorn:

-Jam man

:guitar:

---

### Post by logos34 on 2008-12-21
> **Jammanuser said:**
> hmm...I'll have to test it then, to see I can install the SATA drivers from my XP desktop! :) Because I **really** do not want to have to reinstall XP...:lolflag:

well, good luck because I don't think there's a way other than by floppy F6 as you would with RAID drivers--that's the whole point of slipstreaming:
> 
 Step 3: Add your RAID/SATA Drivers

We’re now ready to add RAID/SATA controller drivers to our CD (if you don’t want to do this, skip ahead to the final step). Open the folder to which you copied your Windows XP CD (C:xpsetupcd) and create a subfolder called $OEM$. Then, create a subfolder of $OEM$ called $1 and a subfolder of $1 called drivers. The resulting path should be C:xpsetupcd$OEM$$1drivers. This is where Windows Setup will look for drivers that aren’t contained in its standard driver library. For organizational purposes, make a subfolder within drivers named for the type of driver it will contain—for instance, create a RAID folder for RAID drivers or an SATA folder for Serial ATA drivers. You can use any name, as long as it has fewer than eight characters.

With the aforementioned folder structure in place, copy the Windows XP RAID/SATA drivers directly into the folder you created above (we used C:xpsetupcd$OEM$$1driversRAID). If your drivers came in a self-extracting executable rather than a zip file, you may be able to extract its contents manually by opening it in a program like WinRAR. (Alternately, you can run the self-extracting executable, then dig around in your system’s TEMP directory—usually C:/documents and settings/YourUsername/LocalSettings/Temp until you find the right directory). Finally, locate the SYS file for your RAID/SATA controller from among the files you just extracted; it should be named after your specific controller (e.g. fasttx2k.sys for a Promise FastTrak TX2 RAID controller). The drivers for different operating systems may be split into distinct folders, so make sure you find the SYS file that’s intended for Windows XP. Once you find the SYS file, copy it to the i386 folder of your Windows CD (C:xpsetupcdi386).

**[COLOR="Red"]Adding RAID or Serial ATA drivers to your Windows CD will save you the trouble of using a floppy disc to manually install them every time you reformat.[/COLOR]** 

[http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation?page=0%2C1](http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation?page=0%2C1)

---

### Post by Jammanuser on 2008-12-21
> **logos34 said:**
> well, good luck because I don't think there's a way other than by floppy F6 as you would with RAID drivers--that's the whole point of slipstreaming:

Ok...so would it be possible then to simply place the SATA drivers on a floppy, and then push F6 at bootup of XP? Of course i don't have a floppy drive right now...but i was planning to buy an **external** one soon, that's compatible with Vista, and I should be able to use it for that! ;)

Cheers! ):P

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-21
I collect information like you are looking for because it might
come in handy with a customer. There are some people who just
dual boot XP and Vista like there are people who just dual boot
Ubuntu and Fedora. There are two good Usenet forums to try:

microsoft.public.windowsxp.general
microsoft.public.windows.vista.general

I will do a search on Google groups for AHCI ATA

Your motherboard manufacturer is the best bet to get 
drivers for XP. But another idea is to look on the Dell
forum. They shipped your computer with Vista preinstalled
so it had Vista drivers for the hard drive. It's possible
that somebody else has already asked at the Dell forum
about an XP driver and gotten a helpful answer.

Knowing how to fix this problem with switching ATA and AHCI is 
quite uncommon knowledge. Perhaps the source for that workaround
has some details about fixing the situation. I've only seen it
mentioned once on this forum.

"The Definitive Bios Optimization Guide for PCs" by Adrian Wong
is about 400 pages and didn't even have AHCI in the index!
Do you have any extra setting in your bios to enable something
like legacy support for IDE drives? There is something like that
for legacy USB is why I ask. The bios has gotten very complicated
in the last few years with lots of new functionality. 

It could be that logos34 knew this answer because he has tried
to fix the same problem himself and would have looked for an
easier way first, I'm sure. Did you say whether you were using
32 bit or 64-bit? There are far fewer XP drivers for 64-bit.

Is your Ubuntu working from grub or Vista bootloader yet?
I found where I saw AHCI mentioned:

---------------------------------

Ubuntu installations will not partition my SATA drives.
"Hi Brian & pmq, This may be of some help to you. I've just 
setup my new PC in the last couple of weeks and I also 
experienced the problem of Ubuntu not seeing my drives. I found 
it very frustrating after fitting three 250 GB SATA hard drives 
on the system. This is what worked for me, give it a try. 


    * My drives are set to AHCI in the systems BIOS.
    * Boot with your Ubuntu LiveCD, choose your language.
    * Press F6 to change the boot options and append this to 
the end of the command line: pci=nomsi "

-------------------------------------------

So other people have problems with AHCI too. This post is not good,
[http://ubuntuforums.org/showthread.php?t=1017601&highlight=ahci](http://ubuntuforums.org/showthread.php?t=1017601&highlight=ahci)
 Help with Inspiron - dual booting XP and Intrepid
"Is this even possible?

From what I gather, I have to disable the Flash Cache Module in 
the BIOS, and also the AHCI setting has to be changed to ATI in 
order to successfully install XP. Once installed you cannot <--
change these back (apparently). Thing is, how will that impact on 
my fresh Intrepid install? Will it still be as functional with these items 
disabled for XP?"

---------------------------------------------

A ray of sunshine:popcorn::guitar:

"First thing we did when we got our new Compaq laptop a few months 
ago (model C770US) was disable AHCI in the system bios. On the 
first reboot, Vista Home Premium (with SP1) booted just fine and 
auto-installed a standard ATA driver for the hard drive."

----------------------------------------- 

I take it Vista did not autoinstall a standard ATA driver so
that compatibility with XP could be maintained? I don't know
how much having an ATA driver would make to Intrepid.

"I was responding to the claim that "AHCI must be enabled for Vista".
It doesn't, at least on our laptop. Once the drive interface is 
set to ATA one should be able to install XP, if proper drivers 
can be rounded up. Lack of drivers is what prevented us from 
downgrading our Compaq from Vista to XP (e.g. no XP driver exists
for its Atheros wireless adapter)."

TeX: Actually I'm a little surprised that XP had drivers for all
hardware since you have a newish computer. Under XP->System Properties
Hardware->Device Manager: There are no yellow exclamation points!?

---

### Post by logos34 on 2008-12-21
I did a little googling but the only thing I could find was a few mentions of an unofficial hack for Intel Matrix Storage Manager.  Do you have an Intel board?

---

### Post by Jammanuser on 2008-12-21
> **TeXtonyx said:**
> I collect information like you are looking for because it might
come in handy with a customer. There are some people who just
dual boot XP and Vista like there are people who just dual boot
Ubuntu and Fedora. There are two good Usenet forums to try:

microsoft.public.windowsxp.general
microsoft.public.windows.vista.general


Hello again, TeX...

Thanks for the links! :) I'll be sure to check them out...:guitar:

> **TeXtonyx said:**
> 
I will do a search on Google groups for AHCI ATA

Your motherboard manufacturer is the best bet to get 
drivers for XP. But another idea is to look on the Dell
forum. They shipped your computer with Vista preinstalled
so it had Vista drivers for the hard drive. It's possible
that somebody else has already asked at the Dell forum
about an XP driver and gotten a helpful answer.


Good idea! :) I will check there...

> **TeXtonyx said:**
> 
Knowing how to fix this problem with switching ATA and AHCI is 
quite uncommon knowledge. Perhaps the source for that workaround
has some details about fixing the situation. I've only seen it
mentioned once on this forum.


I found out how to do that the first time I installed XP...I couldn't get past the "Windows starting up" thing at XP installation, after it went through its setup...i kept getting a BSOD! :) I think I Googled the specific "stop" error, on the BSOD, and I found a place where it suggested changing options in BIOS. It was then pure guesswork that allowed me to find out precisely what to change...i.e. the AHCI operating mode of my SATA controller to ATA instead! :) Unfortunately, I didn't copy down the link to that page, though...and so it might take some digging to find it again! ;)
> **TeXtonyx said:**
> 
 Did you say whether you were using
32 bit or 64-bit? There are far fewer XP drivers for 64-bit.

Is your Ubuntu working from grub or Vista bootloader yet?


My XP and Vista is 32-bit...Ubuntu 8.10 is 64-bit.

Ubuntu is indeed working from my Vista bootloader now...thanks for all your help! :)

Cheers! :guitar:

EDIT: about the XP drivers...i'm still looking for drivers for XP! it seems I need help in that area...my wireless driver doesn't even work, which means i can't access the Internet currently from XP. I have a Dell Studio 1535 laptop.

---

### Post by TeXtonyx on 2008-12-21
> **Jammanuser said:**
> Ok...so it would be possible then to simply place the SATA drivers on a floppy, and then push F6 at bootup of XP? Of course i don't have a floppy drive right now...but i was planning to buy an **external** one soon, that's compatible with Vista, and I should be able to use it for that! ;)

Cheers! ):P

-Jam man

:guitar:

If you can do this with a floppy, then you can do this with a
USB stick, way better than a floppy drive and cheaper. I'm
sure your bios will support booting from USB.

But I'm not sure this works after the fact. I just read where
you got XP, Vista and Ubuntu all working under Vista bootloader
and Bootit. I don't blame you for not wanting to reinstall since 
you and a Bbop guy named Coolname007 put a lot of hours into this!

---

### Post by TeXtonyx on 2008-12-21
> **logos34 said:**
> I did a little googling but the only thing I could find was a few mentions of an unofficial hack for Intel Matrix Storage Manager.  Do you have an Intel board?

Yes, this seems like a good idea. But at the bottom of this quoted
post, it warns against the floppy idea that Jammanuser considered.

--------------------------------------
[http://forum.notebookreview.com/showthread.php?t=149035](http://forum.notebookreview.com/showthread.php?t=149035)

Re: Vostro 1500 dual boot w/Vista & XP
Quote:
Originally Posted by nomadz View Post
I just got my Vostro and wiped the HD. I partitioned the HD into 3. 1 - 100gb 1-40gb and 1- 3gb. I loaded Vista Business on the 100gb. I need to load xp onthe the 40gb. I tried to load the sata drivers but i get the BSOD every time. A little help would be greatly appreciated..

Thanks
Here is my experience for my Vostro 1500 with ACHI enabled:
1.when in windows vista, install intel matrix storage utitlity.
2.reboot and copy x:\Program Files\Intel\Intel Matrix Storage Manager\Driver to somewhere.
3. Use nlite to slipstream the driver. ([http://www.nogodforme.com/HPDV6500T.htm](http://www.nogodforme.com/HPDV6500T.htm))
4. install Windows XP with new CD


Note:
1. slpstream the SATA driver from intel or Dell will cause BSOD.
2. load the driver from floopy during installation also cause BSOD.

--------------------------------------

No workarounds in sight yet.

---

### Post by logos34 on 2008-12-21
> **TeXtonyx said:**
> Yes, this seems like a good idea. But at the bottom of this quoted
post, it warns against the floppy idea that Jammanuser considered.
...

3. Use nlite to slipstream the driver. ([http://www.nogodforme.com/HPDV6500T.htm](http://www.nogodforme.com/HPDV6500T.htm))
4. install Windows XP with new CD


Note:
1. slpstream the SATA driver from intel or Dell will cause BSOD.
2. load the driver from floopy during installation also cause BSOD.

--------------------------------------

No workarounds in sight yet.

well, that's interesting about the floppy giving bsod, but as for the rest it just proves what I thought: you apparently have to actually *reinstall *windows (whether you insert the driver into a new cd image or use the floppy), which is sth the OP wants to avoid (unless the Intel hack really works).

---

### Post by TeXtonyx on 2008-12-21
> **logos34 said:**
> I did a little googling but the only thing I could find was a few mentions of an unofficial hack for Intel Matrix Storage Manager.  Do you have an Intel board?

--------------------------------------------

These are the two available downloads for the Intel*.Manager and
they are radically different sizes, so I'm not sure which is right.
It seems to me though, that if he does a backup of his EMBR and
the MBR, that installing XP will not do anything else that needs
to be corrected but write to the MBR. And the backups will put
things back the way they were except for the XP added driver support.

-----------------------------------------


[http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R180984&formatcnt=1&libid=0&fileid=246755](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R180984&formatcnt=1&libid=0&fileid=246755) 
 Intel Matrix Storage Manager - Notebooks, v.7.8.0.1012, A00 4mb

[http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R180982&formatcnt=1&libid=0&fileid=246752](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R180982&formatcnt=1&libid=0&fileid=246752) 
Intel Matrix Storage Manager - Notebooks, v.7.6.0.1011, A00 322KB

[http://support.dell.com/support/edocs/systems/1535/en/index.htm](http://support.dell.com/support/edocs/systems/1535/en/index.htm) 
Technology Guide probably has the most information. Wireless=p154

--------------------------------------------

[http://wickmanstudios.com/content/view/17/29/](http://wickmanstudios.com/content/view/17/29/)
Dell Studio 1535 converted to XP Professional

This is a tutorial on how to convert Vista to XP but it will 
also work on how to install the XP drivers to you XP OS.

Now onto the Steps...
First you will need to download, extract and copy my zipped 
driver package from *here* \/\/
[http://wickmanstudios.com/tutorials/dell1535/studio1535.zip](http://wickmanstudios.com/tutorials/dell1535/studio1535.zip) 
This package (250mb)may have the wireless driver in it.

From Dell there is more than one wireless driver, so look up
your exact model card under Hardware -> Device Manager in order
to download the right one. I can't tell if it supports XP, yet.
You may have to enable Wireless networking in Control Panel too.
Make sure your model in Device Manager matches with the 
download model I've shown below.

------------------------------------------------

I found this file inside the 250mb XP driver download
linked at *here*

03 Dell Wireless WLAN 1397 Half MiniCard (4312bg) 98mb
R189133.exe

this is the link i was referring to:
[http://forums.msiwind.net/mac/dell-1510-card-half-height-t4342.html](http://forums.msiwind.net/mac/dell-1510-card-half-height-t4342.html)

excerpt:
"Win XP Driver Install
1) Download R189133.exe from dell.com
[http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R1891](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R1891) 33&formatcnt=1&libid=0&fileid=259099
2) When you run the file, it will say it can't install the driver.
3) However, you can manually install the driver via the Device Manager.
(right click My Computer... select Properties... select the Hardware Tab... press the Device Manager button... find the network controller with the yellow question mark... right click and select Update Driver...)"

From the Dell Website Installation Instructions:

Installation Instructions
Download

1. Click Download Now, to download the file.
2. When the File Download window appears, click Save (Windows XP users will click Save) this program to disk and click OK. The Save In: window appears.
3. From the Save In: field, click the down arrow then click to select Desktop and click Save. The file will download to your desktop.
4. If the Download Complete window appears, click Close. The file icon appears on your desktop.

Install

1. Double-click the new icon on the desktop. For example labeled R12345.EXE.
2. The Self-Extracting window appears and prompts you to extract or unzip to C:\DELL\DRIVERS\R12345.EXE. (Example path). Write down this path so the executable (Example - Setup.exe) file can be found later.
3. The Self-Extractor window appears.
4. Click OK.
5. After completing the file extraction, if the Self-Extractor window is still open, close it.
6. Click the Start button and then click Run.
7. Type C:\DELL\DRIVERS\R12345 in the Open textbox and then click OK.
8. Follow the on-screen installation instructions.

USE THIS URL JUST TO GET THE FILE
[http://ftp.us.dell.com/network/R189133.exe](http://ftp.us.dell.com/network/R189133.exe)

--------------------------------------------------

---

### Post by TeXtonyx on 2008-12-21
I think the wireless driver link I put in last post will work, but
still check in Device Manager. These are the Intel links for the
Intel(R) Matrix Storage Manager which might be better than the
Dell ones given in the last post, according to user comment.
I included the floppy config utility because that would be a lot
easier than burning a new XP cd with Nlite. It's for a floppy
at F6, but I now doubt that F6 will work for a usb stick also.
I guess you will want a second opinion but I think that if you
backup the embr and the mbr, that any XP reinstall problem
will be fixed by reinstalling those backups.


[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=2101&DwnldID=17059&strOSs=44&OSFullName=Windows*%20XP%20Professional&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=2101&DwnldID=17059&strOSs=44&OSFullName=Windows*%20XP%20Professional&lang=eng)

1.	
Intel(R) Matrix Storage Manager (6910KB)
	8.6.0.1007	10/23/2008	
Supports SATA RAID 5/10 on specific desktop platforms, SATA RAID 0/1, AHCI, 
and matrix RAID on specific desktop and mobile platforms

 Utilities, Tools and Examples
	Title	Ver.#	Date	
2.	
32-bit Floppy Configuration Utility (201KB)
	8.6.0.1007	10/23/2008	Download
	Creates floppy disk for 32-bit OS with Intel® Matrix Storage Manager 
8.6.0.1007 files - used to preinstall RAID driver (F6 during Windows* setup).

---

### Post by TeXtonyx on 2008-12-21
> **TeXtonyx said:**
> 
No workarounds in sight yet.

Found the solution!:cool::!:

How to enable AHCI : Windows XP

Posted by expertester on July 27, 2008

"In case your your XP installation was done using IDE mode, and 
you decide to use AHCI for what ever reason, don&#8217;t worry. You 
can do that without reinstalling your Windows XP. This trick 
might usefull to for those who are confuse / lazy / afraid / 
<put your reason here> to slipstream AHCI driver into WinXP 
installation disc."

Disclaimer: I did not introduce the potentially inflammatory and/or
insulting descriptions, "lazy" and "afraid" they are owned by expertester.
[http://expertester.wordpress.com/2008/07/27/how-to-enable-ahci-windows-xp/](http://expertester.wordpress.com/2008/07/27/how-to-enable-ahci-windows-xp/)

[http://www-307.ibm.com/pc/support/site.wss/MIGR-70477.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-70477.html)
Intel Matrix Storage Manager Driver for Windows XP, Vista (32bit) 
This package installs the Storage driver to enable the following 
SATA Storage Controller on the system board:
- Intel 82801GBM SATA AHCI Controller
- Intel 82801HEM/HBM SATA AHCI Controller <--[This is the one I think.]
- Intel ICH9M-E/M SATA AHCI Controller
- Intel(R) ICH8M-E/ICH9M-E/M SATA RAID Controller

OR,
[http://www.acerpanam.com/synapse/data/7117/documents/AHCI_Intel_v7.5.0.1017_XP.zip](http://www.acerpanam.com/synapse/data/7117/documents/AHCI_Intel_v7.5.0.1017_XP.zip)

---

### Post by logos34 on 2008-12-21
> **TeXtonyx said:**
> 
[http://expertester.wordpress.com/2008/07/27/how-to-enable-ahci-windows-xp/](http://expertester.wordpress.com/2008/07/27/how-to-enable-ahci-windows-xp/)

Good work, Textonyx.  Interesting...hope it works.  But read the posts at the bottom--it didn't for about half the people who tried it. And it's an Acer

Try it out, Jammenuser!  I'd like to know if this is possible.

---

### Post by logos34 on 2008-12-21
> **TeXtonyx said:**
> 
[http://www-307.ibm.com/pc/support/site.wss/MIGR-70477.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-70477.html)
Intel Matrix Storage Manager Driver for Windows XP, Vista (32bit) 
This package installs the Storage driver to enable the following 
SATA Storage Controller on the system board:
- Intel 82801GBM SATA AHCI Controller
- Intel 82801HEM/HBM SATA AHCI Controller <--[This is the one I think.]
- Intel ICH9M-E/M SATA AHCI Controller
- Intel(R) ICH8M-E/ICH9M-E/M SATA RAID Controller

Isn't that for Lenovo?  I thought Jammenuser had a Dell Studio 1535 (Intel 965 chipset)?

---

### Post by Jammanuser on 2008-12-21
> **TeXtonyx said:**
> If you can do this with a floppy, then you can do this with a
USB stick, way better than a floppy drive and cheaper. I'm
sure your bios will support booting from USB.

But I'm not sure this works after the fact. I just read where
you got XP, Vista and Ubuntu all working under Vista bootloader
and Bootit. I don't blame you for not wanting to reinstall since 
you and a Bbop guy named Coolname007 put a lot of hours into this!

Good idea! :) A USB flash drive should indeed work, **if** the floppy would work, that is...

As for the guy by the name of Coolname007...that would be me, using a different username, as i'm sure you've already figured out! :lolflag: Kind of hard not to notice that the thread about a tri-booting problem there by "Coolname007", has the same name as the thread over here, about the **same** problem! :guitar:

BTW, what does "Bbop" stand for? 

I already have a flash drive, so I could easily use it if it would work to install the SATA drivers! ;)

Cheers! ):P

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-21
> **logos34 said:**
> Isn't that for Lenovo?  I thought Jammenuser had a Dell Studio 1535 (Intel 965 chipset)?

I do indeed have a Dell Studio 1535 laptop...:) If you need or want the specs for it, I think I can provide them for you! ;)

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-21
> **TeXtonyx said:**
> 

[http://wickmanstudios.com/content/view/17/29/](http://wickmanstudios.com/content/view/17/29/)
Dell Studio 1535 converted to XP Professional

This is a tutorial on how to convert Vista to XP but it will 
also work on how to install the XP drivers to you XP OS.



Already beat you to it! 8) If you scroll down on that page, and read the posts at the bottom, you'll see a couple by "Coolname007"...that would be me!

BTW, i've already tried the proposed drivers, but couldn't get them to work...:( Also, it seems that the drivers are for a Dell Studio **1536** laptop, instead of a 1535, which is the one I have...because when I downloaded them, transfered to an external HDD, transferred them again, this time to XP, I noticed that the folder for the drivers was named "Drivers for Studio 1536" or something to that effect...and when I tried extracting them, I got some kind of error message saying that there was nothing to extract, or that the folder was empty! :)

Of course that may have just been due to the drivers somehow getting lost in the transfer to my external HDD...i'll try to extract it in Vista, and see if there's actually anything in it! :popcorn:

Cheers! :guitar:

---

### Post by TeXtonyx on 2008-12-22
> **logos34 said:**
> Isn't that for Lenovo?  I thought Jammenuser had a Dell Studio 1535 (Intel 965 chipset)?

Yes, actually I thought the driver might be generic.

Well, I also saw another method which worked for Steve #10

-----------------------------------------------

"I took a slightly different approach.
1) Get SATA drivers for Windows (whatever flavour you use)
2) Control Panel, Add New Hardware.
3) Yes, already connected, browse to the bottom, hit “add a new device”
4) No, point it to the directory of your SATA drivers
5) Choose your driver from the list that returns. (Mine was the 
nVidia SATA controller)
6) Uninstall other standard IDE controllers.
7) Reboot and enter your BIOS
8) Change to AHCI mode
9) Boot to Windows… which finds the *ACTUAL* AHCI controller, 
and installs the same driver as what you chose in step 5. 
10) Windows wants to reboot. Do that.
11) Go to Device Manager and then uninstall the AHCI controller 
that you installed (there will be two or more now, but you want 
to get rid of the one with the exclamation mark) 

12) Success!

That was a *LOT* easier than what I thought it would. After 
reading many guides on how to do it with Intel chipsets with 
home-made registry entries and copying files around… Installing 
the driver manually as a “dummy” effectively does all that for 
you anyway!"

--------------------------------

---

### Post by TeXtonyx on 2008-12-22
> **Jammanuser said:**
> Already beat you to it! 8) If you scroll down on that page, and read the posts at the bottom, you'll see a couple by "Coolname007"...that would be me!

BTW, i've already tried the proposed drivers, but couldn't get them to work...:( Also, it seems that the drivers are for a Dell Studio **1536** laptop, instead of a 1535, which is the one I have...
Cheers! :guitar:

It seemed to me that at the Dell website they offered the
same drivers for Dell 1535/1536 I'll see if I can find it again.
Some are the same and some are different it seems.

---

### Post by Jammanuser on 2008-12-22
> **TeXtonyx said:**
> 
I found this file inside the 250mb XP driver download
linked at *here*

03 Dell Wireless WLAN 1397 Half MiniCard (4312bg) 98mb
R189133.exe

this is the link i was referring to:
[http://forums.msiwind.net/mac/dell-1510-card-half-height-t4342.html](http://forums.msiwind.net/mac/dell-1510-card-half-height-t4342.html)



hmm...but isn't that for the Dell **1510** computer? :guitar: Mine is a Studio 1535...

Thanks for all the replies! I'm still in the process of reading them...:popcorn:

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-22
> **TeXtonyx said:**
> --------------------------------------------

These are the two available downloads for the Intel*.Manager and
they are radically different sizes, so I'm not sure which is right.
[COLOR="Red"]It seems to me though, that if he does a backup of his EMBR and
the MBR,[/COLOR] that installing XP will not do anything else that needs
to be corrected but write to the MBR. And the backups will put
things back the way they were except for the XP added driver support.



Unfortunately, I cant back up my EMBR at the moment...because it requires a floppy drive, and I don't have one currently. Once I buy an external one, though, I'll back it up! ;)

Cheers! :)

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-22
> **Jammanuser said:**
> hmm...but isn't that for the Dell **1510** computer? :guitar: Mine is a Studio 1535...

Thanks for all the replies! I'm still in the process of reading them...:popcorn:

Cheers! :guitar:

[http://wickmanstudios.com/content/view/17/29/](http://wickmanstudios.com/content/view/17/29/)
It says "Dell Studio 1535 converted to XP Professional"
Now onto the Steps...
First you will need to download, extract and copy my zipped driver 
package from here<-(a link) to the full url below\/
[http://wickmanstudios.com/tutorials/dell1535/studio1535.zip](http://wickmanstudios.com/tutorials/dell1535/studio1535.zip) 

Often the same driver will work for several different models.
The same installation procedure will work for several different
models. There is usually a note that says how many and which
models the driver works for. 

They also use the same parts for many computers in a product
line and your starts with a 15xx Dell 1510 N Card Half Height
Have you looked up what model your wireless card is under
Hardware -> Device Manager -> Network Adapters (probably)?

Besides I already posted the wireless card I thought you had,
Dell Wireless WLAN 1397 Half MiniCard (4312bg) R189133.exe from Dell

Sometimes you will find that a driver for another manufacturer
will work on your system even though your own manfucaturer
hasn't released a driver yet. Many times you will have to try
what might work without knowing for sure.

---

### Post by Jammanuser on 2008-12-22
> **TeXtonyx said:**
> 

Besides I already posted the wireless card I thought you had,
Dell Wireless WLAN 1397 Half MiniCard (4312bg) R189133.exe from Dell

Sometimes you will find that a driver for another manufacturer
will work on your system even though your own manfucaturer
hasn't released a driver yet. Many times you will have to try
what might work without knowing for sure.

Yes. I do believe that is the correct wireless card...but i'll check the documentation that came with my computer to make sure! :)

Thanks! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-22
> **TeXtonyx said:**
> Yes, actually I thought the driver might be generic.

Well, I also saw another method which worked for Steve #10

-----------------------------------------------

"I took a slightly different approach.
1) Get SATA drivers for Windows (whatever flavour you use)
2) Control Panel, Add New Hardware.
3) Yes, already connected, browse to the bottom, hit “add a new device”
4) No, point it to the directory of your SATA drivers
5) Choose your driver from the list that returns. (Mine was the 
nVidia SATA controller)
6) Uninstall other standard IDE controllers.
7) Reboot and enter your BIOS
8) Change to AHCI mode
9) Boot to Windows… which finds the *ACTUAL* AHCI controller, 
and installs the same driver as what you chose in step 5. 
10) Windows wants to reboot. Do that.
11) Go to Device Manager and then uninstall the AHCI controller 
that you installed (there will be two or more now, but you want 
to get rid of the one with the exclamation mark) 

12) Success!

That was a *LOT* easier than what I thought it would. After 
reading many guides on how to do it with Intel chipsets with 
home-made registry entries and copying files around… Installing 
the driver manually as a “dummy” effectively does all that for 
you anyway!"

--------------------------------

I noticed that method too when looking at the link you gave me. I suppose I could try it, although I would of course first have to find the place to get the SATA drivers from...;)

Cheers! :popcorn:

-Jam man

:guitar:

P.S. I think I remember looking at the Dell website for XP drivers for my particular laptop model, but I couldn't find any...of course, as you said, no doubt some drivers work for several different models. So in theory, at least, the drivers posted at the Wickman Studios site **should** work! :) So I don't quite understand why there wasn't anything in the downloaded ZIP file...of course, like I suggested before, that problem could simply be due to the files in it being lost when transferring to the external HDD! I do believe I need to try extracting in Vista, to see if there's actually anything in the downloaded ZIP...

---

### Post by TeXtonyx on 2008-12-22
> **Jammanuser said:**
> Unfortunately, I cant back up my EMBR at the moment...because it requires a floppy drive, and I don't have one currently. Once I buy an external one, though, I'll back it up! ;)

Cheers! :)

-Jam man

:guitar:

Well you can back it up to that fat16 drive or probably fat32
and copy it to a usb stick although you may not have one of those.

---

### Post by Jammanuser on 2008-12-22
> **TeXtonyx said:**
> Well you can back it up to that fat16 drive or probably fat32
and copy it to a usb stick although you may not have one of those.

hmm...now there's a thought! :) i don't know if it would work though...

And I do indeed have a USB flash drive! :popcorn:

Cheers! :)

-Jam man

---

### Post by TeXtonyx on 2008-12-22
> **Jammanuser said:**
> Yes. I do believe that is the correct wireless card...but i'll check the documentation that came with my computer to make sure! :)

Thanks! :popcorn:

-Jam man

:guitar:

Check Device Manager, that should tell you factually what you have.
Sometimes they put out manuals that cover more than one model.
For instance they might sell your model with 2GB or 4GB or ram
and its best to actually check the ram rather than read an invoice.

---

### Post by TeXtonyx on 2008-12-22
> **Jammanuser said:**
> I noticed that method too when looking at the link you gave me. I suppose I could try it, although I would of course first have to find the place to get the SATA drivers from...;)

Cheers! :popcorn:

-Jam man

:guitar:

P.S. I think I remember looking at the Dell website for XP drivers for my particular laptop model, but I couldn't find any...of course, as you said, no doubt some drivers work for several different models. So in theory, at least, the drivers posted at the Wickman Studios site **should** work! :) So I don't quite understand why there wasn't anything in the downloaded ZIP file...of course, like I suggested before, that problem could simply be due to the files in it being lost when transferring to the external HDD! I do believe I need to try extracting in Vista, to see if there's actually anything in the downloaded ZIP...

Yes they should because he was talking about a Dell studio 1535.
[http://www.tastycomputers.com/support/download/intel_sata_ich7-9.htm](http://www.tastycomputers.com/support/download/intel_sata_ich7-9.htm)

That is for your chipset, and for getting AHCI to work, but it
says this is for a floppy for adding drivers during F6. I think
these are many of the files in the studio1535.zip file. I think
there should be a XP sata controller driver. I'm not sure if
the one above is the right file or just also needed.
Intel(R) 82801HEM/HBM SATA AHCI Controller (Mobile ICH8M-E/M) ??
IDE : Intel(R) 82801 HEM/HBM SATA AHCI Controller ?!

They seem to offer only Vista driver for 1535 now, at the Dell
website. Do you have any other yellow ! besides the wireless card?

[http://www.torrentz.com/169ea973c114d06297a7bda51bbe46e25658f4bf](http://www.torrentz.com/169ea973c114d06297a7bda51bbe46e25658f4bf)
# Dell 1535 XP Drivers
#

    * 01 Intel Mobile Chipset
    *
          o R180979.exe 2 Mb
    * 02 Intel GM965 Express Chipset Family
    *
          o winxp_14344.exe 19 Mb
    * 03 Dell Wireless WLAN 1397 Half MiniCard (4312bg)
    *
          o R189133.exe 96 Mb
    * 04 Broadcom BCM5784M LAN
    *
          o R180977.EXE 6 Mb
    * 05 Creative Labs Integrated Webcam
    *
          o R180465.EXE 5 Mb
    * 06 Alps Alps TouchPad
    *
          o R180806.EXE 4 Mb
    * 07 Dell Wireless 370 Bluetooth Mini-Card
    *
          o R189103.exe 95 Mb
    * 08 Ricoh Card Reader R5C833
    *
          o R188094.EXE 4 Mb
    * 09 Dell Studio 1535 Sound XP
    *
          o PIDT001.EXE 9 Mb
    * 10 Bluetooth Kernel
    *
          o P186113.EXE 51 Mb
    * 11 Dell Infrared Device
    *
          o R181761.exe 6 Mb
    * 12 ATI HDMI
    *
          o HDAATI.inf 0 Mb
          o Readme.txt 0 Mb
          o RtHDMI.sys 4 Mb
          o rthdmi32.cat 0 Mb
    * 13 Keyboard Panel

---

### Post by Jammanuser on 2008-12-22
Ok...so here's my specs (I left out the software and a few other unrelevant things):

```
Processor: Intel Core 2 Duo T5850 (2.16 GHz/667MHz FSB/2MB cache)
Pre-installed OS: Genuine Windows Vista Home Premium Edition SP1
Memory: 4GB Shared Dual Channel DDR2
Built-in keyboard Options: Back-lit Keyboard
LCD panel: Glossy, widescreen 15.4 inch display (1280x800)
Video Card: 256 MB ATI Mobility Radeon HD 3450
Hard drive: 320 GB SATA hard drive (5400 RPM)
Sound card: High Definition Audio 2.0
**Wireless networking card**: Dell 1397 Wireless-G Card
Camera module: Integrated 2.0M Pixel Webcam
Battery options: 56 Whr Lithium Ion Battery (6 cell)
Finger Printer Reader Module: Integrated Finger Print Reader
Bluetooth: Dell Wireless 370 Bluetooth Internal (2.0)

```

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by theozzlives on 2008-12-22
My Dell laptops like that, except I trashed Vista completely, I just boot ATA.

---

### Post by Jammanuser on 2008-12-22
> **TeXtonyx said:**
> 
They seem to offer only Vista driver for 1535 now, at the Dell
website. Do you have any other yellow ! besides the wireless card?

Yes. Those yellow ! exist next to practically all of the other ones as well! :)
> **TeXtonyx said:**
> http://www.torrentz.com/169ea973c114d06297a7bda51bbe46e25658f4bf[/url]
# Dell 1535 XP Drivers


AWESOME!!! :D those drivers in that link just may be all I need...thanks! :)

Of course, though, from what I can tell...the SATA controller drivers are not included in the Torrent...:( 

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-22
> **theozzlives said:**
> My Dell laptops like that, except I trashed Vista completely, I just boot ATA.

Like what, if you don't mind me asking? :confused: Are you saying that you also have the Dell Studio 1535 laptop?

Cheers! :lolflag:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-22
> **Jammanuser said:**
> Ok...so here's my specs (I left out the software and a few other unrelevant things):

```
Processor: Intel Core 2 Duo T5850 (2.16 GHz/667MHz FSB/2MB cache)
Pre-installed OS: Genuine Windows Vista Home Premium Edition SP1

**Wireless networking card**: Dell 1397 Wireless-G Card


```

Cheers! :popcorn:

-Jam man

:guitar:

The readme file says this works for the Intel 965 chipset {re logos34}.

[http://downloadcenter.intel.com/Product_Search.aspx?Prod_nm=82801%20Controller&page_nbr=2&lang=eng](http://downloadcenter.intel.com/Product_Search.aspx?Prod_nm=82801%20Controller&page_nbr=2&lang=eng)

12.	Intel® Matrix Storage Manager
 	 File Name:	iata55_enu.exe version: 5.5.0.1035

I think this is the right one. Pick either XP Pro or Home edition
for the sata driver. It is an exe file so pay attention where
it puts its files for the Device Manager update driver later.

"I took a slightly different approach.
1) Get SATA drivers for Windows (whatever flavour you use)
2) Control Panel, Add New Hardware.
3) Yes, already connected, browse to the bottom, hit &#8220;add a new device&#8221;
4) No, point it to the directory of your SATA drivers
5) Choose your driver from the list that returns. (Mine was the
nVidia SATA controller)
6) Uninstall other standard IDE controllers.
7) Reboot and enter your BIOS
Change to AHCI mode
9) Boot to Windows&#8230; which finds the *ACTUAL* AHCI controller,
and installs the same driver as what you chose in step 5.
10) Windows wants to reboot. Do that.
11) Go to Device Manager and then uninstall the AHCI controller
that you installed (there will be two or more now, but you want
to get rid of the one with the exclamation mark)

---

### Post by Jammanuser on 2008-12-22
> **Jammanuser said:**
> 
AWESOME!!! :D those drivers in that link just may be all I need...thanks! :)

Of course, though, from what I can tell...the SATA controller drivers are not included in the Torrent...:( 

Cheers! :guitar:

Update. I just attempted to download those torrents, but it seems they require a membership...which means that they're not free! :-k Do you know of any place that I could get the same XP drivers from...for FREE? ;)

Thanks in advance! :guitar:

---

### Post by TeXtonyx on 2008-12-22
> **Jammanuser said:**
> Update. I just attempted to download those torrents, but it seems they require a membership...which means that they're not free! :-k Do you know of any place that I could get the same XP drivers from...for FREE? ;)

Thanks in advance! :guitar:

Yes, I posted the link in #26. Since you didn't seem excited I
posted the .torrent file which showed the content of the .zip file.
I don't know if all the files in the torrent are in the zip file
but very likely the most important ones are there.

Also I think the files are also available from Dell, like that 
1397 wireless driver was an R18xxIforget and I think its in the 
zip file. The trick at the Dell website is Searching for name of 
the device which you find from Device Manager and the yellow ! 
and matching it up with your XP OS. The files will probably
all be R18xxxx. Cross-referencing the device driver filenames
from the torrent information with the Device Manager of XP
should help if you get stuck. 

A .zip file is a compress file. Unzip the zip file into a folder
named for instance C:\Drivers. A good and free utility for this
is [http://www.7-zip.org/](http://www.7-zip.org/)  download the program from there/install

---

### Post by TeXtonyx on 2008-12-23
> **Jammanuser said:**
> Update. I just attempted to download those torrents, but it seems they require a membership...which means that they're not free! :-k Do you know of any place that I could get the same XP drivers from...for FREE? ;)

Thanks in advance! :guitar:

I noticed that the torrent has all the filename.exe for Dell driver
downloads, or a lot of them any way. To get them from Dell go to
the following link, [http://search.dell.com/](http://search.dell.com/) In the search window, 
top right, type in the filename.exe you want to download. Do a search. 
Check the Compatibility for XP as well as Vista. Screenshots of the 
Search window at Dell, and a sample result for R188094.exe are attached. 
You can use the second Search window from where you get the driver and it 
is easier to narrow the search down to "Support & Help" at Dell. After
you get the result(s) to your search, click on the result, and it will
take you to a download page where you next check the compatibility.

[http://dellstudio.jeroenzelle.nl/Broadcom%20Bluetooth/](http://dellstudio.jeroenzelle.nl/Broadcom%20Bluetooth/)
Broadcom Bluetooth
P186113.EXE  27-Aug-2008 20:08  51.2M

I think the keyboard driver is a MS Intellitype Pro 6.3 but there
are different model types, check your manual. The Dell Infrared Device
is R181761. [http://driverpacks.net/DriverPacks/download.php?pag=ga](http://driverpacks.net/DriverPacks/download.php?pag=ga) 
has ATI HDMI and the drivers are in C:\D\S\R3 if you unpacked to C:\
and 8-12_xp32_dd_ccc_wdm_enu_72271.exe works for your video card, a
display driver and Catalyst configurater. I already mentioned what I 
thought might work for the Sata driver. That .zip file has the others.

---

### Post by Jammanuser on 2008-12-23
Here's a couple of screenshots of my Device Manager in XP...:) See attachment. Notice in particular all the yellow ! near most of the drivers! :guitar:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-23
> **TeXtonyx said:**
> Yes, I posted the link in #26. Since you didn't seem excited I
posted the .torrent file which showed the content of the .zip file.


Yes, and like I believe i mentioned in post #21, the drivers from that page didn't work! :) There was nothing in the zip file I downloaded from there...although I'm going to try downloading them again, in hopes that this time it will download correctly, with the drivers still in the zip! :guitar:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-23
> **TeXtonyx said:**
> 

Also I think the files are also available from Dell, like that 
1397 wireless driver was an R18xxIforget and I think its in the 
zip file. The trick at the Dell website is Searching for name of 
the device which you find from Device Manager and the yellow ! 
and matching it up with your XP OS. The files will probably
all be R18xxxx. Cross-referencing the device driver filenames
from the torrent information with the Device Manager of XP
should help if you get stuck. 


Alright...i'll try that next! :)

Thanks for all your help! :P

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-23
> **TeXtonyx said:**
> I noticed that the torrent has all the filename.exe for Dell driver
downloads, or a lot of them any way. To get them from Dell go to
the following link, [http://search.dell.com/](http://search.dell.com/) In the search window, 
top right, type in the filename.exe you want to download. Do a search. 
Check the Compatibility for XP as well as Vista. Screenshots of the 
Search window at Dell, and a sample result for R188094.exe are attached. 
You can use the second Search window from where you get the driver and it 
is easier to narrow the search down to "Support & Help" at Dell. After
you get the result(s) to your search, click on the result, and it will
take you to a download page where you next check the compatibility.

[http://dellstudio.jeroenzelle.nl/Broadcom%20Bluetooth/](http://dellstudio.jeroenzelle.nl/Broadcom%20Bluetooth/)
Broadcom Bluetooth
P186113.EXE  27-Aug-2008 20:08  51.2M

I think the keyboard driver is a MS Intellitype Pro 6.3 but there
are different model types, check your manual. The Dell Infrared Device
is R181761. [http://driverpacks.net/DriverPacks/download.php?pag=ga](http://driverpacks.net/DriverPacks/download.php?pag=ga) 
has ATI HDMI and the drivers are in C:\D\S\R3 if you unpacked to C:\
and 8-12_xp32_dd_ccc_wdm_enu_72271.exe works for your video card, a
display driver and Catalyst configurater. I already mentioned what I 
thought might work for the Sata driver. That .zip file has the others.

Alright. I'll try try that next! :)

Thanks! :popcorn:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-23
> **Jammanuser said:**
> Yes, and like I believe i mentioned in post #21, the drivers from that page didn't work! :) There was nothing in the zip file I downloaded from there...although I'm going to try downloading them again, in hopes that this time it will download correctly, with the drivers still in the zip! :guitar:

--------------------------------

I use Firefox and the screenshot is the start of the download. 
Double-click on the link shown in the screenshot to start the dl. Post 26
Since the file is 250mb, it should take at least 15 minutes to
download (dl). Once you have the file downloaded, use that utility
I gave you a link to [http://www.7-zip.org/](http://www.7-zip.org/) .zip files will be
associated to that program. Use My Computer, to browse to the
download folder where the zip file is. Doubl-click on it and
then choose to extract it to C: I put drivers in C:\Drivers.
I know this works because I just tested it to make the screenshot.

---

### Post by TeXtonyx on 2008-12-23
> **Jammanuser said:**
> Alright...i'll try that next! :)

Thanks for all your help! :P

------------------------------------------------------------

This is what your folder structure should eventually look like.

C:\Dell 1535 XP Drivers
Folder PATH listing

&#9500;&#9472;&#9472;&#9472;01 Intel Mobile Chipset 
&#9500;&#9472;&#9472;&#9472;02 Intel GM965 Express Chipset Family -->
&#9500;&#9472;&#9472;&#9472;03 Dell Wireless WLAN 1397 Half MiniCard (4312bg)
&#9500;&#9472;&#9472;&#9472;04 Broadcom BCM5784M LAN
&#9500;&#9472;&#9472;&#9472;05 Creative Labs Integrated Webcam
&#9500;&#9472;&#9472;&#9472;06 Alps Alps TouchPad
&#9500;&#9472;&#9472;&#9472;07 Dell Wireless 370 Bluetooth Mini-Card
&#9500;&#9472;&#9472;&#9472;08 Ricoh Card Reader R5C833
&#9500;&#9472;&#9472;&#9472;09 Dell Studio 1535 Sound XP
&#9500;&#9472;&#9472;&#9472;10 Bluetooth Kernel
&#9500;&#9472;&#9472;&#9472;11 Dell Infrared Device
&#9500;&#9472;&#9472;&#9472;12 ATI HDMI
&#9492;&#9472;&#9472;&#9472;13 Keyboard Panel
    &#9500;&#9472;&#9472;&#9472;IType
    &#9474;   &#9500;&#9472;&#9472;&#9472;Setup
    &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;Files
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;1028
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;1031
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;1032
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;1033
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;1034
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;1036
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;1040
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;1041
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;1042
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;1046
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;2052
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;2070
    &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472;&#9472;Components
    &#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472;&#9472;Commands
    &#9474;   &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;DPGFlip3D
    &#9474;   &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;DPGFvs
    &#9474;   &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;DPGHnt
    &#9474;   &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;dpgis
    &#9474;   &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;dpgmacro
    &#9474;   &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;dpgmgy
    &#9474;   &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;DPGPto
    &#9474;   &#9474;   &#9474;   &#9474;       &#9492;&#9472;&#9472;&#9472;DPGQL
    &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472;&#9472;Models
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;ComfortCurveKeyboard2000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;DigitalMediaKeyboard
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;DigitalMediaKeyboard3000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;DigitalMediaProKeyboard
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;EliteKeyboardForBluetooth
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;InternetKeyboard
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;KeyboardWithFingerprintReader
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;MultimediaKeyboard
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;NaturalErgonomicKeyboard4000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;NaturalMultimediaKeyboard
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;NaturalWirelessErgonomicKeyboard7000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;SideWinderX6Keyboard
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WiredKeyboard400
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WiredKeyboard500
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WiredKeyboard600
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessComfortKeyboard
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessComfortKeyboard4000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessDesktopEliteKeyboard
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessEntertainmentKeyboard7000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessEntertainmentKeyboard8000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessKeyboard1000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessKeyboard2000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessKeyboard3000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessKeyboard6000v3
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessLaserKeyboard5000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessLaserKeyboard6000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessLaserKeyboard7000
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessMultimediaKeyboard
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessNaturalMultimediaKeyboard
    &#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessOpticalDesktopForBluetoothKeyboard
    &#9474;   &#9474;   &#9474;       &#9492;&#9472;&#9472;&#9472;WirelessPhotoKeyboard
    &#9474;   &#9474;   &#9492;&#9472;&#9472;&#9472;Fonts
    &#9474;   &#9492;&#9472;&#9472;&#9472;Setup64
    &#9474;       &#9500;&#9472;&#9472;&#9472;Files
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;1028
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;1031
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;1032
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;1033
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;1034
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;1036
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;1040
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;1041
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;1042
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;1046
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;2052
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;2070
    &#9474;       &#9474;   &#9500;&#9472;&#9472;&#9472;Components
    &#9474;       &#9474;   &#9474;   &#9492;&#9472;&#9472;&#9472;Commands
    &#9474;       &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;DPGFlip3D
    &#9474;       &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;DPGFvs
    &#9474;       &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;DPGHnt
    &#9474;       &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;dpgis
    &#9474;       &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;dpgmacro
    &#9474;       &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;dpgmgy
    &#9474;       &#9474;   &#9474;       &#9500;&#9472;&#9472;&#9472;DPGPto
    &#9474;       &#9474;   &#9474;       &#9492;&#9472;&#9472;&#9472;DPGQL
    &#9474;       &#9474;   &#9492;&#9472;&#9472;&#9472;Models
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;ComfortCurveKeyboard2000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;DigitalMediaKeyboard
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;DigitalMediaKeyboard3000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;DigitalMediaProKeyboard
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;EliteKeyboardForBluetooth
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;InternetKeyboard
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;KeyboardWithFingerprintReader
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;MultimediaKeyboard
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;NaturalErgonomicKeyboard4000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;NaturalMultimediaKeyboard
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;NaturalWirelessErgonomicKeyboard7000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;SideWinderX6Keyboard
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WiredKeyboard400
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WiredKeyboard500
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WiredKeyboard600
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessComfortKeyboard
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessComfortKeyboard4000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessDesktopEliteKeyboard
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessEntertainmentKeyboard7000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessEntertainmentKeyboard8000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessKeyboard1000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessKeyboard2000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessKeyboard3000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessKeyboard6000v3
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessLaserKeyboard5000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessLaserKeyboard6000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessLaserKeyboard7000
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessMultimediaKeyboard
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessNaturalMultimediaKeyboard
    &#9474;       &#9474;       &#9500;&#9472;&#9472;&#9472;WirelessOpticalDesktopForBluetoothKeyboard
    &#9474;       &#9474;       &#9492;&#9472;&#9472;&#9472;WirelessPhotoKeyboard
    &#9474;       &#9492;&#9472;&#9472;&#9472;Fonts
    &#9492;&#9472;&#9472;&#9472;Prereq
        &#9500;&#9472;&#9472;&#9472;msxml
        &#9474;   &#9500;&#9472;&#9472;&#9472;x64
        &#9474;   &#9492;&#9472;&#9472;&#9472;x86
        &#9500;&#9472;&#9472;&#9472;Watson
        &#9474;   &#9500;&#9472;&#9472;&#9472;amd64
        &#9474;   &#9492;&#9472;&#9472;&#9472;x86
        &#9492;&#9472;&#9472;&#9472;WindowsInstaller3.1v2
            &#9492;&#9472;&#9472;&#9472;x86

-------------------------------------------------------------

Next, the filenames in those folders and sizes of the downloads.

#
01 Intel Mobile Chipset/R180979.exe
2.22 MB

#
other
02 Intel GM965 Express Chipset Family/winxp_14344.exe
20.08 MB

#
other
03 Dell Wireless WLAN 1397 Half MiniCard (4312bg)/R189133.exe
100.88 MB

#
other
04 Broadcom BCM5784M LAN/R180977.EXE
6.71 MB

#
other
05 Creative Labs Integrated Webcam/R180465.EXE
4.78 MB

#
other
06 Alps Alps TouchPad/R180806.EXE
3.92 MB

#
other
07 Dell Wireless 370 Bluetooth Mini-Card/R189103.exe
99.75 MB

#
other
08 Ricoh Card Reader R5C833/R188094.EXE
3.77 MB

#
other
09 Dell Studio 1535 Sound XP/PIDT001.EXE
9.06 MB

[TeX: The first 9 of these are in the Wickman Dell1535 zip file.]

#
other
10 Bluetooth Kernel/P186113.EXE
53.72 MB

#
other
11 Dell Infrared Device/R181761.exe
5.80 MB

#
other
12 ATI HDMI/HDAATI.inf
8.20 kB

#
text
12 ATI HDMI/Readme.txt
48.00 B

#
other
12 ATI HDMI/RtHDMI.sys
3.69 MB

#
other
12 ATI HDMI/rthdmi32.cat
11.82 kB

#
other
13 Keyboard Panel/IType/Setup/Files/1028/ (more to #13 list)...

[http://www.onlytorrents.com/torrent/dell-1535-drivers-for-downgrading-vista-to-xpv2:169ea973c114d06297a7bda51bbe46e25658f4bf](http://www.onlytorrents.com/torrent/dell-1535-drivers-for-downgrading-vista-to-xpv2:169ea973c114d06297a7bda51bbe46e25658f4bf)

The MS Intellitype Pro 6.3 download is available from MS. One can
install several different keyboard models. Pick the right one
during the installation (maybe refer to manual).

---

### Post by Jammanuser on 2008-12-23
> **TeXtonyx said:**
> 
Since the file is 250mb, it should take at least 15 minutes to
download (dl). Once you have the file downloaded, use that utility
I gave you a link to [http://www.7-zip.org/](http://www.7-zip.org/) .zip files will be
associated to that program. Use My Computer, to browse to the
download folder where the zip file is. Doubl-click on it and
then choose to extract it to C: I put drivers in C:\Drivers.
I know this works because I just tested it to make the screenshot.

I already have 7-zip, and I just tried it, after downloading the same zip file again. Once again, I got the same error message saying it wasn't a valid archive, and there was no files in it...

It still doesn't work! 

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-23
> **TeXtonyx said:**
> 
This is what your folder structure should eventually look like.


Yes it should...only problem is the files don't exist, when I download the zip! :)

Cheers! :popcorn:

-Jam man

:guitar:

EDIT: never mind...i just realized you were talking about the other drivers, not the ones from Wickman Studios! I just downloaded the torrent from the other site, and am now downloading it, using BitTorrent...thanks! :D

---

### Post by TeXtonyx on 2008-12-23
> **Jammanuser said:**
> Here's a couple of screenshots of my Device Manager in XP...:) See attachment. Notice in particular all the yellow ! near most of the drivers! :guitar:

Cheers! :popcorn:

-Jam man

:guitar:

Yes, good job. I notice 12 yellow exclamation points !
in the second screenshot. 9 of those drivers are in the zip file,
and I gave you links for the other 3 I think. 

Your keyboard probably works but with a generic keyboard driver.
I think they include a #13 keyboard download for MS Intellitype
because it will give your keyboard some added functionality.

Most drivers can be installed from Device Manager, and then
right-click on the device with the yellow ! on it,-> Update Driver,
and then you usually have to navigate to C:\Drivers and the
right sub-directory for that driver. That's why I included
the directory structure post, to help out with the organization.
It takes a little practice. But once you get the files, the hard
part is over, and just new subject material for your tutorial :-)
I forgot to warn you that the website with the list of filenames,
and their sizes, has dirty pictures, so don't look!

[http://wickmanstudios.com/content/view/17/29/](http://wickmanstudios.com/content/view/17/29/)
There are two ways to install the drivers described, try them
both if you have to, and the method for installing them is more
automatic(if it works) than my manual method described above.

You are at the best part of the game, annihilating those yellow
!!!!. They are actually enemy alien warriors in disguise. The
cartoon version I and IIesp. of Tales From the Darkside, Gary Larson,
is very funny and is why I thought about the yellows !'s masquerading
as evil alien game hunters in sheep's clothing, sort of like Predator.

---

### Post by Jammanuser on 2008-12-23
> **TeXtonyx said:**
> 
[COLOR="Red"]Most drivers can be installed from Device Manager, and then
right-click on the device with the yellow ! on it,-> Update Driver,[/COLOR]
and then you usually have to navigate to C:\Drivers and the
right sub-directory for that driver. That's why I included
the directory structure post, to help out with the organization.
It takes a little practice. But once you get the files, the hard
part is over, and just new subject material for your tutorial :-)
I forgot to warn you that the website with the list of filenames,
and their sizes, has dirty pictures, so don't look!

[http://wickmanstudios.com/content/view/17/29/](http://wickmanstudios.com/content/view/17/29/)
There are two ways to install the drivers described, try them
both if you have to, and the method for installing them is more
automatic(if it works) than my manual method described above.

You are at the best part of the game, annihilating those yellow
!!!!. They are actually enemy alien warriors in disguise. The
cartoon version I and IIesp. of Tales From the Darkside, Gary Larson,
is very funny and is why I thought about the yellows !'s masquerading
as evil alien game hunters in sheep's clothing, sort of like Predator.

Yes, I already knew how to do that...to update the drivers, I mean.

about the dirty pictures...yeah! :) I noticed that! :lol: It seems that porn has managed to infiltrate all parts of our society, so that its to the point now where you can't even download drivers, without seeing some...never mind! :-$

I liked the analogy of the yellow !, btw! :) It was really great! :lolflag:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-23
> **Jammanuser said:**
> I already have 7-zip, and I just tried it, after downloading the same zip file again. Once again, I got the same error message saying it wasn't a valid archive, and there was no files in it...

It still doesn't work! 

-Jam man

:guitar:

I don't know why 7-zip didn't work, it has a good reputation, and
is free. I just looked at the file and the icon says that Winrar
is associated with it, and is what I used to open it. But Winrar
costs money which is why I didn't recommend it to begin with.
I think though that it may have a 30 day trial download.

---

### Post by Jammanuser on 2008-12-23
> **TeXtonyx said:**
> 
But once you get the files, the hard
part is over, and just new subject material for your tutorial :-)


Speaking of my tutorial...I did some work on it last night, just FYI! :) I hope to finish it by a few days' time...and once i do, i'll post it here, as well as maybe other places! :popcorn:

No doubt the info will help others who may also want to tri-boot with BootIT NG! ;)

Cheers! :cool:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-23
> **Jammanuser said:**
> Speaking of my tutorial...I did some work on it last night, just FYI! :) I hope to finish it by a few days' time...and once i do, i'll post it here, as well as maybe other places! :popcorn:

No doubt the info will help others who may also want to tri-boot with BootIT NG! ;)

Cheers! :cool:


I think it is very generous of you to supply the tutorial for free
especially since the high demand would drive the price up. But,
have you thought about the demands on your time? All those emails
of appreciation streaming in, take some time to reply to. Some of
those emails though will be asking questions because they have 
gotten stuck so I guess answering them just goes with the territory
which means having to read all the fan mail too.

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
> I think it is very generous of you to supply the tutorial for free
especially since the high demand would drive the price up. But,
have you thought about the demands on your time? All those emails
of appreciation streaming in, take some time to reply to. Some of
those emails though will be asking questions because they have 
gotten stuck so I guess answering them just goes with the territory
which means having to read all the fan mail too.

I don't believe it will take that much time to complete...:) And as for the other...I wouldn't mind if all the said stuff happened! ;) I enjoy helping other people with their problems! :popcorn:

Cheers! :lolflag:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-24
hmm...I just tried the zip package I downloaded from that alternate mirror at the Wickman Studios, and this time I was able to unzip them to a folder. And I just looked in that folder, and the drivers appear to be there this time! \\:D/ Although the drivers are considerably less in number than the ones in the torrent...which i'm still downloading, btw! :)

I'll go try the Wickman drivers in XP...and post back here if they work! :guitar:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
> I don't know why 7-zip didn't work, it has a good reputation, and
is free. I just looked at the file and the icon says that Winrar
is associated with it, and is what I used to open it. But Winrar
costs money which is why I didn't recommend it to begin with.
I think though that it may have a 30 day trial download.

Backtracking a bit...I don't think 7-zip was the issue with the drivers not in my zip file! ;) I believe the reason why the other drivers didn't work, was because either they didn't download correctly, or because the zip file never actually contained them to begin with! :) Although I think the latter possibility is highly unlikely...:lolflag:
Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-24
Success! :guitar: I just tried the drivers for XP from Wickman Studios...and they worked! :) Now I have sound and Internet in XP! \\:D/ Thank you, TeX! Of course, not **all** of the drivers worked...a couple of them didn't, specifically the "02 Intel GM965 Express Chipset Family" (Winxp_14344), and the "05 Creative Labs Integrated Webcam" (R180465) drivers. :(

But at least, the most important drivers work, i.e. the sound card driver and the network controller driver...so at least I now have sound and Internet on XP! :popcorn:

Cheers! :)

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-24
Here is how my Device Manager in XP **now** looks...:guitar: See attachment.

-Jam man

:popcorn:

---

### Post by TeXtonyx on 2008-12-24
> **Jammanuser said:**
> Here is how my Device Manager in XP **now** looks...:guitar: See attachment. 

---------------------------
Post #40

[http://dellstudio.jeroenzelle.nl/Broadcom%20Bluetooth/](http://dellstudio.jeroenzelle.nl/Broadcom%20Bluetooth/)
Broadcom Bluetooth
P186113.EXE 27-Aug-2008 20:08 51.2M

I think the keyboard driver is a MS Intellitype Pro 6.3 but there
are different model types, check your manual. The Dell Infrared Device
is R181761. [http://driverpacks.net/DriverPacks/download.php?pag=ga](http://driverpacks.net/DriverPacks/download.php?pag=ga)
has ATI HDMI and the drivers are in C:\D\S\R3 if you unpacked to C:\
and 8-12_xp32_dd_ccc_wdm_enu_72271.exe works for your video card, a
display driver and Catalyst configurater. I already mentioned what I
thought might work for the Sata driver. That .zip file has the others.

----------------------------------------------------------------

Video Controller (VGA Compatible) yellow !
You have the generic video driver which is not so good.
 8-12_xp32_dd_ccc_wdm_enu_72271.exe Good!

"For ati mobility radeon HD 3450 Graphics 256mb"
"version 2008.1201.1504.27008

First download this file
----> MSXML 6.0msxml6.msi

Second this file
----> MMDotNETSetup.exe
run and install first msxml 6.0 then MMDotNETSetup ........

Download this latest ati catalyst 8.12 display driver from ati websites
8-12_xp32_dd_ccc_wdm_enu_72271.exe

Extract into C: directory
8-12_xp32_dd_ccc_wdm_enu_72271

Run DH Mobility Modder.NET ATI Edition
Locate driver location from C: directory
and try to modify it...

Go to C:\8-12_xp32_dd_ccc_wdm_enu_72271Driver
then run SETUP.EXE

Im using XP PROFESSIONAL SERVICE PACK 2

Ex400 - vb
Core 2 duo
2.00GHz
2.00GB of RAM
msi brand
Need Dot.net Framework

TeX: Don't forget to get Service Pack 2 and install it.

-----------------------------------------------------------

[http://wickmanstudios.com/content/view/17/29/](http://wickmanstudios.com/content/view/17/29/)
Wickman says: "UPDATE: For the users who configured their 
notebook Dell Studio with the ATI Radeon video card, they will 
have to download the software "ATI Catalyst graphics" that is 
available for Windows XP and then patch it using the appropriate 
Mobility Modder Patch."-> [http://www.driverheaven.net/modtool.php](http://www.driverheaven.net/modtool.php)
You should read this because I don't have any experience with it.

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
[http://ati.amd.com/support/drivers/xp/fireglv-xp.html](http://ati.amd.com/support/drivers/xp/fireglv-xp.html)
Two options, #1= Display Driver ATI Catalyst Control Center  
HDMI Audio Driver or #2 just the driver

[http://games.on.net/file/22897/ATI_Catalyst_8.12_Display_Driver_for_Windows_XP_Professional](http://games.on.net/file/22897/ATI_Catalyst_8.12_Display_Driver_for_Windows_XP_Professional)
choose _download_.  (8-12_xp32_dd_ccc_wdm_enu_72271.exe)
TeX: I think this is the better choice

----------------------------------------------------

PCI device, yellow !

I guess that is due to this driver failing
02 Intel GM965 Express Chipset Family" (Winxp_14344)

---------------------------------------------------

Fingerprint Sensor yellow !
"UPDATE: Download the Fingerprint Reader Drivers from Lenovo."
[ftp://ftp.software.ibm.com/pc/pccbbs/mobiles/7wf114ww.exe](ftp://ftp.software.ibm.com/pc/pccbbs/mobiles/7wf114ww.exe)

----------------------------------------------

Integrated Webcam yellow !
05 Creative Labs Integrated Webcam/R180465.EXE
4.78 MB
What can you do but try it again or post at Wickman's.

---------------------------------------------

Audio Device on High Definition Audio Bus yellow !

Under audio I have 09 -> PIDT001.EXE
             
and also C:\audio\HDMI
R158235.EXE 
8,384 IntcHDMI.cat
16,128 IntcHdmi.inf
108,032 IntcHdmi.sys

and also under C:\audioXP #12
8,197 HDAATI.inf
3,688,064 RtHDMI.sys
11,822 rthdmi32.cat

Wickman: UPDATE: "For those with the ATI HDMI Audio, you will need to download the following driver here." \/\/
[http://rapidshare.com/files/142342404/WinXP_ATI_Audio_Driver.zip](http://rapidshare.com/files/142342404/WinXP_ATI_Audio_Driver.zip)

or [http://driverpacks.net/DriverPacks/download.php?pag=ga](http://driverpacks.net/DriverPacks/download.php?pag=ga)
C:\D\S\R3 much bigger download

UPDATE: "Speaker Crackle Fix - Control Panel > IDT Audio Control Center > Advanced (gear wheels) and disable "Power Management" option."

-------------------------------------------

Keyboard #13
I don't think they would have included the Keyboard drivers
unless they offered something better the generic keyboard driver.
Microsoft Intellitype Pro 6.3 driver package available at MS.

----------------------------------------------

Bluetooth kernel #10
P186113.EXE

----------------------------------------------

Dell Infrared Device #11
R181761.exe
Wickman: "This 'unknown device' is a device on Intel(R) ICH8M 
LPC Interface Controller - 2815 has been fixed by downloading 
and installing the ITE CIR InfraRed receiver."
[http://wickmanstudios.com/tutorials/dell1535/R181761.exe](http://wickmanstudios.com/tutorials/dell1535/R181761.exe)

---------------------------------------- 

It's a big improvement to get the internet going, for sure! 
I think though, that all of these drivers are supposed to work.
The reports of failing were for fixing the need to change bios 
when you boot between XP and Vista without doing a reinstall. 
If you have specific problems, maybe you can contact Wickman
through the comment section for this article on his website,
although it seems you have to register. Tally Ho the Fox!

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
> 

Second this file
----> MMDotNETSetup.exe
run and install first msxml 6.0 then MMDotNETSetup ........


Already downloaded! :) I downloaded the Mobility Modder patch mentioned on that page...but unfortunately, I haven't been able to install it yet, due to it requiring ".net framework 2.0 or greater", which I just recently downloaded from XP, btw, but unfortunately, it seems that that program in turn requires XP SP3, and I only have SP1! :( I was going to upgrade it to SP3 though, when I had the time, and so I should have all that working soon, I hope! :)
> 
Download this latest ati catalyst 8.12 display driver from ati websites
8-12_xp32_dd_ccc_wdm_enu_72271.exe


Already downloaded as well...:popcorn:

> 
Im using XP PROFESSIONAL SERVICE PACK 2


I'm using XP PROFESSIONAL SERVICE PACK 1, unfortunately...:)

> 
Need Dot.net Framework

 
Indeed I do! But unfortunately, though, it requires XP SP3...
> 
TeX: Don't forget to get Service Pack 2 and install it.


I'm going to get Service Pack 3 instead, and install it...:guitar:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
>  Fingerprint Sensor yellow !
"UPDATE: Download the Fingerprint Reader Drivers from Lenovo."
[ftp://ftp.software.ibm.com/pc/pccbbs/mobiles/7wf114ww.exe](ftp://ftp.software.ibm.com/pc/pccbbs/mobiles/7wf114ww.exe)


Already downloaded and installed on XP! :guitar: But unfortunately, though, my fingerprint reader is still not working...:( But I think that may be due to me not installing the fingerprint software that came with my laptop yet! :popcorn:
> 
Integrated Webcam yellow !
05 Creative Labs Integrated Webcam/R180465.EXE
4.78 MB
What can you do but try it again or post at Wickman's.


Yes, I will post over there, and ask about it! ;)

Cheers! :guitar:
> 
UPDATE: "Speaker Crackle Fix - Control Panel > IDT Audio Control Center > Advanced (gear wheels) and disable "Power Management" option."


Already fixed! :)

Cheers! :lolflag:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-24
Quote:
TeX: Don't forget to get Service Pack 2 and install it.
Jammanuser: I'm going to get Service Pack 3 instead, and install it.

Maybe you should get Dot net Framework 3.5, I had to download
that just the other day for something. 
Don't forget to disable your anti-virus while installing SP3
because the anti-virus can interfere with the SP3 script.
Recommended by Microsoft. If you download the whole package 
first, then you can just disconnect from the internet while
you upgrade to SP3, and then enable anti-virus and connection.
I will be here less, moving into the season's spirit.
Happy Holidays

---

### Post by Jammanuser on 2008-12-24
Incidentally, I have already downloaded all the drivers that I found at Wickman Studios, and transferred them over to XP...

Some of them didn't work though, as you can see from the screenshot of my Device Manager. The HDMI audio driver I was unable to install, simply because I couldn't find the setup for it in the folder! :confused:

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
> Quote:
TeX: Don't forget to get Service Pack 2 and install it.
Jammanuser: I'm going to get Service Pack 3 instead, and install it.

Maybe you should get Dot net Framework 3.5, I had to download
that just the other day for something. 
[COLOR="Red"]Don't forget to disable your anti-virus while installing SP3
because the anti-virus can interfere with the SP3 script.[/COLOR]
Recommended by Microsoft. If you download the whole package 
first, then you can just disconnect from the internet while
you upgrade to SP3, and then enable anti-virus and connection.
Happy Holidays, I will be moving into the season's spirit.

As far as I know there is no anti-virus currently installed on XP...;) And 3.5 is the version of .net framework that I downloaded,and is the one that doesn't work with SP1...

Cheers! :lolflag:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
> 
It's a big improvement to get the internet going, for sure! 
I think though, that all of these drivers are supposed to work.
The reports of failing were for fixing the need to change bios 
when you boot between XP and Vista without doing a reinstall. 
If you have specific problems, [COLOR="Red"]maybe you can contact Wickman
through the comment section for this article on his website,
although it seems you have to register.[/COLOR] Tally Ho the Fox!

Already registered over there, and made a couple comments, **quite** a while ago...:lolflag:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-24
> **Jammanuser said:**
> Incidentally, I have already downloaded all the drivers that I found at Wickman Studios, and transferred them over to XP...

Some of them didn't work though, as you can see from the screenshot of my Device Manager. The HDMI audio driver I was unable to install, simply because I couldn't find the setup for it in the folder! :confused:

-------------------------------------------

If you don't have a directory to extract files to and you 
need one, then make the directory before extracting the files.
In Post #46 I showed directory names and a structure you could use.

&#9500;&#9472;&#9472;&#9472;09 Dell Studio 1535 Sound XP
&#9500;&#9472;&#9472;&#9472;10 Bluetooth Kernel
&#9500;&#9472;&#9472;&#9472;11 Dell Infrared Device
&#9500;&#9472;&#9472;&#9472;12 ATI HDMI
&#9492;&#9472;&#9472;&#9472;13 Keyboard Panel

Audio Device on High Definition Audio Bus yellow !

Under audio I have 09 -> PIDT001.EXE

and also C:\audio\HDMI
R158235.EXE
8,384 IntcHDMI.cat
16,128 IntcHdmi.inf
108,032 IntcHdmi.sys

and also under C:\audioXP #12 ATI HDMI
8,197 HDAATI.inf
3,688,064 RtHDMI.sys
11,822 rthdmi32.cat
The above files are contained in the .zip file download below\/\/
Wickman: UPDATE: "For those with the ATI HDMI Audio, you will need to download the following driver here." \/\/
[http://rapidshare.com/files/14234240...dio_Driver.zip](http://rapidshare.com/files/14234240...dio_Driver.zip) #12

or [http://driverpacks.net/DriverPacks/download.php?pag=ga](http://driverpacks.net/DriverPacks/download.php?pag=ga)
C:\D\S\R3 much bigger download

------------------------------------------------

I posted where to get the HDMI files, or what to get,
the files that start with R, like R158235.EXE should
be available from Dell. The PIDT001.exe file is here\/
[http://rapidshare.de/files/40173729/PIDT001.EXE.html](http://rapidshare.de/files/40173729/PIDT001.EXE.html)

I used google to locate R158235 at Dell
[http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R158235&formatcnt=1&libid=0&fileid=211297](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R158235&formatcnt=1&libid=0&fileid=211297)

I look for files on google also. Sometimes running .exe
files will extract files to some folder, often in 
Documents and Settings. Make a note of where the files have been 
extracted so that when you do a manual install of the drivers 
from Device Manager (right-click device->update driver, you may 
have to navigate to the folder on the drive where the drivers are)
in order to install them. If you are not sure which one of the
audio files you need download them all. Most of the time the
system will know what file is right, if you get to the folder.

HDMI <--<---------------------------

[http://rapidshare.de/files/40173712/P163694.EXE.html](http://rapidshare.de/files/40173712/P163694.EXE.html)

---------------------------------------------------------

[http://forum.notebookreview.com/showthread.php?t=270228&page=4](http://forum.notebookreview.com/showthread.php?t=270228&page=4)
Audio Post #40
[http://rapidshare.de/files/40173729/PIDT001.EXE.html](http://rapidshare.de/files/40173729/PIDT001.EXE.html)

Intel Chipset
[http://rapidshare.de/files/40173743/...autol.zip.html](http://rapidshare.de/files/40173743/...autol.zip.html)

HDMI <--<-------------------------
[http://rapidshare.de/files/40173712/P163694.EXE.html](http://rapidshare.de/files/40173712/P163694.EXE.html)

Dell 1510 / 1397 Wirelesscard
[http://rapidshare.de/files/40173613/sp39243.exe.html](http://rapidshare.de/files/40173613/sp39243.exe.html)

ATI HD 3450
[http://rapidshare.de/files/40173755/P108617.EXE.html](http://rapidshare.de/files/40173755/P108617.EXE.html)

Cardreader
[http://rapidshare.de/files/40173687/R166188.EXE.html](http://rapidshare.de/files/40173687/R166188.EXE.html)

Touchpad
[http://rapidshare.de/files/40173670/R179644.exe.html](http://rapidshare.de/files/40173670/R179644.exe.html)

Broadcom Gigabit Ethernet
[http://rapidshare.de/files/40173666/R180977.exe.html](http://rapidshare.de/files/40173666/R180977.exe.html)

IR Receiver
[http://rapidshare.de/files/40173639/R181761.exe.html](http://rapidshare.de/files/40173639/R181761.exe.html)

---

### Post by TeXtonyx on 2008-12-24
Game Master had this to say which was in Spanish so the translated
screenshot is below. Here is his link to the (mic?) audio driver,

[http://www.4shared.com/file/67343753/d2a27d86/Audio.html](http://www.4shared.com/file/67343753/d2a27d86/Audio.html)
and also C:\audio\HDMI -> The link above downloads the files below.
R158235.EXE
8,384 IntcHDMI.cat
16,128 IntcHdmi.inf
108,032 IntcHdmi.sys

----------------------------------

Notice that he also gives a hint about using the .inf file if
setup doesn't work as part of manual install from Device Manager.

[http://foro.noticias3d.com/vbulletin/showthread.php?p=2395679](http://foro.noticias3d.com/vbulletin/showthread.php?p=2395679) #6

---

### Post by Jammanuser on 2008-12-24
Update. :) I just did a little bit of searching with Google myself over the last few hours...and this is what I obtained:

[http://www.laptops-drivers.com/laptop-news/installing-windows-xp-in-dell-studio-1535.html](http://www.laptops-drivers.com/laptop-news/installing-windows-xp-in-dell-studio-1535.html) 

From this link: I downloaded the Chipset driver, the HDMI driver, and the ATI Video HD 3450 Drivers. All worked, and its no longer showing an yellow ! right next to the Video controller, nor is it anymore showing the exclamation point beside the Audio High Definition. 

[http://www.getpcmemory.com/drivers/download-dell-studio-1535-windows-xp-drivers/](http://www.getpcmemory.com/drivers/download-dell-studio-1535-windows-xp-drivers/) 

From this link: I downloaded the &#8220;Dell Studio 1535 Creative Integrated Webcam XP 32/64 Driver&#8221;, and the &#8220;Dell Studio 1535 Intel WiFi Link 5300 Wireless Lan XP Driver&#8221; (P181050.EXE), and the &#8220;Dell Studio 1535 Fingerprint Reader XP Driver&#8221; (7wf114ww.exe)&#8230;however, the only one that worked for me was the WiFi driver. When I tried installing the Webcam driver, I got an error message saying that the device driver did not support the current operating system. And when I tried installing the fingerprint driver, it installed fine, but the Device Manager didn&#8217;t show a driver for my fingerprint reader&#8230;and when I tried installing the DigitalPersona Personal Fingerprint Software, I got an error message saying it couldn&#8217;t find a certain file. 

So everything&#8217;s now working fine, except for the fingerprint reader, the webcam, and a &#8220;PCI Device&#8221;, which I&#8217;m not sure exactly what it is...as can be seen from my attached screenshot of the Device Manager in XP! :guitar:

Cheers! :popcorn:

-Jam man

:guitar:

EDIT: So that means that all of my drivers now work fine, including audio, video, bluetooth, etc...leaving out only the ones above I already mentioned that didn't work! :D

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
> Game Master had this to say which was in Spanish so the translated
screenshot is below. Here is his link to the (mic?) audio driver,

[http://www.4shared.com/file/67343753/d2a27d86/Audio.html](http://www.4shared.com/file/67343753/d2a27d86/Audio.html)
and also C:\audio\HDMI -> The link above downloads the files below.
R158235.EXE
8,384 IntcHDMI.cat
16,128 IntcHdmi.inf
108,032 IntcHdmi.sys

----------------------------------

Notice that he also gives a hint about using the .inf file if
setup doesn't work as part of manual install from Device Manager.

[http://foro.noticias3d.com/vbulletin/showthread.php?p=2395679](http://foro.noticias3d.com/vbulletin/showthread.php?p=2395679) #6

Thanks for taking all the time to search all this out for me...but as mentioned above, I now have all the drivers that I need except for the fingerprint, webcam, and "PCI Device" drivers! :lolflag:

Cheers! :popcorn:

-Jam man

:guitar:

EDIT: and of course the AHCI SATA controller for XP...which is what I was really after, when I started this thread in the first place! :D

---

### Post by TeXtonyx on 2008-12-24
> **Jammanuser said:**
> Update. :) I just did a little bit of searching with Google myself over the last few hours...and this is what I obtained:

[http://www.laptops-drivers.com/laptop-news/installing-windows-xp-in-dell-studio-1535.html](http://www.laptops-drivers.com/laptop-news/installing-windows-xp-in-dell-studio-1535.html) 

From this link: I downloaded the Chipset driver, the HDMI driver, and the ATI Video HD 3450 Drivers. All worked, and its no longer showing an yellow ! right next to the Video controller, nor is it anymore showing the exclamation point beside the Audio High Definition. 

[http://www.getpcmemory.com/drivers/download-dell-studio-1535-windows-xp-drivers/](http://www.getpcmemory.com/drivers/download-dell-studio-1535-windows-xp-drivers/) 

From this link: I downloaded the “Dell Studio 1535 Creative Integrated Webcam XP 32/64 Driver”, and the “Dell Studio 1535 Intel WiFi Link 5300 Wireless Lan XP Driver” (P181050.EXE), and the “Dell Studio 1535 Fingerprint Reader XP Driver” (7wf114ww.exe)…however, the only one that worked for me was the WiFi driver. When I tried installing the Webcam driver, I got an error message saying that the device driver did not support the current operating system. And when I tried installing the fingerprint driver, it installed fine, but the Device Manager didn’t show a driver for my fingerprint reader…and when I tried installing the DigitalPersona Personal Fingerprint Software, I got an error message saying it couldn’t find a certain file. 

So everything’s now working fine, except for the fingerprint reader, the webcam, and a “PCI Device”, which I’m not sure exactly what it is...as can be seen from my attached screenshot of the Device Manager in XP! :guitar:

Cheers! :popcorn:

-Jam man

:guitar:

---------------------------------------
Before I forget
[http://forum.aumha.org/viewtopic.php?f=62&t=31844](http://forum.aumha.org/viewtopic.php?f=62&t=31844)
This adds cmdcons which is the XP recovery console to the
boot.ini menu. I did the registry fixes too.
------------------------------------------------

Write down the name of the missing file for the fingerprint
reader. Google it and post it here and I'll also look for it.
It could depend on something that didn't get installed yet,
I doubt the Webcam but maybe the PCI Device because I'm not
sure yet what that is or how important it is.

---

### Post by Coder543 on 2008-12-24
I apologize for not having read all seven pages of this thread, but may I ask **why** you want to have the nightmare of updating both XP and Vista? In any case, what makes you need windows?

---

### Post by TeXtonyx on 2008-12-24
> **Jammanuser said:**
> Thanks for taking all the time to search all this out for me...but as mentioned above, I now have all the drivers that I need except for the fingerprint, webcam, and "PCI Device" drivers! :lolflag:

Cheers! :popcorn:

EDIT: and of course the AHCI SATA controller for XP...which is what I was really after, when I started this thread in the first place! :D
--------------------------------------------

From this link: I downloaded the &#8220;Dell Studio 1535 Creative 
Integrated Webcam XP 32/64 Driver&#8221;,  When I tried installing 
the Webcam driver, I got an error message saying that the 
device driver did not support the current operating system.

TeX: I suppose you tried this because the webcam driver from
the folder, R180465.EXE, failed. I have gotten this error when
the installation program tried to install the 64 driver into
my 32 XP OS. I tried this, and though I don't own your webcam
device, the installation appeared to finish. That's a bit odd,
see screenshot, on left attached.

You said the winxp_14344.exe failed before. Did you try the
manual installation, viewable at the beginning when the file
is opened? See screenshot, on right attached.

-----------------------------------

"and of course the AHCI SATA controller for XP"

TeX repeating Post #37; you tried this suggestion with no luck?:

The readme file says this works for the Intel 965 chipset {re logos34}.

[http://downloadcenter.intel.com/Product_Search.aspx?Prod_nm=82801%20Controller&page_nbr=2&lang=eng](http://downloadcenter.intel.com/Product_Search.aspx?Prod_nm=82801%20Controller&page_nbr=2&lang=eng)
12. Intel® Matrix Storage Manager
File Name: iata55_enu.exe version: 5.5.0.1035

I think this is the right one. Pick either XP Pro or Home edition
for the sata driver. It is an exe file so pay attention where
it puts its files for the Device Manager update driver later.

"I took a slightly different approach.
1) Get SATA drivers for Windows (whatever flavour you use)
2) Control Panel, Add New Hardware.
3) Yes, already connected, browse to the bottom, hit &#8220;add a new device&#8221;
4) No, point it to the directory of your SATA drivers
5) Choose your driver from the list that returns. (Mine was the
nVidia SATA controller)
6) Uninstall other standard IDE controllers.
7) Reboot and enter your BIOS
Change to AHCI mode
9) Boot to Windows&#8230; which finds the *ACTUAL* AHCI controller,
and installs the same driver as what you chose in step 5.
10) Windows wants to reboot. Do that.
11) Go to Device Manager and then uninstall the AHCI controller
that you installed (there will be two or more now, but you want
to get rid of the one with the exclamation mark)

--------------------------------------------------------

What is the name of the missing file for the fingerprint sensor?
Maybe you already have winxp_14344.exe working, so then forget that.
This is about as far as I can go with suggestions for fixing a
computer that I don't have access to.

---

### Post by Jammanuser on 2008-12-24
EDIT: never mind

---

### Post by Jammanuser on 2008-12-24
> **Coder543 said:**
> I apologize for not having read all seven pages of this thread, but may I ask **why** you want to have the nightmare of updating both XP and Vista? In any case, what makes you need windows?

I only need to update XP, not Vista...and the reason **why** I need XP and Vista is because half of the programs in the universe **only** operate on Windows, unfortunately! :lolflag:

Cheers! :)

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
> 
From this link: I downloaded the “Dell Studio 1535 Creative 
Integrated Webcam XP 32/64 Driver”,  When I tried installing 
the Webcam driver, I got an error message saying that the 
device driver did not support the current operating system.

TeX: [COLOR="Red"]I suppose you tried this because the webcam driver from
the folder, R180465.EXE, failed.[/COLOR] I have gotten this error when
the installation program tried to install the 64 driver into
my 32 XP OS. I tried this, and though I don't own your webcam
device, the installation appeared to finish. That's a bit odd,
see screenshot, on left attached.


That is correct...the webcam driver from Wickman Studios also failed. 

And the page I gave the link to showed the webcam driver that I downloaded, as a driver for 32-bit, not 64-bit, I believe...:-k
> 
You said the winxp_14344.exe failed before. [COLOR="Red"]Did you try the
manual installation[/COLOR], viewable at the beginning when the file
is opened? See screenshot, on right attached.


Not yet. I only tried to install it from the .exe file itself from within the folder. I haven't tried the manual install yet...but I imagine I will obtain the same results. It seems, though, it wouldn't hurt to try...

> 
"and of course the AHCI SATA controller for XP"

TeX repeating Post #37; you tried this suggestion with no luck?:

The readme file says this works for the Intel 965 chipset {re logos34}.

[http://downloadcenter.intel.com/Product_Search.aspx?Prod_nm=82801%20Controller&page_nbr=2&lang=eng](http://downloadcenter.intel.com/Product_Search.aspx?Prod_nm=82801%20Controller&page_nbr=2&lang=eng)
12. Intel® Matrix Storage Manager
File Name: iata55_enu.exe version: 5.5.0.1035

I think this is the right one. Pick either XP Pro or Home edition
for the sata driver. It is an exe file so pay attention where
it puts its files for the Device Manager update driver later.

"I took a slightly different approach.
1) Get SATA drivers for Windows (whatever flavour you use)
2) Control Panel, Add New Hardware.
3) Yes, already connected, browse to the bottom, hit “add a new device”
4) No, point it to the directory of your SATA drivers
5) Choose your driver from the list that returns. (Mine was the
nVidia SATA controller)
6) Uninstall other standard IDE controllers.
7) Reboot and enter your BIOS
Change to AHCI mode
9) Boot to Windows… which finds the *ACTUAL* AHCI controller,
and installs the same driver as what you chose in step 5.
10) Windows wants to reboot. Do that.
11) Go to Device Manager and then uninstall the AHCI controller
that you installed (there will be two or more now, but you want
to get rid of the one with the exclamation mark)


The problem with that tutorial is the fact that it doesn't give the SATA drivers! :) I believe it only says "**Get** SATA drivers for Windows (whatever flavour you use)", and doesn't tell you where exactly to get them from! :lolflag:

> 
[COLOR="Red"]What is the name of the missing file for the fingerprint sensor?[/COLOR]
Maybe you already have winxp_14344.exe working, so then forget that.
This is about as far as I can go with suggestions for fixing a
computer that I don't have access to.

I'm not sure...I didn't write down the name of the missing file, simply because I assumed that it was lacking the necessary fingerprint driver, even though I installed the Lenuvo one successfully. Perhaps it only works for SP3, and not SP1...

Thanks for all your help! :(:)

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-24
> **Jammanuser said:**
> I already gave you the name in Post #68...:) However, if you want it again, I guess I can oblige...:guitar:

The name of the fingerprint driver is "7wf114ww.exe" without the quotes. :popcorn:

Cheers! :lolflag:

-Jam man

:guitar:

 Originally Posted by TeXtonyx  #61
Fingerprint Sensor yellow !
"UPDATE: Download the Fingerprint Reader Drivers from Lenovo."
[ftp://ftp.software.ibm.com/pc/pccbbs...s/7wf114ww.exe](ftp://ftp.software.ibm.com/pc/pccbbs...s/7wf114ww.exe)

Jammanuser replied in #61:
"Already downloaded and installed on XP!  But unfortunately, though, my fingerprint reader is still not working... But I think that may be due to me not installing the fingerprint software that came with my laptop yet!"

So if you downloaded and executed (installed) 7wf114ww.exe
then it shouldn't be missing. Did you make a note where the
file 7wf114ww.exe extracted its contents, to what folder?
So that when you install the driver it knows where to find 
all the files. Recall, that Game Master said all the files 
should be in the same directory.

I guess you are not completely describing your missing file
error message since it's improbable that you would overlook
the obvious answer that I provided.

---

### Post by Jammanuser on 2008-12-25
> **TeXtonyx said:**
> 
So if you downloaded and executed (installed) 7wf114ww.exe
then it shouldn't be missing. [COLOR="Red"]Did you make a note where the
file 7wf114ww.exe extracted its contents, to what folder?[/COLOR]
So that when you install the driver it knows where to find 
all the files. Recall, that Game Master said all the files 
should be in the same directory.

I believe it was C:/Dell/Drivers/ and like I mentioned before, even though it installed fine, the fingerprint sensor still didn't work...there was still the yellow ! right beside it in Device Manager. :(

Anyway, I would understand if you don't want to help me anymore with my problem...you have obviously helped **quite** enough already! :) I don't mean to take up all your time...

You have been a **lot** of help to me, and I really appreciate it. Anyway, those particular drivers aren't all that important...;) At least I managed to get the most important drivers working in XP...I'm pretty sure I could continue the search myself if you no longer want to help, or feel that you have helped enough. :popcorn:

Cheers! :)

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-25
> **Jammanuser said:**
> That is correct...the webcam driver from Wickman Studios also failed. 

And the page I gave the link to showed the webcam driver that I downloaded, as a driver for 32-bit, not 64-bit, I believe...:-k

Not yet. I only tried to install it from the .exe file itself from within the folder. I haven't tried the manual install yet...but I imagine I will obtain the same results. It seems, though, it wouldn't hurt to try...

The problem with that tutorial is the fact that it doesn't give the SATA drivers! :) I believe it only says "**Get** SATA drivers for Windows (whatever flavour you use)", and doesn't tell you where exactly to get them from! :lolflag:

Thanks for all your help! :(:)

-Jam man

:guitar:

There were two parts to my post. I provided what I think is
the right driver. 
[http://downloadcenter.intel.com/Prod...nbr=2&lang=eng](http://downloadcenter.intel.com/Prod...nbr=2&lang=eng)
12. Intel® Matrix Storage Manager
File Name: iata55_enu.exe version: 5.5.0.1035

That answers: "I believe it only says "**Get** SATA drivers 
for Windows (whatever flavour you use)", and doesn't tell you 
where exactly to get them from!"

The rest of the post is the instructions of how to install the
driver than you just downloaded: Intel Matrix Storage Manager
I'm not sure it will work, but I put significant research into it.

----------------------------------------------

And the page I gave the link to showed the webcam driver that I 
downloaded, as a driver for 32-bit, not 64-bit, I believe...:-k

TeX: Nope it says "Integrated Webcam XP 32/64 Driver" which means
the package contains both the 32 and 64 versions of the driver.

Well then Adios, Feliz Año Nuevo

---

### Post by Jammanuser on 2008-12-25
> **TeXtonyx said:**
> 
I guess you are not completely describing your missing file
error message since it's improbable that you would overlook
the obvious answer that I provided.

Hold on. Let me go copy down the **exact** error message in XP...:guitar:

Be back in a few...

-Jam man

:popcorn:

---

### Post by Jammanuser on 2008-12-25
> **TeXtonyx said:**
> 
The rest of the post is the instructions of how to install the
driver than you just downloaded: Intel Matrix Storage Manager
I'm not sure it will work, but I put significant research into it.


I did a bit of research myself on the Intel Matrix Storage Manager...and it appears as if it has to be installed **before** the OS! :) Which is why I turned elsewhere...
> 
And the page I gave the link to showed the webcam driver that I 
downloaded, as a driver for 32-bit, not 64-bit, I believe...:-k

TeX: [COLOR="Red"]Nope it says "Integrated Webcam XP 32/64 Driver" which means
the package contains both the 32 and 64 versions of the driver.[/COLOR]

Right. However, I believe the same one works for both! ;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-25
> **Jammanuser said:**
> I did a bit of research myself on the Intel Matrix Storage Manager...and it appears as if it has to be installed **before** the OS! :) Which is why I turned elsewhere...


The Readme says:
8.  Installing the INF Files Prior to OS Installation
    8A. Installing the Windows* 2000 INF Files Prior
        to OS Installation
    8B. Installing the Windows* XP INF Files Prior
        to OS Installation
    8C. Installing the Windows Server* 2003 INF Files 
        Prior to OS Installation
9.  Installing the INF Files After OS Installation <---<--- (etc.)
9A. Installing the Windows* 2000 INF Files After
        OS Installation
    9B. Installing the Windows* XP INF Files After
        OS Installation 
    9C. Installing the Windows Server* 2003 INF Files 
        After OS Installation

-----------------------------------------------

[http://support.intel.com/support/chipsets/inf/sb/CS-009270.htm](http://support.intel.com/support/chipsets/inf/sb/CS-009270.htm)

"Answer the following question to determine if you need the 
Intel® Chipset Software Installation Utility. 
Did you just install the operating system?

If the answer is yes, you should install the Intel 
Chipset Software Installation Utility to ensure that 
your chipset is optimally configured." (ICSIU)

-----------------------------------------------------------

The Readme provides instructions for installing the .inf after
the OS has been installed. The next quote says that if you 
just installed the OS, yes, you should also install the Intel
Chipset Software Installation Utility. Intel wouldn't make such
a utility if you couldn't use the ICSIU after the OS installation.

There is a more expert method and an easier method, but the
easier methods aren't as flexible and this may require expertise.

Drivers ZIP format Screenshot attached
	Title	Ver.#	Date	
1.	
INF Update Utility - Zip Format  (2231KB)
	9.0.0.1008	6/2/2008	Download
NOTE: File is intended for use by developers/advanced 
users. If you are not a developer/advanced user, please 
download INFINST_AUTOL.EXE instead. 

----------------------------------------------------

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2529&OSFullName=Windows*+XP+Professional&lang=eng&strOSs=44&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2529&OSFullName=Windows*+XP+Professional&lang=eng&strOSs=44&submit=Go)!

Intel® 965 Express Chipset Family

8 downloads on 1 page supported for Windows* XP Professional
Download Types:
Drivers
Utilities, Tools and Examples
	
Drivers (Embedded, for Developers)
		
  Drivers
	Title	Ver.#	Date	
1.	
Intel(R) Matrix Storage Manager (6910KB)
	8.6.0.1007	10/23/2008	
	Supports SATA RAID 5/10 on specific desktop platforms, SATA 
RAID 0/1, AHCI, and matrix RAID on specific desktop and mobile platforms	
Read Me (txt)    Release Notes (htm)   

OS:Windows Server* 2003, Windows Server* 2003 Enterprise x64 Edition, 
Windows Server* 2003 Standard Edition, Windows Server* 2003 Standard 
x64 Edition, Windows Server* 2008, Windows Vista*, Windows Vista* 32, 
Windows Vista* 64, Windows* XP Home Edition, Windows* XP Media Center 
Edition, Windows* XP Professional, Windows* XP Professional x64 Edition
	
Download File(s):English  6910KB, Multi language  22955KB
	2.	
INF Update Utility - Zip Format  (2231KB) [screenshot provided]
	9.0.0.1008	6/2/2008	Download
NOTE: File is intended for use by developers/advanced users. 
If you are not a developer/advanced user, please download 
INFINST_AUTOL.EXE instead. 	
Read Me (txt)    Release Notes (htm)   
	
OS:Windows Server* 2003, Windows Server* 2003 Enterprise x64 Edition, 
Windows Server* 2003 Standard Edition, Windows Server* 2003 Standard 
x64 Edition, Windows Server* 2008, Windows Vista*, Windows Vista* 32, 
Windows Vista* 64, Windows* 2000, Windows* XP Home Edition, Windows* 
XP Media Center Edition, Windows* XP Professional, Windows* XP 
Professional x64 Edition

I attached a screenshot of this zip file unpacked.

---------------------------------------------------------

Here is the url for the INFINST_AUTOL.EXE also
[http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/16023/a08/infinst_autol.exe&agr=N&ProductID=955&DwnldId=16023&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/16023/a08/infinst_autol.exe&agr=N&ProductID=955&DwnldId=16023&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)

And a tool to determine your chipset:
Intel Chipset Identification Utility (224KB)
	3.23	3/27/2008	Download
Helps you identify the Intel® chipset or Intel chipset 
family on your motherboard.	

This download is also valid for the products listed below. 
Use the links below for additional product downloads:
	
	Intel® 3 Series Chipsets
	Intel® 4 Series Chipset
	Intel® 6300ESB I/O Controller Hub
	Intel® 848P Chipset
	Intel® 865 Chipset Family
	Intel® 875P Chipset
	Intel® 910 Express Chipset Family
	Intel® 915 Express Chipset Family
	Intel® 925X Express Chipset Family
	Intel® 945 Express Chipset Family
	Intel® 946 Express Chipset Family
	Intel® 955X Express Chipset
	Intel® 965 Express Chipset Family


-------------------------------------------------

logos34
I thought Jammenuser had a Dell Studio 1535 (Intel 965 chipset)?
TeX: You could make sure of it with the above Identification utility.

So I think it it clear that this can be installed after the OS
is installed. The normal order is: disconnect from the internet,
install OS, install drivers, install anti-virus, and then
reconnect to the internet (I pull the router power plug).
Then download anti-virus definitions, updates and Service Packs.
You are still at the stage of installing drivers after the OS
even though it is taking awhile. You can use either helper
configuration file (zip or .exe) for the main download 
I've already given for Intel(R) Matrix Storage Manager (6910KB)

---

### Post by TeXtonyx on 2008-12-25
Originally Posted by Jammanuser  
"Thanks for taking all the time to search all this out for me...
but as mentioned above, I now have all the drivers that I need 
except for the fingerprint, webcam, and "PCI Device" drivers!"

-------------------------------------------------------

I went over to the Wickman website and I noticed he had a step 
for installing the Webcam. He says you have a cd for it, much 
like you have a cd for installing the fingerprint sensor.

#8 "You will next use the CD labeled "For Reinstalling 
Dell Webcam Central" to get the webcam interface setup 
(do not worry if a prompt shows up in your system tray 
letting you know that you do not have a driver 
installed for the webcam)."

That means you should install the cd first, then reinstall the
XP webcam driver again, if it doesn't work immediately.

Here is a website that several people recommended for drivers.
[http://dellstudio.jeroenzelle.nl/](http://dellstudio.jeroenzelle.nl/)
Creative Integrated Webcam Driver/   25-Oct-2008 12:58  
CREATIVE-LABS_INTEGRATED-WEB_A03_R200491.EXE  25-Oct-2008   4.5M

Have you backed up your system yet, ya never know?

---

### Post by Jammanuser on 2008-12-25
I have been having Internet problems lately, and so haven't been able to post this before...but anyway, here is the info you requested, TeX. This is the error message that I received when trying to install my fingerprint software that came with my computer:

```
1155: File E:\install\instmsi30.exe not found
```

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-25
> **Jammanuser said:**
> I have been having Internet problems lately, and so haven't been able to post this before...but anyway, here is the info you requested, TeX. This is the error message that I received when trying to install my fingerprint software that came with my computer:

```
1155: File E:\install\instmsi30.exe not found
```

------------------------------------

For an error message, that is really good news because it is so
easily fixed. Many of those XP 1535 drivers were released within
the last year or so. That means they were tested for use with
up to date Windows XP installs, SPs and fixes.

It means that your current Windows installer is too old to work
with the current software it is trying to install. So you could just
upgrade the installer. But, this is probably part of the SP3 upgrade
and it is hard to say whether SP3 could help any other driver install.

I've read several posts about Dell XP 1535 success. The problems are 
all due to user error, except for one, the microphone doesn't work. 
That is the only driver that most rather than a few people have
a problem with. All the drivers should work. Some tutorials were
tested with SP3. The other thing is .Net Framework 3.5 which
includes the lower numbered versions. I'm not sure it comes with
SP3, I think it's a separate download. The SATA AHCI issue is a
different area, with quite a few more failures than successes. 

Here are the links to MS to download the newest installer and
and .Net framework. The thing is, that you might run into another
error that wouldn't happen if you had SP3 installed. SP3 might
fix the other driver install problems or prevent more errors
with fingerprint sensor. One can't tell until it's attempted.

[http://www.microsoft.com/downloads/details.aspx?familyid=889482fc-5f56-4a38-b838-de776fd4138c&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=889482fc-5f56-4a38-b838-de776fd4138c&displaylang=en)
Newest installer

-------------------------------------------------

[http://www.microsoft.com/downloads/details.aspx?FamilyID=333325fd-ae52-4e35-b531-508d977d32a6&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=333325fd-ae52-4e35-b531-508d977d32a6&DisplayLang=en)
newest .Net Framework

----------------------------------------------------

[http://www.microsoft.com/downloads/details.aspx?FamilyID=5b33b5a8-5e76-401f-be08-1e1555d4f3d4&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=5b33b5a8-5e76-401f-be08-1e1555d4f3d4&displaylang=en)

This is the SP3 download. It is safer to download the whole thing
and then install it, rather than do a live download install if
you are having internet problems. Fixing a broken SP3 install
can take hours; I had one customer whose cdrom wouldn't even boot
any cd at all, much less the XP install cd. If the internet dl
fails for SP3 just as a file dl, not a live install, it is no big deal.

---

### Post by Jammanuser on 2008-12-25
> **TeXtonyx said:**
> 
I went over to the Wickman website and I noticed he had a step 
for installing the Webcam. He says you have a cd for it, much 
like you have a cd for installing the fingerprint sensor.


Yes...I had noticed that as well, but I didn't think it made much of a difference which to install first. I have already installed the Dell Webcam Software, although it was after installing the webcam driver. I also tried installing the driver, **after** installing the webcam software, but with no success...it still doesn't work.:(

> 
Here is a website that several people recommended for drivers.
[http://dellstudio.jeroenzelle.nl/](http://dellstudio.jeroenzelle.nl/)
Creative Integrated Webcam Driver/   25-Oct-2008 12:58  
CREATIVE-LABS_INTEGRATED-WEB_A03_R200491.EXE  25-Oct-2008   4.5M

Have you backed up your system yet, ya never know?

Thanks for the link. I will try downloading the driver from there, instead, and hopefully it will work...

I haven't backed up my system yet.

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-25
Good luck.
instmsi30.exe not found
That does the installing which means practically nothing got 
installed when instmsi30.exe doesn't execute because it's not found
so I'm just being sure you understand the consequence. I think the
30 at the end means version 3.0 and the newest one is 3.1.
Windows Installer 3.1 WindowsInstaller-KB893803-v2-x86.exe

When already installed (I think with SP3) it shows the attachment.

---

### Post by Jammanuser on 2008-12-25
> **TeXtonyx said:**
> The Readme says:
8.  Installing the INF Files Prior to OS Installation
    8A. Installing the Windows* 2000 INF Files Prior
        to OS Installation
    8B. Installing the Windows* XP INF Files Prior
        to OS Installation
    8C. Installing the Windows Server* 2003 INF Files 
        Prior to OS Installation
9.  [COLOR="Red"]Installing the INF Files After OS Installation <---<--- (etc.)[/COLOR]


This is the site I was referring to: [http://www-307.ibm.com/pc/support/site.wss/MIGR-70477.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-70477.html) 

If you scroll down the page, and read the installation instructions for XP, you will see the following text:

"**Note:** Be sure to install Intel Matrix Storage Manager Driver **before** installing the operating system. Otherwise your computer will not respond; [COLOR="Red"]it will only display a [COLOR="Blue"]blue screen.[/COLOR][/COLOR]"

Cheers! :lolflag:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-25
> **TeXtonyx said:**
> 
Here are the links to MS to download the newest installer and
and .Net framework. The thing is, that you might run into another
error that wouldn't happen if you had SP3 installed. SP3 might
fix the other driver install problems or prevent more errors
with fingerprint sensor. One can't tell until it's attempted.

[http://www.microsoft.com/downloads/details.aspx?familyid=889482fc-5f56-4a38-b838-de776fd4138c&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=889482fc-5f56-4a38-b838-de776fd4138c&displaylang=en)
Newest installer


I just downloaded the newest MS installer, and installed it. I also tried downloading the webcam driver from that other link you gave, but it turns out that it was the **exact** same driver that I tried before, and I got the **exact** same error about the OS not being supported, when i tried to install it...even after installing the latest MS installer! :(

I also downloaded that "Unknown audio device-look inside!" patch from [the same link]("http://dellstudio.jeroenzelle.nl/"), thinking that it might work for the "PCI Device", but I was unable to install it, because it required SP2...see attachment to see the exact error I received when trying to install the patch. 

Cheers! :popcorn:

-Jam man

:guitar:

EDIT: I also downloaded and installed the chipset driver from the same link...and at least **that** one worked fine! :D

---

### Post by TeXtonyx on 2008-12-26
> **Jammanuser said:**
> This is the site I was referring to: [http://www-307.ibm.com/pc/support/site.wss/MIGR-70477.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-70477.html) 

If you scroll down the page, and read the installation instructions for XP, you will see the following text:

"**Note:** Be sure to install Intel Matrix Storage Manager Driver **before** installing the operating system. Otherwise your computer will not respond; [COLOR="Red"]it will only display a [COLOR="Blue"]blue screen.[/COLOR][/COLOR]"

Cheers! :lolflag:

-Jam man

:guitar:

From the very same page that you link to, underneath the part you quote
from it says,

-------------------------------------------------------------------------

If you do not have a diskette drive, you can install Intel Matrix Storage Manager Driver by the following alternative procedure:

   1. Start the BIOS Setup Utility menu.
   2. Select Config.
   3. Select Serial ATA (SATA).
   4. Select Compatibility.
   5. Install Windows XP and Service Pack 2.
   6. Download Intel Matrix Storage Manager Driver from the Web site and extract the driver to C:\DRIVERS\WIN\IMSM.
   7. Run Intel Matrix Storage Manager Driver. To do this, go to C:\DRIVERS\WIN\IMSM\PREPARE, and double-click install.cmd.
   8. Turn the computer off and then on again.
   9. Start the BIOS Setup Utility menu.
  10. Select Config.
  11. Select Serial ATA (SATA).
  12. Select AHCI.
  13. Start Windows XP. The Welcome to the Found New Hardware Wizard appears.
  14. Click No, not this time and click Next.
  15. Select Install from a list or specific location(Advanced), then click Next.
  16. Select Search for the best driver in these locations. Then select Include this location in the search:, specify the path, C:\DRIVERS\WIN\IMSM, and click Next. The Completing the Found New Hardware Wizard appears.
  17. Click Finish.
  18. When the System Settings Change window appears, click Yes. The computer restarts.

TeX: This says in Step 5, to install XP and SP2. In Step 6 one downloads
the Intel*Driver. This is for a Lenovo laptop. It does say to select
Compatility in step 4. You could at least try this method and select
Compatibility (if your Dell bios supports that) before installing SP3.
But in this method the driver is installed after the OS.

Update install

   1. Start Windows XP.
   2. Right-click My Computer and select Properties from the pop-up menu.
   3. Click the Hardware tab and click Device Manager.
   4. Click the + mark to expand IDE ATA/ATAPI controllers.
   5. Right-click Intel 82801HEM/HBM SATA AHCI or Intel 82801GBM SATA AHCI Controller or Intel(R) ICH9M-E/M SATA AHCI Controller or Intel(R) ICH8M-E/ICH9M-E/M SATA RAID Controller and click Properties.
   6. Click the Driver tab.
   7. Click Update Driver.
   8. If running Windows XP:
         1. Select No, not this time and click Next.
         2. Select Install from a list or specific location.
         3. Click Next button.
         4. Select Search for the best driver in these locations and Include this location in the search.
   9. Click Browse.
  10. Locate the driver folder and click OK.
  11. Click Next. The driver installation starts.
  12. Click Finish when the installation completes.
  13. Click Close.

TeX: This method surely works after XP is installed and mentions nothing
about compatibility. This is what I've been calling a manual installation
rather than clicking on a setup.exe file. This way works for other drivers
also. Lenovo is a computer brand and its possible they customize their
drives a bit. But the download I gave you is from Intel and they don't
sell computers but chips and stuff, so it will be a more neutral driver.

Actually, this sounds a little too easy to me, because lots of people know
this approach. I think the instructions in the other post are more likely
to work. I would do the bios compatibility step first, install SP3, reboot
and use the approach from the other post. You're going to be inclined to
doubt that I know what I'm talking about. So I don't think it would hurt
to try this approach first (but still do Compatibility and then SP3 before)
but if it doesn't work, don't give up, try the way I think it may work.
I think its worth the effort because your present workaround is a pita.

Another thing is that SP3 going from SP1 is a large upgrade, It may even
offer you the chance to use F6 to add the SATA driver in the more ordinary
way, sort of before the OS because SP3 is a large chunk of the OS.

---

### Post by TeXtonyx on 2008-12-26
> **Jammanuser said:**
> I just downloaded the newest MS installer, and installed it. I also tried downloading the webcam driver from that other link you gave, but it turns out that it was the **exact** same driver that I tried before, and I got the **exact** same error about the OS not being supported, when i tried to install it...even after installing the latest MS installer! :(

I also downloaded that "Unknown audio device-look inside!" patch from [the same link]("http://dellstudio.jeroenzelle.nl/"), thinking that it might work for the "PCI Device", but I was unable to install it, because it required SP2...see attachment to see the exact error I received when trying to install the patch. 

Cheers! :popcorn:

-Jam man

:guitar:

EDIT: I also downloaded and installed the chipset driver from the same link...and at least **that** one worked fine! :D

That is definitely progress. So do you have two or 3 yellow exclamation
points left? SP3 includes SP2 so that will likely help with the webcam
also. Something I just thought of. SP3 may write to the MBR. So it's a
good idea to back up both your EMBR and MBR. I'm fairly sure that you
can save it to your fat16 partition, I think it says so on page 31 of
your Bootit NG user guide. Then you can copy to a USB stick to be safe,
but you won't need it. You will be able to restore your EMBR and MBR
from the backups on your fat16 partition by entering Maintenance mode
I think its called when you boot up to the Bootit screen. I've seen
how to restore the EMBR in the instructions, actually in the same post
about how to restore EMBR after grub overwrites the MBR and EMBR.
I thought the chipset driver was for the PCI device? What yellow !
was the chipset driver for if not the PCI device?

---

### Post by Jammanuser on 2008-12-26
> **TeXtonyx said:**
> That is definitely progress. So do you have two or 3 yellow exclamation
points left? SP3 includes SP2 so that will likely help with the webcam
also. Something I just thought of. SP3 may write to the MBR. So it's a
good idea to back up both your EMBR and MBR. I'm fairly sure that you
can save it to your fat16 partition, I think it says so on page 31 of
your Bootit NG user guide. Then you can copy to a USB stick to be safe,
but you won't need it. You will be able to restore your EMBR and MBR
from the backups on your fat16 partition by entering Maintenance mode
I think its called when you boot up to the Bootit screen. I've seen
how to restore the EMBR in the instructions, actually in the same post
about how to restore EMBR after grub overwrites the MBR and EMBR.
I thought the chipset driver was for the PCI device? What yellow !
was the chipset driver for if not the PCI device?

Thanks for all the info! :) I really appreciate it...

I just found your last two posts a few seconds ago, and so haven't had the time to read **all** of what you wrote...but just wanted to mention that I ordered an external floppy drive last night, so I should be able to back up my EMBR soon, after which I can do all the other stuff! :) I prefer to do it that way, rather then backing it up to a partition...

I have 3 yellow ! left! :)

Cheers! :)

:guitar:

---

### Post by Jammanuser on 2008-12-26
> **TeXtonyx said:**
> 
 TeX: This says in Step 5, to install XP and SP2. In Step 6 one downloads
the Intel*Driver. This is for a Lenovo laptop. [COLOR="Red"]It does say to select
Compatility in step 4.[/COLOR] You could at least try this method and select
Compatibility (if your Dell bios supports that) before installing SP3.
But in this method the driver is installed after the OS.


Unfortunately, there is no "Compatibility" mode in my BIOS...:( I have only the AHCI and the ATA operating modes for my SATA controller...

So I guess that's out! :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-26
> **TeXtonyx said:**
> That is definitely progress. So do you have two or 3 yellow exclamation
points left? SP3 includes SP2 so that will likely help with the webcam
also. Something I just thought of. [COLOR="Red"]SP3 may write to the MBR.[/COLOR] So it's a
good idea to back up both your EMBR and MBR. I'm fairly sure that you
can save it to your fat16 partition, I think it says so on page 31 of
your Bootit NG user guide. Then you can copy to a USB stick to be safe,
but you won't need it. You will be able to restore your EMBR and MBR
from the backups on your fat16 partition by entering Maintenance mode
I think its called when you boot up to the Bootit screen. I've seen
how to restore the EMBR in the instructions, actually in the same post
about how to restore EMBR after grub overwrites the MBR and EMBR.
I thought the chipset driver was for the PCI device? What yellow !
was the chipset driver for if not the PCI device?

I most certainly do **not** want that to happen! :lolflag: I think I am going to be a bit of research on XP SP3, to make sure it doesn't install to the MBR, which is what you suggested...;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-26
Ok...I just tried installing the fingerprint software again, after the MS installer was installed, as suggested, and this time I got past that one error! :) Unfortunately, though, I'm now getting a message saying that it requires Windows Vista to install...see the screenshot for the exact error message. :(

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-26
I also downloaded and **tried** to install the Intel Chipset Software Installation Utility, but I got another error...8-[ See attachment.

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-26
> **Jammanuser said:**
> Ok...I just tried installing the fingerprint software again, after the MS installer was installed, as suggested, and this time I got past that one error! :) Unfortunately, though, I'm now getting a message saying that it requires Windows Vista to install...see the screenshot for the exact error message. :(

-Jam man

:guitar:

That means you aren't using an XP compatible driver, which is
main challenge for all the drivers when you downgrade from Vista.

You are on your own now. I'm going to terminate the moderation
authority of the Ubuntu staff which will have consequences.
Good luck.

---

### Post by Jammanuser on 2008-12-26
> **TeXtonyx said:**
>  What yellow !
was the chipset driver for if not the PCI device?

It didn't have a yellow ! beside it, AFAIK. I installed it because the chipset driver from Wickman Studios didn't work, and I just wanted to close the door on all possible problems that might exist on my XP installation. :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by solwic on 2008-12-26
Perhaps I'm missing the point...but I have two questions:

1.  Isn't this an U/K/X/buntu forum?

2.  If Windows is giving you so much trouble, why not use Linux?  If nothing else, run Vista and install VirtualBox to emulate Windows XP.  Then you can dual boot Vista/Ubuntu, and fake XP in either one.

If you're just in it for games and the like...well, pick an OS.  :P  You can't have it all.

---

### Post by Jammanuser on 2008-12-26
> **TeXtonyx said:**
> [COLOR="Red"]That means you aren't using an XP compatible driver[/COLOR], which is
main challenge for all the drivers when you downgrade from Vista.

You are on your own now. I'm going to terminate the moderation
authority of the Ubuntu staff which will have consequences.
Good luck.

hmm...then, that is most certainly odd, seeing as the fingerprint driver was supposed to be for XP! :lolflag:

about the moderation thing...no comment! :) 

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-26
> **jrock612 said:**
> Perhaps I'm missing the point...but I have two questions:

1.  [COLOR="Red"]Isn't this an U/K/X/buntu forum?[/COLOR]

2.  If Windows is giving you so much trouble, why not use Linux?  If nothing else, run Vista and install VirtualBox to emulate Windows XP.  Then you can dual boot Vista/Ubuntu, and fake XP in either one.

If you're just in it for games and the like...well, pick an OS.  :P  You can't have it all.

Indeed it is. But it is a problem that I'm having on a tri-boot with Ubuntu, as well, so if I don't fix it, it may extend somehow to my Ubuntu installation, and this will no longer just be a MS problem! :lolflag:

Cheers! :)

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-27
> **TeXtonyx said:**
> 
TeX: [COLOR="Red"]This method surely works after XP is installed[/COLOR] and mentions nothing
about compatibility. This is what I've been calling a manual installation
rather than clicking on a setup.exe file. This way works for other drivers
also. Lenovo is a computer brand and its possible they customize their
drives a bit. But the download I gave you is from Intel and they don't
sell computers but chips and stuff, so it will be a more neutral driver.


Yes, that is most certainly odd that they have that proceedure to install the Intel Matrix Storage Manager **after** XP is already installed, when they say it will cause a blue screen error if you install it before the OS, right before that...:-s

I am still a bit leery of following this proceedure, if it may cause a BSOD...;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-31
> **TeXtonyx said:**
> Found the solution!:cool::!:

How to enable AHCI : Windows XP

Posted by expertester on July 27, 2008

"In case your your XP installation was done using IDE mode, and 
you decide to use AHCI for what ever reason, don’t worry. You 
can do that without reinstalling your Windows XP. This trick 
might usefull to for those who are confuse / lazy / afraid / 
<put your reason here> to slipstream AHCI driver into WinXP 
installation disc."

Disclaimer: I did not introduce the potentially inflammatory and/or
insulting descriptions, "lazy" and "afraid" they are owned by expertester.
[http://expertester.wordpress.com/2008/07/27/how-to-enable-ahci-windows-xp/](http://expertester.wordpress.com/2008/07/27/how-to-enable-ahci-windows-xp/)

[http://www-307.ibm.com/pc/support/site.wss/MIGR-70477.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-70477.html)
Intel Matrix Storage Manager Driver for Windows XP, Vista (32bit) 
This package installs the Storage driver to enable the following 
SATA Storage Controller on the system board:
- Intel 82801GBM SATA AHCI Controller
- Intel 82801HEM/HBM SATA AHCI Controller <--[This is the one I think.]
- Intel ICH9M-E/M SATA AHCI Controller
- Intel(R) ICH8M-E/ICH9M-E/M SATA RAID Controller

OR,
[http://www.acerpanam.com/synapse/data/7117/documents/AHCI_Intel_v7.5.0.1017_XP.zip](http://www.acerpanam.com/synapse/data/7117/documents/AHCI_Intel_v7.5.0.1017_XP.zip)

Success! =D> Thank you very much, TeX (even though I know you probably wont get to read this, because you got banned)! :D I tried your suggestion with the Intel Matrix Storage manager, using the link you give in the post I quote, and following the instructions on how to install it if you don't have a floppy drive...and it WORKED!!! :D The reason why I didn't try it sooner, because I didn't think it would...but I finally broke down, and installed it, and it worked! :P

I can now boot into XP using the AHCI setting in BIOS, without getting a BSOD! 

Cheers! :D

-Jam man

:guitar:

---


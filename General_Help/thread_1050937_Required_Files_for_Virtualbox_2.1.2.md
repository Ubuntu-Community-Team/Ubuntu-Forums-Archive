---
title: "Required Files for Virtualbox 2.1.2"
date: 2009-01-26
forum: General Help
---

### Post by Indyviews on 2009-01-26
I thought I would give Virtualbox one more go at it. I have tried the Puel version and the new 2.1.2 version. I am having trouble with getting the USB to work.

Supposedly...the 2.1.2 version has added help for USB. I have just noticed on this page: [http://linux.softpedia.com/get/System/Emulators/Sun-xVM-VirtualBox]("http://linux.softpedia.com/get/System/Emulators/Sun-xVM-VirtualBox")......that there is a requirement for three additional libraries and that they need to be installed according to the version of Linux one is using.

The files are: libxalan-c
libxerces-c
version of libstdc

What are the exact command lines to get and install these...if that is the way to this.

Thanks for any help!

---

### Post by Vadi on 2009-01-26
USB was present earlier than that actually. 

I haven't heard anything about those libraries, but first make sure that you're in the vboxusers group - go to system&#8594;administration&#8594;users and groups, unlock, manage groups, find the vboxusers one and in properties make sure that the checkbox beside your name is ticked.

Might need to restart for the changes to take effect.

---

### Post by ollesbrorsa on 2009-01-26
Hello,

Found [this thread]("http://ubuntuforums.org/showthread.php?t=1015763") while browsing the Virtualization sub section of the forums. Hope it helps!

Br,
ollesbrorsa

---

### Post by sdennie on 2009-01-26
The easiest way to get those dependencies is to just install the .deb file and, if/when it fails run:

```

sudo apt-get install -f

```

That will automatically download the missing dependencies.

---

### Post by Indyviews on 2009-01-26
**Vadi**.....I made sure I was in the users list but it didn't seem to help.

**ollesbrosa**.....The link you gave me is one of three guides that I already have open to help me. I have installed Virtualbox three times though without success.

This is why I wish to try the 2.1.2 version again...but I need to know about the three 'required' files...how to get and install them.

For a newbie I don't understand why Virtualbox doesn't explain these things, evidently...there are many folks who doesn't understand.

---

### Post by boof1988 on 2009-01-26
> **Indyviews said:**
> **Vadi**.....I made sure I was in the users list but it didn't seem to help.

**ollesbrosa**.....The link you gave me is one of three guides that I already have open to help me. I have installed Virtualbox three times though without success.

This is why I wish to try the 2.1.2 version again...but I need to know about the three 'required' files...how to get and install them.

For a newbie I don't understand why Virtualbox doesn't explain these things, evidently...there are many folks who doesn't understand.

I assume that you are able to install some OS in VirtualBox already.  So have you downloaded/installed the VirtualBox Guest Additions in the Virtual OS?  I haven't used USB with VirtualBox yet, but the Guest Additions help with Mouse-Pointer Capture, USB-stuff, among other things.  Maybe try googling "virtualbox guest additions", I'd put a link here but I can't remember any.  IIRC you can (while in a virtual machine) go to the menus (I've attached a screen shot) to download Guest-Additions.

---

### Post by sdennie on 2009-01-26
> **Indyviews said:**
> 
This is why I wish to try the 2.1.2 version again...but I need to know about the three 'required' files...how to get and install them.

For a newbie I don't understand why Virtualbox doesn't explain these things, evidently...there are many folks who doesn't understand.

I'm not sure how much more clear I can make it.  Install the .deb you've downloaded and if/when it fails type:

```

sudo apt-get install -f

```

That will download the 3 needed files and make virtualbox work.

---

### Post by albinootje on 2009-01-26
> **Indyviews said:**
>  I have just noticed on this page: [http://linux.softpedia.com/get/System/Emulators/Sun-xVM-VirtualBox]("http://linux.softpedia.com/get/System/Emulators/Sun-xVM-VirtualBox")......that there is a requirement for three additional libraries and that they need to be installed according

How did you install VirtualBox exactly ?

Personally I find softpedia.com a bad download resource for Ubuntu :( 
I recommend not using it at all.

Please use add/remove or Synaptic package manager or learn some more apt-get or in case of VirtualBox download from the VirtualBox website directly.

---

### Post by Indyviews on 2009-01-26
This is such a fast moving forum! I didn't realize I had so many responses and I have been checking quite often.

**sdennie**.....we cross posted, even though your post is before mine...yours wasn't on when I posted mine, therefore I couldn't respond to your suggestion. Your suggestion is clear just didn't know your post was  there until now.

**Boof1988**.....yes I had a virtual OS.....here is where I was yesterday (and still am) when I posted this thread on the Virtualbox forum:

[I]Hello, I am using Virtualbox for the purpose of getting my Epson Perfection 3170 scanner to work. My host OS is Ubuntu 8.10 and the Virtual machine is Windows 2000. I am a newbie at Ubuntu and Virtualbox and don't understand command lines although I have changed a few accordingly to several suggestions on the forums. 

At this time, I have had no problem in installing Virtualbox or Windows 2000. After a few terminal changes I have Windows detecting my scanner and I have installed the scanner with the Epson disk. After bringing up the Epson scan page and clicking &#8220;Scan & Save&#8221;...I am told the scanner can not be started. 

I have installed the Virtualbox 2.1 edtion, PUEL version, uninstalled it and then downloaded and installed the new 2.12 and I am not sure if the first was actually uninstalled..I used Synaptic and I also don't see any difference with the supposed changes in the 2.12. I have put my name in the users group through the Systems-Administration-Users Group etc. I have used the terminal command of gksudo gedit /etc/fstab and have added the following line to the end of the file: 
none /proc/bus/usb usbfs devgid=127,devmode=664 0 0 (after finding my correct # of 127) 

There was also a change where I removed several # symbols from some settings. These last two changes helped in getting Windows to detect the scanner. (at least I think it did..I have been at this for many days) 

I have also enabled the USB Controller and the USB 2.0 (EHCI) Controller. This brings me to my present state: 

On the settings-USB page after right clicking I see my USB mouse listed and also my Backup power unit. (why I don't know) but there is no listing for my USB scanner. (USB Device Filters) I am thinking that I am to enter the name and serial # of the device and perhaps another # (I am unclear on this). My problem is: I can't figure out how to do this. 

My questions are: Am I correct in this and how do I enter this info? Will this help in enabling my scanner? Can anyone offer any help in solving this problem for me...please remember that I am a newbie at this and I am also not a spring chicken either. I would sure appreciate any help if it is put as simply as possible. 

I went through quite a few pages of the forum without seeing a problem like this one.
[/I]
I wasn't able to bring up your screenshot. I will have to check into the downloading and installing  guestusers...perhaps that is the problem.

**Albinootje**.....I downloaded both 2.10 PUEL and 2.1.2 from the Virtualbox site. I believe I have used both synaptic and by clicking on the download for installing. 

I will try these suggestions later and may start all over again by downloading 2.1.0. I just know that I want Virtualbox to work....don't care for the alternative of dualbooting with windows.

---

### Post by Jose Catre-Vandis on 2009-01-26
If you need USB, use the closed source version from the Virtualbox website. ( I might be a bit out of date on the groovy new 2.1 but historically the OSE version in the repos doesn't support USB)

---

### Post by albinootje on 2009-01-26
> **Indyviews said:**
> I downloaded both 2.10 PUEL and 2.1.2 from the Virtualbox site. I believe I have used both synaptic and by clicking on the download for installing. 

I will try these suggestions later and may start all over again by downloading 2.1.0. I just know that I want Virtualbox to work....don't care for the alternative of dualbooting with windows.

VirtualBox 2.1.2 is the latest right now. I was also trying to tell you that you should forget about the requirements mentioned at softpedia.com.
Your guest VM seems to be fine, but for some reason your usb scanner is not recognized.

---

### Post by Indyviews on 2009-01-27
As I mentioned before...my virtual OS which is Windows 2000 works   and my USB mouse works.

Here is an Update: After installing Virtualbox guest additions on Windows 2000 as **boof1988** recommended, I now am able to 2000 full screen and I have seamless mouse function which is great!    USB is enabled on Virtual box and now my scanner is now listed on the USB filters list.  However...the scanner still doesn't work! 

Is there something I still have to do on the USB filters list?

I ran the command line that **sdennie** gave me “sudu apt-get install -f” and I got the following:

steve@steve-desktop:~$ sudo apt-get install -f
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
steve@steve-desktop:~$

How do I get the 24 upgraded and this be my problem? 

The reason I am asking is I feel like starting all over. I have been reading apt-gets and the installation etc, I believe on Virtualbox. I seem to have lost the site even though I saved my Firefox tabs. Anyway....at the same time I am thinking I am very close to getting the scanner to work.

---

### Post by Indyviews on 2009-01-27
After trying what boof1988 recommended...my scanner is working..not just quite right..but close. Instead of double clicking on the scanner icon...I click on 'Devices' and then ck on the scanner.

I would say this is half resolved and I am thinking about reinstalling the scanner. I also have my Virtual OS (Windows 2000) in fullscreen and seamless mouse function! I love the program...now to get the scanner to function 100%.

Thanks all for your help. I have another problem and may have to do all of this over but I will be a little more experienced.

---

### Post by MaindotC on 2009-01-29
> **Indyviews said:**
> 

How do I get the 24 upgraded and this be my problem? 


When I try installing it and it doesn't work I get the following output:
```

angry@angry-desktop:~/Desktop$ sudo dpkg -i virtualbox-2.1_2.1.2-41885_Ubuntu_hardy_i386.deb 
dpkg: regarding virtualbox-2.1_2.1.2-41885_Ubuntu_hardy_i386.deb containing virtualbox-2.1:
 virtualbox-2.1 conflicts with virtualbox
  virtualbox-2.0 provides virtualbox and is installed.
dpkg: error processing virtualbox-2.1_2.1.2-41885_Ubuntu_hardy_i386.deb (--install):
 conflicting packages - not installing virtualbox-2.1
Errors were encountered while processing:
 virtualbox-2.1_2.1.2-41885_Ubuntu_hardy_i386.deb
angry@angry-desktop:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
angry@angry-desktop:~/Desktop$

```

---

### Post by albinootje on 2009-01-29
> **strAlan said:**
> 
angry@angry-desktop:~/Desktop$ sudo dpkg -i virtualbox-2.1_2.1.2-41885_Ubuntu_hardy_i386.deb 
dpkg: regarding virtualbox-2.1_2.1.2-41885_Ubuntu_hardy_i386.deb containing virtualbox-2.1:
 virtualbox-2.1 conflicts with virtualbox
  virtualbox-2.0 provides virtualbox and is installed.


Uninstall the virtualbox-2.0 package first, and then install virtualbox-2.1

---

### Post by MaindotC on 2009-01-29
But I don't want to lose my .vdi's :(

---

### Post by albinootje on 2009-01-29
> **strAlan said:**
> But I don't want to lose my .vdi's :(

You won't lose them, because the deletion of the VirtualBox 2.0 package will not remove any of your personal stuff in ~/.VirtualBox/

It will probably ask you after installation whether you want to convert your settings from 2.0 to 2.1.

---

### Post by MaindotC on 2009-01-29
You're right - I'm wrong :D  I uninstalled VBox and I watched ~/.Virtualbox to see that the files were still there.  I successfully installed 2.1 and it worked fine :D  Now I have USB support so I can use the PL-2303 to connect to an Oscope and take screenshots of the output.  Thank you so much for your advice!

---

### Post by ben2talk on 2009-02-07
I don't think any extra files are needed - my printer/scanner connected easily with no add-ons to my fstab (with XP in virtualbox 2.1.2). USB connects, the hardware installs easily, then I install the Canon XP scangear software and bingo - open a window, click to initiate a scan and wait 5 seconds. The lamp lights, the scan begins and then...
[B][I]
Scangear
An error has occurred turn the device off and then back on. Scanner driver will be closed.
code : 2,250,0[/I][/B]

The printer is fine (canon Pixma MP150) this is not happening if I reboot and do the same in XP.

I'm considering trying it out with my Vista Ultimate - but right now too lazy to install it. I'm sure it's a problem with the upgraded Virtualbox.

---


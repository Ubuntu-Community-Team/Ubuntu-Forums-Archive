---
title: "New to Ubunutu Blackberry Software ?? Backup/restore"
date: 2009-02-26
forum: General Help
---

### Post by telmore007 on 2009-02-26
Does anyone one this forum have a blackberry curve? I just put ubuntu on my laptop. I was going to try and have to also boot with Vista. :( But I'm having problems I'm going to try and partition it later within Ubunutu and then install Vista. I really need someone to help me, that knows Ubuntu. I'm on Yahoo all the time. Be nice to have some online Ubuntu friends. I would like to be able to sync my blackberry with Ubuntu to back it up and contacts. If I can't I can do that at work. :( 

I did the updates for this, but I do not have many programs on here yet. Like that wine program. I'm not sure how to install some stuff. And I want to get all the cool themes working that you see on youtube. This is a new laptop. 160 hard drive, 3 gbs of ram, its a dell studio 15 model. 

So far no main problems other than the partitioning part, I'll work on later. Only programs I would need that I would have to have windows for is Photoshop cs3 master collection, Spore ea game, and sims 3, blackberry software. But I can't get the ATI/AMD FGLRX graphics driver to Activate.

Thank you,
[email]Lady_Tiffany_2002@yahoo.com[/email]

---

### Post by steveneddy on 2009-03-02
Use barry for your Berry

[http://www.netdirect.ca/software/packages/barry/](http://www.netdirect.ca/software/packages/barry/)

---

### Post by RedSingularity on 2009-03-02
You can use Wine to fool around with Photoshop and other windows software but i personally just log into vista within Ubuntu and do my "Windows" work from there.  What you should look at for this is [VIRTUALBOX]("http://www.virtualbox.org").  I use this all the time and recomand it to everyone.  Wine is nice and all but i found it didnt work for some of the software i wanted so i just use a Virtual Operating System (Vista).  As for your drivers..........are you connected to the internet?

---

### Post by jacjr56 on 2009-04-09
I downloaded Barry the suggested files and installed them but It is still not usable. Is there a followup interface? I noticed that after instaling Barry I was able to connect my phone Berry to the laptop and not just get the tunes section to work I could also see the pics I have taken and stored on my berry, which is cool but.... I cannot see my address book etc.

---

### Post by Elludium_Q-36 on 2009-04-18
Unfortunately, Barry is not really ready for the novice or intermediate user who's not engrossed and immersed in perpetual terminal sessions.  The OP appears to be in need of advice for newer users...

Even the Guru would appreciate a GUI as total recall of commands and much typing can be taxing.
Barry does offer a GUI but it's only for specifying which information to backup and restore, then effect such backups or restore.   The project page proffers more recent funcionality but doesn't tout a GUI.

Last I checked, Barry was released to Ubuntu as part of the yet to be declared stable Jaunty so you would have to:

    * Force that versions packages without miffing the rest of your distro OR
    * Download the dependency satiated .deb files, letting gdebi fetch the required balance. OR
    * Enable Debian repositories, which can be deleterious for the newbie and cause Synaptic and Apt to cease retrieving packages. 

I have added other packages while offline, using a flash drive and downloading .deb files.  It would have been nice to have successfully used a synaptic generated download script on a Bill Gates box...

Anyway I gave up from frustration of seeing so many unsatisfied dependicies that I used the Debian method after getting a working internet connection.  It worked well enough on my BB 7520 but there was no apparent way to manipulate or change data on the Kubuntu box.

I tried installing BB's Desktop Manager using Wine a couple times.  From a win box, I downloaded files named: 470_b050_english_nomediamanager.exe and BlackBerry USB and Modem Drivers_ENG (DM4.7b50).msi  Best was that it asked to download a gecko and I finised the install but it did nothing other than put a device manager icon in the system tray when opening BlackBerry Device Manager.  Desktop Manager was a virtual paperweight...

I have had other good Ubuntu boxes before but this hp pavilion AMD 3200+ came to me with Kubuntu compiled using a power supply devoid the -5 volt current. :(  A dilemma that can cause hard to diagnose headaches.  Not realizing that I could save package markings in synaptic or how to backup configuration settings and data, I reinstalled Kubuntu 8.04-alt a couple times which seemed stable after changing power supplies.  Particularly frustrating considering that I'm using a wireless iDEN modem that sometimes grinds at 2Kb/Sec.  KPPP once showed a peak of 22Kb/S. Whoo-Hoot!!!
 :popcorn:

I haven't bothered to add the barry packages again via Debian...

I went through and added cross platform, cab extract, etc. and any other packages that would seem to help wine make DM work but to no avail and the .msi file wants to open in an editor...:(

I'm not a noob but this takes time and research, especially for things still in development.

Synaptic finds a whole slew of virtualbox-ose packages.  
The descriptions could be more helpful...
[http://www.virtualbox.org/](http://www.virtualbox.org/) offers some insight but it seems like a few hours reading and then trial and error tweaking.  We are all beta testers really but I'm losing patience as an unwitting alpha tester...

Wine was zip-bang done but I only installed it since I have the BB... Had I known I would have found another sprint/nextel/boost PCS smartphone or waited for a WiFi BB with more Bluetooth/OBEX profiles enabled...  I expected to have been able to have a BB tethered modem and not needed to have bought another phone to do so...  I have no use for windows, that's why I went with open source *nix...

So unless there's a package that will help wine, it's not going to do the job.
In place of BB/DM, Barry is not ready for users without the gumption or time to grind on a command line.

VirtualBox, well I'm open to suggestions from the experienced and informed... :KS

---

### Post by alloyduf on 2009-06-15
Thanks for putting me out of my misery. I'm a new Ubuntu user having brought a new dell mini 9 netbook with it pre installed and I'm not into coding - if it's not point and click I'm lost. Using 8.04, Evolution and a blackberry 8310 and have been trying for days but can't sync the two together - indeed I can't even load the v.14 barry packages as I get a warning about no libary0.

All I wanted to do was upload diary from blackberry to evolution and address book to blackberry and then sync the 2 via USB cable from time to time. I'm a few days away from giving up on Ubuntu, loading Windows XP as this sync is the most important function for me. I know it's RIM's fault for not thinking about us Ubuntu users but these Blackberry things are massive and I'm now of no doubt why Windows is winning the Netbook war. It's such a pity as the concept of real competition was one I brought into.

Sorry to be a misery, I'm just very frustrated with my lack of technical computer skills and waste3d time.

Andy

---

### Post by Elludium_Q-36 on 2009-06-22
There are a few "virtual Machine" programs, such as Sun's VirtualBox.

I downloaded the "Non-Free" version that posters on these forums suggested.
There was no charge for the download but I think I read the "free" version was not USB friendly.  Version 2.2.0 downloaded and installed fine and I see Version 2.2.4 is available but I have yet to get an installable copy of windows...  RIM's Desktop Manager, as I recall, is specific to the windows version...  They have an apple DM too...  


I think I saw reference to four or so Virtual Machine/emulators for Linux.
What that does is open another virtual computer from within Ubuntu or a *nix.  I have heard of being able to run linux from inside windows but who would want to do that? 

I had previously used Debian to download barry and that worked for backup restore but I had to recompile my machine as it was compiled on a bad power-supply.  You have to be careful about adding Debian repositories as it can screw up your package manager.  I tried barry v13, from some other site, on the second go round, installing all the requisite filed but it won't work... 
 
Portableapps.com has "mac on a stick" where you can run an old mac os from a flash-drive.  I think it's for windows but I have ran portable apps via wine...  Some people call Wine an emulator, but their website frowns upon that.  Wine allows you to run individual ms/windows programs from ubuntu/linux but it doesn't seem to like Desktop manager, unless there are other files I need to download...

Last thing I would want to do is go back to windows and there are other smartphones...  There are used windows boxes out there and you can connect to a win box with smb/samba.  You don't need much of a machine just to sync you BB.

Good Luck.

---


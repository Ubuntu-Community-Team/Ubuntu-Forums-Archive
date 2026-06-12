---
title: "Computer disaster"
date: 2006-02-01
forum: Desktop Environments
---

### Post by rtgh4 on 2006-02-01
Help me fix these problems so I don't have to be dragged down by Windows!

I am trying to connect to a cable modem through a LAN swith.  Ubuntu does not reognize the connection of the switch and will not start. Ethernet card is fine, have enough RAM, good processer(AMD Athelon 2400+), switch and cable modem work fine with other computers.

I cannot install anything from CD.  Ubuntu will not start Driver Cd for motherboard(gigabyte k7 triton0 or video card(ATI Radeon 9200).  Ubuntu will not even start or install UT2004(a linux supported game). My Cdrw and DVD work fine on other OS's. WAS able to install Ubuntu itself.

I want to remove the screensavers from system. They lock up whenever they try to run, and I want them gone.

The system will not open any outside program(program icluded in the network/cd errors).

Somebody please help me!

---

### Post by ekarni on 2006-02-01
OK, slow down, take a deep breath, let's try to fix one problem at a time.  First off, let me confirm that you said that you DID get Ubuntu to install?

1.  No internet:  take a look at System->Administration->Networking and play around a bit with the different options, especially make sure DHCP is enabled.   Try searching the forums - chances are someone has had similar problems/ 

2.  Not clear what you mean by "driver CD for motherboard or video card."  Are you trying to use the driver CD's that came with those items?  Odds are, they won't work with Ubuntu.  Video card drivers have been discussed extensively here; again try searching the forum for "ATI video card" and you should get plenty of info about getting that setup.  I'm not aware of any particular drivers required for motherboards.

3.  Screensavers:  go to System->Preferences->Screensaver; on the "Display Modes" tab there's a pulldown for Mode.  Set it to "Disable Screensaver."  I suspect that the system is locking in screensaver because it's trying to do something with the video card.  After you get the video card working you can try re-enabling this.

4.  "System won't open any outside programs"  Like what?  Please try to be very specific when you post; it makes it much easier to help.

---

### Post by rtgh4 on 2006-02-01
thank you! the screensvaers are down!
 
Ubuntu once said that it did not find a sound card(built into mainboard) and would not use.

Yes, ubuntu did initially install.

I will look for ati radeon 9200 drivers

I still cannot install some games that I would like to play.
(warcraft 3, Unreal Tournament '04 [which has linux installer and still wont work])

---

### Post by siorai on 2006-02-01
For UT2004, you need to copy the installer onto your harddrive, doesn't matter where, and run it from there. Afterwards, you can go to [http://www.liflg.org/]("http://www.liflg.org/") and get the necessary updates for it.

---

### Post by rtgh4 on 2006-02-02
ok, what about games w/o linux installer, like warcraft, C&C Generals, or even games I pull off the web?

---

### Post by darth_vector on 2006-02-02
have a read of the "using the drivers from ati.com" part of this wikipage: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

dont try to install the binary drivers from the repository because your card isnt supported (according to the wiki at least)

---

### Post by rtgh4 on 2006-02-02
The wiki doesn't work. every step I get stupid error and failed attempts.

---

### Post by ekarni on 2006-02-02
Games without a Linux installer are a mixed bag.  Most games are written for Windows and won't run directly on Linux.  However, there's a program called Cedega that WILL let you run some Windows games on Linux.  The gotcha is that they charge a monthly subscription fee.  I'm not a gamer, but lots of people around here are - just search for Cedega and you should get plenty of info.  

Of the games written for Linux, most will come in some sort of Linux package format (eg .deb or .rpm file) or as source code.  If it's a package, just install it like any other.  See  [http://www.ubuntuguide.org/]("http://www.ubuntuguide.org/") for more info on doing this.  If it's source code, you need to compile it on your computer, which can range from easy to a real pain.

But (and this is a big one), you gotta get your graphics card drivers working before you can play the games...

> The wiki doesn't work. every step I get stupid error and failed attempts.

I know you're frustrated.  Getting things working can be.  But a post like that isn't going to help us help you.  If step 1 doesn't work, of course steps 2-? aren't going to either.  So start with step 1, then when you get the errors, post them here.  We'll do our best to help you figure them out and get to step 2.  Then repeat.  Like I said, take it slow, have some patience...

---

### Post by rtgh4 on 2006-02-03
Thanks for the help, Games work, cd drives work fine, video devides are good.\\:D/ 
I got internet up, now I just need help getting and installing the Cox security Suite(Cox is my ISP)

---

### Post by ekarni on 2006-02-03
Way to go! I don't think you'll be able to get the security suite to work - I get the impression that most programs like that aren't written for Linux and don't work too well under WINE.  (WINE is a program that lets you run *some* windows programs under Linux)   Spyware and virus' haven't made it to Linux yet, so you should be ok though.  If you're concerned, there are Linux firewall and anti-virus programs.  Firestarter and ClamAV are examples.  Both are available from the repositories via Synaptic.  Security is topic that comes up alot around here, I hate to sound like a broken record, but search and you're bound to find plenty of info!  Again, congrats on getting your system up and running!

---

### Post by carlosqueso on 2006-02-03
[QUOTE=rtgh4]Thanks for the help, Games work, cd drives work fine, video devides are good.\\:D/ 
I got internet up, now I just need help getting and installing the Cox security Suite(Cox is my ISP)[/QUOTE]

Odds are you can't install their security suite on your computer.  The good news is that you probably don't need it and there are free and easy to install replacements for most components in internet security things.   There is no spyware for linux, and viruses are few and mostly not released in the wild.  If you do feel the need for an antivirus, the most popular seems to be clamAV you can install it with ```
sudo apt-get install clamav
``` if you want.  As for a firewall, again, it's not crucial as linux doesn't listen to the outside world by default, but if you want, you can install firestarter ```
sudo apt-get install firestarter
``` to take care of that.

---

### Post by Flintkalle on 2006-02-03
I will borrow your thread a bit.
I get a error when I try to run the last step of the ATI driver installation guide,             ( **sudo dpkg -i *.deb**
sudo module-assistant build,install fglrx-kernel
reboot )

I get this error when i try to run the "bold" command:
dpkg: Error when managing *.deb (--install):
 can't acess the archive: The file or the catalog dosn't excist
Error when managing:
 *.deb

Sorry for the wierd english, fast translation from Swedish :)

But to the question. What should I do? Should I change to some other dir (In the download dir when entering the command)?

---

### Post by ekarni on 2006-02-03
That command looks in the current directory, so yes, you do need to cd to the directory where the file you downloaded is located.  Right now it's giving you the error because it's not finding the file.  Also, it's probably better to specify the name of the file you want installed - * matches anything, so if you have other .deb files in that directory for other programs, it will try installing them (again) too.

---

### Post by rtgh4 on 2006-02-03
the repositories does not work, i get random errors whenever i start synaptic
and when i try to use therepositoties.

---

### Post by ekarni on 2006-02-03
OK, what kind of errors when starting Synaptic?  Please post them *exactly.*
Also please post your sources.list file located /etc/apt/sources.list
This contains a list of which repositories you're using.  Did you add the universe and multiverse repositories per ubuntuguide.org?

---

### Post by Flintkalle on 2006-02-03
[QUOTE=ekarni]That command looks in the current directory, so yes, you do need to cd to the directory where the file you downloaded is located.  Right now it's giving you the error because it's not finding the file.  Also, it's probably better to specify the name of the file you want installed - * matches anything, so if you have other .deb files in that directory for other programs, it will try installing them (again) too.[/QUOTE]

I didn't download any .deb files. I downloaded the .run file from ati.com. so should I use the "sudo dkpg -i *.run" command instead?

---

### Post by ekarni on 2006-02-03
I just looked at ATI's site - the .run file IS the installer.  It should be an executable file - just run it by entering *sudo ./filename* at the command prompt.  (./ means "run the file in this directory, don't try to find it in the path")  If it's not executable, you can fix that with
*sudo chmod a+x filename*
Chmod changes file permissions, a+x means "make it executable (+x) for [u]a[\u]ll users.  You can't use dpkg with the .run file

---

### Post by rtgh4 on 2006-02-13
what do i do for the password thing? I dont have a root login. the aV command says that it is missing:(

---

### Post by rtgh4 on 2006-02-13
well, tanx anyway:)

---

### Post by ekarni on 2006-02-13
If it needs root permissions, put "sudo" before the rest of the command, then use your user password.  Ubuntu doesn't have root - theoretically this helps with security, but I couldn't explain how.

---


---
title: "Print to Fax, what a shamefull mess"
date: 2006-12-17
forum: Desktop Environments
---

### Post by pksings on 2006-12-17
This morning I had an urgent need to print something to the fax modem that's installed on ttyS0 so as to fax it to a client in a hurry.

Oops, not setup. Haven't used it since the format/re-install to get Breezy on here. No big deal, crank up Synaptic.  Install Efax. Installed, no problem, what, no print fax capability? Maybe there is but I couldn't find it. Nothing in printer admin, OpenOffice can't see one either. 10 minutes down. Uninstall Efax, install Hylafax. "Probemodem ?" What ? "Man probemodem" cool there is a class2 string right in the man pages, thank you!.
Cut/paste, change to ttyS0, syntax error? Unknown parameter?  Mind you I'm in a hurry...
Nope, still no print to fax capability.. Nothing in Printer admin, OpenOffice can't see one... Back to synaptic,  search on "fax".  Hmm, mgetty-sendfax was removed by Hylafax, let's put it back, it used to work quite well in Mandrake and Gentoo, oh yeah get lprfax too! Select it, what!?! You want to remove Ubuntu desktop to install lprfax? Huh?  I can't not do this, okay, remove Ubuntu Desktop and install lprfax, enter...... yes, configure samba to allow printing please, whatever... enter, enter...   All done....

Still can't print to fax, 30 minutes later....

Okay, save the document as a Windows .doc file. Copy to USB stick. Insert in my wife's Windows machine which has Winfax 9, which took all of two minutes to install and configure I might add.  Open, print, put in the phone number, done...  

A simple thing that I can install, configure and do in Windows in less than 5 minutes can't be done on Breezy in thirty(30). At least not by me, an experienced user. I'm sure there's some guru somewhere that can.

Efax's documentation states that it provides print to fax capability....
Hylafax does also... 
Neither works for me, is it my fault?   I'm sure some will say yes, read the documentation.
Should I have to? This is a simple thing! At least it seems that way on the surface to me, the non-programming end-user.  It certainly was on Windows, just pay the money to get the license and CDROM, insert, follow the prompts. Bingo, whammo, done! It works..
But Linux is "ready" for the desktop!!!!   REALLY!!!!  It certainly doesn't seem that way here,  and I've had it on my desktop for almost ten years.  

This is getting old, very old. And I'm tired of spending my time fooling with stuff like this just to get simple functionality.  I'm seriously evaluating the $400 question, is my time worth the extra money to get stuff working that I need. Windows XP, antivirus, anti-spyware, Office. Should add up to about $700. How much of my time adds up to that? And is it worth it anymore to spend hours at getting simple stuff like faxing to work?

If Efax is supposed to provide something, it should, the install should complete and the functionality should be there, the same with Hylafax.  Our traditional development model seems to be make a program that works, put it out there and let the users figure out how to make it work for them, read the manual, ask questions on the forums... make them spend time..
It won't work, people will spend loads of money to save time... Especially people like me, educated professionals who have it to spend. That is why Microsoft is great from an end user perspective, most stuff just works, no time needed to make it work, no forums, no research. Just buy the program, install it and go. I have just always felt UNIX/Linux is the better way.  But now I'm short on time and seemingly am going to have to start spending money instead... This really brought into focus to me why I don't recommend Linux to friends, I can't commit their time to it like I have committed mine.  And that's a shame.
Until Linux saves people time over Windows only the poor/cheap will use it, they will have to trade their time instead of money.  I think this might already be evident in the exploding use in developing countries but not in the USA at near the same rates.  Would I have dropped $75 to $100 this morning to get a program that installs and works to provide print to fax? No, probably not because supposedly these "free" programs provide that functionality. Would I now? You betcha, I need to fax from this machine and am not going to spend the time to make it happen via the forums etc.... Just my frustration with this is making me spend the time composing this..

Wake up developers, Linux lovers, if this doesn't change Windows will always be the choice of non-technical people who can afford to buy what they need to save the time.. And I think that includes most of the general public, at least here in the US where I live...

Unfortunately this is the only place I have where I can voice this sentiment and it probably will do very little if any good. And that too is a shame...

---

### Post by linux4me on 2007-01-17
It sounds like you're not really asking for help, just venting, but for others who are experiencing the same frustration--or just want to fax easily from Open Office with eFax--and run across your post, here's what you need to do:

[LIST=1]
[*]Install and configure your modem using the wiki ([https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")).
[*]Use Synaptic to install eFax-gtk.
[*]Go to Administration -> Printing
[*]Double-click New Printer.
[*]Select network printer, HP JetDirect
[*]Type 'localhost' in the Host box.
[*]Set the port to 9900.
[*]Click Forward.
[*]Select 'Raw' as the printer manufacturer.
[*]Click on 'queue' to select it and then click Forward.
[*]Type 'eFax' in for the Name instead of queue.
[*]Click Apply.
[*]Go to Applications -> Office -> eFax-gtk.
[*]Select 'Socket' as the fax entry method, then close eFax.
[/LIST]

To send a fax from Open Office, just click File -> Print and select 'eFax' or whatever name you gave the printer you installed above and click 'Print'. EFax will open a little dialog box prompting you for the fax number to which to send the fax.

Thanks to frrobert who showed the way ([http://www.ubuntuforums.org/showthread.php?t=234456](http://www.ubuntuforums.org/showthread.php?t=234456))

---

### Post by Calculator on 2007-01-23
Dear Linux4me

All was fine following your clear instructions except at:

"... EFax will open a little dialog box prompting you for the fax number to which to send the fax."

The fax prints to eFax without requesting a phone number.

When I click on the printer icon to see the print que I find following "eFax Paused"

On resume I get no relief.  

Is this because I have both ADSL and a modem in place simultaneously and the ADSL is chosen over the fax modem (connected via the serial port)?

Thanks to all for your thoughts

---

### Post by linux4me on 2007-01-24
Hi Calculator,

I don't know for sure, but I don't think it will matter if you have both an ADSL modem and a dial-up modem installed. 

The problem you're having may be because you haven't identified the dial-up modem to eFax. Make sure you know the name of your dial-up modem as identified in the modem installation wiki then try this:

[LIST=1]
[*]Open eFax: Applications -> Office -> Efax-gtk.
[*]Click File -> Settings and then the Modem Tab.
[*]Make sure the name of your modem is displayed in the 'Serial Device' box. I have an Intel 536 modem, so mine says '536ep0'. Yours will vary depending on the way you identified your modem when you configured it according to the wiki.
[/LIST]

I hope that helps!

---

### Post by linux4me on 2007-01-24
One other thing that should help get you going.

You can test Efax to make sure it is communicating with your modem by opening Efax and clicking the 'Standby' button. You should get some output similar to this:

Socket running on port 9900
efax-0.9a: 08:44 opened /dev/536ep0
efax-0.9a: 08:48 using 536EP in class 1
efax-0.9a: 08:48 waiting for activity

The '536ep0' will vary depending on the name you gave your modem when configuring it. If you get any errors, post them here and I or someone more knowledgeable should be able to help you get it working.

---

### Post by Calculator on 2007-01-30
Dear Linux4me 

Thank you kindly for your help and sorry that I did not reply earlier.

I still have a problem and it is problaby fairly basic:

1) In OpenOffice I draft a test document;

2) I go to print and select eFax as the printer; 

3) I press OK at the printer stage;

4) I go to efax-gtk and I see the following error message:

"Socket running on port 9900
ESP Ghostscript 815.02: Unrecoverable error, exit code 1
Not valid postscript file"

Should I be doing something different?

Thanks again for all your help.

---

### Post by linux4me on 2007-02-01
I believe that error ordinarily occurs when the file you are trying to fax isn't in postscript format, which the printer you configured is supposed to deal with. 

You might take a look at my original post in this thread and verify that the printer you set up as your fax is configured correctly according to those instructions, or delete it and set it up again. I suspect there is something in its configuration that is causing the problem.

The other thing I have noticed in using eFax and Open Office is that sometimes if I don't have eFax already open when I try to fax a document I won't be prompted for the number. If I open eFax first and have it running in the background, it has never failed me.

---

### Post by chip616 on 2007-02-03
Linux4Me:

Your post did indeed help me.  I found it by googling.  I am a new member here, having just begun trying to use Ubuntu.  However, I needed to be able to fax from another distro, which I have been using for the past 5 years.  While your instructions did not work in the distro I was using (the print setup features are different), I was able to decode enough of it to duplicate the process using the CUPS printer utility at localhost:631.  Setting up a CUPS printer using raw, port 9900, queue and localhost were the clues I needed.  In the CUPS printer utility, that works out to:

lpd://localhost:9900/queue

That was the 'magic incantation' that I needed to get it to work.

Leaving efax-gtk open when printing was also a big help.  I wouldn't have known what to do otherwise.

Thanks again.

Frank.

---

### Post by chip616 on 2007-02-03
pksings:

I agree with your rant.  It shouldn't be this hard to get something this simple working.  However, Windows has many years and many dollars behind it.  Linux on the desktop is in its infancy.  Give it time.

---

### Post by sicofante on 2007-02-08
I've followed your instructions and tried to print a PDF to the eFax. The "Print" button is greyed out when I select eFax.

So I printed a test page from the printer's properties. Nothing happened.

Then I started eFax and saw this:

Socket running on port 9900
Print job received on socket
efax-0.9a: 03:40 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 03:40 opened /dev/ttyS1
efax-0.9a: 03:41 Error: fax device write: Input/output error
efax-0.9a: 03:43 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 03:45 Error: fax device write: Input/output error
efax-0.9a: 03:47 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 03:47 sync: dropping DTR
efax-0.9a: 03:47 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 03:47 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 03:49 Error: fax device write: Input/output error

*** Stopping send/receive session ***

No need to say all these error lines don't mean a thing to me or any other ordinary human being... eFax programmers obviously don't care.

I have a Zoom 3025c modem that apparently has been recognised (I can see it in Networking). I have no idea if it's a software or hardware modem. I tend to think it's the latter for it was expensive. No idea of which serial port it is connected to, since it's plugged in a PCI slot. Asking a user to know all these things is much too much.

Anyway, I sort of imagined eFax would use postscript files (it's not mentioned anywhere, and the file browser doesn't give any hint whatsover), so I printed my PDF to a file. Tried to fax that file from eFax with similar errors as above.

I'm probably going down to the shop across the street and have my file faxed... :(

The post opening this thread is accurate and I couldn't agree more. A simple and most needed task like this can't be this hard for ordinary users. I've been using computers for 20 years now, some of them with IRIX (SGI's Unix). I can't imagine where my mom would start looking if she needed fax abilities in her computer.

---

### Post by Irony on 2007-02-08
I don't know whether this helps;
[I]
System > Admin > Users and Groups > select your username > properties > user privileges > tick the send and receive fax[/I]

I notice that it is unticked by default.

---

### Post by Phil_McCrackin on 2007-02-08
Hello!

I am attempting to set up my conexant modem for fax. I have followed [this]("http://www.ubuntuforums.org/showthread.php?t=190728&highlight=conexant+driver+installation")  driver installation HOWTO prior to following this thread on eFax. 

When testing I get the following:

```
Socket running on port 9900
Print job received on socket
efax-0.9a: 36:59 opened /dev/ttyS1
efax-0.9a: 36:59 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 36:59 failed page /home/deacon/efax-gtk-server/efax-gtk-server-pk5yQu.001
efax-0.9a: 37:00 failed page /home/deacon/efax-gtk-server/efax-gtk-server-pk5yQu.002
efax-0.9a: 37:00 Error: fax device write: Input/output error
efax-0.9a: 37:02 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 37:04 Error: fax device write: Input/output error
efax-0.9a: 37:06 sync: dropping DTR
efax-0.9a: 37:06 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 37:06 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 37:06 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 37:08 Error: fax device write: Input/output error
efax-0.9a: 37:10 sync: sending escapes
efax-0.9a: 37:10 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 37:10 Error: fax device write: Input/output error
efax-0.9a: 37:10 Error: fax device write: Input/output error
efax-0.9a: 37:10 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 37:10 Error: fax device write: Input/output error
efax-0.9a: 37:10 Error: fax device write: Input/output error
efax-0.9a: 37:12 Error: fax device write: Input/output error
efax-0.9a: 37:14 Error: fax device write: Input/output error
efax-0.9a: 37:16 Error: sync: modem not responding
efax-0.9a: 37:16 Error: tcgetattr on fd=3 failed: Input/output error

```
Now, I am stuck.

Any help or ideas would be greatly appreciated.

---

### Post by Phil_McCrackin on 2007-02-09
OK I discovered the wrong serial was listed in Efax File->Settings.
After changing it to ttySHSF0 and testing, I get this:

```

efax-0.9a: 09:32 opened /dev/ttySHSF0
efax-0.9a: 09:33 Error: can't determine fax modem class support
efax-0.9a: 09:33 finished - invalid modem response

```

Which is...er better right? It seems it is at least communicating with the modem now. Still can't send a fax.
Wish my coding skills were up to par. This really is a rediculously silly thing that *should* be very easy.

---

### Post by chip616 on 2007-02-09
Phil:

I was going to suggest you try another port, but I see you have already done that.

The other obvious thing that comes to mind:  Is this a winmodem?  Winmodems are hardware-crippled devices that rely on the Windows OS to provide a lot of functionality that the hardware would ordinarily supply.  I use an external full hardware modem, so it has all the pieces needed to work.  A lot of internal modems don't have all the hardware.

If what you have is a winmodem, then the easiest thing to do is to forget about it and use an external serial port hardware modem instead.  SOME Winmodems can be made to work in Linux, but I understand that it a bit of a chore to get them going.

---

### Post by dabl on 2007-02-09
pksings speaks the truth.  Few professional people of the non-technical variety, who view computers as a tool for general productivity, are willing or able to make the investment of precious time that Linux requires in order to achieve a level of personal productivity comparable to what they can do with a Wintel box, viruses and all.

Microsoft spent $bajillions on the "plug-n-play" capability for Win95, and it is that basic capability that still makes Windows "better" in the eyes of typical non-technical computer users (except the adherents of the Mac religion).

Personally, I love my Kubuntu Edgy system and am glad I invested LOTS of time to learn to work with it, but I'm an admitted enthusiast, not typical of folks who "just need it to work NOW", like pksings did.

---

### Post by Phil_McCrackin on 2007-02-09
> 
The other obvious thing that comes to mind: Is this a winmodem? Winmodems are hardware-crippled devices that rely on the Windows OS to provide a lot of functionality that the hardware would ordinarily supply. I use an external full hardware modem, so it has all the pieces needed to work. A lot of internal modems don't have all the hardware.


I actually tried the linuxant (FREE) driver earlier and my modem just stayed ON all the time. It was really irritating. Plus, having to pay $20 for full functionality of a $5 modem really kind of defeated itself. I really only want it for faxing.

> 
pksings speaks the truth. Few professional people of the non-technical variety, who view computers as a tool for general productivity, are willing or able to make the investment of precious time that Linux requires in order to achieve a level of personal productivity comparable to what they can do with a Wintel box, viruses and all.

Microsoft spent $bajillions on the "plug-n-play" capability for Win95, and it is that basic capability that still makes Windows "better" in the eyes of typical non-technical computer users (except the adherents of the Mac religion).

Personally, I love my Kubuntu Edgy system and am glad I invested LOTS of time to learn to work with it, but I'm an admitted enthusiast, not typical of folks who "just need it to work NOW", like pksings did.


I completely agree. I am a third year infosec student and know (on a beginner level -1sem each) C/C++ and java. I enjoy programming to an EXTENT. I really mostly enjoy learning the tools others have created and implementing them. I do enjoy the whole broke/fix thing though. I have a box operating as a file server running on Ubuntu and 2 Windows boxes communicating to it via Samba. I am getting an Inspirion 1501 next week and am going to put Ubuntu on that. I enjoy the challenge, satisfaction, and the knowledge of the inner workings. I just don't know enough about the software/hardware interface to make a difference in development.

I am giving my mother a computer next week. She has never owned one. Needless and sad to say, it will not have Linux on it.

I will keep trying. There IS a way, I am certain. 
I have working faxs on my .cough ...win cough dows boxes... so I am not without. But this is now a mission!

---

### Post by sicofante on 2007-02-09
Well, I finally got my fax sent from a Windows computer. I'm most amazed by this issue now and I'm willing to put some effort on it in the near future. I have never developed for Linux but it might be an interesting experience, so I hope I get some spare time to do it soon.

Faxing is both the first big hurdle I've found with Ubuntu ("it just doesn't work") and a hard to understand one. I mean, I installed Ubuntu on my  little sister's computer. She's a musician and finding good notation software for Ubuntu is mission impossible, but I can understand that. It's a "niche market" and commercial developers don't have compelling reasons to do Linux versions of their software (and I don't expect them to have any for the next five years at least). But printing to a fax should be such a common feature of the OS itself that is hard to understand why it is so overlooked. Maybe young developers don't use fax any more?

Blaming winmodems for the issues is hard to understand for me too. If it's true that they do most of their work in software, why is it so hard to do that work under Linux? I mean, we have Wine which seems a lot bigger effort. What's it that makes winmodems so hard to master?

And don't forget my Ubuntu has detected a modem which is available to Networking (I haven't tried it yet for that function though).

---

### Post by chip616 on 2007-02-09
Phil:

> I actually tried the linuxant (FREE) driver earlier and my modem just stayed ON all the time. It was really irritating. 

Then it is a winmodem?  Junk it.  If you really NEED faxing, buy an external hardware modem.  They are not expensive.  If you NEED faxing, you can afford $50 to enable it.  :)  You can always take the external fax modem with you when you upgrade as well.

I got a couple of 56K USR external serial modems from the local computer recycler -- one for my business and one for my home office.  They work just fine.

---

### Post by Phil_McCrackin on 2007-02-09
@chip616

I'm not sure if it is a winmodem. There are Linux drivers for it (obviously linuxant has one with fax capabilities).

I'm not one to give up that easily. Where there is a will there is a way.

Faxing is a necessity for me, but like I said, I have windows machines and always will due to the nature of my profession. It's just that this is a hurdle to overcome. I am very pro-Linux and community-contributive software (not free). If it is expected that Linux will ever be what most Linux enthusiasts hope it will be, issues like this will need to be resolved. There are just certain things, like faxing, that should not be a problem. A fax/modem is equivalent, these days, technologically to a washing machine. There is just not that much to it. That's why you can pick one up for $5.

Apparently, there just has not been enough of a demand for this within the Linux culture. For some, like me, it is a necessity. At the very least a major convenience.

I appreciate the advice, but will elect to hold on to it and maybe figure it out and help some poor shmo like me with the same problem in the future. If nothing else, I can always drop it in another windows box.

---

### Post by tonywhelan on 2007-03-17
> **Irony said:**
> I don't know whether this helps;
[I]
System > Admin > Users and Groups > select your username > properties > user privileges > tick the send and receive fax[/I]

I notice that it is unticked by default.
-----------------------------------

Thanks for the above tip!

But for those people using HP multifunction devices with fax capability, and the HPLIP drivers/toolbox, it appears that faxing via HPLIP is broken in Edgy (6.10).  Apparently it worked in Dapper (6.06).

Quoting from: [http://www.mail-archive.com/hplip-devel@lists.sourceforge.net/msg00240.html](http://www.mail-archive.com/hplip-devel@lists.sourceforge.net/msg00240.html)

"faxing with HPLIP 1.6.7, 1.6.9, and 1.6.10 does not work at all with Ubuntu Edgy/6.10 .... on the transition from PyQt 3.15 to 3.16 a new bug was introduced which broke inter-process communication (IPC) between hpssd and hp-sendfax .... From PyQt 3.16 on, Fax jobs sent out by hpssd seem to run into a black hole instead of being picked up by hp-sendfax."

A new version of HPLIP 1.7.2 is available  from [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)
   1. Download the file to a convenient location (e.g., home directory or desktop, etc).
   2. Open a console/terminal and cd to the download directory.
   3. Type in and run this command: 'sh hplip-1.7.2.run'

Haven't tried it yet but it is supposed to fix the fax issue

Tony

---

### Post by vgrisham on 2007-03-17
Never mind.

---


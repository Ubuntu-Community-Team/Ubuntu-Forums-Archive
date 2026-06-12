---
title: "Can't get pSX, ePSXe, or PCSX to run at all.  Been trying all day, please help!"
date: 2010-12-20
forum: Gaming &amp; Leisure
---

### Post by thenumbereight on 2010-12-20
Hello,

Please forgive me if it's something bone-headed, but I've been trying all day to get a Playstation emulator working.  I can't even get any of the programs to start.

First off, YES I understand how the plug-ins work (in ePSXe and PCSX, obviously).  YES I (may or may not have) dumped the BIOS and placed it in the correct folder.  And YES I checked to make sure all the requirements were set.

I've tried every install guide I could find, but to no avail.

What happens is this:

I get everything installed; all the folders, the BIOS, plug-ins (if necessary) and what-have-you are in place, but when I try to run the executable file for PSX or ePSXe, absolutely nothing happens... whether it be from the terminal or the browser.  With PCSX, it brings up the configuration screen, but once I complete it and hit OK (or whatever the button says), the program disappears and again... nothing happens.

I'm running 10.04 (dual booted with XP) on a Dell Latitude from 2006.  This is not a configuration issue, mind you.

If anyone has any possible solution, I would really appreciate your help a whole lot.  I've spent countless hours trying to play PS on my machine, and I'm getting really close to giving up, at this point.

---

### Post by thatguruguy on 2010-12-20
what is 10?

---

### Post by Philsoki on 2010-12-20
> **thenumbereight said:**
> Hello,

Please forgive me if it's something bone-headed, but I've been trying all day to get a Playstation emulator working.  I can't even get any of the programs to start.

First off, YES I understand how the plug-ins work (in ePSXe and PCSX, obviously).  YES I (may or may not have) dumped the BIOS and placed it in the correct folder.  And YES I checked to make sure all the requirements were set.

I've tried every install guide I could find, but to no avail.

What happens is this:

I get everything installed; all the folders, the BIOS, plug-ins (if necessary) and what-have-you are in place, but when I try to run the executable file for PSX or ePSXe, absolutely nothing happens... whether it be from the terminal or the browser.  With PCSX, it brings up the configuration screen, but once I complete it and hit OK (or whatever the button says), the program disappears and again... nothing happens.

I'm running 10 (dual booted with XP) on a Dell Latitude from 2006.  This is not a configuration issue, mind you.

If anyone has any possible solution, I would really appreciate your help a whole lot.  I've spent countless hours trying to play PS on my machine, and I'm getting really close to giving up, at this point.

If the executable doesn't even open then you're missing the dependencies needed to run it. You need:

    OpenGL
    ALSA
    GTK
    GTKGLEXT
    libxml2

They should all be in the software centre.

---

### Post by thenumbereight on 2010-12-20
> **thatguruguy said:**
> what is 10?

I was meaning to say that I'm running Lucid Lynx 10.04... though I suppose the sidebar already tells all y'all that, doesn't it?  Sorry for the confusion... there are in fact other distros that start in "10." so, I should probably be more specific when referring to it.

---

### Post by thatguruguy on 2010-12-20
64-bit? 32-bit?

Any error messages when you're running whichever program from the terminal?

For what it's worth, I run pcsx-r without any significant problems.  It's available in 64-bit and 32-bit .deb files [here]("http://pcsxr.codeplex.com/releases/view/50048").  Since .deb files won't install if there are any missing dependencies, that potential problem will be avoided.

Prior to installation, I strongly suggest that you completely remove psx, epsxe and pcsx completely from your system, INCLUDING removing the .pcsx directory from your home folder.

---

### Post by thenumbereight on 2010-12-20
> **Philsoki said:**
> If the executable doesn't even open then you're missing the dependencies needed to run it. You need:

    OpenGL
    ALSA
    GTK
    GTKGLEXT
    libxml2

They should all be in the software centre.


I could've sworn I searched the software center for all 5 dependencies, finding checkmarks on all of them... but I suppose I could have mistook something for something else.  I'll check again.

---

### Post by thenumbereight on 2010-12-20
> **thatguruguy said:**
> 64-bit? 32-bit?

Any error messages when you're running whichever program from the terminal?

For what it's worth, I run pcsx-r without any significant problems.  It's available in 64-bit and 32-bit .deb files [here]("http://pcsxr.codeplex.com/releases/view/50048").  Since .deb files won't install if there are any missing dependencies, that potential problem will be avoided.

Prior to installation, I strongly suggest that you completely remove psx, epsxe and pcsx completely from your system, INCLUDING removing the .pcsx directory from your home folder.

The only error message I recall when trying to run the programs from the terminal was "no such file or directory exists", which clearly wasn't true, because I was copying and pasting the locations into a txt file, making sure the correct command was typed out, and then copying and pasting into the terminal.

Also, it's 32-bit.

Package Installer is working on installing the 32-bit .deb file, but it's been "unpacking" for a really long time.  Is that usual, or is something wrong?  Does that mean the dependencies aren't in place?  Package Installer is not frozen.

Also, thanks much for the help.

---

### Post by wingnux on 2010-12-21
You may try installing ePSXe 1.6.0 using this deb: [http://www.4shared.com/file/EuMKHEJH/epsxe-v160_all.html](http://www.4shared.com/file/EuMKHEJH/epsxe-v160_all.html)


Or the pcsx-Reloaded deb from here: [http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048)


Also, try installing the deb from the command line to see if there are any errors.

---

### Post by thenumbereight on 2010-12-21
> **wingnux said:**
> You may try installing ePSXe 1.6.0 using this deb: [http://www.4shared.com/file/EuMKHEJH/epsxe-v160_all.html](http://www.4shared.com/file/EuMKHEJH/epsxe-v160_all.html)


Or the pcsx-Reloaded deb from here: [http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048)


Also, try installing the deb from the command line to see if there are any errors.

Now, I have an entirely different issue and am unable to install from .deb files... woe is me.

It says "Only one software management tool is allowed to run at the same time", but the only software management tool I've run since the last time I had the package installer working was... the same program.  It ended up freezing when I gave up on waiting and tried to close it... I've restarted multiple times.  I'm sure there's some command I can put in the terminal to fix this, but I don't know what it is.  Anyone?  It would really suck, being unable to install using .deb files.

Thanks guys!

PS:  I do not know how to install a .deb from the command line.

---

### Post by wingnux on 2010-12-22
You may try running:
> sudo apt-get install -f to fix any previous install issues
> sudo dpkg -i *packagename.deb* to install a .deb file via the command line

---

### Post by thenumbereight on 2010-12-22
_
sudo apt-get install -f 
tim@tim-laptop:~$ sudo apt-get install -f 
[sudo] password for tim: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
tim@tim-laptop:~$ sudo dpkg --configure -a
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
tim@tim-laptop:~$ sudo dpkg -i /home/tim/pcsxr_1.9.92-1_i386.deb
(Reading database ... 
dpkg: warning: files list file for package `pcsxr' missing, assuming package has no files currently installed.
(Reading database ... 219940 files and directories currently installed.)
Preparing to replace pcsxr 2:1.9.92-1 (using .../tim/pcsxr_1.9.92-1_i386.deb) ...
Unpacking replacement pcsxr ...
_

That's what's up.
It gets stuck like that.
Also, now my Update Manager is screwing up...

Anyone?  I have no idea what's going on at this point.

---

### Post by inkrypted on 2010-12-22
I run PCSX and found the easiest way to install and keep updated was the Playdeb repository .

Link
[http://www.playdeb.net/updates/Ubuntu/10.10#how_to_install](http://www.playdeb.net/updates/Ubuntu/10.10#how_to_install)

seeing how you have trouble installing deb files you may have to follow the alternative method. also my launch command is "padsp pcsx" due to sound issues. also make sure your using a recommended video card like Nvidia or ATI (no integrated stuff). Best of luck.;)

---

### Post by thenumbereight on 2010-12-22
> **inkrypted said:**
> I run PCSX and found the easiest way to install and keep updated was the Playdeb repository .

Link
[http://www.playdeb.net/updates/Ubuntu/10.10#how_to_install](http://www.playdeb.net/updates/Ubuntu/10.10#how_to_install)

seeing how you have trouble installing deb files you may have to follow the alternative method. also my launch command is "padsp pcsx" due to sound issues. also make sure your using a recommended video card like Nvidia or ATI (no integrated stuff). Best of luck.;)

They make plugins for older video cards, though.

---

### Post by inkrypted on 2010-12-22
Very true the important words being video cards. Not integrated onboard stuff like Intel and the like. Even thought it emulates a PSX which is an older machine it still takes a pretty beefy machine to run it at a descent speed.

---

### Post by thenumbereight on 2010-12-22
So, after doing the things suggested to me on this thread, my Update Manager started saying it could only do a "partial upgrade".  I was confused by this.  I went ahead and proceeded with the "partial upgrade", and I get this error message:

"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first."

WTF?!?!?!

CAN SOMEONE PLEASE HELP ME?!  MY COMPUTER IS BLOWING UP!  I DON'T CARE ABOUT HAVING AN EMULATOR ANYMORE, I JUST WANT MY SYSTEM RESTORED TO WHERE IT WAS BEFORE I CAME TO THIS FORUM!

---

### Post by inkrypted on 2010-12-22
That happened to me once and I rescued my system by doing this command in terminal. It reinstalls and reconfigures all packages. Takes a while though.

sudo dpkg-reconfigure -phigh -a

you might try using this command first though.
sudo apt-get install -f

---

### Post by thenumbereight on 2010-12-23
Looks like I got the Update Manager problem fixed through that command.  Thanks!

I think those .deb packages might be outdated or corrupted.  That's what makes sense to me.  I can't see any other reason why the installer would keep freezing every time it tries to unpack the packages.

What I'm looking for is a new, short and simple tutorial for installing a Playstation emulator on Ubuntu.  I've read through a couple existing guides, but they simply didn't work, for whatever reason.  I know there are some of you out there that would go about installing it a certain way, and I'm just curious to know what an ideal installation process entails.  I don't mind installing it from a compressed file if that's the best way to do it.  I could just use some better instructions than the one's I've found thus far.  However, it is no longer urgent (nor was it ever in the first place, I suppose), because I think I'm discovering that my video hardware is far too archaic and inferior to perform at the kinds of speeds we're talking about here.  Other people might come across this thread for the same reason I posted it, though.

I greatly appreciate any and all help I've had here, and thank you guys taking the time out of your day to help with my silly computer problems.

---


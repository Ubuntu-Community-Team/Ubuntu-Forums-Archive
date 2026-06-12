---
title: "3D Acceleration Help - Intel i810 vs 3Dfx VooDoo2"
date: 2005-12-25
forum: Gaming &amp; Leisure
---

### Post by quincunx on 2005-12-25
I just recently started using Linux again, last time was in 1996; and tried a Fedora distro before installing Ubuntu.

In both distributions my 3D acceleration isn't set up to use hardware.  My motherboard is an Intel i810 with onboard video and AGP.  It's actually probably faster than the Diamond/3Dfx VooDoo2 accelerator card that I have, but after reading other peoples problems with the i810; maybe it's the better option.

I'm not sure what to set up, or how.  I've been attempting to get Wolfenstein Enemy Territory installed, since that's what I had on my Win98 install until a few days ago...figured it would be a good litmus test ;)

However, when I launch the program I get:

***********************************************************
You are using software Mesa (no hardware acceleration)!
Driver DLL used: libGL.so.1
If this is intentional, add   "+set r_allowSoftwareGL 1"
to the command line when starting the game.
***********************************************************

When I run the game with that option the opening menu is so slow it takes me 10 minutes just to exit.

With my previous distro, the research I did indicated that I need to install Glide, and compile Mesa to use Glide.  Anyone know how to do this, or if that's even if that's the best way to take care of this issue?

I've gotta play 3D games!  Right?

Thank you

---

### Post by snooze on 2005-12-28
Wow this takes me back.
If I remember correctly, the Intel is a 2d/3d solution, although very weak
in the 3d department.
The Voodoo2 was 3d only.
You needed a seperate 2d card and used an external video cable to join
the 2 cards together.

The Voodoo2 was awesome in it's day.

I'd like to suggest that you use the Voodoo2 together with your Intel
on-board video.

If you search the 'synaptic package manager' for '3dfx' you should find
the appropriate drivers to install automatically.

Hope this helps.

---

### Post by quincunx on 2005-12-28
[QUOTE=snooze]Wow this takes me back.
If I remember correctly, the Intel is a 2d/3d solution, although very weak
in the 3d department.
The Voodoo2 was 3d only.
You needed a seperate 2d card and used an external video cable to join
the 2 cards together.

The Voodoo2 was awesome in it's day.

I'd like to suggest that you use the Voodoo2 together with your Intel
on-board video.

If you search the 'synaptic package manager' for '3dfx' you should find
the appropriate drivers to install automatically.

Hope this helps.[/QUOTE]


My 3Dfx-Voodoo2 card is a "pass-through", and I've got the cable connected to the motherboard's monitor socket/port/plug; and the monitor plugged into the 3Dfx card.  From what I can tell, all of my graphics (execpt 3D) are being done by my i810.

When I do a search in Synaptic for "3Dfx" only one file came up and it's already installed.  From the reading online that I've done (mostly from pages and posts made prior to 2000) I need to have Glide installed, then install Mesa with the glide option.

From what else I can tell, Glide3 is for Voodoo3 and Glide2 is for Voodoo2.  The most current version of Mesa does not mention Voodoo2 support, only Voodoo3.  I attempted to install Mesa3.5, since version 3 was the newest one when the documents that I read were written.

During my last attempt at installing it I got errors (just after gpp printed it's "help" options) see [this post]("http://ubuntuforums.org/showthread.php?t=109241") for the out details.  I don't remember any errors during ./config.  There were some initially, but I took care of it by installing gpp.

I'll have to go back and look at the readme for ./config options, but some of the instructions conflict and I'm not sure which readme is correct.  There's "README", "README.3DFX", "INSTALL", "INSTALL.GNU", and I haven't read, "README.X11" and "README.THREADS" because I wasn't sure if they applied or not.

Thanks for you reply!  I was starting to wonder if anyone was going to post anything.

---

### Post by snooze on 2005-12-29
Sorry I wasn't any help. It appears you already did the easy stuff and
much of the hard stuff.

I did a search on the Ubuntu forums and found many others with similar issues.
No definative answers though.
At least you aren't alone.;) 

I admire you for getting this far.

Don't give up.

---

### Post by quincunx on 2005-12-30
[QUOTE=snooze]Sorry I wasn't any help. It appears you already did the easy stuff and
much of the hard stuff.

I did a search on the Ubuntu forums and found many others with similar issues.
No definative answers though.
At least you aren't alone.;) 

I admire you for getting this far.

Don't give up.[/QUOTE]
You were actually great help, I was starting to wonder if the "linux is supported by it's online community" was partial myth.   Since I saw other people getting help, but silence on my thread(s).  Especially for an issue related to hardware that used to be one of the _only_ ways to get 3D acceleration under Linux.

I'm still tracking down why I get errors during compile of Mesa, still assuming that doing so will get my 3D hardware accelerated.  If anyone knows of an easier way (without having to buy new hardware) please let me know :)

Thanks again,

Quincunx

---


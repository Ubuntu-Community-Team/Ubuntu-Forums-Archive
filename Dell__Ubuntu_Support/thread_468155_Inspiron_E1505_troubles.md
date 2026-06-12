---
title: "Inspiron E1505 troubles"
date: 2007-06-08
forum: Dell  Ubuntu Support
---

### Post by namelessone on 2007-06-08
So I just got one of Dell's new ubuntu laptops...and it worked great...until I downloaded the 50 updates that were available. One of the updates was a new kernel version and when I restarted my machine, it couldn't find any of the kernels (and thus wouldn't start) because of the screwy partition setup that Dell set up on the computer. Rather than editing the grub boot commands, I decided just to reinstall and make the partitions more logical. Now it all works great except for these two small sound issues--

when I push the sound button on the front of the laptop (I think dell calls it the media now interface or something like that) a little picture comes on the screen but it has an x by the speaker symbol and it doesn't let me change the volume. How do i fix this?

The second, and more important problem is one I noticed before I reinstalled everything: When playing games, sound is choppy. I tested on three games: Wesnoth, Chromium, and AstroMenace. playing mp3s n such works fine... it's just the sound in games. My limited experience says it would be a lack of ram, but this laptop has 2 gigs. Can anyone help me?

---

### Post by haftan on 2007-06-08
There is a documented fix for the first 50 updates that overwrite the menu.lst file and try to boot from the first hard drive (ubu default), rather than the third partition (dell design).


 
GRUB problem:
[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=9825](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=9825)

---

### Post by danielandrews on 2007-06-08
That really sucks that people's first experience with ubuntu + dell updates hoses their computer (although does have a pretty 'easy' solution).

---

### Post by namelessone on 2007-06-08
> There is a documented fix for the first 50 updates that overwrite the menu.lst file and try to boot from the first hard drive (ubu default), rather than the third partition (dell design).

Yeah...well I took it into my own hands and reinstalled. The real problem is that now the sound isn't working right...

---

### Post by camarojones on 2007-06-09
When you reinstalled, did you wipe and install, or use Dell's recovery?

With a wipe and install, the downloaded Ubuntu 7.04 disk recognized everything on my computer just as it came from Dell. I'm impressed in the hardware compatibility so far.

---

### Post by jpeddicord on 2007-06-09
The sound problem happens with games that use SDL-mixer and don't have the volume set to 100%. Affects intel sound chipsets.

The bug is located here, but it has never really received any attention.

[https://bugs.launchpad.net/ubuntu/+source/sdl-mixer1.2/+bug/66483](https://bugs.launchpad.net/ubuntu/+source/sdl-mixer1.2/+bug/66483)

Correction: As of re-testing, it also happens now even when sound levels are set to 100%. I'm searching the bug tracker for an update.

---

### Post by namelessone on 2007-06-11
> **camarojones said:**
> When you reinstalled, did you wipe and install, or use Dell's recovery?

With a wipe and install, the downloaded Ubuntu 7.04 disk recognized everything on my computer just as it came from Dell. I'm impressed in the hardware compatibility so far.

I did a whole wipe and install--and I am impressed with the hardware detection...

and that sound button randomly works now...it's just that skippy sound problem now...

---

### Post by loserboy on 2007-06-11
I guess this is fixed for inspirons shipped after 6-8-07 cuz mine is fine (yay)

---

### Post by hasimir44 on 2007-06-12
> I guess this is fixed for inspirons shipped after 6-8-07 cuz mine is fine (yay)

even after it's fully updated? did they change the partition layout? I'm curious because I just ordered one 3 days ago.

---

### Post by bunted on 2007-06-12
My 1505n is also functioning without the SDL problem I keep reading about.

---

### Post by loserboy on 2007-06-12
I haven't looked at the Grub layout yet but I will and I'll let you know, but yea I did my 54 updates with the workaround page sitting in front of me on my other comp....  and no need for it

eta: I mean partition layout

---

### Post by loserboy on 2007-06-12
oh also the Media direct button now by default opens Rhythmbox, so thats pretty cool I guess

---

### Post by loserboy on 2007-06-12
heres a screenshot of gparted on the Dell so you can see how all the partitions are setup, seems other people are curious so I may put this in a thread somewhere.

---

### Post by cody50 on 2007-06-12
how can I tell if my inspiron will be affected or not?

---

### Post by namelessone on 2007-06-13
> **cody50 said:**
> how can I tell if my inspiron will be affected or not?

well, pretty much just update it and see if it crashes. if it does, you can hit Escape when you restart your computer on the screen that says GRUB. Then scroll down in the menu, select "return to factory defaults" and press enter.

After that, just follow the aforementioned fix.

---

### Post by fjgaude on 2007-06-13
> **cody50 said:**
> how can I tell if my inspiron will be affected or not?

As best as we can tell, Dell has fixed the update issue on all boxes shipped after about 6/9/07. So from here on out kernel updates should go without a hitch.

frank

---

### Post by imsorryidontdowindows on 2007-06-13
I got mine shipped 06/11 i ran the updates and no problems.

> **loserboy said:**
> I guess this is fixed for inspirons shipped after 6-8-07 cuz mine is fine (yay)

---

### Post by dwhitney67 on 2007-06-16
I purchased my E1505 during the 06/2006 period with MS Windows MCE installed.  Last Saturday I waxed it and installed Ubuntu.  Everything worked fine, although I had to side-step a bit to get the appropriate video drivers from ATI (my system has the x1300).

So anyhow, I now have wireless, NTFS support (for an external drive), an SSH-daemon running, and an Apache server running.  All this in one day!

---

### Post by jazzcat on 2007-06-16
> **loserboy said:**
> oh also the Media direct button now by default opens Rhythmbox, so thats pretty cool I guess

Isn't the media direct key supposed to turn the machine on in a mode that it doesn't have to boot up to play DVD's?  Ours doesn't do this; it just turns the machine on.

---

### Post by jaybuntu on 2007-06-16
My E1505N worked fine after the first 50 updates as well.  All the media buttons work the way they should and I haven't noticed any problems with sound - although I'm not much of a game player.

---

### Post by R_U_Q_R_U on 2007-06-19
> **dwhitney67 said:**
> I purchased my E1505 during the 06/2006 period with MS Windows MCE installed.  Last Saturday I waxed it and installed Ubuntu.  Everything worked fine, although I had to side-step a bit to get the appropriate video drivers from ATI (my system has the x1300).

So anyhow, I now have wireless, NTFS support (for an external drive), an SSH-daemon running, and an Apache server running.  All this in one day!

Do you have a link for the ATI drivers? I am going to go a clean install with E1505 with the AT X1400 card.

Thanks.

---

### Post by meuge on 2007-06-20
Follow this guide...

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

If you run into the "white screen bug" when you start beryl, you can search for my posts, and I made a thread a couple of days ago with the solution.

---


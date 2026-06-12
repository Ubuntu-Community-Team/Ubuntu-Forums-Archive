---
title: "Wacked out display"
date: 2007-12-20
forum: Desktop Environments
---

### Post by DonDodge on 2007-12-20
A recent installation going on here and it's not going too well. I've been unable to run my preferred windoze screen resolution of 1152x864 @ 75 Hz so  I went looking for a driver that would allow it to function properly. I found ubuntu had set up some experimental intel controller so I changed it to the proper Intel 815 trying to match my Intel 82815. Logged off and back on and it didn't help. It only offered me 60 Hz.  Next try was  an Intel agp controller. Logged off and back on and my x server shut down and ever since then, I can't log on. The screen is all wonky and I can't see a thing to be able to fix anything. Nothing but lines jumping across the screen

Recovery  mode gives me nothing I can work with. It ends at a prompt after failing to load the display.

I booted with the live CD and found the controller was back to the Intel experimental thingy so I changed it  to the Intel 815. No matter what I do, the screen is crazy.

Anything I can do to rescue this installation short of doing a reinstall which wasts to repartiition my drive?

Oh yeah, I looked in the x files that should control the display and controller and it shows the proper controller.

---

### Post by as0l0 on 2007-12-20
you might want to use that recovery console to find a backup of xorg.conf and then copy that to /etc/X11

there's a chance that there will be one in your home directory /home/*username*

---

### Post by DonDodge on 2007-12-21
I don't have a hope in hell of finding that  file or doing anything with it from a command line. I also couldn't find anything remotely similar when booting from CD but I was locked out of a lot of places in my /Home directory because of not being able to log on.

Is there any way to do a repair installation of this silly operating system to avoid redoing all the partitions and starting completely from scratch? I hate to dial up and download all those stinkin' updates and packages again.

---

### Post by as0l0 on 2007-12-21
I'm not an expert, barely a beginner, but i'll tell you how i would find the file and move it

find / -name "xorg*"

it should find a few, then you basically need to copy it to the right spot

cp /whateverthelocationofthefilewas /etc/X11

so, if i found one in my home, then i might type.

cp /home/username /etc/X11

of course, you change out suername for whatever your username is.

there might be a repair option that i don't know about, but this way will no doubt be much faster.

---

### Post by DonDodge on 2007-12-21
Thanks. Before I tried that, I found this in an old post:
------------------------------------------------
If your X server is misconfigured, boot into recovery mode and run



dpkg-reconfigure -phigh xserver-xorg



and then



init 2
---------------------------------------------------

It worked. The backup files were in the same /etc/x11 directory as the xorg.conf file

---

### Post by as0l0 on 2007-12-21
ahh, brilliant.  glad you figured it out :)

---

### Post by Purplecatty on 2007-12-22
I had tried several suggestions from other blogs similiar what u did.  The monitor still off.  I suspected that old 17" Acer 76c monitor don't automatically adjust screen resolution if changed.  I got another old 17" monitor, Gateway Crystalscan from my parent.  I decided to swap to see how it works w/ Ubuntu.  It did works nicely regardless what screen resolution set.  Interesting cuz Acer or some monitor doesn't have automatic resolution while others can do automatically.

Suggestion:  If any of you are over the head with screen resolution issue, try swap to another monitor or get used monitor that would work w/ Ubuntu.

Thanks
Catty

---


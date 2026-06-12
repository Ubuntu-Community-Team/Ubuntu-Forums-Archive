---
title: "Need help replacing /usr/X11R6/bin/X please"
date: 2006-05-13
forum: Desktop Environments
---

### Post by Lordskull on 2006-05-13
So, I'm a newbie and managed to very handily destroy my X server file "/usr/X11r6/bin/X".

     All of my configuration files should still be set up. Can I just replace the binary "X" file? And if so where could I download just the X file? Or can I get it with apt-get somehow without having to replace all of the X11R6 type files? I don't have the Install CD or anything. I'm using Breezey 5.10, kernel 2.6.12-10-386. If that helps at all. 

     I was trying to fix my gamma, I remembered that the conf file I needed was X something. Went searching around. Saw Xorg, it sounded familiar. So I went to back it up before I touched it and my finger slip before I finished typing. So I backed it up to X. Thought I better clean up my mistake so "sudo rm X". 

     I knew it was an exe, and I wasn't going to be able to get into it but wanted to try anyways. By the way I did manage to find the right file and change my gamma.
I didn't have any problems until after rebooting to see if I had fixed the gamma, of course then I realized that I had screwed up.

Any help would be greatly appreicated. Thanks!

Here is the error messages just in case:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem ? Yes No

GDM: Xserver not found: /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 Error: Command could not be executed! Please install the X server or correct GDM configuration and restart GDM.

---

### Post by Lordskull on 2006-05-13
I searched around for answers before hand but with what I found most of the solutions were to replace large packets of files. I don't want to mess with the config files I have set up, before I removed X everything was working perfect (minus the gamma which even that I was just fixing with xgamma each session).

---

### Post by Lordskull on 2006-05-13
I tired removing xserver-xorg and replacing it. Also redoing dpkg-configure. again, no go. Apt-get won't replace the X exe I seemed to have erased. I'm sure if I can figure out what package it came with apt-get would be able to but I'm not finding any clues anywhere. 

I'm sure its just a one line simple fix to get this stupid file back, I can't find any mention of how to replace it in the forums or in the install guide or really anywhere I've looked. And its always the simple things no one ever talks about. 

Not sure what else to do short of just reinstalling all of Unbuntu. Which I really don't want to have to do, if nothing else than because I'd have to find all of my files via the command line to move them over to another partition. 

There is a site run by the X.Org guys ([http://www.x.org/)](http://www.x.org/)), but they just provide source code. So I'd have to rebuild my X file from that, and I'm not sure if its even possible or how I'd do it.

---

### Post by Lordskull on 2006-05-13
O.K. As stated in the earlier post it is in fact such a simple fix that no one had bothered to post about it. 

/usr/X11R6/bin/X is a link, nothing more. So after all that all I had to do was:

ln -s /usr/X11R6/bin/Xorg /usr/X11R6/bin/X

One of my Linux budies got a email of mine and was going to send me the file, after he navigated to it and saw that it was a link he laughed.

I did have to replace my new xorg.conf file with the back-up I had made when I started this whole deal. BUT! now all back as it should be. :) 

P.S. Thanks BEN!

---


---
title: "where can I get libmp3lame.so?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by king_aaronj on 2005-11-06
I want to be able to create mp3s in Audacity.  I don't can't find the libmp3lame.so file that it wants to work with mp3s.  Is there a place I can download it?  Or how do I go about this?  I've already searched google for answers, but can't seem to find any.  Also, all the threads on this site that I've seen about Audacity don't give me any answers. :confused:

---

### Post by ammiel on 2005-11-06
go to Applications -> Add Applications then go under File to Advanced, click on Search (to the top right) and type in lame, you should find liblame (or something along those lines) right click go to add for installation, click apply at the top, it will install..... then in Audacity go to export to mp3 and you'll get the dialog for libmp3lame.so... where it says filetype in the dialog go to show all files, find libmp3lame.so.0 and select it click ok, it'll say something about it not being libmp3lame.so dont worry about it, just proceed and everything should work!

---

### Post by king_aaronj on 2005-11-07
Ok, I tried what you said and the synaptic package manager doesn't find anything even close to liblame.  The closest was toollame.  I tried this but it didn't help at all.

Any other ideas?

---

### Post by RAOF on 2005-11-07
Do you have the universe & multiverse repositories enabled?  Look at the [installation howto]("http://help.ubuntu.com/starterguide/C/ch02.html").

The exact package you are after is "liblame0"

---

### Post by king_aaronj on 2005-11-07
Thanks!  I didn't have all the respositories set up, but now I do and I was able to find the package in Synaptic.

I also just tested exporting to mp3 in Audacity and it works fine.  Thanks a lot :D

---

### Post by MNGS on 2006-04-17
Ouch!

Okay, new guy, same problem, couldn't find liblame...

I've just tried everything suggested in this thread, thought I did the repositories thing right, but now when I try to open Synaptic, I get

-------
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
-------

Can I beg for easy, using small words, help???

All I wanna do is just get lame installed.

Thanks.

---

### Post by dcstar on 2006-04-17
[QUOTE=MNGS]Ouch!

Okay, new guy, same problem, couldn't find liblame...

I've just tried everything suggested in this thread, thought I did the repositories thing right, but now when I try to open Synaptic, I get

-------
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
-------

Can I beg for easy, using small words, help???

All I wanna do is just get lame installed.

Thanks.[/QUOTE]
Try removing the "us." from the first two repositories.

---

### Post by MNGS on 2006-04-17
Okay, I think I got it.

As long as we're talkin'... (new thread?)

Audacity finally works, but is overmodulated and seems to limit at like 50%

I'm going line-in...same mic and mixer, same way I do using Linspire (sorry), which works fine.

Is there some other Audio setting in Audacity...or in other guts here to fix this???

Thanks yet again!

---

### Post by heislord5 on 2006-04-21
if you guys actually post what packages you use and exactly how you navigated to it for people who come along, it would be helpful.  I always try to post my solution after I find one...not just say "never mind I got it to work." without any explanation to help the next guy down the road.

---


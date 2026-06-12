---
title: "No sound in Flash"
date: 2005-09-12
forum: Desktop Environments
---

### Post by Jackster on 2005-09-12
Hey people! I just installed Hoary onto my hard drive. It's the first distro I've used that installed without any problems. The only problem now is flash animation.

I went onto Weebls Stuff (c'mon, you know you love that site) and tried to watch a cartoon or two, but FF said I needed the Flash plugin, so I downloaded it, it installed, the flash animations were playing fine, except with no sound. ](*,) 

anyone got any advice?

Thanks,
Jack

EDIT: I've also noticed that ScummVM doesnt have any sound either  :?

---

### Post by Gamabunta on 2005-09-12
Ubuntu and Linux in general is famous for its incredible sound/multimedia problems.

The problem is with ESD (Enlightenment Sound Daemon). Type **sudo killall esd** in a terminal and it should work, but that disables sound for other applications, for some reason. Try consulting [this guide](http://ubuntuguide.org/#configuresoundproperly); it might help.

---

### Post by Toddy on 2005-09-12
Try this:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

---

### Post by Hairy_Palms on 2005-09-12
if u change all your programs to Alsa it gets rid of the problem too.

---

### Post by graigsmith on 2005-09-12
[QUOTE=Hairy_Palms]if u change all your programs to Alsa it gets rid of the problem too.[/QUOTE]
 
you can only change everything to alsa, IF you have hardware mixing.  if you don't only ONE program will be able to use the sound at once.  and that is usually ESD cause it starts first.  and lots of things fail to use esd, which is why it sucks.

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

this page lists all the creative labs sound cards that support hardware mixing.  if you are having sound problems- its likely your card only has software mixing (thats what esd is supposed to provide)

since esd sucks so bad, i would recommend trying to find any card you see on that list with a 3 by it.  because that one supports hardware mixing.  i was having tons of problems with a card that only had software mixing.  i pulled out the sound blaster live that i had stored in a box in my closet, installed that card and it started working flawlessly, i even disabled ESD.

---

### Post by Jackster on 2005-09-13
OK guys, I followed the Ubuntu Guide and it sorted my Flash sound problem. But I tried all your suggestions (except the Alsa one, as I only have onboard sound) and ScummVM still has no sound, I've tried two different games in ScummVM, but neither had sound. This is the only program (I think) that has no sound. 

Any further advice would be highly appreciated,
otherwise, I think it may just be a bug in ScummVM

Thanks,
Jack

---

### Post by graigsmith on 2005-09-14
some programs don't work with ESD.   i know dosbox does not.  this scummvm probably doesn't either.   if you kill esd's task it should release the sound device, then scummvm might be able to access the sound device, as long as some other program doesn't grab the sound device first.

---


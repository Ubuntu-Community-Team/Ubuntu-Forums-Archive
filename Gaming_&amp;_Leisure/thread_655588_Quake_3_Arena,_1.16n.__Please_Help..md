---
title: "Quake 3 Arena, 1.16n.  Please Help."
date: 2008-01-01
forum: Gaming &amp; Leisure
---

### Post by The Titan on 2008-01-01
Ive been searching and searching all over the web for someone with the same problem i am having with this and cant find anything.  I have successfully installed quake 3 point release 1.32 on my Ubuntu 7.10 box without ANY problems at all using the linuxq3apoint-1.32b.x86.run installer.  But when i do the same with the linuxq3apoint-1.16n.x86.run on my machine a small black box pops up and disappears very fast.  The only way i could get the box to stay there so i could read it is to use the -target option to extract the files to a directory.  From what i can tell it looks like the same error as the regular command but there isn't time to read that so here is the output of the command with the -target option:
```

titan@theDungeon:~$ ./linuxq3apoint-1.16n.x86.run -target quaketemp

(in the little box)
Creating Directory quaketemp
verifying archive integrity...tail: Warning: "+number" syntax is depreciated, please use "-n +number"
[: 122: 4183380385: out of range
OK
Uncompressing Quake III Arena Point Release 1.16n........................
./setup.sh: 9: function: not found
X86
press return to close this window...
(end of little box)

titan@theDungeon:~$ 


```

when I look in the folder where it has been extracted the setup.sh file is in fact there whether  that matters or not.  Any help is much appreciated. 

 Thank You,
 Dan

---

### Post by Sockerdrickan on 2008-01-01
[www.ioquake3.org](www.ioquake3.org) ;)

---

### Post by The Titan on 2008-01-01
that installs version 1.34.....  thanks anyways

---

### Post by Sockerdrickan on 2008-01-01
chmod +x linuxq3apoint-1.16n.x86.run

---

### Post by BreathEasy on 2008-01-01
Really, really old Linux install scripts will not work with modern distros due to significant changes in the commands/shells the scripts use since then. I've had similar issues with a few older installer scripts too.

Any particular reason you need such an out-of-date version? Just curious.

---

### Post by The Titan on 2008-01-01
Yes, i need to run it so i can run a noghost server.  Besides, its hard to enjoy the new versions they went so crazy with features i think anyways... Im a little bit old school :P.   Thank you for a response that dosent treat me like an idiot by the way, that explains whats going on.  I think all i need is the executable right?  I may be wrong but if anyone has a copy i would really like to give it a try.  The executable is the only thing that changed, they just added new .pk3's for the new point releases.

---

### Post by BreathEasy on 2008-01-01
Yes, it's very likely the executables for the game will work fine, it's just the installer that's stopping you. My advice? Find an old copy of Debian or another distro released around the same time as Quake 3. Install that in a virtual machine like VirtualBox, run the setup, then somehow copy the files back onto your regular system. They should work fine.

---

### Post by The Titan on 2008-01-01
Excellent Idea, Thank You

---

### Post by Sockerdrickan on 2008-01-01
> **The Titan said:**
> Excellent Idea, Thank You
Did you even try
chmod +x linuxq3apoint-1.16n.x86.run
then sh linuxq3apoint-1.16n.x86.run
it might work

---

### Post by kernelpasha on 2008-01-16
i am still searching solution for this. But i couldnt even get close to solution. As a result, i guess, i have to find already installed old linux and copy some files. Is there a way to modify 1.16n installer? Any idea? By the way i got this error:

---

### Post by smokey2k on 2008-04-26
hi kernelpasha!

Im reedited the linuxq3apoint-1.16n.x86.run to a simple tar package.
You can download from here: [http://smokey.uw.hu/stuffz/linuxq3apoint-1.16n.x86.tar](http://smokey.uw.hu/stuffz/linuxq3apoint-1.16n.x86.tar)

---

### Post by Sp@rK on 2008-10-29
hi, for the same reason (Im playing on noghost servers) im also trying to get the 1.16 on my ubuntu.

Smokey, once i have uncompressed your .tar, i guess i have to put my pak0.pk3 from my q3 cd into the baseq3 folder and then how do i launch the game???

---


---
title: "How to find all installed programs in Ubuntu"
date: 2009-05-29
forum: General Help
---

### Post by Danial on 2009-05-29
Hi,

Can anyone guide me on how to list/print or catalog all the installed applications on current system (8.10)?  What I am after is to write down all the applications/programs I have installed on this system before I do a clean install of Ubuntu 9.04 on a new HD.  I know there are few default programs and then some I added as time passes by. Now I want to setup a system with minimum overhead and junk; so a listing of the installed program can help me to determine which and what I need to install after the OS is installed.

Your help, time and guidance is very appreciated in advance (because you have helped me too many times in the past :-$ - Yes I am a noob :???:

Danial

---

### Post by TeoBigusGeekus on 2009-05-29
If you go to System -> Administration -> Synaptic
there should be a filter to show you the installed applications on your system.

---

### Post by meeples on 2009-05-29
also in add/remove applications at the top drop down box where it says what kind of apps to show (canonical maintained etc) theres an option to select installed apps, and it lists what is installed on your machine :)

---

### Post by DeMus on 2009-05-29
> **TeoBigusGeekus said:**
> If you go to System -> Administration -> Synaptic
there should be a filter to show you the installed applications on your system.

Yes, when you open Synaptic you get a listing of all programs avalaible. The ones marked with a green square in front of them are installed.
Click with your mouse on the column head of the green dots column and the list will be sorted according to that column: hence all installed programs are listed together.

---

### Post by bowens44 on 2009-05-29
from terminal:

This will list all installed

 dpkg --get-selections

This will direct it to file

 dpkg --get-selections > filename

---

### Post by Danial on 2009-05-29
Hi,

**Thanks a lot** for the help and pointing out the solution.

In Synaptic, however, I do see all the installed libraries and dependencies (and honestly, I don't know what do they do), so that may be a little sifting thru.  Add/Remove is a choice here.  Now expanding my question further, how do I print?  Synaptic gives an option to "generte package download script", however, I am not able to execute it properly.

Any more words for this noob here ...

Danial

---

### Post by Danial on 2009-05-29
> **bowens44 said:**
> from terminal:

This will list all installed

 dpkg --get-selections

This will direct it to file

 dpkg --get-selections > filename

Thanks bowens... that nailed it....

Once again, I appreciate great help from all of you....

Danial - a happy puppy now

---

### Post by CatKiller on 2009-05-29
To re-mark the packages from the list on the new system,

```

 dpkg --set-selections < filename

```
should do it.

---

### Post by Danial on 2009-05-30
> **CatKiller said:**
> To re-mark the packages from the list on the new system,

```

 dpkg --set-selections < filename

```
should do it.

Hey guys/gals...

You are good....
Thanks a lot for the help and giving the perfect path for finding and restoring... Really thanks a bunch...

I am on my way to wipe the drive clean and do a fresh install... 

\\:D/

Danial

---


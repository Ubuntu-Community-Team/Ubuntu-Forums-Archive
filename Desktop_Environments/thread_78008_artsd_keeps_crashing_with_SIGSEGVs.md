---
title: "artsd keeps crashing with SIGSEGVs"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Takis on 2005-10-17
I don't think there's anything I can easily change that will fix up a seg fault, but before I put in a bug report, is there anyone else who's been experiencing this? Maybe I've gone and done something wrong accidentally.

---

### Post by sinbad782 on 2005-10-21
I'm getting this ever since I installed the KDE 3.5 Beta 2 packages - it's a bit of a nightmare bug to have. After a while a box came up asking if the system should just disable arts - I did this, but I haven't been able to use AmaroK since. 

Hopefully there'll be a fix soon!

---

### Post by sal on 2005-10-21
[QUOTE=sinbad782]I'm getting this ever since I installed the KDE 3.5 Beta 2 packages - it's a bit of a nightmare bug to have. After a while a box came up asking if the system should just disable arts - I did this, but I haven't been able to use AmaroK since. 

Hopefully there'll be a fix soon![/QUOTE]

you could use Juk. it's prity much the same. alsa if you use Amarok can't you just pipe the sound through alsa?

---

### Post by z-vet on 2005-10-21
Well, i upgraded to KDE 3.5 Beta 2 too and had the same error. The problem is that there are some programs that failing to start without aRts (KDED, KNemo...). The solution for this problem is to downgrade aRts to it's previous version:
```
sudo dpkg -i /var/cache/apt/archives/*arts*.91-*deb
```
as described on [this page](https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems).
If dpkg fails saying it can't find it, just download aRts packages from any KDE mirror and install them with dpkg. 
Now everything works fine here... :)

---

### Post by beefsprocket on 2005-10-22
Just a quick note for those who haven't gone through beta 1 to beta 2: you have to add the beta 1 repository and then lock arts, and libarts (2 packages in the lib section I think) to the .91 version instead of .92. 

To reenable sound after it is disabled, go to system settings --> sound and multimedia --> system notifications --> the player settings button. Choose use the KDE sound system. 

Again, make sure to LOCK your arts and libarts to .91 else the next time you upgrade without remebering, you'll break it again (until a bugfix anyways).

Hope this helps, should I add it to the beta2 wiki?

---

### Post by Hobbsee on 2005-10-22
[QUOTE=beefsprocket]Hope this helps, should I add it to the beta2 wiki?[/QUOTE]

Yes, definitely

---

### Post by Paulus on 2005-10-22
hmm yeah, I had to disable arts, but amarok continued to work :)  btw i am using xine-output-streamer thinggy!

---

### Post by Takis on 2005-10-25
Yeah all seems to be well for the moment. Thanks people!

---

### Post by MButterman on 2005-10-26
I love the new KDE 3.5 but I have had the same issues with the sound. I tried to look for package and found one for hoary. Will this package work with breezy? I looked for the last stable version of arts as a reference. When the sound error occurred, I first removed the arts package and then disabled sound using Kcontrol. If I could get a step by step how-to to correct the problem, I would appreciate it greatly. 

MButterman

---


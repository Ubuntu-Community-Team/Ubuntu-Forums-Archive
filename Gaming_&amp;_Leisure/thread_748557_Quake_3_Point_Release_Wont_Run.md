---
title: "Quake 3 Point Release Wont Run"
date: 2008-04-07
forum: Gaming &amp; Leisure
---

### Post by dlovley on 2008-04-07
Hi Everyone,

I am trying to install quake3 arena to run native on ubuntu heron. I ran quake three data which installed all of my files under user/share

/games/./usr/share/games/quake3
/usr/share/games/quake3/baseq3
/usr/share/games/quake3/baseq3/pak0.pk3
/usr/share/games/quake3/baseq3/pak1.pk3
/usr/share/games/quake3/baseq3/pak2.pk3
/usr/share/games/quake3/baseq3/pak3.pk3
/usr/share/games/quake3/baseq3/pak4.pk3
/usr/share/games/quake3/baseq3/pak5.pk3
/usr/share/games/quake3/baseq3/pak6.pk3
/usr/share/games/quake3/baseq3/pak7.pk3
/usr/share/games/quake3/baseq3/pak8.pk3

The point release file was automatically downloaded to by quake-data to the root folder. When I try to run the point release to set it up I get the same error. 

darrel@Rig:~$ sudo /root/linuxq3apoint-1.32b-3.x86.run
sudo: /root/linuxq3apoint-1.32b-3.x86.run: command not found

I have read a ton of articles on doing this but its probably something I am doing wrong.

-D

---

### Post by DoktorSeven on 2008-04-07
You have to either set the file as executable:

```
sudo chmod 755 /root/linuxq3apoint*.run
```
then run as you tried...

or run using **bash**:
```
sudo bash /root/linuxq3apoint*.run
```

By default, nothing downloaded is executable directly, you have to make it that way (or if it's a script, run it with its interpreter, as this file is).

---

### Post by disturbedite on 2008-04-07
i'd recommend not using the official q3 release.  please see my post here:
[http://ubuntuforums.org/showthread.php?p=4637809#post4637809](http://ubuntuforums.org/showthread.php?p=4637809#post4637809)

---

### Post by dlovley on 2008-04-07
Ok, 

I have the ioquake file set to install aftermaking it executable (by right clicking etc.). Its on my desktop  and says it wants to install a path to my home folder. Does it need to be moved into baseq3 before running it? If so whats the cmd?

-D

---

### Post by dlovley on 2008-04-07
Update,

I just installed it to the home directory like it asked. Then I copied the pak0 file into it and attempted to run it in console using ioqake3 but it woulld not open. I then went into the actual ioquake folder and clicked the executable icon and the game fired right up for me. So I just made a link to the desktop of the executable to run off of. 

Is there some reason it wont fire from the console cmd that I should be concerned about? 

Thanks so much for the help.

-D

---

### Post by disturbedite on 2008-04-08
you're prolly not executing it properly if it isn't launching from term.
please post the command you executed to try to run it.

---


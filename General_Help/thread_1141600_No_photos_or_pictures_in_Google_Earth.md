---
title: "No photos or pictures in Google Earth"
date: 2009-04-28
forum: General Help
---

### Post by sh-tfish on 2009-04-28
I have just installed Google Earth 5.0. from medibuntu repos. Unfortunatelly I cannot see any photos or pictures on objects wondows. Instead of pictures only "?" sign is shown ([see screenshot]("http://img299.imageshack.us/img299/7210/googleearth.png")). Does anybody know solution of this problem? Thanks a lot.

PS: 
I am using Ubuntu 9.04 JJ 64bit
I prefer "point and click" solution, but I can use terminal if needed

---

### Post by fireoftroy on 2009-04-30
I installed GE 5 using the same method and have the same problem.  If I click the ? it lauches the respective website and I can see it just fine.  I have 9.04 JJ 32bit with NVIDIA GeForce 9500M GS and driver version 180.  Thus far everything else appears to work fine (and I must add that the rendering is faster and 1000X smoother than it is in winblows mista :P).

---

### Post by jespdj on 2009-04-30
Sorry, no solution to the problem, just a Me Too.... :(

I'm running 64-bit Jaunty with Google Earth from Medibuntu, and any pictures and photos show up as a "?", just like you describe.

---

### Post by El Zoido on 2009-04-30
+1

---

### Post by fireoftroy on 2009-04-30
I have an open thread in the Google Earth Help forum as well.  If I learn anything I'll be sure to post it here.

---

### Post by fireoftroy on 2009-04-30
I updated my winblows xp machine at work to GE5 and verified that it was rendering in openGL.  The pictures work fine there.  I'm starting to think the GE5 package in Medibuntu has a bad link to the Panoramio site since the icon seems to indicate a missing link and all other graphical items work fine, including 3D buildings.  I'll keep ya posted as I learn more.

---

### Post by jespdj on 2009-05-02
Look at this [bug report](https://bugs.launchpad.net/medibuntu/+bug/358749).

There are workarounds in the bug report! ;) I fixed it by replacing the content of the file /usr/share/googleearth/qt.conf with the following:
```
[Paths]
Documentation=/usr/share/doc
Libraries=/usr/lib32
Plugins=/usr/lib32/qt4/plugins
Translations=/usr/share/qt4/translations
```
(Do this with: **gksu gedit /usr/share/googleearth/qt.conf**, then delete the content of the file and replace it with the above).

Note, this fix is for 64-bit Ubuntu, for 32-bit Ubuntu you should probably change the occurrences of "/usr/lib32" to "/usr/lib" (not tested, I don't have 32-bit Ubuntu installed).

---

### Post by Mangust22 on 2009-05-02
> **jespdj said:**
> Ubuntu you should probably change the occurrences of "/usr/lib32" to "/usr/lib" (not tested, I don't have 32-bit Ubuntu installed).

Thanks a lot. Works for 32-bit.

---

### Post by fireoftroy on 2009-05-02
I looked at the bug report and one person posted:

"i just deleted the /usr/share/googleearth/qt.conf file and the problem cleared right up.

type: sudo rm /usr/share/googleearth/qt.conf"

I did this command and it solved the problem for me. :)  (I was going to rename it as I don't like outright deleting files but it only contained '[PATH]' so I was willing to try it.  Glad I did!)

---

### Post by sh-tfish on 2009-05-03
> **fireoftroy said:**
> I looked at the bug report and one person posted:

"i just deleted the /usr/share/googleearth/qt.conf file and the problem cleared right up.

type: sudo rm /usr/share/googleearth/qt.conf"

I did this command and it solved the problem for me. :)  (I was going to rename it as I don't like outright deleting files but it only contained '[PATH]' so I was willing to try it.  Glad I did!)

Unfortunatelly neither removing or editing qt.conf worked for me. :(

---

### Post by fatphilthethird on 2009-05-03
> **fireoftroy said:**
> I looked at the bug report and one person posted:

"i just deleted the /usr/share/googleearth/qt.conf file and the problem cleared right up.

type: sudo rm /usr/share/googleearth/qt.conf"

I did this command and it solved the problem for me. :)  (I was going to rename it as I don't like outright deleting files but it only contained '[PATH]' so I was willing to try it.  Glad I did!)

Had the same problem and this solution worked for me too.

---

### Post by fireoftroy on 2009-05-03
> **sh-tfish said:**
> Unfortunatelly neither removing or editing qt.conf worked for me. :(

Just a stab in the dark, but do you have the ubuntu-restricted-extras in the medibuntu repository installed?  What about qt4-qtconfig?

---

### Post by cariboo on 2009-05-03
Me too, thanks that worked for me.

---

### Post by sh-tfish on 2009-05-04
> **fireoftroy said:**
> Just a stab in the dark, but do you have the ubuntu-restricted-extras in the medibuntu repository installed?  What about qt4-qtconfig?

Yes I have both installed. Look [_there_]("http://img384.imageshack.us/img384/6592/restrictedextras.png"), [_there_]("http://img133.imageshack.us/img133/1607/qt4.png") and [_there_]("http://img87.imageshack.us/img87/8628/qt4menu.png"). 

I even tried to uninstall Google earth (with remove configuration files option) in Synaptic and deleted ".googleearth" dir in my home folder. It did not do the job. Problem is still there no matter what I am trying to do with qt.conf. It looks I have to vait for newer version in repos.

---

### Post by harecanada on 2009-05-05
jespdj,
Just wanted to thank you for this fix. It worked great for me. I'm still such a newbee and I'll never understand how you guys figure out these fixes.
Thanks again,
harecanada

---

### Post by harecanada on 2009-05-05
jespdj,
Now if we could handle video clips that come up in Panoramio that would be great. I get YouTube videos and they are blank with the little checkmark in them.
What do you think? Is there a simple solution to that too?
harecanada

---

### Post by jespdj on 2009-05-07
The bug has been fixed and a new version of Google Earth 5 is available in Medibuntu! :) See [the bug report](https://bugs.launchpad.net/medibuntu/+bug/358749).

If you just run the Update Manager (System > Administration > Update Manager) you should see an update for Google Earth, which will fix the problem.

---

### Post by jespdj on 2009-05-07
Grrr! :( The patch that I installed from the update does not work, in fact it breaks my manual fix.

Besides replacing the content of /usr/share/googleearth/qt.conf with this:
```
[Paths]
Documentation=/usr/share/doc
Libraries=/usr/lib32
Plugins=/usr/lib32/qt4/plugins
Translations=/usr/share/qt4/translations
```
I now also have to make a symbolic link to make it work again:
```
cd /usr/lib32/googleearth
sudo ln -s ../../share/googleearth/qt.conf qt.conf
```
Note, this is for **64-bit**. For 32-bit Ubuntu, just deleting qt.conf might work. (I don't know, I didn't test it on 32-bit Ubuntu).

---

### Post by harecanada on 2009-05-07
I tried this but still can't get the videos to play. Not sure what to do . The pics are fine though.
harecanada

---

### Post by sh-tfish on 2009-05-09
> **jespdj said:**
> Grrr! :( The patch that I installed from the update does not work, in fact it breaks my manual fix.

Besides replacing the content of /usr/share/googleearth/qt.conf with this:
```
[Paths]
Documentation=/usr/share/doc
Libraries=/usr/lib32
Plugins=/usr/lib32/qt4/plugins
Translations=/usr/share/qt4/translations
```I now also have to make a symbolic link to make it work again:
```
cd /usr/lib32/googleearth
sudo ln -s ../../share/googleearth/qt.conf qt.conf
```Note, this is for **64-bit**. For 32-bit Ubuntu, just deleting qt.conf might work. (I don't know, I didn't test it on 32-bit Ubuntu).


Thanks a lot! Finally solution that works for me! :D

---

### Post by calibansfolly on 2009-05-13
Hi. Found this thread after installing ge5 today, and it seems to be right up my alley. Except that I don't see this file: /usr/share/googleearth/qt.conf  

Am I missing something? Is it possible the file is in a different place now?

---

### Post by DeMus on 2009-05-13
> **calibansfolly said:**
> Hi. Found this thread after installing ge5 today, and it seems to be right up my alley. Except that I don't see this file: /usr/share/googleearth/qt.conf  

Am I missing something? Is it possible the file is in a different place now?

How did you install it? Did you use sudo sh gog...bin or without sudo?
Without sudo it is installed in your homedirectory. Have a look there.

---

### Post by Menthu_Rae on 2009-05-16
> **calibansfolly said:**
> Hi. Found this thread after installing ge5 today, and it seems to be right up my alley. Except that I don't see this file: /usr/share/googleearth/qt.conf  

Am I missing something? Is it possible the file is in a different place now?

> **DeMus said:**
> How did you install it? Did you use sudo sh gog...bin or without sudo?
Without sudo it is installed in your homedirectory. Have a look there.

Jaunty 64-bit here, with ubuntu installed from the repos several weeks ago. Manually editing my qt.conf (which was blank originally!) with the text below and then creating the symbolic link fixed it for me. :D

> **jespdj said:**
> Grrr! :( The patch that I installed from the update does not work, in fact it breaks my manual fix.

Besides replacing the content of /usr/share/googleearth/qt.conf with this:
```
[Paths]
Documentation=/usr/share/doc
Libraries=/usr/lib32
Plugins=/usr/lib32/qt4/plugins
Translations=/usr/share/qt4/translations
```
I now also have to make a symbolic link to make it work again:
```
cd /usr/lib32/googleearth
sudo ln -s ../../share/googleearth/qt.conf qt.conf
```
Note, this is for **64-bit**. For 32-bit Ubuntu, just deleting qt.conf might work. (I don't know, I didn't test it on 32-bit Ubuntu).

---

### Post by sornen on 2009-06-17
ty the editing and linking fixed it for me on 64 bit jaunty.

---


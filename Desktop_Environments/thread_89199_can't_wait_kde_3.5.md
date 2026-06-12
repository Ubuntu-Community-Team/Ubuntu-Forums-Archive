---
title: "can't wait kde 3.5"
date: 2005-11-12
forum: Desktop Environments
---

### Post by Josef K. on 2005-11-12
kde 3.5 first release candidate is out :KS
since I miss _so_ much adblock function I can't wait to try it
anybody try it? any comment?
if I'd find it too unstable (how) can I go back to old version? :confused:

---

### Post by skyboy on 2005-11-12
well, I ugraded this morning and for few hours now, I found it very stable already. Arts is working again :)
Everything is working like a charm.

---

### Post by dr.drake on 2005-11-12
how do we upgrade to this version?
(I'm still running the version that came with the kubuntu breezy install...)

eric. (forever noob)

---

### Post by Rob2687 on 2005-11-12
Download this
**[http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg](http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg)**
Run this
**sudo apt-key add kubuntu-packages-jriddell-key.gpg**
Add this to your apt/sources.list
**deb [http://kubuntu.org/packages/kde35rc1](http://kubuntu.org/packages/kde35rc1) breezy main**
Run this
**sudo apt-get update**
**sudo apt-get upgrade**

---

### Post by dr.drake on 2005-11-12
hmmmm....
> 
Preconfiguring packages ...
(Reading database ... 94470 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.3-0ubuntu1 (using .../kdelibs-data_4%3a3.5-rc1-0ubuntu0breezy1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.5-rc1-0ubuntu0breezy1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/crystalsvg/22x22/apps/kmenu.png', which is also in package kicker
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.5-rc1-0ubuntu0breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I reckon this means it didn't work?

eric.

---

### Post by ace2005 on 2005-11-12
/var/cache/apt/archives/kdelibs-data_4%3a3.5-rc1-0ubuntu0breezy1_all.deb

Same here, i went into the failsafe terminal and ran adept, clicked on Full Upgrade and it gave me the same error, clicked on Full Update again and it worked ok. I don't know whats wrong but i'm in KDE now and it seems ok.

Could it have been something to do with adept using the KDE skin?

---

### Post by ace2005 on 2005-11-12
My Konqueror won't stop crashing, it starts fine but the second my mouse goes over a icon it will just fade out and the crash dialogue will come up.

My Juk will not start at all, just the crash diaogue

My synaptic will give a segmentation fault but will work if i use sudo synaptic

And on top of that there is something wrong with fonts or whatever
> couldn't open fontconfigs chosen font with Xft!!!

So i guess its not been so fun upgrading, the previous version worked fine

---

### Post by Jeff Eklund on 2005-11-13
[QUOTE=ace2005]My Konqueror won't stop crashing, it starts fine but the second my mouse goes over a icon it will just fade out and the crash dialogue will come up.[/QUOTE]Hey! I recognise that problem ;-)
Check [this thread]("http://ubuntuforums.org/showthread.php?t=88813") out.

---

### Post by Josef K. on 2005-11-13
I got it! :KS 
I've just installed kde 3.5 and works sweet
expecially konqueror-adblock (I've simply imported firefox filterset from [http://www.pierceive.com/filtersetg/](http://www.pierceive.com/filtersetg/) and goodbye to adv! \\:D/)

just one thing: sometimes my desktop flash and loose icon and wallpaper image for a couple of second :confused:

anybody experience this bug?!

---

### Post by cowlip on 2005-11-13
[QUOTE=Josef K.]I got it! :KS 
I've just installed kde 3.5 and works sweet
expecially konqueror-adblock (I've simply imported firefox filterset from [http://www.pierceive.com/filtersetg/](http://www.pierceive.com/filtersetg/) and goodbye to adv! \\:D/)

just one thing: sometimes my desktop flash and loose icon and wallpaper image for a couple of second :confused:

anybody experience this bug?![/QUOTE]

yes disable sound previews undeer configure desktop

---

### Post by rosslaird on 2005-11-13
To continue a previous issue:

Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.91-0ubuntu1_all.deb

The wiki solution...

"kdelibs has a file conflicting with kttsd. Install it with dpkg --install --force-overwrite /var/cache/apt/archives/kdelibs-data_4%3a3.4.91-0ubuntu1_all.deb"

does not work on my system:

dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.91-0ubuntu1_all.deb (--install):
 cannot access archive: No such file or directory

Suggestions anyone?

Ross


Solved:

sudo dpkg --install --force-overwrite /var/cache/apt/archives/kdelibs-data_4%3a3.5-rc1-0ubuntu0breezy1_all.deb

---

### Post by Josef K. on 2005-11-14
I had the same error message when I logged out kde and tried an apt-get update  (but the conflict was with a custom cursor set :confused: )
I didn't forced anything, simply log in kde and run update from adept (not the updater)
adept went fine (but icons on my desktop are still flashing :( )

---


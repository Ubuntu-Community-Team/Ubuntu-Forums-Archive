---
title: "KDE fails to start"
date: 2010-09-14
forum: Desktop Environments
---

### Post by hamiljf on 2010-09-14
Two problems really.  Just upgraded kubuntu to Lucid and found no KDE installed: bad news: if you're on kubuntu KDE should be upgraded automatically.  So using kpackagekit in gnome installed the standard metapackage and got the option to log in with KDE (good news) but then KDE failed: segmentation fault in knotify4... it would not report the error: too little information.  it dropped me back into an incomplete gnome environment (no top and bottom tool lines).
Any ideas ?
And has kubuntu been abandonded ??

---

### Post by ankspo71 on 2010-09-14
Hi,
> And has kubuntu been abandonded ?? 
Kubuntu continues to live on... I'm using Kubuntu Maverick Beta.

I recommend backing up your files now, just in case you will end up doing a clean install of Kubuntu Lucid. By the way, it might be a good idea to download the Kubuntu Lucid live cd to see if you still have the segfault problem while logging into a KDE live session.

Did you get any error messages during the upgrade process? I have a feeling it is probably a failed upgrade, since you mentioned your KDE packages didn't get upgraded automatically, and you are left with an incomplete gnome desktop. I don't know if this could explain the segfault in knotify4 though. 

Do you get any error messages if you use this command in a terminal?
```
sudo apt-get dist-upgrade
```

If none of this helps, just consider this a bump for your post.

---

### Post by ianmillington on 2010-09-14
Some things to try

I'm assuming you were using karmic previously and had not before the upgrade updated KDE from 4.3 to 4.4?

There is a difference in structure between the 2 - in particular 4.4 introduced the package "plasma-desktop" which wasn't in 4.3. Without it, plasma won't start. 

First

sudo dpkg --configure -a

in case any packages got broke in the upgrade (possible)- if that doesn't work

Then 

sudo apt-get install plasma-desktop 

If that doesn't fix it try 

sudo apt-get install kubuntu-desktop

If none of the above sort it out a possible cause is a conflict in your KDE config.

From within gnome (my command line expertise is pretty basic - sorry)rename the hidden file /home/.kde/config which will effectively reset your kde settings. Hopefully you will be up and running then.

---

### Post by wayward4now on 2010-10-03
[QUOTE=ianmillington;9844408]Some things to try

From within gnome (my command line expertise is pretty basic - sorry)rename the hidden file /home/.kde/config which will effectively reset your kde settings. Hopefully you will be up and running then.

I found it was ~/.kde/share/config that you have to mv to another directory name like config.old

Today KDE just failed to crank up (Lucid) period. So, I fired up Gnome, which worked just fine, opened a terminal, made the change and I'm back up and running. I did have to re-config the desktop, but it's running. I have no clue what happened to break it. :) Ric

---

### Post by ianmillington on 2010-10-03
Sorry about that, I was working at an XP box at the time.

Glad you found the right file.

---


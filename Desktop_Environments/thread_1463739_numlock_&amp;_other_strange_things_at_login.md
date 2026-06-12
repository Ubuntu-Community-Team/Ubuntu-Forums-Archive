---
title: "numlock &amp; other strange things at login"
date: 2010-04-27
forum: Desktop Environments
---

### Post by Lokesh123 on 2010-04-27
Hi,
being new to Linux I tried out different things, e.g. KDE and Gnome in parallel....was no good idea. Even though I purged everything from KDE, there are residual changes that I can't get under control. As I installed the whole kde desktop plus kdm (resulting in kubuntu greeting). All that contains kde or kubuntu has been removed again.

1) numlock s set at login (I have an Apple keyboard without the numlock). Correspondingly, the backround colour of the task panel is white. Opening the keyboard settings, i.e. not doing anything else, in the System Preferences releases numlock and the panel backround turns into black. At the same time, the image for the speaker loudness changes.
After log-out log-in the same situation as before. Weird:confused:

2) in Cairo-dock the images were also changed by the KDE installation. After (!) opening and closing the keyboard settings the images change to the defaults when I do right click, modify, apply. I change nothing in the settings! E.g. the symbol for Evolution is an envelope with a clock in front, after the change it is just the envelope as was before I installed and removed KDE.

Any ideas?

My System: apple Intel iMac coreduo2, ubuntu karmic koala AMD64, gnome desktop, apple keyboard white 2006

---

### Post by P4man on 2010-04-27
This might be a pain to figure out. Perhaps you can try this "quick fix":

```
sudo aptitude reinstall ubuntu-desktop
```

Not much hope, but worth trying.

---

### Post by Lokesh123 on 2010-04-27
Its funny, but I realised that ubuntu-desktop is not even installed. I assumed it is by default???

Maybe I give it a try.

---

### Post by P4man on 2010-04-27
ubuntu-desktop is a meta package. IT just contains all packages installed by default, so if you uninstalled a bit too much, that should reinstall them. Im also hoping, reconfigure some things, but I honestly dont know if it does.

---

### Post by Lokesh123 on 2010-04-27
> **P4man said:**
> This might be a pain to figure out. Perhaps you can try this "quick fix":

```
sudo aptitude reinstall ubuntu-desktop
```

Not much hope, but worth trying.

Unfortunately, it did not help. I installed ubuntu-desktop, shut down and turned on, it took quite long at the first time to show the desktop, i.e. something was going on. 

But the issue remains.

---

### Post by dE_logics on 2010-04-27
Man you're having one helluva problem... really unique.

But this appears to be a gnome issue you know.

How about - 

apt-get autoremove

---

### Post by P4man on 2010-04-27
> **Lokesh123 said:**
> Unfortunately, it did not help. I installed ubuntu-desktop, shut down and turned on, it took quite long at the first time to show the desktop, i.e. something was going on. 

But the issue remains.

I didnt really expect anything else, but was worth the small effort. Lets try something else; create a new user, and log in with that user. Do you have the same problem?

---

### Post by Lokesh123 on 2010-04-28
Apologies for the late reply, I was travelling the whole day.

> **P4man said:**
> create a new user, and log in with that user. Do you have the same problem?

No! Different user, more luck.

---

### Post by P4man on 2010-04-28
well, then its something in your user settings. Dont ask me what. you could try copying files from one home folder to the other until the problem appears with the other user (dont forget to change ownership). or just stick with the new user and copy the files you need, unless someone has a better idea.

---

### Post by Lokesh123 on 2010-04-29
It seems that removing kde is the most difficult if not impossible thing!

I did a re-install of all installed packages, which resulted in complete re-installation of KDE! I had purged them before!?

Ok, run apt-get --purge remove kde*

After that the synaptic package manager does not show any kde package. But when I search for kde* files in the file manager, tons of them are still around, including desktop config files etc. 

Thats not an impressing package management. As it looks, the only way to get rid of the kde/gnome interference in a reasonable way is to wipe out the whole installation and start all over again with a fresh installation.

So the lesson learned: stay away from parallel installation of gnome and kde.

Sh...

---

### Post by rnerwein on 2010-04-29
hi
got i similar problem with lynx beta 2.
my solution was:
[COLOR=Blue]sudo /bin/bash[/COLOR]
mv my_home_dir  __my_home_dir
mkdir my_home_dir
[COLOR=Blue]chown my_username:my_groupname my_home_dir[/COLOR]
[COLOR=Blue]exit[/COLOR]
logout
login   ( i got a brand new gnome environmen - but keeped my user-id )
copy back my stuff
you can then try to copy back !!! but step by step all the .files ( dot files ) login logout ..... to see wich one caused the fault.
but this i think that you don't really want that.
have fun
ciao

---

### Post by P4man on 2010-04-29
> **Lokesh123 said:**
> It seems that removing kde is the most difficult if not impossible thing!

Ok, run apt-get --purge remove kde*

After that the synaptic package manager does not show any kde package. But when I search for kde* files in the file manager, tons of them are still around, including desktop config files etc. 

I dont think its a given any KDE package starts with kde. many start just with k and depend on other kde packages.

Instead, try this:

```
sudo apt-get autoremove kubuntu-desktop
```

Have a look at the packages it suggests to remove before accepting it though, you never know.

---


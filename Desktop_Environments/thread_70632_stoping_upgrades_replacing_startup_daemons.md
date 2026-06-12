---
title: "stoping upgrades replacing startup daemons"
date: 2005-09-30
forum: Desktop Environments
---

### Post by dninja on 2005-09-30
I occasionally use apache on my desktop so I have it installed but I've removed the startup script from the rc?.d directories. Whenever I do an upgrade the upgrade puts the links back.

It does this for all the other daemons I don't want starting automatically as well such as mysql, at and others.

I understand why it does this and belive that, by default, it should probably keep doing this. What I'm wondering is, is there some magic setting somewhere to stop it. I've now come to the point of having a script, called exorcise, which I run after upgrades to remove all the unwanted daemon startup scripts.

I guess I could probably make some fixed files in place of the startup symlinks which may stop it, I don't know if it would delete a file that it needed to replace.

Anyone else have this problem? Any other solutions?

---

### Post by mlomker on 2005-09-30
> Any other solutions?

Have you tried chmod'ding the directories to read-only?

EDIT: Nevermind...I don't see any way to revoke permissions from root and apt-get runs as root.

---

### Post by az on 2005-09-30
update-rc.d [-n] [-f] servicename remove

---

### Post by mlomker on 2005-09-30
[QUOTE=azz]update-rc.d [-n] [-f] servicename remove[/QUOTE]

The OP said that they've already removed the scripts.

---

### Post by dninja on 2005-10-01
[QUOTE=mlomker]The OP said that they've already removed the scripts.[/QUOTE]

Ye, I know how to remove them I'm just trying to stop them coming back. Next time I see that something like apache is going to be updated I'm going to try creating a file in place of the symlink and setting the file permission to read only. I know that apt-get runs as root but it may just check to see if the file exists and create the symlink if it doesn't.

---

### Post by mlomker on 2005-10-01
I suppose you could just put an empty file (or perhaps with an echo to /dev/null) in /etc/init.d and point the symlink at it.

---

### Post by dninja on 2005-10-01
ye, an option.
I guess from this though that no one know of a "correct" solution to this using existing flags or settings and whatever I do will have to be a hack of some kind. Thats ok, as long as I'm not missing something obvious I don't mind doing it my own way :)

---

### Post by mlomker on 2005-10-01
> I guess from this though that no one know of a "correct" solution to this using existing flags or 

I'd imagine that the *correct* option would be to either remove the package or lock it in Synaptic so that it no longer upgrades.  It didn't sound like you wanted to do either of those.

---

### Post by dninja on 2005-10-01
No, I want to keep things installed.

Basically I have a devlopment server which gets used 99% of the time, if I want to play with some config changes or for some reason the server is down I use my local box. I want to keep the box up-to-date just disabled till I need it.

Thanks for the info.

---

### Post by az on 2005-10-02
[QUOTE=dninja]ye, an option.
I guess from this though that no one know of a "correct" solution to this using existing flags or settings and whatever...[/QUOTE]


I just read the update-rc.d manual:  The correct way:

       If  any  files  /etc/rcrunlevel.d/[SK]??name already exist then update-
       rc.d does nothing.  This is so that the system administrator can  rear&#8208;
       range  the links, provided that they leave at least one link remaining,
       without having their configuration overwritten.

...
Any  files  in  the /etc/rcrunlevel.d directories that are not symbolic
       links to the script /etc/init.d/name will be left untouched.

---

### Post by dninja on 2005-10-02
[QUOTE=azz]I just read the update-rc.d manual:  The correct way:

       If  any  files  /etc/rcrunlevel.d/[SK]??name already exist then update-
       rc.d does nothing.  This is so that the system administrator can  rear&#8208;
       range  the links, provided that they leave at least one link remaining,
       without having their configuration overwritten.

...
Any  files  in  the /etc/rcrunlevel.d directories that are not symbolic
       links to the script /etc/init.d/name will be left untouched.[/QUOTE]
That sounds good to me, my little plan should work a treat :-)

---


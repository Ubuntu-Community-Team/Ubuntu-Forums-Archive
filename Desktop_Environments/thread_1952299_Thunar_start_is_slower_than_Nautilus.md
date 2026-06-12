---
title: "Thunar start is slower than Nautilus"
date: 2012-04-04
forum: Desktop Environments
---

### Post by fomik on 2012-04-04
Hi,
I've moved to the Xfce as many people says that it's faster, but first thing which I noticed was that the Thunar starts several seconds (for the first time during the session). But when I moved to the Gnome, Nautilus starts immediately when the double click is made. What's wrong there? How can I speed the Thunar's (first) start?

Thanks for help.

---

### Post by sudodus on 2012-04-04
Maybe because Nautilus is already running in gnome de. (I think it is managing the desktop.)

In my computer with Ubuntu 10.04 LTS Nautilus is running without any file browser window open. You can test it with
```
ps -A | grep nautilus
```

I guess you can test if the second Thunar window is opened faster than the first one.

For me it is important to be able to play high definition video, and Xubuntu is better than Ubuntu and Kubuntu, but Lubuntu with LXDE is better than Xubuntu.

---

### Post by brainwash on 2012-04-04
This question has been already answered many times. For example here:

[http://ubuntuforums.org/showthread.php?t=1859528&page=12](http://ubuntuforums.org/showthread.php?t=1859528&page=12)

---

### Post by Morbius1 on 2012-04-04
There is one thing that slows Thunar down and it can be changed but it depends on when you want the delay to occur.

When Nautilus opens it opens to the filesystem and does not check to see if there are any networked resources available. If you want to browse your lan you select Browse Network and it then does a search and that could take some time.

When Thunar opens it checks to see if there are any networked resources available automatically and will not render until it either finds them or convinces itself that there aren't any.

You can change Thunar's behavior by editing a file as root:
```
gksu leafpad /usr/share/gvfs/mounts/network.mount
```and changing this:
> [Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
AutoMount=trueTo this:
> [Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
[COLOR=Blue]**#**[/COLOR]AutoMount=true
[COLOR=Blue]**AutoMount=false**[/COLOR][COLOR=Blue]*I commented out ( # ) the AutoMount=true line just in case you decide to go back to the way it was by default.*[/COLOR]

---

### Post by UbuntuPaul on 2012-04-27
> **Morbius1 said:**
> There is one thing that slows Thunar down and it can be changed but it depends on when you want the delay to occur.

When Nautilus opens it opens to the filesystem and does not check to see if there are any networked resources available. If you want to browse your lan you select Browse Network and it then does a search and that could take some time.

When Thunar opens it checks to see if there are any networked resources available automatically and will not render until it either finds them or convinces itself that there aren't any.

You can change Thunar's behavior by editing a file as root:
```
gksu leafpad /usr/share/gvfs/mounts/network.mount
```and changing this:
To this:
[COLOR=Blue]*I commented out ( # ) the AutoMount=true line just in case you decide to go back to the way it was by default.*[/COLOR]

I want to thank you from the bottom of my heart Morbius1 ... 1) I'd never "done anything" like that before (editing in Leafpad) .. and 2) IT WORKED. It's been driving me nuts since XUB 12.04B2 (I had 15 good months with Ubuntu 10.10 and felt I "needed" to upgrade but I hate Unity, so Xubuntu it is) :-)

Cheers and best regards to you. Folders opened right up, "whizzo." Thank you.:guitar:

---


---
title: "Ubuntu Desktop ?"
date: 2005-02-24
forum: Desktop Environments
---

### Post by ThePainter on 2005-02-24
Hi,
I have hit this problem a few times now.
It all started when I prefered Thunderbird to Evolution and someone told me you could uninstall Evolution but when I tried it uninstalled the Ubuntu Desktop and I only got a prompt when I tried to boot up.
Now I am not happy with the fact that Totem freezes on just about every media file I offer it so I use VLC but again some one told me to try to install Totem-Xine instead of Totem-gstreamer cos its better.
Again when I try this it threatens to uninstall ubuntu-desktop.

Is there a way to dispose of these unwanted apps ?

If I uninstall ubuntu desktop and install Gnome desktop at the same time will I be able to boot into that instead or does that have a collection of tied apps as well.

I thought Linux was supposed to give you more freedom to configure your system the way you want to but this is more restrctive than XP ?

---

### Post by poofyhairguy on 2005-02-24
[QUOTE=ThePainter]Hi,
I have hit this problem a few times now.
It all started when I prefered Thunderbird to Evolution and someone told me you could uninstall Evolution but when I tried it uninstalled the Ubuntu Desktop and I only got a prompt when I tried to boot up.
Now I am not happy with the fact that Totem freezes on just about every media file I offer it so I use VLC but again some one told me to try to install Totem-Xine instead of Totem-gstreamer cos its better.
Again when I try this it threatens to uninstall ubuntu-desktop.

Is there a way to dispose of these unwanted apps ?

If I uninstall ubuntu desktop and install Gnome desktop at the same time will I be able to boot into that instead or does that have a collection of tied apps as well.

I thought Linux was supposed to give you more freedom to configure your system the way you want to but this is more restrctive than XP ?[/QUOTE]


ubuntu-desktop is a meta package. That means that you can install a lot of other packages by installing it. It does nothing itself. I've unistalled it on every Ubuntu Box I've touched, and no problems. 

Also I would recommend that you don't use totem at all. Use xine-ui or (my favorite) gxine, or mplayer. I've never gotten totem to not suck.

---

### Post by adbak on 2005-02-24
[QUOTE=ThePainter]Hi,
I have hit this problem a few times now.
It all started when I prefered Thunderbird to Evolution and someone told me you could uninstall Evolution but when I tried it uninstalled the Ubuntu Desktop and I only got a prompt when I tried to boot up.
Now I am not happy with the fact that Totem freezes on just about every media file I offer it so I use VLC but again some one told me to try to install Totem-Xine instead of Totem-gstreamer cos its better.
Again when I try this it threatens to uninstall ubuntu-desktop.

Is there a way to dispose of these unwanted apps ?

If I uninstall ubuntu desktop and install Gnome desktop at the same time will I be able to boot into that instead or does that have a collection of tied apps as well.

I thought Linux was supposed to give you more freedom to configure your system the way you want to but this is more restrctive than XP ?[/QUOTE]
 Uninstalling Ubuntu-desktop is okay.  Ubuntu-desktop is what's called a "meta package", it's a package where you can click to install it and it will install all things under that.  I guess you can consider a meta package to be an umbrella that is really just a group of programs.  It's just under a meta package to make it easier to install.

As far as uninstalling Evolution, I believe you can do that and I don't believe uninstalling Evolution is what broke your Ubuntu, it was probably something else done since you last rebooted.  But you should have plenty of space on your hard drive so that you don't have to  uninstall Evolution.

Also, if you're looking for a multimedia player, I highly recommend GXine.  You can apt-get it (or use Synaptic) and it plays pretty much any multimedia file.

---

### Post by ThePainter on 2005-02-25
Hi,
I know Im naughty I should have done a search for this subject first but I did know after.
Anyway I found a thread on my first problem and apparently Evolution is part of the Gnome package and if you uninstall it you uninstall al the Gnome package with it, but apparently you can uninstall the mail part by itself.
Anyway I have since then startedusing Evolution mail and apart from the fact that it doesnt import contact lists from "Outlook Express" ( sorry for swearing there) It is in my opinion a better mail client to Thunderbird. For one you can click on a link in a EMail and it will open Firefox at that page where as with Thunderbird you have to copy the link and paste it into your browser. This is so even in XP.

Anyway Ive drifted off subject.
I am now wondering if I remove totem and install xine does it come with its own codecs or do I still need all the gstreamer plugins etc.
Ive found that Rythmbox doesnt work with mp3's without them.
Ill give it a go today and see what happens.

There seems to be different Xines like gxine etc. Are they all the same but with different gui's so it is only their appearance that is different ?

---

### Post by ThePainter on 2005-02-25
Hi,
Sorry for putting this in the wrong message board, Thanks for moving it.

OK Ive uninstalled Totem and installed Xine and uninstalled all of the gstreamer stuff apart from two which threaten to remove nautilus and the control panel, and xine still plays everything.
Its great it does everything that VLC does and more. It plays real and shoutcast and comes with its own list of radio stations and it also plays WMV which VLC will only play the audio. and it plays DVD's OK. It also plays .asx and saves its own playlists in this format where as VLC wont save playlists.

So anyone (like me) who wanted a good player without all the work involved in installing MPlayer should try this one.

One thing though, when uninstalling a few of the gstreamer things, Sound juicer, Rythmbox and Gnome media are removed so becareful to check whats been uninstalled if you use these, I dont so I let them go.

---

### Post by ThePainter on 2005-02-25
Hi,
Ive found one strange thing with it.
I had the sym link set up for the DVD as shown at "ubuntuguide" and VlC and Xine could open and play DVD's fine from both of my Disc drives.
I have two the slave can do everything and the Master can do eveything but burn DVD's.
Anyway after uninstalling all the gstreamer stuff I try to play a DVD on my Master CD drive and it errors with "Cant start xine Engine" ? but it plays them fine on my slave drive ?
strange ?
Even if I try to open the .vob as a file it does the same.
Both drives mount the DVD in nautilus OK as files.

This isnt a problem but it is strange, does anyone have any ideas what has caused this ?

---


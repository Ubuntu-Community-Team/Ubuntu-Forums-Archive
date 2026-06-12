---
title: "Mediaplaying in Ubuntu"
date: 2005-11-25
forum: Desktop Environments
---

### Post by Mackan on 2005-11-25
Ok, just wondering a little. I recently installed Ubuntu Breezy, and as with all other distros, browser plugins for playing multimedia files in firefox are not installed, and a working mediaplayer with codecs is not installed either. I have read there are some license issues, but not sure if that is the whole story.

So, I check the synaptic package manager. I see the official ubuntu repository is already there. I start search for mplayer or totem-xine, which some people have recommended. But no results. No vlc either. Does this mean that I have to add some kind of unofficial repository to synaptic in order to get these packages? And since it is not official packages, I may break unbuntu, and/or complicate things when I upgrade the dist in 6 months or something?

Is this basically the case, what I have written above? Or are there official working mediaplayers with codecs and plugins available for ubuntu, and I just have to add some other official repository?

Thanks if anyone can provide some light over this.

/Mack

---

### Post by earobinson on 2005-11-25
As for your first Q read this [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

As for installing the codecs i searched the forums for (codecs) and i found this [http://www.ubuntuforums.org/showthread.php?t=75278&highlight=codecs](http://www.ubuntuforums.org/showthread.php?t=75278&highlight=codecs)

---

### Post by Zotova on 2005-11-25
[QUOTE=Mackan]So, I check the synaptic package manager. I see the official ubuntu repository is already there. I start search for mplayer or totem-xine, which some people have recommended. But no results. No vlc either. Does this mean that I have to add some kind of unofficial repository to synaptic in order to get these packages? [/QUOTE]

Yes, you do have to add more repositories to ubuntu to get things like totem, vlc etc

```
sudo gedit /etc/apt/sources.list
```

Your sources.list file should look something like this:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

```

With the new additions in your sources.list the media players you are after will now be available to install. Windows codecs will not be available however, so for those codecs use the links the earobinson supplied. Hope that helps.

---

### Post by frodon on 2005-11-25
You can use the plf repositories to install restricted formats like w32codecs, libdvdcss2, ...
[http://ubuntuforums.org/showthread.php?t=81577](http://ubuntuforums.org/showthread.php?t=81577)

---

### Post by Mackan on 2005-11-25
Thanks for the replies guys. :smile: I will take a look on it now. I am mostly concerned with mixing unofficial packages with official, but hopefully it will not cause any troubles on my system. 

/Mack

---


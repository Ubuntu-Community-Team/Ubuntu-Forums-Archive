---
title: "Need Mplayer Installation Instructions"
date: 2006-03-10
forum: Desktop Environments
---

### Post by galume on 2006-03-10
Hi,

I am trying to open up a radio station's media player, and I get the error:

Totem could not play
'fd://0'.
No decoder to handle stream...yada yada yada :( 

The web site says:

Question: How do I stream if I am a LINUX user?
Answer: You can download the mplayer plug-in for Firefox.
[http://www.linux-sxs.org/multimedia/mplayermozplug.html](http://www.linux-sxs.org/multimedia/mplayermozplug.html)

Oh, that's all?  Just go to that site?  Cool....:-D 

Yeah right!  Does anyone know of more gooder instructions for installing mplayer and the mozilla plug-in?  A search of the forums didn't yeild much, except I did get a page with some packages, but again, there's no instructions with any of them.:confused: 

BTW, the site I'm trying to install for is: [www.kfiam640.com](www.kfiam640.com).

Are there any better howtos out there than one that starts off like:
1) Build & install a fully functional copy of MPlayer, then just....

Thanks and have a good weekend!

---

### Post by hw-tph on 2006-03-10
Enable the universe and multiverse repositories. Then install mplayer and mozilla-mplayer (the latter installs mplayerplug-in).


Håkan

---

### Post by galume on 2006-03-10
Sorry, I should have mentioned that I tried that...

It just errors out...something about the package or repository not being available...

---

### Post by galume on 2006-03-10
Here's the output when trying to enable the multiverse & universe:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

Click OK, then:
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

After that I go to Add Apps & check off MPlayer and get this:

This program is currently not installable, but should be available in the 'multiverse' repository. Would you like to enable this repository?

Back to square one.  Tried enabling the multiverse & universe several times but it's always the same thing...:( 

Galume

---

### Post by ronmarley1 on 2006-03-10
galume,
You might want to look at Automatix.  See this thread -->[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)
It's a nice little script that will install a bunch of stuff for you, including MPlayer and the MPlayer plug-in for Firefox.  Please read the thread before installing.  Some folks don't like it (I do).

---

### Post by galume on 2006-03-13
Thanks Dude.  Tried it.  Got this:

"Resolving beerorkid.com... failed: Temporary failure in name resolution."

I'll try again later :???: 

Oh, somehting in Linux didn't install right...what a surprise.

---

### Post by ronmarley1 on 2006-03-13
I just tried the link, and the site seems to be up now.  1:45 PM EST.

---


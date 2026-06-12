---
title: "Just deleted all of /var/cache/apt/archives"
date: 2008-12-27
forum: General Help
---

### Post by Ghostknyght on 2008-12-27
Like a fool I've been using the root account as my default account, and have just deleted the /var/cache/apt/archives folder during the install of a program (calibre).  The install asked to be directed to a folder, which it would empty out then install. I forgot to dictate another folder and just had the contents of the archives deleted. 

1. is this a really bad thing?
2. How can I easily fix this problem?
3. in the future is there another place I can install things?

---

### Post by RealPSL on 2008-12-27
The command ```
sudo apt-get clean
``` cleans that directory for future reference. You can see this by running ```
man apt-get
``` and reading the section on clean.

That directory just contained packages you have installed on the computer post installation and could have been deleted. However, I do not recommend install other software there because it should only be used by apt to cache files for installation.

---

### Post by cb34 on 2008-12-28
everything you've ever downloaded/installed using synaptic or apt-get or ADD/REMOVE is kept in the apt/cache folder.. just the install files, not the program/s.
just means if you uninstall n reinstall something, it has the packages there already, and no need to download off the net from the ubuntu repo's. everything can and will be downloaded again if you reinstall.. you just erased your backed up .deb install files, which are all available from the ubuntu repos at any time. :D

---

### Post by Ghostknyght on 2008-12-30
Whew, thanks alot, that eases alot off of my mind, especially as I just encountered the problem with removing a program that came with the add/remove. Does anyone have any advice as to a good location for installing apps and whatnot?

---

### Post by sdennie on 2008-12-30
As stated above, blasting /var/cache/apt/archives shouldn't cause you any harm.  Usually anything in a "cache" directory implies that it can be gotten from the original source again (but, at a lower speed if it was gotten from the cache).

Common places to install applications locally are ~/bin or a subdirectory under ~/bin (and then a subsequent symlink/helper script in ~/bin to the executable in the subdirectory), /usr/local is also common as is /opt on some Unix variants.  I really prefer the ~/bin method for a single user machine because it reminds you that the things there were installed outside of the normal packaging system and make it less likely that things you install will clobber installed software in unexpected ways.  You will also need to make sure that ~/bin is in your path to make that method feel like the rest of the system.

---

### Post by cb34 on 2008-12-30
> You will also need to make sure that ~/bin is in your path to make that method feel like the rest of the system. just to continue with this thought and help any future time consuming investigations..LoL
~/.profile has these lines in it, or at least mine does.. and i think any ubuntu install should, or maybe just intrepid not sure, don't remember if hardy has these lines.
```

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```
(if /home/username/bin directory exists, then add it to the path.)

---


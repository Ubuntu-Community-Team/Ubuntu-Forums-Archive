---
title: "Wine questions (hopefully very simple)"
date: 2006-03-07
forum: Desktop Environments
---

### Post by Ruskie on 2006-03-07
Hello,

I installed wine time ago and forgot about it.
Now I'd like to use it again, but I can't remember which program I already installed and which I didn't! Or, I know I installed Total Commander, but I don't remember the executable name and therefore I don't know how to launch it.
My question are: 
1) Is there a way to get a list of all the installed program?
2) If I uninstall wine (remove of the wine package), what happens to all the Windows program I installed (and to the fake windows disk)? Are they erased as well?
3) How can I locate the position of the fake windows disk?

Thank you very much
Marco

---

### Post by towsonu2003 on 2006-03-07
[QUOTE=Ruskie]
3) How can I locate the position of the fake windows disk?
[/QUOTE]
I guess 3rd one is key. look under ~/.wine/drive_c
all instalkled programs are in Program Files folder
.wine folder will stay when you uninstall it, but a new version of wine may not be compatible with the old .wine directory. what I do is: just back up that folder and remember the wine version, delete .wine folder, instakll new version, winecfg, use setup executables to reinstall the programs when you install the new version of wine (if you do).

---

### Post by Ruskie on 2006-03-07
Thank you, will try it this evening.

---

### Post by linuxfanatic1024 on 2006-03-10
The version in the Ubuntu repositories is woefully out of date. It is an alpha version. (Wine is now in beta.) I recommend doing this if you're using the apt wine:

```

$ sudo su

# echo "deb http://wine.sourceforge.net/apt/ binary/" >> /etc/apt/sources.list

# apt-get update

# apt-get upgrade

# exit

```

The "sudo su" to get a root shell is necessary because the echo command wouldn't work without it.

---


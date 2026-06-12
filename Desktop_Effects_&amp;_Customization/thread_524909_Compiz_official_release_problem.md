---
title: "Compiz official release problem"
date: 2007-08-13
forum: Desktop Effects &amp; Customization
---

### Post by MeathooK427 on 2007-08-13
I'm having a problem w/ the official release of compiz fusion. Whenever I execute "fusion" my window borders disappear. I've added the composite extension in my xorg as well as argb. Here's the terminal log whenever I execute fusion. Any help would be appreciated.

```
* nvidia found, exporting: __GL_YIELD="NOTHING"
* Executing: compiz --replace --sm-disable --ignore-desktop-hints ccp
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"
compiz (core) - Error: Couldn't load plugin 'ccp'

```

---

### Post by Happy_Man on 2007-08-13
How did you install it?

---

### Post by MeathooK427 on 2007-08-14
[http://ace2016.net/tutorials/linux/how-to-install-compiz-fusion](http://ace2016.net/tutorials/linux/how-to-install-compiz-fusion)

I followed that guide.

---

### Post by bricksen on 2007-08-14
when I try to download this nessecery package I get this?

[email]bricksen@bricksen:~/.comp[/email]iz_compile$ git://anongit.opencompositing.org/fusion/compizconfig/libcompizconfig git clone
bash: git://anongit.opencompositing.org/fusion/compizconfig/libcompizconfig: No such file or directory

---

### Post by MeathooK427 on 2007-08-14
I don't think I'd follow that guide if I were you, considering I'm having problems with it ;)

---

### Post by tekkenlord on 2007-08-15
Meathook427, the page you linked has three screenshots of compiz fusion in action. How can one get the effect showed in the second and third picture? Thanks!

---

### Post by petit.padavoine on 2007-08-15
The second and third screenshots show
Flip 3D (a clone of the Windows Vista effect)
and Cover Flow (a clone of the iTunes effect).

Both are part of the Shift Switcher plugin.

If you don't have the Shift Switcher plugin, I guess you're using Amaranth's repositories. Switch to Trevino's.

Meathook, you didn't compile the official release, you compiled a development version (from the git repository).

Try installing from the repositories ([http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz-Fusion_.28a_Compiz-Beryl_fusion.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz-Fusion_.28a_Compiz-Beryl_fusion.29)) or compiling the official release ([http://releases.compiz-fusion.org/0.5.2/](http://releases.compiz-fusion.org/0.5.2/))

---

### Post by MeathooK427 on 2007-08-15
No, I didn't compile from the git repositories in his follow through, I downloaded the source from the compiz-fusion website. Maybe there's something else conflicting in that guide. I don't know. My install won't boot past the login screen anymore anyways. Have to figure that out first :(

---

### Post by daradib on 2007-09-05
> **MeathooK427 said:**
> 
```

compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"

```

See this:
> **grdnwsl said:**
> Apparently Compiz-Fusion is undergoing a rewrite of the compiz-core module.  Apparently this has broken compiz-fusion on quite a few machines.  I'm having the same problem with the same error and this started happening after upgrading from a working installation to the latest packages.  Compiz-Fusion is still ALPHA software, so expect breakage as the developers work things out.

Here's a link to one of the developer's blogs:
[http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/](http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/)

---

### Post by daradib on 2007-09-06
```
compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"
```
To solve this problem, you can do the following:

Uninstall Compiz

```
sudo apt-get --purge remove compiz* libcompizconfig0 libdecoration0
```
then

```
sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev
```
Put this whole string in terminal, if it fails remove the filenames that it fails on and run it again until it works.

Then follow this howto ([http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)) to install a backported "stable" compiz from Gutsy.

Read the howto and do the setup stuff at the end carefully where he covers the window frame problem.

Taken from the following post on Ubuntu Forums ([http://ubuntuforums.org/showpost.php?p=3317998&postcount=32](http://ubuntuforums.org/showpost.php?p=3317998&postcount=32))

---

### Post by Inxsible on 2007-09-07
It would be a better idea if this command was simulated rather than executed

```
sudo apt-get --purge remove -s compiz* libcompizconfig0 libdecoration0
```

---

### Post by daradib on 2007-09-07
You have a good point. You could try not doing that step, but following the instructions on the page I linked to see if it fixes the problem.

---


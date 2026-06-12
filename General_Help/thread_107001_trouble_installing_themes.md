---
title: "trouble installing themes"
date: 2005-12-22
forum: General Help
---

### Post by equal on 2005-12-22
So here's an interesting one. I'm trying to install this theme:[HTML]http://kde-look.org/content/show.php?content=18223[/HTML]

I go through the steps lined out in the Install file, but here's the problem. I do this command and it works fine: ```
$ ./configure
```

Then I get to the "make" command and this happens:

```
$ make
make: *** No targets specified and no makefile found.  Stop.
```

I noticed further down it said if anything failed to try this step, and this was the result:

```

$ make -f Makefile.dist
This Makefile is only for the CVS repository

./admin/cvs.sh: line 60: automake: command not found
*** AUTOMAKE NOT FOUND!.
*** KDE requires automake 1.6.1 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
```

I tried running this: ```
sudo apt-get install automake
``` and it says I already have the latest version. Then when i tried specifically installing the version 1.6.1, I got ```
$ sudo apt-get install automake 1.6.1
Reading package lists... Done
Building dependency tree... Done
Note, selecting automake1.4 instead of automake
automake1.4 is already the newest version.
E: Couldn't find package 1.6.1

```

So lost. So, so lost.

---

### Post by aysiu on 2005-12-22
Try this.
Download this:
[http://kde-look.org/content/download.php?content=29600&id=1](http://kde-look.org/content/download.php?content=29600&id=1)

You'll end up with this on your desktop:
29600-Blue_Lipstik_Crystal_Theme-1.tar.gz

Unzip it (you can do this graphically--just click on it, then click the purple arrow).

Inside, you'll see a file called Blue Lipstik Crystal.kth--remember where that file is.

Then Alt-F2 and ```
kcontrol
``` Go to Appearances & Themes and Theme Manager... then, Install New Theme. Find the .kth file and select it.

Lipstik should now be in there.

---

### Post by Freddy on 2005-12-22
I found automake1.9 (1.9.5-1) in our repos, happy hunting.   /// Freddan

---


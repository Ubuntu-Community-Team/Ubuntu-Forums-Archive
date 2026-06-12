---
title: "Kile problem: Toolbars and menus gone after upgrade to hardy"
date: 2008-06-03
forum: Desktop Environments
---

### Post by jostein on 2008-06-03
Hi!

I'm having a strange problem with kile (installed from source, version 2.0.1) after upgrading to hardy from feisty. Most of the toolbars in kile are missing, I can only see the left edge of the build, tools, edit, error and math toolbars (while the main toolbar is still there). The keyboard shortcuts work for the missing toolbars (at least the few of them that I still remember). In addition to this there is no "Help" menu. I have reconfigured and recompiled the source package and done a make install again after the upgrade, but theese problems are still there. I have also tried to install the version of kile in the hardy repositories, with exactly the same result.

Another problem I had was with kbib (also from source and recompiled after upgrade, version 0.6.4). On startup kbib complained about two missing files, entryDefs.xml and kbibuirc. Both were installed to /usr/local/kde/share/apps/kbib/. I found that KDEDIRS was blank, and kde-config --path data did not include this directory. After adding the path /usr/local/kde to KDEDIRS in my .bashrc, I tried logging out and in again, but the problem was still there. Copying (or symlinking) the files to the corresponding directory under $HOME/.kde resolved the problem. Could this be related to my Kile problem (i.e., could the kile problems be caused by kile not finding some installed datafiles)?

Any help would be much appreciated -- I think I might have to downgrade Kubuntu to feisty again if I can't solve this.

Jostein.

---

### Post by jostein on 2008-06-03
SOLVED:

The cause was that /usr/local/kde was missing from $KDEDIRS. Setting $KDEDIRS in .bashrc doesn't work -- see [http://lists.debian.org/debian-kde/2004/11/msg00002.html](http://lists.debian.org/debian-kde/2004/11/msg00002.html) for details. The correct method of setting the enviroment variable is described there.

Jostein.

---

### Post by randysnookums on 2011-11-24
I stumbled across this problem lately and this thread was the only hint to a solution that I could find. A very simple fix is to restore Kile to its default settings by removing your own settings (this does not affect your user defined shortcuts). Close Kile, open a terminal and type
```
rm $HOME/.kde/share/config/kilerc
```
Restart Kile. Done.

---

### Post by Krabby.Linux on 2012-02-08
Thanks buddy, this one helped me out :-)

---

### Post by overdrank on 2012-02-08
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---


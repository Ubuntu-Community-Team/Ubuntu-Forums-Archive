---
title: "Xgl starts, compiz exits/quit/crashes(?), no borders. Since last update"
date: 2006-08-23
forum: Desktop Environments
---

### Post by BungaMan on 2006-08-23
Background info: I had a stable running Xgl with compiz and all effects on.  Yesterday (23 august) I installed the compiz updates.  The ones that remove compiz, install/upgrade compiz-gnome, compiz-core, compiz-plugins etc...  Yesterday I've also had the xserver-xorg-core installed/broken/recovered.  It is after recovering I continued the compiz update because it appeared -f install was necessary etc.

I always start xgl and compiz using a script for each.  I select the Xgl session, it shows me gnome but there are no borders anymore.

gnome-window-decorator is running but compiz is not.  I've tried starting compiz manually with compiz --replace gconf and all the plugins appended but compiz exits.  I've tried without the plugins but that doesn't work either.  The only thing that makes compiz running is simply using compiz --replace.  Of course without the plugins it doesn't do much.  And while compiz is running there are still no borders to the windows.

I'm running 
- 686 arch
- gnome
- fglrx
- quinn repository (with the latest update the name quinn seems to have changed to ubuntu)
- Xgl/compiz (or at least trying)
- need more specs?
everything is up-to-date with the latest package

Does anyone know what is wrong, how to fix it, what to double-check?  Nothing changed to these scripts, the only difference is the package updates.  I've searched all over different forums without any luck.  Similar problems but no similar causes or working fixes.  When compiz quits there is no output and I don't know of any log files it writes to.  Might be a VERY good suggestion to the developer since this is still not a VERY stable product.

---

### Post by anasofiapaixao on 2006-08-23
I have the same problem. Looks like we are passing through update Hell in the Ubuntu community... maybe all we can do is wait for a fix or a tutorial to configure the new packages.

Also I think the packages should configure a GDM session automatically rather than forcing us to do it by hand...

This weird update removed cgwd, the xgl window border manager... and it also trashed MY EMACS WITH GTK SUPPORT, that was hell to install, by uninstalling emac-xft-gtk. Now *what in the world does emacs has to do with compiz???*

---

### Post by BungaMan on 2006-08-23
Today there was an other update which fixed compiz but gnome-window-manager did not run.  Everything is fine now, also got cgwd installed and working now.

---

### Post by anasofiapaixao on 2006-08-23
Could you tell how did you do it? Currently I have XGL bot nothing compiz-related installed. What packages should I get? I am going through dependency hell, especially because compiz is depending on compiz-plugins v0.2 (which I won't find anywhere, nor compiz-plugins-quinn AND THE COMPIZ FORUM IS DOWN SO I'M SCREWED), while the repos only have 0.1 (like, cleeeever...), and when I try to install compiz-plugins it says... it depends on compiz and can't be installed.

PLUS cgwd depends on compiz-vanilla AND compiz-plugins on compiz, being of course compiz and compiz-vanilla incompatible, and I don't know already what does the new compiz-core do in the middle of all of this. All I know is that any possible way combining all the elements on this salad *doesn't work. ARGHHH HELP! ](*,)

August 22 should be called the repos fiasco day.

---

### Post by BungaMan on 2006-08-24
simply installed the latest updates and that's it.  with the latest updates cgwd does not depend on compiz-vanilla any more.

compiz is obsolete and replaced by compiz-core and compiz-gnome i think.

---


---
title: "Copiz not working after upgrade"
date: 2008-04-11
forum: Desktop Effects &amp; Customization
---

### Post by kulebreeze on 2008-04-11
Hi all, I just did an upgrade on my Ubuntu 8.04 of compiz and now am not getting any respond from it it says in the package manager that it is install but when i try to put the settingg manager it tell me i need dependencies. When i try to install the dependencies it not going through...:( i miss my compiz:mad:

---

### Post by chrisolof on 2008-04-11
(I think I'm experiencing the same issue as kulebreeze)

Starting info:  Running 8.04 Beta with NVidia Restricted Driver enabled, Visual Effects on Extra, and compizconfig-settings-manager installed to customize my compiz-fusion experience.  Everything was working great.

I logged into Ubuntu 8.04 (Hardy) beta today, and was presented with updates to my software, as usual.  When I clicked the icon in the upper right it said something about only being able to do a partial upgrade.  I said 'ok' to that and it proceeded to do a "Distribution Upgrade," which removed some things (including compizconfig-settings-manager, among others) and added some things.  This seemed strange because I was and still am running 8.04 (Hardy) beta, not upgrading from some previous release.  But, I proceeded and after rebooting I have the following problems:

Desktop Effects was turned to "Normal" and I no longer had titlebars on any of the windows I opened.
All Windows opened were located at the top left of the screen (had they title-bars the bars would be obscured by the top "Applications" menu), which isn't normal.
Turning Desktop Effects to Extra does not fix the titlebar issue.
Turning Desktop Effects to None fixed the window decoration issues above (I assume metacity takes over again), but that leaves me stuck with no desktop effects.
When I try to install compizconfig-settings-manager from synaptic I get:  
compizconfig-settings-manager:
 Depends: python-compizconfig but it is not going to be installed

So I'm really stuck here and this seems like a bug with the latest software updates.  I assume others will be facing the same situation as my setup doesn't seem that out of the ordinary (8.04 beta + Nvidia Restricted Driver + Desktop Effects: Extra + compizconfig-settings-manager).  I thought I'd post here before reporting a bug on launchpad.

Thanks in advance for any help!

---

### Post by PinkFloyd102489 on 2008-04-11
Im having troubles also. I turned off Emerald but wanted to keep Compiz, yet it killed off also. Now I cant enable it.


Ubuntu 8.04 on Nvidia 5200 FX. Latest driver from the site, 169.12 or whatever.

---

### Post by wile_e8 on 2008-04-11
I am getting the same errors when updating Hardy, following pretty much the exact same steps as chrisolof.  I just want to add that after what he did, I tried to install python-compizconfig in Synaptic.  This led to a dependency on libcompizconfig0.  When I tried to install that, I got an error saying that to install libcompizconfig0, I need to remove compiz-core, compiz-fusion-plugins-extra, compiz-fusion-plugins-main, compiz-plugins, and emerald.  Which is pretty much all of compiz as far as I can tell.  Also, I had the fusion-icon installed, and used this to switch my window manager to emerald, but now this is uninstalled and I get the same dependency errors trying to reinstall it.  I think I could get the titlebars back if I could switch back to metacity, but don't know how to do that without fusion-icon or compizconfig-settings-manager.

---

### Post by PinkFloyd102489 on 2008-04-11
There's a few Compiz updates being held back right now, so maybe it'll get fixed soon.

---

### Post by Therion on 2008-04-11
Relax... And before you start installing/removing packages, might I suggest you wait for the next round of  updates?  Hardy does still have a couple weeks to go before it's finalized.

If you didn't expect this sort of thing when installing a beta version, you should have.

---

### Post by wile_e8 on 2008-04-11
Just checked for updates, and two of the packages in the previous remove list were updated.  Upon installing the updates, libcompizconfig0 installed properly without any dependency issues, as did compizconfig-settings-manager and fusion-icon.  I went back to advanced appearance, and everything worked fine.

---

### Post by pencilcheck on 2008-04-11
People, I fixed this by installing compiz which is uninstall by the update (don't know the real reason) which means the update doesn't do it's job...

Anyways, compiz is now 0.7.4 the lastest version available, check that and the compizconfig finally the fusion icon are checkable!!

Good Luck guys!!
Cheers, 

PS: love the curve view of Expo

---

### Post by PinkFloyd102489 on 2008-04-12
Installing the latest kernel did it for me. Allowed me to install new Nvidia driver and turn on Compiz.

---

### Post by comandrei on 2008-04-12
Compiz stopped working for me too. I'm using Kubuntu 8.04 Beta and after the upgrade the output of compiz --replace & is :
```

Checking for Xgl: [2] 7590
fester@fawkes:~$ not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: not present.
aborting and using fallback: /usr/bin/kwin

```
It's still a beta and it's normal for things like this to happen. Let's hope it gets fixed soon.
LE: I installed the lastest kernel but still nothing. I think it's something related to libcompizconfig0

---

### Post by kulebreeze on 2008-04-13
Hay guy what i did was just uninstall compiz then reinstall and now everything working like new..

---

### Post by Amranu on 2008-04-13
After this update compiz wasn't removed for me, but cube effects (and other effects too, but most obvious with cube) are choppy for a few seconds after not having been used for a minute. After a few seconds of use they become normal speed. :(

---

### Post by chrisolof on 2008-05-19
Well still dealing with no titlebars on my windows when I turn desktop effects on.  I've kept up with all of the updates, which did fix the dependency problem I was having - but nothing else.  I also tried uninstalling everything compiz-related and re-installing it - but still no titlebars.

I'm about ready to do a fresh re-install using the non-beta 8.04 disk.  Kind of a hassle setting everything up again - but Compiz-Fusion is worth it.

---

### Post by chrisolof on 2008-07-01
Just an update - reinstalling Ubuntu 8.04 from the non-beta disc did the trick - now everything works wonderfully.  Won't jump the gun by installing and configuring a beta Ubuntu again. . .

---

### Post by evoviiigsr on 2008-07-09
I'm having trouble too...here is my terminal output:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1360x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found

This happened after I install and then uninstalled GIT

---


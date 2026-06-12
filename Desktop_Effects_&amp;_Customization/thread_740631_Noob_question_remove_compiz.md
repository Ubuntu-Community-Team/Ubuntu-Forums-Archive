---
title: "Noob question: remove compiz"
date: 2008-03-30
forum: Desktop Effects &amp; Customization
---

### Post by Sugi on 2008-03-30
Yea, how do I remove compiz?  I used
sudo apt-get remove compiz
and then it shows everything being removed.  I do a restart, and I stil have my 3d and compiz.  I don't want it anymore.  What should I do?


Sugi

---

### Post by azanoncello on 2008-03-31
I removed mine by going to "Synaptic package manager" and then searching for "compiz" I then removed everything that had "compiz" in its name.

---

### Post by Sugi on 2008-03-31
Does the terminal command doesn't work?  Is there  common reason for this?  Anyways, thanks for the heads up.  I'll give it a try.  

Thanks,
Sugi

---

### Post by Sugi on 2008-04-15
Should I be careful not to remove something (when I am removing the compiz thingy) anything with comiz in it's name?

---

### Post by kutjara on 2008-04-15
> **Sugi said:**
> Yea, how do I remove compiz?  I used
sudo apt-get remove compiz
and then it shows everything being removed.  I do a restart, and I stil have my 3d and compiz.  I don't want it anymore.  What should I do?


Sugi

When you use Synaptic to remove compiz, make sure to choose the "completely uninstall" option from the dropdown menu. That will clear out the configuration files, too.

Removing everything with Compiz in the name is fine. You won't encounter any problems doing that.

Just to be on the safe side, type:

metacity --replace

in the terminal window. This will reenable the default metacity 2D window manager and stop your computer from trying to use Compiz.

---

### Post by st0nedpenguin on 2008-04-16
> **kutjara said:**
> Just to be on the safe side, type:

metacity --replace

in the terminal window. This will reenable the default metacity 2D window manager and stop your computer from trying to use Compiz.

Definitely do this before you uninstall Compiz, I forgot the first time round and had much fun on the next boot. :-?

---

### Post by Zorael on 2008-04-16
Terminal solution!

```
$ metacity --replace
$ sudo apt-get autoremove **--purge** compiz* libcompiz* libdeco* *emerald* libemerald**
```
(can omit packages in italics if you wish, but Emerald isn't going to work without a compositioner)


Because we all love that deliciously monospaced wall of text!

---

### Post by kutjara on 2008-04-16
> **Zorael said:**
> Terminal solution!

```
$ metacity --replace
$ sudo apt-get autoremove **--purge** compiz* libcompiz* libdeco* *emerald* libemerald**
```
(can omit packages in italics if you wish, but Emerald isn't going to work without a compositioner)


Because we all love that deliciously monospaced wall of text!

Should probably include ccsm and some of the pythoncompiz stuff too, just to be on the safe side. That's why I found the Synaptic approach worked better for me in this circumstance (I could be sure anything with compiz in the name was completely gone).

My problem was that I stupidly installed gnome-compiz-manager, "just to see what it would do"(TM), and it hosed my Compiz setup comprehensively. After a lot of fruitless messing around, I decided to uninstall Compiz and then reinstall it. After using autoremove --purge and then reinstalling, I found I had exactly the same problem as before. I autoremove --purged again, then did a search on "compiz" in Synaptic and found a lot of stuff still sitting there. When I got rid of all that (using the "completely remove" option) and then reinstalled, my problems cleared up.

I suppose my point is that the terminal command is great, if you know the name of everything you need to uninstall. If not, a search in Synaptic can be the better option.

---

### Post by Zorael on 2008-04-16
> **kutjara said:**
> Should probably include ccsm and some of the pythoncompiz stuff too, just to be on the safe side. That's why I found the Synaptic approach worked better for me in this circumstance (I could be sure anything with compiz in the name was completely gone).

CCSM is included in the compiz* regex (being compizconfig-settings-manager), and pythoncompiz and its ilk were installed as dependencies, so autoremove *should* find and remove those as well. :<

edit: aptitude would've removed the dependencies as well, after building dependency trees and seeing them orphaned, but autoremove gets the job done, bundled with the fact that you can easily use wildcards to get to all the packages. There's likely some sign that aptitude accepts as well, I've never delved into it.


I guess I didn't include gnome-compiz-manager, never used it myself so didn't spring to mind. But naturally, Synaptic (and Adept Manager) gives you a better overview of the packages in question.

---

### Post by kutjara on 2008-04-16
> **Zorael said:**
> CCSM is included in the compiz* regex (being compizconfig-settings-manager), and pythoncompiz and its ilk were installed as dependencies, so autoremove *should* find and remove those as well. :<

edit: aptitude would've removed the dependencies as well, after building dependency trees and seeing them orphaned, but autoremove gets the job done, bundled with the fact that you can easily use wildcards to get to all the packages. There's likely some sign that aptitude accepts as well, I've never delved into it.


I guess I didn't include gnome-compiz-manager, never used it myself so didn't spring to mind. But naturally, Synaptic (and Adept Manager) gives you a better overview of the packages in question.

Weirdly, when I chose the "complete" compiz install using Synaptic, ccsm didn't automatically highlight to be installed with it. I had to select that pakcage manually. I guessed that was why it didn't uninstall as part of the purge process.

---

### Post by Zorael on 2008-04-16
> **kutjara said:**
> Weirdly, when I chose the "complete" compiz install using Synaptic, ccsm didn't automatically highlight to be installed with it. I had to select that pakcage manually. I guessed that was why it didn't uninstall as part of the purge process.

Yes, because it's not included in the compiz meta-package "bundle". :>

apt-get autoremove --purge compiz* will select everything from compiz, compiz-core, compiz-plugins, compiz-bcop, compiz-gnome, compiz-kde, all the way to compizconfig-settings-manager.

The compiz "package" only includes compiz-core, compiz-fusion-plugins-extra, compiz-fusion-plugins-main, compiz-gnome, compiz-plugins and libcompizconfig0. So that's what'd get removed.

So if you installed compiz-kde on the side (like us kubuntulings do), it'd remain if you only removed compiz. But it'd get hit by the compiz* regex. :>

---

### Post by kutjara on 2008-04-16
> **Zorael said:**
> Yes, because it's not included in the compiz meta-package "bundle". :>

apt-get autoremove --purge compiz* will select everything from compiz, compiz-core, compiz-plugins, compiz-bcop, compiz-gnome, compiz-kde, all the way to compizconfig-settings-manager.

The compiz "package" only includes compiz-core, compiz-fusion-plugins-extra, compiz-fusion-plugins-main, compiz-gnome, compiz-plugins and libcompizconfig0. So that's what'd get removed.

So if you installed compiz-kde on the side (like us kubuntulings do), it'd remain if you only removed compiz. But it'd get hit by the compiz* regex. :>

Thanks, that makes sense. I must have left out an important wildcard, which is why so much got left behind. Damn my stubby fingers. :)

---


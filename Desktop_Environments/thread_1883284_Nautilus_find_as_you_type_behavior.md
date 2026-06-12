---
title: "Nautilus find as you type behavior"
date: 2011-11-18
forum: Desktop Environments
---

### Post by paulisdead on 2011-11-18
So one of the things that has been driving me nuts is the find as you type behavior in the newer versions of Nautilus.  In previous versions of Ubuntu, you could easily type in the name of a file or folder and it'd take you there and everything worked great.  The newer versions don't even accept a space in their search.  The pop up search box also doesn't clear once you've pressed enter or entered another folder.  Pressing backspace with that box open doesn't let you delete the text, it just takes you back a folder.  Even worse pressing the delete key while in that box just deletes whatever files/folders you had highlighted and doesn't clear the text.

The behavior is just insane and totally useless.  Even Explorer in Windows 7 ripped off the old behavior that Nautilus has been using for years, because it makes so much sense.  This has always been one of the most awesome features of nautilus.  I've grown to really love gnome 3, but this has been my one big annoyance with it.  Anyone aware of a way to get it back through gconf/dconf or some other hidden setting?  

PS:  Just to clarify, I'm not talking about clicking on search.  I mean when you just type into the window without hitting anything first.

---

### Post by stinkeye on 2011-11-19
The behaviour here on 11.10 seems to work.
I'm in Unity(with the global menu disabled) but have also installed gnome-shell.
Backspace, delete spaces all work as expected.
I've attached a pic of my versions of apps with nautilus in the name,
if it's any help.

---

### Post by paulisdead on 2011-11-19
Yup, I've got the same versions.  Did you clean install or upgrade?  I see this behavior on three different systems, so it's not particular to my desktop.

Well there's apparently a bug report on it already, so I guess there's nothing to do but wait. [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/881704](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/881704)

---

### Post by stinkeye on 2011-11-19
It was a clean install.
You could enable the proposed updates repo,
upgrade nautilus and then disable the repo.

---

### Post by paulisdead on 2011-11-19
ppa:bsantos/ppa had an updated version that works, since I didn't want to enable the whole proposed repo just for that one package.  Looks like it's at least fixed upstream, though.

---


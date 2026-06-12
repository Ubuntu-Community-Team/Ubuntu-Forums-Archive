---
title: "Content of / on desktop"
date: 2008-04-27
forum: Desktop Environments
---

### Post by ElVirolo on 2008-04-27
Hi everyone,

I'm currently experiencing a strange problem with Kubuntu Hardy (kde 3.5.9) : my desktop icons are actually the directories from / (i.e /bin, /usr, /var, etc.) but ~/Desktop contains (obviously) completely different files!

Why is that ?

Many thanks in advance,

Alex.

---

### Post by ElVirolo on 2008-04-27
Up

---

### Post by interzoneuk on 2008-04-30
Also happening to me - only with some users ??

This was an upgrade to hardy from gutsy (originally from feisty) 

Anyone any ideas ?

---

### Post by Xiong Chiamiov on 2008-05-02
bump

I have no idea, nor do I have this problem, but it interests me greatly.

---

### Post by Zorael on 2008-05-02
This is a bug in the "module" in systemsettings and kcontrol that changes the path to your desktop. There is a workaround.

First, set the path you want (About me -> Paths in systemsettings or System administration -> Paths in kcontrol) to get it properly saved in the KDE config backend. Then open up **~/.config/user-dirs.dirs** in an editor and remove any occurences of **[$E]** (or some such).
```
$ kate ~/.config/user-dirs.dirs
```
Once you have it opened, you could define other paths if you wish, such as download paths and template paths, since they're not alterable through the normal KDE configuration apps.

Log out and back in to apply changes.


Read about what XDG is here: [http://en.wikipedia.org/wiki/Freedesktop.org](http://en.wikipedia.org/wiki/Freedesktop.org)

---


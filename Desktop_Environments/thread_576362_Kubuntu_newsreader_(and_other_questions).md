---
title: "Kubuntu newsreader? (and other questions)"
date: 2007-10-15
forum: Desktop Environments
---

### Post by meburke on 2007-10-15
I may have to start fresh. I used the upgrade options to upgrade my Kubuntu installation to feisty, and now I've got a little confusion. lsb_release -a tells me I have no LSB modules available, then gives me the following info:

Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

My sources.list seems to point to breezy repositories. How can I tell which repositories are being used by apt?

Knode is apparently not an installable option anymore. Where can I find a good newsreader for Kubuntu? I have nothing against Gnome, but I've trained a few of my customers to use KDE on Gentoo, and I want to be consistent on my laptop. Everyone seems to like PAN, but I see it is recommended for Gnome, not KDE.

---

### Post by meburke on 2007-10-16
OK, first of all, I noticed from my history that I had accidentally cp'd the wrong sources.list backup. I got rid of the extras (like I should have done before).

apt wouldn't install Knode because of a glitch installing the jav-6 docs. (???!!!???) I needed to update my Java stuff anyway. Problem partially fixed. It turns out that Knode is so lame it won't process multi-part mime messages. OK, so I'm a little lazy and don't want to go back to running shar on elm-retrieved mail and using Xview. (That is SO last century!) I haven't gotten klibido to actually download any messages yet. (Sigh.) But I now have two newsreaders. Neither of them is satisfactory, so I guess I still need to look around. BTW, Automatix doesn't seem to work on feisty for me, Aptitude and apt didn't download either application, but Synaptic worked...Go figure!

Still looking for a killer newsreader.

---

### Post by Zillion on 2007-10-20
Had the same on Klibido. Did u try clickin on the tab servers (left vertical) in Klibido? Than it started downloading for me. Klibido downloads like 500 KB to 1 MB/s faster than Grabit for me. :guitar:

Only feature I miss to see how much time is left before download is complete.

---


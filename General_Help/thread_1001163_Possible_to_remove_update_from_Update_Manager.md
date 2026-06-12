---
title: "Possible to remove update from Update Manager?"
date: 2008-12-03
forum: General Help
---

### Post by fwallace99 on 2008-12-03
Hi all --

I believe this is possible because somehow I got this going in Feisty (but I can't recall how I did it).

I want to stop an upgrade from appearing in the Update Manager.

It's showing the flash-plugin, which does not work, and I have the manually installed .deb file from Adobe (v 10) which works. 

I don't want it showing up, too easy to nuke flash by mistake (now that I have it working).

I am running 32 bit Hardy Heron.

Thanks.

---

### Post by anjilslaire on 2008-12-03
do this:

Open Synaptic.
Search for Flash. YOu should find the nonfree version and the Flash 10 deb version you manualy installed.
Check Remove completely on the nonfree version, and apply the updates. 

The nonfree version will be removed, and therefore will not be offered to be updated. Essentially you have 2 versions of Flash: the nonfree Flash9 version, and the newer Flash10 version.

---


---
title: "[SOLVED] hal-storage-fixed-mount-all-options refused uid 1000"
date: 2008-03-26
forum: Desktop Environments
---

### Post by Dexter Saint Jock on 2008-03-26
What does this mean and how do I resolve this?

Running Gutsy with Kde installed. I've been a linux convert since december and have booted my vista only about 4 times since then.  I'm diggin' it.

I get the above error message when I try to mount an internal HD from KDE. In Gnome I can mount the volume with no issues. 

I've been using KDE for only about 4 days so I am just beginning to learn the basics on it. I like it, though. 

I normally don't post because of the ENORMOUS AMOUNT OF INFO AVAILABLE IF YOU JUST USE THE SEARCH FUNCTION!!!!! It has answered every issue I have had until now.

 You guys and gals ROCK!!!!

---

### Post by Dexter Saint Jock on 2008-03-27
I got it fixed. Still not sure what the message means but I got it.

Went to synaptic and installed ntfs-config. Then in a terminal typed: sudo ntfs-config.

a gui popped up and configured from there.

Any ideas why KDE requires this and gnome does not? I'm at a loss.

---


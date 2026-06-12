---
title: "[SOLVED] Cairo-dock applets...where are they???"
date: 2008-03-20
forum: Desktop Effects &amp; Customization
---

### Post by brundlelinux on 2008-03-20
Background info:

I'm working on a pretty fresh Ubuntu Gutsy install.  Less than a week anyhow, and besides a few media apps like Gpodder, VLC, and Kaffeine, the only things I've installed are the standard "Linux media FTW" codecs like ubuntu-restricted-extras and the various Gstreamer plugins.  Other than that, it's a fresh install still.

So, having grown ever-so-tired of the standard Gnome taskbars at the top and bottom of the screen, I've set out to find a good eye-candy dock replacement to phase the Gnome standard out completely.

The first issue I had was getting Cairo-dock installed.  The latest deb files for Cairo-dock and it's plugins from the Beirros project page were corrupt according to Gdebi.  So, I just downloaded the most recent tarball and compiled from source.  It works beautifully.

My only issue now is getting the various applets installed (volume control, clock, trash, etc) so I can nix the unsightly Gnome standard taskbars off my desktop.  The problem is, no matter what combination of keywords I put into Google, I CANNOT find these applets.  As far as I can tell, they're like the Loch Ness Monster or Bigfoot... lots of people claim to have seen them or use them, but proof doesn't exist.   LMAO

So, anybody have info for me on where I can find the support for these applets and how I can get them installed?  I'm not usually a source-compiler, so I admit that I don't know if I can install applet support from a deb, or if I have to compile those as well.  Any info is appreciated.  Thanks in advance.

---

### Post by cybergalvez on 2008-03-20
did you look at:  [https://developer.berlios.de/projects/cairo-dock/](https://developer.berlios.de/projects/cairo-dock/)

---

### Post by brundlelinux on 2008-03-20
Yes.  That was the page that I was originally downloading the debs from before I compiled from source.  I tried the debs from several different versions, but Gdebi kept saying that those debs are corrupted.  The v.1.5.2.1 source tarball is what I compiled from.

I had assumed that compiling from source would give me both the dock itself as well as the plugin applets, but I guess not.  Once I go to the configure menu, I have no applets listed at all to edit.

Just on a whim, I'm going to try and download the latest deb applets package and see what happens now that I have Cairo installed and running.

---

### Post by brundlelinux on 2008-03-20
Just did another attempt at one of those deb files.  Gdebi returns that it cannot open it because it is either corrupted or that I don't have permission.  A quick check of the properties reveals that I am the owner with read and write capability.  Any other ideas?

---

### Post by kawaji on 2008-03-20
My Gdebi says the same messages on v 1.5.3.2 deb packages. they seems corrupted.
But I got no problems with v 1.5.2.1 packages .

If you cant install v 1.5.2.1 downloaded from Berlios, 
How about packages from this repository [the official cairo-dock site]("http://www.cairo-dock.org/") recommends ?
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) gutsy cairo-dock

---

### Post by brundlelinux on 2008-03-20
Eh, it's worth a shot.  Thanks for the info and the leads.  :)

I'll update with results.

---

### Post by IanW on 2008-03-21
For the applets, you'll need to download & install the "Plug-ins" tarball or deb.

If you get the tarball, each plugin must be compiled & installed separately.

Played this game last night with 1.5.3.2 from SVN on a Hardy-powered EeePC.

---

### Post by brundlelinux on 2008-03-23
Okay, I got this all up and running working perfectly.  I'm going to tag this as solved.  For anybody else who is in this boat, here's  the deal:

Currently, as of March 23rd, 2008, the BerliOS page has corrupted Deb files posted for the newest version of Cairo-dock (V1.5.3.2).  If you want to install from Debs, you'll have to use a previous version, obviously.  Using Deb packages, you'll have to install both the Cairo-dock and the plug-ins packages.

Using source, you can compile from the V. 1.5.3.2 source tarball.  However, as pointed out, compiling from the source, you will have to compile each plug-in individually, but the source is provided for each to do so.

---


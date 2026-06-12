---
title: "Can you hide the disk icons on the desktop?"
date: 2005-10-27
forum: Desktop Environments
---

### Post by SpectralDesign on 2005-10-27
I want to make a login for my son -- he's got motor-control and learning difficulties, but he still wants to use the computer like daddy does :)

To make it "safer" for him to use the computer, is there some way to hide the disk links on the desktop? (hda1, hda4, etc....) Because he does lots of clicking and dragging, but doesn't understand the consequences very well.

Thanks in advance!

---

### Post by Diziet Asahi on 2005-10-27
install **gtweakui**, you'll have a tweak nautilus icon in system > preferences where you'll be able to do that

---

### Post by stuporglue on 2005-10-27
In user settings when you create a new user for him, make him a "Default" user (see the advanced tab). You can fine tune what he can do in the "User privileges" tab in the same window. I think the one you'll want to uncheck are "Enable access to external storage devices automatically".

---

### Post by jnoreiko on 2005-10-27
[QUOTE=Diziet Asahi]install **gtweakui**, you'll have a tweak nautilus icon in system > preferences where you'll be able to do that[/QUOTE]

You can change the setting with Gconf, that's already installed.

---

### Post by SpectralDesign on 2005-10-27
Thanks for the pointers!

My system doesn't seem to have gconf bt it's got:

gconf-editor      gconfigger        gconf-merge-tree  gconftool         gconftool-2

I'm not quite sure what to do with it though :)  I'll poke around and see if I can figure it out.

I thought I'd selected the proper options on making his account to disable the disk access, but it didn't work -- I'll try recreating the account and see what happens.

I tried to get gtweakui but something's gone scrwey in my package-tool so I need to get that fixed first.

Thanks again!

---

### Post by 23meg on 2005-10-27
1) launch gconf-editor, or hit Applications / System Tools / Configuration Editor

2) go to gconf apps/nautilus/desktop/

3) untick the volumes_visible checkbox

---

### Post by SpectralDesign on 2005-10-28
23Meg, thanks a bunch for the explicit breakdown of what I needed to do.... (I didn't even realize nautilus was responsible for that! :)

---

### Post by Xzoky on 2008-04-24
Very helpful, thanks. Nothing to hide my beautiful wallpaper now !

---


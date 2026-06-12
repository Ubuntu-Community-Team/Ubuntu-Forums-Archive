---
title: "beryl can't select"
date: 2007-04-14
forum: Desktop Effects &amp; Customization
---

### Post by neo_weapon on 2007-04-14
I installed the beryl manager on my edgy but everytime i select beryl as a windows manager, it reverts back to GNOME. how do i enable the beryl features?

---

### Post by freebird54 on 2007-04-14
First thing - Beryl questions should go in the Desktop Effects & Customization forum -as that is the experts hang out.  Second thing - they will need to know a bit more!  Beryl is set up to hand off control to another window manager whe it encounters troubles, but those troubles could be anything at this point.

When you post on the other forum - include your video card name/model, and the howto link you used to get started - that way they'll know some of 
the possible issues...

OK? - should be fixable in most cases...

---

### Post by neo_weapon on 2007-04-14
sure no problem sorry about that.
so here are my specs

Ubuntu edgy
6600gt evga 128mb 
penti D 915
1gb value kingston ram

---

### Post by serialdae on 2007-04-14
starting beryl from the manager you can not see any error messages plus if things go wrong you can be somewhat locked out of your session.

Try starting beryl from a console and see what it says.

---

### Post by neo_weapon on 2007-04-14
ok so i did:

sudo beryl

and this is what i got:

[B]Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension[/B]

---

### Post by serialdae on 2007-04-14
It sounds like something is missing out of your xorg.conf file

My Nvidia systems need several lines added to make them work with beryl.

in the section device
 Option "RenderAccel" "True"
 Option "AddARGBGLXVisuals" "True"
 Option "DisableGLXRootClipping" "True"
 

Check out the Beryl WIKI

---

### Post by neo_weapon on 2007-04-14
PERFECT THANK YOU!!! hahaha.

Here are some more detailed instructions

[http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia)

---

### Post by dreadlord_chris on 2007-04-17
> **neo_weapon said:**
> ok so i did:

sudo beryl

and this is what i got:

[B]Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension[/B]

just a note - you shouldn't ***sudo*** beryl

---


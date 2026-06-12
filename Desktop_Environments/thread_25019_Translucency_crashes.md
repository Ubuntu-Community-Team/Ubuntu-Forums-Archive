---
title: "Translucency crashes"
date: 2005-04-09
forum: Desktop Environments
---

### Post by coldsalmon on 2005-04-09
Hi,

Whenever I try to enable translucency, I get an immediate message upon restart saying that the composite system has crashed twice in one minute and will be disabled.  I also get a message saying that I have to use XOrg that is > 6.8, and that I have to add the following to the xorg.conf file:

Section "Extensions"
Option "Composite" "Enable"
EndSection

I checked the man pages, and XOrg is version 6.8.2.  I also added that section verbatim to the xorg.conf file, and I get the same messages.

I'm running on a Gateway 450ROG laptop.  Any help would be appreciated.

--C

---

### Post by coldsalmon on 2005-04-09
I booted up this morning, and it magically worked all of a sudden.  It was so slow, though, that I had to turn it off to make the desktop useable.  The shadows also broke Superkarabma's "fake translucency,"  so I think I'll just stick to a "flat" desktop for now.

--C

---

### Post by cmikepee on 2005-04-13
also having this problem and getting the same message.  anyone have tranlucency working on there systems?

---

### Post by ltmon on 2005-04-14
[QUOTE=coldsalmon]I booted up this morning, and it magically worked all of a sudden.  It was so slow, though, that I had to turn it off to make the desktop useable.  The shadows also broke Superkarabma's "fake translucency,"  so I think I'll just stick to a "flat" desktop for now.

--C[/QUOTE]

Composite is really slow unless you're using hardware accelleration.

I know if you have nvidia card you should add the following to /etc/X11/xorg.conf:

In section "Device"
...
Option      "RenderAccel" "true"
Option      "AllowGLXWithComposite" "true"
...

Apparrently if you have an ATI card you can use:

In section "Device"
Option      "backingstore" "true"

Try [here](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency) for some tips (it's gentoo specific, but many of the sections we can use too).

If you don't have hardware accelleration you're fresh out of luck... it's going to be slow.

---

### Post by raid517 on 2005-04-14
I have the same problem. Does anyone have an ATI specific guide for enabling drop shadows? The guy who wrote that guide only has an Nvidia card. I have never heard of anyone enabling backingstore before - it's been around for a few years and the ati driver configuration utility fglrxconfig always disables it by default.

GJ

---

### Post by Lord Illidan on 2005-07-03
[QUOTE=ltmon]Composite is really slow unless you're using hardware accelleration.

I know if you have nvidia card you should add the following to /etc/X11/xorg.conf:

In section "Device"
...
Option      "RenderAccel" "true"
Option      "AllowGLXWithComposite" "true"
...

Apparrently if you have an ATI card you can use:

In section "Device"
Option      "backingstore" "true"

Try [here](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency) for some tips (it's gentoo specific, but many of the sections we can use too).

If you don't have hardware accelleration you're fresh out of luck... it's going to be slow.[/QUOTE]

The NVIDIA settings worked fine for me...Very, very nice...but slightly slow...but really attractive..Kubuntu rules \\:D/

---

### Post by fig_jam_uk on 2005-07-07
[QUOTE=cmikepee]also having this problem and getting the same message.  anyone have tranlucency working on there systems?[/QUOTE]


YEP  :razz:  bit of a pain in the a$$ to get working but sexy when it is...

---


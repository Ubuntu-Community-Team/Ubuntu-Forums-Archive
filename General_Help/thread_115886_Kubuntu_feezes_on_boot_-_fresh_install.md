---
title: "Kubuntu feezes on boot - fresh install"
date: 2006-01-11
forum: General Help
---

### Post by eqisow on 2006-01-11
OK, so I recently tried to switch from Ubuntu to Kubuntu. I downloaded the Kubuntu ISO and did a fresh install over the old Ubuntu partition. The install appeared to go smoothly. I logged into my new Kubuntu install to be greeted with a pretty new KDE desktop. 

However, if I try to do *anything* at all, the system freezes. Right click the desktop, click the Kicker, doesn't matter. The mouse will still move, but everything else is completely unresponsive.

Has anybody else had a similiar experience? Is there anything that can be done to fix it, short of installing yet again? I really wanted to give KDE another shot, but it's looking like I might have to run back to Ubuntu.

---

### Post by eqisow on 2006-01-11
I booted into recovery mode and used apt-get to update the system. Still having the same problem...

---

### Post by GeneralZod on 2006-01-11
Hmm...could be almost anything, I'm afraid :/

What graphics card do you have? Is Composite enabled in your xorg.conf? If so, comment out the line

```

Option "Composite" "Enable"

```

---

### Post by eqisow on 2006-01-11
I'm using a Geforce 6800, and unfortunately I can't check the xorg.conf atm... I decided to give resinstallation a try (and was already in the process when I saw your post), not that I really believe it will help. If I still have the problem after reinstallation, however, I will certainly check that out.

And yea, you're right... feels like it will be very tough problem to pinpoint. :???:

---

### Post by GeneralZod on 2006-01-11
[QUOTE=eqisow]I'm using a Geforce 6800, and unfortunately I can't check the xorg.conf atm... I decided to give resinstallation a try (and was already in the process when I saw your post), not that I really believe it will help. If I still have the problem after reinstallation, however, I will certainly check that out.

And yea, you're right... feels like it will be very tough problem to pinpoint. :???:[/QUOTE]

Ok - let us know how it goes! :)

---

### Post by eqisow on 2006-01-11
After getting everything reistalled I (as expected) had the same problem. Going to recovery mode I checked my xorg.conf file for the option ```
"Composite" "Enable"
``` and didn't see it.

Instead, I tried installing nvidia-glx as then ran dpkg-reconfigure xserver-xorg. I ran the update again, just for good measure, and rebooted. I am now posting this from inside Kubuntu, hopefully everything will go smoothly from here.

Thanks for the help Zod. :)

---

### Post by GeneralZod on 2006-01-11
[QUOTE=eqisow]
Thanks for the help Zod. :)[/QUOTE]

Looks to me like you got it all sorted by yourself :) Anyway, best of luck with it all!

---

### Post by eqisow on 2006-01-11
Apparently things are not sorted out as well as I thought. After a few hicups and near freezes KDE finally locked up yet again after 5 minutes or so. I'm a bit lost as to where to go from here. I could always go back to Gnome I suppose, but I really wanted to give KDE another go.

---

### Post by GeneralZod on 2006-01-11
[QUOTE=eqisow]Apparently things are not sorted out as well as I thought. After a few hicups and near freezes KDE finally locked up yet again after 5 minutes or so. I'm a bit lost as to where to go from here. I could always go back to Gnome I suppose, but I really wanted to give KDE another go.[/QUOTE]

That's a shame :(  Make doubly sure there is no Composite thingy in your xorg.conf (do something like

```

cat /etc/X11/xorg.conf | grep -i compos

```
), and maybe disable RenderAccel if that's enabled.  After that, I'm completely out of ideas, I'm afraid :/

---


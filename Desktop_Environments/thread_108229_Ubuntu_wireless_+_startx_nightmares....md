---
title: "Ubuntu wireless + startx nightmares..."
date: 2005-12-25
forum: Desktop Environments
---

### Post by Dafydd on 2005-12-25
I've been a happy Ubuntu-user for almost four months now and then ... suddenly .. this week things went downhill.

1) On my Dell Dimension, I downloaded K3B and this obviously asked to replace some important file (Ubuntu-base?!). That wrecked my system. I could not get startx to start. After some fiddling I could get xfce to start but not gnome. And there was no automatic logging.

2) My laptop (Sony Vaio PCG-TR5MP) everything works fine. I can surf on the wireless at two places where I work. However, on my home interest wireless router (D-Link) it has never really worked. Now, I can't seem to get any internet. I've tried absolutely everything (disabling IPV6 in Firefox, in the network aliases). I installed wifi-radar which helped but when I rebooted the system would not load into Gnome.

Anyone have any ideas on the above? Or any suggestions about other Linux OS? I've tried PCLinuxOs on my laptop (Knoppix too) and the wireless works fine. But with PCLinuxOS the sound is choppy.

After four months with Linux, I'm not goign back to Windows, but Linux is not mature (in my own experience - at least for a stupide newbie like myself).

Dafydd

PS. I'm writing this on my Dell Dimension.

---

### Post by kaamos on 2005-12-25
[QUOTE=Dafydd]1) On my Dell Dimension, I downloaded K3B and this obviously asked to replace some important file (Ubuntu-base?!). That wrecked my system. I could not get startx to start. After some fiddling I could get xfce to start but not gnome. And there was no automatic logging.[/quote]
Let me get this straight, you installed k3b from ubuntu repositories (with synaptic or apt-get) and it screwed your system? Sound quite strange to me.. You could try installing the ubuntu-desktop metapackage to get gnome running, but I really don't get how installing a burning software could get a window manager not to work.
[QUOTE=Dafydd]2) My laptop (Sony Vaio PCG-TR5MP) everything works fine. I can surf on the wireless at two places where I work. However, on my home interest wireless router (D-Link) it has never really worked. Now, I can't seem to get any internet. I've tried absolutely everything (disabling IPV6 in Firefox, in the network aliases). I installed wifi-radar which helped but when I rebooted the system would not load into Gnome.[/QUOTE]
If it the wireless is running ok elsewhere, are you shure this is not a problem with your router? Or does wireless work fine with knoppix?

btw, do you get gdm or any other login manager to start?

---

### Post by Dafydd on 2005-12-26
[QUOTE=kaamos]Let me get this straight, you installed k3b from ubuntu repositories (with synaptic or apt-get) and it screwed your system? Sound quite strange to me.. You could try installing the ubuntu-desktop metapackage to get gnome running, but I really don't get how installing a burning software could get a window manager not to work.[/QUOTE]

I've fiddled so much that I don't know anymore, but I could not log in to Gnome on my Dimension machine after using Synaptic to install K3b and/or dvdrip. Then I tried installing 'fonts' as that was what the error message told me to do but that has not helped. I'll try your suggestion (ubuntu-desktop - thanks!)

[QUOTE=kaamos]If it the wireless is running ok elsewhere, are you shure this is not a problem with your router? Or does wireless work fine with knoppix? btw, do you get gdm or any other login manager to start?[/QUOTE]
Wireless works fine with Knoppix. I'm just sick and tired of manually entering DNS, activating and deactivating etc. And to top it all after ten or 15 minutes I often lose the connection again + have to put up with frustratingly slow page loads.

I don't think I'll waste more time (most of the suggestions on this forum are too technical for me). It's just a shame that Ubuntu will not work on my laptop using my home wireless network. i might try installing another distro just to access the network from my sofa! I would uninstall Ubuntu if it did not work so well on the other wireless networks I use.

Merry Xmas
Dafydd

---


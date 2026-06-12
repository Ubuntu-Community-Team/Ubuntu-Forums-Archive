---
title: "regular login fails before dm. recovery allows login, &amp; other weirdness"
date: 2013-10-11
forum: Desktop Environments
---

### Post by Dreamer Fithp Apprentice on 2013-10-11
My normal login started failing by hanging while still in a tty after 
> Loading /etc/console-setup/cached.Kmap.gz
Loading Unicode mapping table . . .
After booting in recovery mode I've tried most of the options I get there. None of them change what happens on reboot. I've also fscked when booted from another partition and fsck didn't find anything to fix. If I select "resume normal boot" it boots fine after warning that some graphics drivers will fail without a full graphical boot. So presumably booting that way, I'm skipping something that constitutes a part of "a full graphical boot". So I figured maybe the dm was somhow messed up. So I reinstalled with synaptic lightdm and lxdedm (the only 2 already installed I could find, and all the greeters I could find, including the unity greeter I've been useing with lightdm for more than a week with no problems and changed the dm to be used to lxdedm (or maybe it's lxdm). Didn't help. Still failed at the same place. And when I went the recovery-resume route it booted to a single panel desktop I didn't recognise, maybe fluxbox (I have several of the light DEs installed with the intention of trying them all out as I get around to it. I've tweaked the lubuntu and the lxde some. The others I've only looked at) but right clicking on the desktop didn't cause any response. I rebooted again using the recovery-resume approach but this time changed the setting for DE from "default" to "lubuntu" and the result was an improvement but it was the lxde desktop, not the lubuntu desktop. I'm not sure what to make of all this. But I thought before I give up and reinstall I'd see if anyone wanted to suggest something else. To me it is not so much a disaster as a curiosity. How the devil did I screw it up so? I don't think I installed anything or changed any settings of config files before just before things went south.
------------
And under the "if that ain't weird enough" heading now I find that if I right click "open folder" in Transmission or right click "open containing folder" in the downloads window of firefox instead of thunar I get lxterminal asking for my password:
```
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fsarchiver is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtksourceview2.0-0 libgtksourceview2.0-common mate-dialogs
  pluma-common python-gtksourceview2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Since this happened, as near as I can tell, at the same time, I tend to suspect a common cause, although I'm darned if I can imagine what it would be.
=================
added by edit 3 days later:

I gave up and reinstalled. That was the weirdest malf I've seen since all my qt aps started using a greek font with englsh words in their ui, without any identifiable greek font installed. I learned my lesson from that. Messed around with it for weeks before finally giving up and reinstalling. I'm not marking this solved since it wasn't and I'm still curious why it happened.  But it's no longer an issue for me.

---


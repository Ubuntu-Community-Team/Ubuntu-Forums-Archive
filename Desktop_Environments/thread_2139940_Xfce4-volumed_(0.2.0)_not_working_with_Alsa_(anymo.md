---
title: "Xfce4-volumed (0.2.0) not working with Alsa (anymore?)"
date: 2013-04-28
forum: Desktop Environments
---

### Post by Rexilion on 2013-04-28
Since 13.04 I installed it and of course, everything seems to work just fine. However, it turns out that [xfce4-volumed was upgraded]("http://packages.ubuntu.com/search?keywords=xfce4-volumed&searchon=names&exact=1&suite=all&section=all") in Ubuntu Raring.

Looking at the [xfce git repo for xfce4-volumed]("http://git.xfce.org/apps/xfce4-volumed/"), it was not released from there.

Instead, [Ubuntu made it's own]("http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/raring/xfce4-volumed/raring/changes"). And this made a lot of things more obvious: they added support for Pulseaudio. They replaced gstreamer with Pulseaudio to fix a lot of bugs related to somewhat more complex audio setups like bluetooth headsets and such.

Bottom line is, it's not working anymore with normal Alsa. I added my own keys (e.g. 'amixer sset Master (%1+|%1-|toggle)') for the respective keys. But, there is no visual display of volume anymore.

Does anyone know of a nice drop-in replacement?

---

### Post by rusta on 2013-06-29
we have 'old-releases.ubuntu.com' and 11.04 distro (the one I tried, you can try 11.10). I think 12.04 change it all, not sure.

Extract from package 'xfce4-volumed_0.1.12-0ubuntu1_amd64.deb'  the binary 'xfce4-volumed' where you want. (I'm under 64 bits)

Make a symbolic link to libnotify.so named libnotify.so.1 in the same path.

Run the old xfce4-volumed and you're done.

Happy Volume OSDing under Alsa at 13.04

---

### Post by Rexilion on 2013-06-30
Thanks, I'll try that sometime. In the meantime, I just used amixer with keybindings to fix it. But, that does not give any visual feedback :/ . So this might come in handy. Didn't knew about the old-releases site as well.

---

### Post by rusta on 2013-06-30
Sorry, I took the package from here, forger the ubuntu distro:

[http://old-releases.ubuntu.com/ubuntu/pool/universe/x/xfce4-volumed/xfce4-volumed_0.1.12-0ubuntu1_amd64.deb](http://old-releases.ubuntu.com/ubuntu/pool/universe/x/xfce4-volumed/xfce4-volumed_0.1.12-0ubuntu1_amd64.deb)       (or i386 or what you have)

With this one I had no problem with osd and multimedia keys under alsa (without pulseaudio) under xubuntu 13.04

DO NOT INSTALL THE PACKAGE, extract xfce4-volumed, rename it like what you want, save it at /usr/bin/ and make the symlink I wrote before.

Execute it at startup user session .

---


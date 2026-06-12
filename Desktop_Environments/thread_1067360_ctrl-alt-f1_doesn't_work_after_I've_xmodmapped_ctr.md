---
title: "ctrl-alt-f1 doesn't work after I've xmodmapped ctrl &amp; alt -- how to switch ttys?"
date: 2009-02-11
forum: Desktop Environments
---

### Post by Zed on 2009-02-11
I'm running Ubuntu 8.10 without a desktop environment (but this category still seemed most appropriate in the absence of a separate X category.) 

With xmodmap, I remap my keyboard's physical ctrl and alt keys to different things, and establish new ones. These work perfectly for everything except ctrl-alt-f[1-6] and ctrl-alt-backspace.

The xmodmapping is run by a script in my /etc/X11/Xsession.d, so when I'm at the xdm login screen, it hasn't run yet. ctrl-alt-f1 works there (so it doesn't seem to be any of the video driver issues that have been reported.) After Xsession has run, I can still "sudo chvt 1", so there's no problem with the tty somehow not being there. (And once I'm in one of the consoles, the ctrl-alt sequences work as expected until I go back to X with ctrl-alt-f7.)

How can I convince X to respect my xmodmapping for the purposes of the ctrl-alt sequences? I'd've thought some other compulsive-customizing crank had long ago dealt with this, but I haven't been able to find it.

thanks.

---


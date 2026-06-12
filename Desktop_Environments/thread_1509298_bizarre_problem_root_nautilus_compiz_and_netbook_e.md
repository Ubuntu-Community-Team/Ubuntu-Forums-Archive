---
title: "bizarre problem root nautilus compiz and netbook edition"
date: 2010-06-14
forum: Desktop Environments
---

### Post by soumo on 2010-06-14
Hey folks, 

I installed UNE KK on an Asus EEEPC 900HA.

I then decided I didn't like the UNE interface and uninstalled it via Synaptic:

maximus, human-netbook-theme, ume-launcher

Installed:

ubuntu-desktop

But still failed to get access to the desktop.  It is there, I can't right click on it, create icons/files/folders on it directly, but can indirectly, using nautilus for example, create objects on it.  But even if I use nautilus to create a folder in ~/Desktop, it does not appear.  I can change the desktop background via picture preview or other apps.  I accepted this as a 'bug by design' as I'd seen in a few bug reports (launchpad). Note 'show desktop'under 'nautilus' in gconf editor tool is greyed out, but is available if accessed via sudo.

I then installed compiz enabling cube rotation and other effects (works okay), however a few effects don't work (eg. cube deformation to make the cube a cylinder) -cube stays a cube.

By accident, after today's update, I used 'sudo nautilus' and presto! all the modifications I'd made to the desktop suddenly appeared!  Some old folders, the cylinder deformation etc. all working!

After rebooting, back to the old desktop, 'sudonaut' and everything working.  This only works when accessed by a terminal, the panel launcher does not help.

I guess I could put sudo nautilus in start up or a script, but there are a few issues.  1. I still don't know what the issue is, 2a. I can't seem to be able to properly access my home folder eg. 'operation not permitted error' unless I use eg. sudo history >> hist.txt and 2b. I'm afraid there's a great chance I'll mess up my system inadvertently.

Any thoughts?

---

### Post by soumo on 2010-06-15
Okay, solved, or at least worked around:

gconftool-2 --unset /apps/nautilus/preferences/show_desktop

Note: setting 'true', did not work for me. nor did sudoing the above.

If this doesn't persist, I'll try utting it in start up, otherwise I'll create a launcher/alias. Please PM me if a solution is found.

---

### Post by soumo on 2010-06-25
No permanent soution, but an easy way to get this working is to drop:

/usr/bin/gconftool-2 --unset /apps/nautilus/preferences/show_desktop

in a start-up script or .bashrc, so it's out of mind.  Works like a charm.

---


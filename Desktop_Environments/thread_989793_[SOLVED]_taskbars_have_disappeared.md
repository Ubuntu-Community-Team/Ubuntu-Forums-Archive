---
title: "[SOLVED] taskbars have disappeared"
date: 2008-11-22
forum: Desktop Environments
---

### Post by rudeboyskunk on 2008-11-22
I had to do a clean install of Intrepid Ibex.  After I installed, it rebooted, and I installed the proprietary ATI driver, added the medibuntu repos and the wine repo, then did a sudo apt-get update && sudo apt-get dist-upgrade.  I restarted after this, and everything was fine.  Then I installed everything that I usually install and got rid of everything I usually get rid of.  However, now when I restart my computer, there are no taskbars, only the background.  I can switch between workspaces with ctrl+alt+arrow, but that's the extent of my capabilities.  What could be causing this?

The packages I add after installation are basic things, like skype, google earth, adobe reader, firefox plugins, compiz manager (which I thought might be it, so I uninstalled it from command line, didn't work), wine, and other various items.

Any ideas?

---

### Post by rudeboyskunk on 2008-11-22
Ok, as it turns out, I'm a total idiot who doesn't pay attention when I do things.  I always uninstall Evolution because I like Thunderbird better, and I forgot that certain files with "evolution" in the name are dependencies for gnome-panel.  All is well now.

---

### Post by shcaesar on 2008-11-22
Do you mean the panel?
If you did, try this:
alt+F2
enter gnome-panel
check run

If everything goes normal, the panel will show up. Then you can do everything you want.

---


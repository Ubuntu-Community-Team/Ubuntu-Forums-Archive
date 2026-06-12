---
title: "serious bug in Edgy GNOME"
date: 2007-02-02
forum: Desktop Environments
---

### Post by Locke2053 on 2007-02-02
There is a serious bug in GNOME that will make your system unusable!

Right click on the gnome panel. Set the size to 64 pixels and the background to solid with semi-transparent style.

Now, log out and log back in. After 1 second or so, your desktop will crash and send you back to GDM!

This does not seem to happen with other panel sizes (like 32), just 64 (from what I've seen).

If you do this, you can't even load a failsafe GNOME session! It crashes after just a second.

The only way I have found to fix this is to load a failsafe terminal session and then delete all the files in your home directory, and then reboot your PC. Because GNOME pukes about 20 hidden files in your home directory to store your settings (great engineering GNOME!), I have no choice but to delete them all. Because your settings are cached somewhere OUTSIDE your home directory (WTF?) you need to reboot to clear that cache.

After you do this, you can finally use your Ubuntu system again... until you make the mistake of setting 64px/transparent.

---

### Post by lhtown on 2007-02-02
OK, take a deep breath. Now exhale slowly. Feel better? I thought so.

Now, if you are looking for an answer to a question, you can ask it.

If you are trying to raise some kind of hysteria, you are in the wrong place. Email works better for that and reaches far more people.

If you want to file a bug report, you can do that with the Gnome people.

---


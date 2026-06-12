---
title: "Desktop lost"
date: 2020-04-27
forum: Desktop Environments
---

### Post by Mel_Blakey on 2020-04-27
Xubuntu 20.04

I installed Cairo Dock (with Synaptic) and it just froze on my desktop. So, I uninstalled it.

It took with it my desktop. Left with just a black screen. No wallpaper available in settings and just a very basic 'x' for the mouse cursor. It does however have the top panel.

I tried to get it back for a couple of hours and then decided on a re-install.

I have a separate Home folder.

After a fresh install, the situation is the same, except that I have no mouse all (not even a hidden one).

I can not use terminal as it won't accept any characters that I type.

Everything is working fine in the live USB that I am using that to access the forum.

Is the new install picking up an old configuration?

Thanks!

---

### Post by CelticWarrior on 2020-04-27
> Is the new install picking up an old configuration?

Yes, of course, if you reused the old /home . There some serious problem happened. Installing/uninstalling Cairo Dock shouldn't do any harm. Maybe we can do some troubleshooting if you described exactly how you did that installation.

Meanwhile, my suggestion is to use the live session to backup your personal files only from the old /home, reinstall the OS and not reuse it. Then copy back the files. This avoids keeping the problematic configurations files that are also stored in /home.

---

### Post by Mel_Blakey on 2020-04-27
I was thinking of doing this. But, it will not let me delete or rename the .dot files / folders stored in /home.

I was going to try copying the .config from the live session USB and replace the one in /home.

---

### Post by CelticWarrior on 2020-04-27
Again, a new /home without ANY of the previous configs will work. All that really matters is your personal files saved there. Backing up those and copying them to a new fresh /home is perfectly safe. Copying anything else from the old /home has the potential to bring the same problem.

We don't know yet what happened therefore nobody can tell the settings that are safe to import back and the ones that are causing the problem. But you should know. Surely it wasn't the Cairo Dock, it was something else you did.

---

### Post by Mel_Blakey on 2020-04-27
Hi Thanks

I backed up using Rsync. Then deleted everything from Home except my personal files, Docs, Pics, Videos etc and reinstalled Xubuntu and all is fine.

I installed Cairo Dock using Synaptic.
Cairo Dock froze at the bottom of my desktop. I uninstalled Cairo Dock and everything went pear shaped.

---

### Post by Mel_Blakey on 2020-04-27
I installed Cairo Dock again, this time via Software Centre.

Unfortunately, it's thrown up at error:

[ATTACH=CONFIG]285643[/ATTACH]

---


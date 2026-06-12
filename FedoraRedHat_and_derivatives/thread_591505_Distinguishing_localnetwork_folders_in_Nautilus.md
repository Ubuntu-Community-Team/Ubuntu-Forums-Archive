---
title: "Distinguishing local/network folders in Nautilus"
date: 2007-10-25
forum: Fedora/RedHat and derivatives
---

### Post by hrod beraht on 2007-10-25
Is there an easy way to distinguish between a local folder and a mounted network folder in Nautilus?

For example, if I create a folder **/home/me/foo**, that folder foo is obviously local.
However, if I mount a networked folder to it, say, **mount -t cifs //someserver/somefolder /home/me/foo** , then foo is no longer a local folder.

I know I can do a **mount** command in a terminal to see if it's mounted. But is there an easy way to tell in Nautilus if the remote share is actually mounted? The folder icons look the same, whether the share is mounted or not (manually or via fstab).

Or am I looking at this in the wrong way? Is there a better way to mount the remote folder?

Bob

---

### Post by igknighted on 2007-10-26
> **hrod beraht said:**
> Is there an easy way to distinguish between a local folder and a mounted network folder in Nautilus?

For example, if I create a folder **/home/me/foo**, that folder foo is obviously local.
However, if I mount a networked folder to it, say, **mount -t cifs //someserver/somefolder /home/me/foo** , then foo is no longer a local folder.

I know I can do a **mount** command in a terminal to see if it's mounted. But is there an easy way to tell in Nautilus if the remote share is actually mounted? The folder icons look the same, whether the share is mounted or not (manually or via fstab).

Or am I looking at this in the wrong way? Is there a better way to mount the remote folder?

Bob

Well you can change the icon yourself... I would think every time you mount a network folder you might want to just change that icon.  Being (originally) a server/multiuser OS, linux was designed to have that network transparency so you couldn't tell if a file was local or remote.  On a desktop, clearly this can be annoying at times, but I'm not sure there is a good way around that at the moment.

---


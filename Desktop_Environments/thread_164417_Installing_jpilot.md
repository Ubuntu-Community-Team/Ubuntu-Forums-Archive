---
title: "Installing jpilot"
date: 2006-04-22
forum: Desktop Environments
---

### Post by jonathanhayward on 2006-04-22
I want to install jpilot, but apt-get doesn't recognize it. How do I say "I want this package; please search Universe for matches?" And, more to the point, how do I download jpilot?

---

### Post by wylfing on 2006-04-22
Jpilot is defintely in universe and it's definitely called "jpilot". If this command:
```
sudo apt-get install jpilot
```
does not work for you, then the most likely problem is that you do not have universe enabled. Launch Synaptic and choose Settings > Repositories. Click Add and then make sure universe is selected. After that's all taken care of, reload your repositories by choosing Edit > Reload Package Information.

After that jpilot should be installable.

---

### Post by jonathanhayward on 2006-05-20
Thank you. I know I had it syncing before I migrated, but could you send a link to how I can get jpilot to sync? I have it interrogating ttyS0 now; what settings are appropriate (or is that even the problem?)

When I clicked the "Sync" button, it said

"""J-Pilot: press the hotsync button on the cradle or "kill 8475"."""

My palm says, "**HotSync Problem** The connection between your handheld computer and the desktop could not be established. Please check your setup and try again."

There is a pause of several seconds before this happens, during which time my Palm says, "Connecting with the desktop using Direct Serial".

What should I try next?

---


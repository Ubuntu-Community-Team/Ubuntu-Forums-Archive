---
title: "Can't get back default settings for gnome-session-fallback under Ubuntu 12.04."
date: 2012-11-25
forum: Desktop Environments
---

### Post by Roger-H on 2012-11-25
So I was playing around with the launcher in Ubuntu 12.04 using gnome-session-fallback and accidentally deleted a few things. I wanted to return the panel to the original state. After Googling, i read that I could go to ~/.config/gnome-session/saved-session/ and delete everything in there to accomplish this. Unfortunately there is nothing in the directory. Removing and re-installing gnome-session-fallback doesn't return it to the default, either. Can someone please point me in the right direction? Thanks.

---

### Post by ajgreeny on 2012-11-25
When you say "original state" do you mean the default that you get after installing **gnome-panel** and **gnome-session-fallback**, or do you want to get back to how you had configured it yourself?

If you want the default as after installation I think you can remove (or perhaps just rename) the hidden ~/.gconf folder as well as the ~/.config/dconf folder.  If you want to get back to the way you had previously changed it to yourself, I suspect that you will need to reconfigure it, unless you had made a backup of your /home.

---

### Post by Roger-H on 2012-11-25
Yes, I mean the original state it was in when I installed gnome-session-fallback. I didn't install gnome-panel but I believe those are the same thing, right?

I will try doing those two things you specified.

---

### Post by Roger-H on 2012-11-25
That worked, thanks!

---


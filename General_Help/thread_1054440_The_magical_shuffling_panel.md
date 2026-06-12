---
title: "The magical shuffling panel"
date: 2009-01-29
forum: General Help
---

### Post by Chops II on 2009-01-29
Now, I'm getting quite fond of all the things that can be put on the Gnome "panels" and that I can have one per screen that only show the open programs on that screen and everything, but:
Everytime I reboot the panels will move and rearrange the things on them. Even though I have everything locked to panel. Which means the only way to fix it is to go and unlock everything and move things around.

This is really getting quite annoying and seems like something that really shouldn't happen.

Anyone got any ideas on how to prevent this or give me a reason why its doing it?

Thanks,
Chops II

---

### Post by Chops II on 2009-01-30
Can someone please help me with this.
It's quite annoying, and happens on both of my 8.10 machines, pretty much every reboot.

Chops II

---

### Post by callan79 on 2009-01-30
> **Chops II said:**
> Can someone please help me with this.
It's quite annoying, and happens on both of my 8.10 machines, pretty much every reboot.


Hi Chops II,

I don't have an answer to your Q, but I do want to tell you that 'occasionally' I've seen the panels do this ... generally it only happens after changing display settings, but I have seen it occur at random.

What I do is go through ALL the panel applets and UNLOCK them from the panel. Then rearrange as needed. Then LOCK them again.

Then finally, run gconf-editor (press ALT+F2, type gconf-editor), go to apps >> panel >> global, and choose LOCKED DOWN. Then you cannot make any changes to the panel at all.

Hope this helps

CD

---


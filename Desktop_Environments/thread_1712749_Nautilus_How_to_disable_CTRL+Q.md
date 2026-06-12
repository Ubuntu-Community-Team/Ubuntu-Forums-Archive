---
title: "Nautilus: How to disable CTRL+Q ?"
date: 2011-03-23
forum: Desktop Environments
---

### Post by Sylchat on 2011-03-23
Hi

There must be a way to disable CTRL+Q for Nautilus, but google has failed me :|

Actually, I usually have several permanent nautilus windows opened, and when I just hit CTRL+Q on the wrong window, it closed all of nautilus!

So I just "pkill nautilus" to restore the previous nautilus session (even if we can't control nautilus window session manually).

But there are still a few things that could be improved for Nautilus...
So for now, can we disable CTRL+Q shortcut for Nautilus?

Thanks
Syl

---

### Post by Sylchat on 2011-04-05
Any ideas?

I found a [_bug_]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/563226") asking to implement CTRL+Q instead of CTRL+SHIFT+W, but it doesn't say how I can disable it (because it's hard-coded)

---

### Post by vanadium on 2011-04-05
By convention, Ctrl+q completely quits an application. To close a windows, turn into the habit of using Alt+F4.

Anyway, traditional, highly powerful customization options of gnome have now been burried deep away. In gconf-editor, locate the key "Desktop - Interface". Turn "can_change_accels" on.

Now, you can change an acceleration key by highlighting the menu entry, then pressing a key (Ctrl, Ctrl+Alt, but not Alt).

---

### Post by Sylchat on 2011-04-05
> **vanadium said:**
> By convention, Ctrl+q completely quits an application. To close a windows, turn into the habit of using Alt+F4.

Anyway, traditional, highly powerful customization options of gnome have now been burried deep away. In gconf-editor, locate the key "Desktop - Interface". Turn "can_change_accels" on.

Now, you can change an acceleration key by highlighting the menu entry, then pressing a key (Ctrl, Ctrl+Alt, but not Alt).

Thanks!!! I definitely would not have found it myself...
I did search in gconf-editor though, but not using "Accelerator Key" keyword :P

---

### Post by harun3d on 2012-04-27
> **vanadium said:**
> By convention, Ctrl+q completely quits an application. To close a windows, turn into the habit of using Alt+F4.

Anyway, traditional, highly powerful customization options of gnome have now been burried deep away. In gconf-editor, locate the key "Desktop - Interface". Turn "can_change_accels" on.

Now, you can change an acceleration key by highlighting the menu entry, then pressing a key (Ctrl, Ctrl+Alt, but not Alt).
I did not find "Desktop - Interface" in gconf-editor.  I have only gnome, ibus, pgp under desktop.

---


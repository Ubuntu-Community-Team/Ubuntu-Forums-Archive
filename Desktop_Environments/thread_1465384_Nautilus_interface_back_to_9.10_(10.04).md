---
title: "Nautilus interface back to 9.10 (10.04)"
date: 2010-04-29
forum: Desktop Environments
---

### Post by Flake Remix on 2010-04-29
Hello,

[IMG]http://i42.tinypic.com/149pmkl.png[/IMG]
How can I bring back "Show path" button?

[IMG]http://i40.tinypic.com/vo74t2.png[/IMG]
and how can I shift side panel lower, now it on the same level as address bar and take too much space from it.

I know it's all somewhere in gconf-editor, but I cannot find.

Thanks!

---

### Post by skaboss on 2010-04-29
This link should give you the answer :

[https://help.ubuntu.com/community/RestoreNautilusLocationBar]("https://help.ubuntu.com/community/RestoreNautilusLocationBar")

---

### Post by Flake Remix on 2010-04-29
Thanks, I didn't know about Ctrl+L. I hope there is a fix for second problem too.

---

### Post by Flake Remix on 2010-04-29
I see now, that was some idiotic decision from upstream and won't be fix.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/508632](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/508632)

---

### Post by jelofson on 2010-04-29
> **Flake Remix said:**
> I see now, that was some idiotic decision from upstream and won't be fix.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/508632](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/508632)

Agreed. That is an unfortunate design decision (IMHO). Is this Ubuntu-specific?

---

### Post by Flake Remix on 2010-04-30
> **jelofson said:**
> Agreed. That is an unfortunate design decision (IMHO). Is this Ubuntu-specific?

I'm afraid it's Gnome 2.30 specific, meaning all new distros will be concerned.

---

### Post by lord_phantom on 2010-04-30
Argh, at least it could be disabled by default! I don't understand the decision to remove the button completely. Using ctrl+l sucks! I thought the world of free software gives you freedom, it's going to be the Apple way...

---

### Post by kuric on 2010-05-04
Bad decision remove nautilus location bar with the **full path displayed**, placing buttons by default. Frequently I need to copy-paste some full paths, so the buttons are very pretty but unuseful. Restoring this simple configuration through GConf is a pain... For those who need, here's the trick:
Alt+F2
Execute gconf-editor
apps folder > nautilus > preferences > check "always_use_location_entry"

---

### Post by Siegfried80 on 2010-05-21
Thanks, very helpful post for a newbie!
ES

---

### Post by KdotJ on 2010-05-21
Indeed a shame about the text path toggle button. But I have now got used to ctrl+L

---


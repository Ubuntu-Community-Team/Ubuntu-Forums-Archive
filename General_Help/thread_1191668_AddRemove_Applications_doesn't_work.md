---
title: "Add/Remove Applications doesn't work"
date: 2009-06-19
forum: General Help
---

### Post by krusadr on 2009-06-19
I go to "Applications > Add/Remove" and it opens the Add/Remove Applications window but then gets stuck on "Loading Universal Access".

Perhaps the screenshot below will explain it better :)

[http://img223.imageshack.us/img223/5589/screenshotpps.png]("http://img223.imageshack.us/img223/5589/screenshotpps.png")

It's been stuck like that for about 10 minutes now; Any help would be greatly apreciated :)

* Edit *
I've used "Add/Remove Applications" before, infact I used it just last night...?

---

### Post by kostkon on 2009-06-19
First of all, open a terminal and give
```
sudo apt-get update
```
and see if you will get any errors.

Also, try running Add/Remove in the terminal and check again for any error messages. You can run it by giving:
```
gnome-app-install
```

---

### Post by krusadr on 2009-06-19
Tried both commands, neither gives any errors and the second just opens the Add/Remove window with the same result :(

Thanks for the response though :)

---

### Post by kostkon on 2009-06-19
You could try reinstalling it, either using Synaptic or in the terminal like this
```
sudo apt-get install gnome-app-install --reinstall
```

---

### Post by krusadr on 2009-06-19
Thanks; That's fixed it :)

---

### Post by Bondrake on 2009-06-21
I'm seeing this issue with a fully patched Karmic Koala (9.10) and wasn't able to resolve it by forcing a reinstall of gnome-app-install.  Any other suggestions?

---

### Post by MrD_scifi on 2011-04-27
> **Bondrake said:**
> I'm seeing this issue with a fully patched Karmic Koala (9.10) and wasn't able to resolve it by forcing a reinstall of gnome-app-install.  Any other suggestions?

I have been hit by this after upgrading the current release of Uberstudent (10.04) manually to 10.10.  It's an annoyance right now, having to install everything manually.

---


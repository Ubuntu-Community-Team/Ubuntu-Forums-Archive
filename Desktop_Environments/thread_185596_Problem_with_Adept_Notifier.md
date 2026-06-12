---
title: "Problem with Adept Notifier"
date: 2006-06-01
forum: Desktop Environments
---

### Post by abhitux on 2006-06-01
I have a problem with Adept Notifier (and it's installation of updates). I was in the process of downloading and installing the updates when the electricity went off. I had to close the application (because my UPS doesn't support for more than 2 minutes). 

Now, it wouldn't  install any new programme via apt get. 

It gives me the following error:
*E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.*

Anyway, I could solve this out? Any guidance would be more than appreciated. Thanks in advance.

---

### Post by tonyr on 2006-06-01
Did you try to run **sudo dpkg --configure -a** as suggested in a terminal?
Gnome Terminal: **Applications->Accessories->Terminal**
KDE Terminal: Kmenu->**System->Terminal Program (Konsole)**

---

### Post by abhitux on 2006-06-01
Yes, now it works just fine. I didn't know about the correct command; because I had copied the same thing that had displayed on the terminal.

In future what is the best way to avoid it? 

Thanks!

---

### Post by tonyr on 2006-06-01
I don't know of any way to avoid it.  Even without power outages, things can still
go wrong with updates, leaving the overall state of update record keeping
somewhat confused.  The best that can be done is to try to recover gracefully.
I think a majority of Ubuntu users have, at one time or another, had to recover
after some update failure.  The most common recovery commands are
```

sudo dpkg --configure -a
sudo apt-get install -f

```

See **man dpkg** and **man apt-get**.

---

### Post by abhitux on 2006-06-05
Thanks! However, I still dont feel comfortable with the notifier; it consumes a lot of resources and tends to hang; even while other applications work great. 

I was expecting that KDE would be optimised for ubuntu; it definitely feels "faster" but the key components like this notifier throw up at times.

---


---
title: "Maximized windows don't have a title bar"
date: 2009-04-27
forum: General Help
---

### Post by snyperof1 on 2009-04-27
Fresh install of Ubuntu 9.04, and in gnome+compiz desktop environment my maximized windows do not have a title bar [Screenshot.png]. 

Non-maximized windows behave and look perfectly normal [Screenshot-1.png].

I've played around with CCSM to no avail, some older threads talk about the Place Plugin, but nothing is working for me. I know its a simple setting and not a major problem with the window manager, graphics, etc. Does anyone know the magical setting that will fix this? 

I can provide more details if things still aren't clear.

Thanks for the help

---

### Post by kiwikat on 2009-04-27
Do you happen to have maximus installed?  If so, you should remove that.

Also, installing an emerald theme or a window border with gnome-art should fix it.

I spent a couple hours last night trying to fix the problem myself.  I'm still relatively a linux n00b, so if someone else has better advice, feel free to add something. :)

---

### Post by snyperof1 on 2009-04-27
Thats it!

Uninstalled maximus using:

```
sudo apt-get purge maximus
```

And its fixed.

Still a little puzzling why maximus was installed/configured to behave that way on a freshly installed system. But alls well and purging the package doesn't seem to have any negative side effects.

Thank you very much

---

### Post by Seventh Reign on 2009-04-27
Maximus is installed with the Netbook Remix if you have that.

---


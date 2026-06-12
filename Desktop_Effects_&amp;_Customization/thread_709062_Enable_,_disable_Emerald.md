---
title: "Enable , disable Emerald"
date: 2008-02-27
forum: Desktop Effects &amp; Customization
---

### Post by HuBaghdadi on 2008-02-27
Hi.
I use Emerald to decorate my lovely Ubuntu.
Yesterday, I tried to switch back to Ubuntu original theme (you know, the orange one) to remember how it looks, but I couldn't.
How to disable Emerald?
Other threads suggest to uninstall Emerald, well I don't want to un-install it completely, I just want to live a couple of days with Ubuntu original theme.
Any ideas?
Of course, I want to know how to enable Emerald again :)
Thanks.

---

### Post by swatto on 2008-02-27
Hi,

You could install fusion-icon and manage compiz and emerald from there - I think it gives you the option to switch window decorator (from emerald to your default one) so this may work - not sure though because im new to linux but you could always give it a try :)

---

### Post by bwang on 2008-02-28
To return to Metacity (GNOME's default window manager):

Alt+F2, then type
metacity --replace

---

### Post by Yellow Pasque on 2008-02-28
```
sudo gedit /usr/bin/compiz
```
Go to Line 71 and you'll see this:
> # Use emerald by default if it exist
USE_EMERALD="yes"
Change it to no, Save it, and restart Compiz.

---


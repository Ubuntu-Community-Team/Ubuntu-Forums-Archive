---
title: "Setting Nautilus as default file manager on Xubuntu"
date: 2008-09-26
forum: Desktop Environments
---

### Post by kwaanens on 2008-09-26
I'm using Xubuntu, and would like to change the file manager from Thunar to Nautilus.

I've tried seraching, and fiddling with some things, but to no avail.

How do I do that?

---

### Post by Vahids on 2008-11-02
goto Terminal and type:

```
sudo apt-get install nautilus
```

;)

---

### Post by kwaanens on 2008-11-02
That installs Nautilus, but it obviously does _not_ set it as default file manager in XFCE. (However, I'm back to using Gnome exclusively, so it does not matter that much to me anymore)

---

### Post by jittopjose on 2008-11-02
i have installed xubuntu-desktop on my ubuntu intallation. so have nautilus, thunar, pcmanfm in my system. how can i make pcman or nautilus defalut in my xubuntu session?
jittos....

---

### Post by fallingleaf on 2008-12-30
I'd love to find this out too.  I love XFCE but I miss the features of Nautilus.  I found an old howto thread but the config files it says to edit don't seem to exist.

---

### Post by grausch on 2009-04-05
Hi,

I realise this is an older thread, but I have recently switched to Xubuntu 9.04. Now, I need Nautilus to access my network shares. I have tried the other methods in these forums to access the shares through thunar, but they did not work. Nautilus works perfectly, and I can access the terminal to open it, but I would like to set Nautilus to the default browser to enable other users to access my network shares. Can anyone help with this?

---

### Post by chessnerd on 2009-04-05
Well, I recently put Nautilus on Xubuntu 8.04. I don't know if they've changed anything in Jaunty, and I don't know how to make it the default file manager, but to add it, open a terminal and put in:
```
sudo apt-get install nautilus
```
Then, after it installs, open Nautilus with:
```
nautilus --no-desktop
```
You should now be able to use Nautilus in Xubuntu.

(Important: if you just put in the command "nautilus" your desktop environment will change to GNOME. Found this out through personal experience ;))

---

### Post by phoinx on 2010-10-06
Maybe [https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager) help someone...

---


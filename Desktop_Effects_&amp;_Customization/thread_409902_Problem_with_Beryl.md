---
title: "Problem with Beryl"
date: 2007-04-15
forum: Desktop Effects &amp; Customization
---

### Post by thorosius on 2007-04-15
Hy!
I do not have a working modem and I am for months been trying to share an internet connection with a windows machine. Bottom line: I have no internet connection in ubuntu:( . I downloaded all the packages from ubunut beryl website. Now how do I install beryl considering I am offline. I have searched the internet and most of the guides assume that an Internet connection is present. If you can point me to any helpful material please do.

---

### Post by aidanr on 2007-04-15
grab beryl, beryl-core, libberyldecoration0, libberylsettings0, libberylsettings0-gconf, beryl-manager, beryl-plugins, beryl-plugins-data, beryl-settings, beryl-settings-bindings, emerald, libemeraldengine0, emerald-themes from [http://ubuntu.beryl-project.org/dists/edgy/main/](http://ubuntu.beryl-project.org/dists/edgy/main/)

save them to a folder, open a terminal at that directory and do a 
sudo dpkg -i *.deb

i think that should work, someone correct me if i'm wrong

---

### Post by thorosius on 2007-04-15
I have installed it and it runs fine but only animations are active and the title bar has changed to a transparent one other than that nothings changed like icons or windows. And it certainly is not like what I see in the screenshots on the internet. Have I missed something?

---

### Post by aidanr on 2007-04-15
> **thorosius said:**
> the title bar has changed to a transparent one

as in there is no window border with maximise, minimise etc?
run beryl-manager from the terminal and see if it gives and errors and also right click on the tray icon and select reload window decorator

---

### Post by ronocdh on 2007-04-21
> **aidanr said:**
> as in there is no window border with maximise, minimise etc?
run beryl-manager from the terminal and see if it gives and errors and also right click on the tray icon and select reload window decorator
I'm having the same trouble. When I run beryl-manager in a terminal, I get:
```
** (beryl-manager:19519): CRITICAL **: can't execute beryl-xgl: Success

** (beryl-manager:19519): CRITICAL **: can't execute beryl-xgl: Success

** (beryl-manager:19519): CRITICAL **: can't execute beryl-xgl: Success

```
That repeats a LOT. However, the BM still starts, as I can see the icon in the tray and I can use it to open preference panes and all.

---

### Post by ronocdh on 2007-04-21
> **ronocdh said:**
> I'm having the same trouble. When I run beryl-manager in a terminal, I get:
```
** (beryl-manager:19519): CRITICAL **: can't execute beryl-xgl: Success

** (beryl-manager:19519): CRITICAL **: can't execute beryl-xgl: Success

** (beryl-manager:19519): CRITICAL **: can't execute beryl-xgl: Success

```
That repeats a LOT. However, the BM still starts, as I can see the icon in the tray and I can use it to open preference panes and all.
I solved this for the time being by right clicking on beryl manager and doing Select Window Decorator>GTK Window Decorator.

At least I can see my title bars now!

---


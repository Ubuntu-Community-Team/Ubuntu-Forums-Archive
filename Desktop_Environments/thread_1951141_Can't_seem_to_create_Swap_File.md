---
title: "Can't seem to create Swap File"
date: 2012-04-02
forum: Desktop Environments
---

### Post by johnq1216 on 2012-04-02
Hi!  I'm a long time Windows user, first time Ubuntu user.  From windows, I've partitioned 10 GB for Ubuntu.  I installed it from a USB Flash Drive (I'm using a netbook that doesn't have a CD tray)

During the installation, I've chosen not to create a Swap File because I had a hard time getting this thing installed and I just wanted to get it over with and create a Swap File later.

Following directions from this site:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I went to terminal and typed this command:
gksu gparted

but I get this error message:
john@Acer-AOD250:~$ gksu gparted

(gksu:3957): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:3957): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:3957): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:3957): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


Where do I go from here?  How can I create a Swap File from that 1 GB partition I created?

---

### Post by papibe on 2012-04-02
> **johnq1216 said:**
> (gksu:3957): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"

Hi johnq1216. Welcome to forums!

That's is a known bug (check it [here]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/762167")). To solve it install this package: gtk2-engines-pixbuf
```
sudo apt-get install gtk2-engines-pixbuf
```
Hope that helps.
Regards.

---


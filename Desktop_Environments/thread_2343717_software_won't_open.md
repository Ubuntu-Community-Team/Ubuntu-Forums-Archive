---
title: "software won't open"
date: 2016-11-18
forum: Desktop Environments
---

### Post by yegnal on 2016-11-18
Cannot open Ubuntu Software, 16.04 LTS, what gives ?

---

### Post by Frogs Hair on 2016-11-18
Start by running the software updater if you haven't already. If it still doesn't open try the following command.

```
ubuntu-software
```

---

### Post by yegnal on 2016-11-18
The output of that command is:
(ubuntu-software:2307): Gs-WARNING **: failed to open plugin /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: cannot open shared object file: No such file or directory

---

### Post by Frogs Hair on 2016-11-18
There is a bug report on this , Ubuntu Software is the re-branded Gnome software . The synaptic package manger will work in place of Ubuntu Software  until it's sorted though I thought this was resolved by an update. Copy and paste th following in the terminal. There will be a password prompt.  

```
sudo apt-get install synaptic 
``````
sudo apt-get install apt-xapian-index
```
```
sudo update-apt-xapian-index -vf
```


[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573453](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573453)

---

### Post by Derek_Stafford on 2016-11-24
I have the same issue with Ubuntu Software on 16.04. 
Running the command ...  ubuntu-software results in the following:

(ubuntu-software:3893): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:3893): GLib-CRITICAL **: g_dir_read_name: assertion 'dir != NULL' failed

(ubuntu-software:3893): Gtk-WARNING **: Error loading image 'file:///usr/share/gnome-software/featured-gimp.png': Error opening file: Too many open files

(ubuntu-software:3893): GLib-ERROR **: Creating pipes for GWakeup: Too many open files

---


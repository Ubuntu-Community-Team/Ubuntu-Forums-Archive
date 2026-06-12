---
title: "Advanced Compiz settings in 7.10?"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by tom66 on 2007-10-19
I've done a couple of Google searches and I can't seem to find out how to enable the extra effects I've heard about, such as the Cube and various other animations and widgets I've heard about. I've upgraded from XP (it's uber awesome so far) so I'm relatively new to Linux / Ubuntu / Unix-like systems (only a bit of ssh experience, but not much), so please explain everything carefully. 

Thanks.

---

### Post by frenchcr on 2007-10-19
read the thread above this one called
Desktop cube 7.10 ( 1 2)
it tells you in there

pls read other threads first

---

### Post by tom66 on 2007-10-19
Thanks, but...

I found the following happened when I tried the solution in the thread:

```

thomas@orpheus:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for thomas:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
thomas@orpheus:~$ 

```

---

### Post by GnuB on 2007-10-19
> **tom66 said:**
> Thanks, but...

I found the following happened when I tried the solution in the thread:

```

thomas@orpheus:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for thomas:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
thomas@orpheus:~$ 

```

I am having the same problem. Just like the name implies, I'm a noob to linux, so any help would be greatly appreciated. Thanks!

---

### Post by epicurus on 2007-10-19
Hi 

I have installed compiz with the extra effect (so cool)

I have a Nvidia 8800GTX card and this is what I did from a fresh install and restricted drivers installed.

went to system/administration/synaptic package manager

searched for compiz and selected to install the following

compizconfig-settings-manager
gnome-compiz-manager

after installed I had the "advanced desktop effect settings" in System/Preference which allowed me to enable or disable most of the effects.

hope this helps

---

### Post by GnuB on 2007-10-19
epicurus,

Thanks for the help! I have been messing around with the add/remove applications and noticed that when I was searching, the "Show:" wasn't set to all available so I couldn't see the package. When I went back to the Synaptics Manager, I found everything and installed it. I'm installing right now. I'll let yall know how it goes.

---

### Post by tom66 on 2007-10-20
I tried removing then uninstalling them, but to no avail. I still have the desktop effects but I can't seem to get the cube to work or anything else.

This is the message I get:

```

libcompizconfig0:

Package libcompizconfig0 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

```

All help appreciated... thanks. :)

---


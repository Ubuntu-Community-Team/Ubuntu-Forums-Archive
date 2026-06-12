---
title: "how do i install adobe flashplayer?"
date: 2009-03-22
forum: General Help
---

### Post by lyssa on 2009-03-22
I need help, i'm new and i don't know how to install adobe flashplayer! Can anyone help me?

---

### Post by men28 on 2009-03-22
Download Flash player from there:
[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")
and then for Firefox extract and copy an .so file to ~/.mozilla/plugins

This worked for me very fine.

---

### Post by 3Miro on 2009-03-22
> **men28 said:**
> Download Flash player from there:
[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")
and then for Firefox extract and copy an .so file to ~/.mozilla/plugins

This worked for me very fine.
 Go to add/remove programs, select all available programs and install Ubuntu-restricted-extras. That is the correct method since you will get automatic updates for it later on.

---

### Post by sekinto on 2009-03-22
The best way to do it is to install it using the package manager.
You can search for the package flashplugin-nonfree in Synaptic Package Manager (System > Administration > Synaptic Package Manager). Or you can install it by opening up a terminal (Applications > Accessories > Terminal) and entering the following:
```
sudo apt-get install flashplugin-nonfree
```

---


---
title: "How to install a bugzilla patch"
date: 2009-06-23
forum: General Help
---

### Post by justcop on 2009-06-23
I have found a patch that repairs a problem I have with banshee on bugzilla.
The problem is I don't know how to intergrate the patch. Can someone help me please.

The patch I would like to install is [here]("http://bugzilla.gnome.org/attachment.cgi?id=136069&action=view")
and the application 

And the application is [banshee]("http://banshee-project.org/")

---

### Post by blueridgedog on 2009-06-23
If it is purely an issue with Banshee, then perhaps installing the latest version will be the same as applying the patch.  

I did this by adding the banshee repository via synaptic, then settings, repositories, or system then administration then software sources, then the third party software tab.  I added:

[http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main

If you hare using jaunty, you will need to change it accordingly.  Once added, issue from a terminal:

```
sudo apt-get update
```

you can do an update and you will be prompted to install the latest version.

---


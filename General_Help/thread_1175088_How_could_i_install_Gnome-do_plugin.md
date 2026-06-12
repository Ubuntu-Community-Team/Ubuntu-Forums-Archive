---
title: "How could i install Gnome-do plugin?"
date: 2009-05-31
forum: General Help
---

### Post by AlNaimi on 2009-05-31
Hi every one....
As you can see on my post title, I'm very new with ubuntu, So i need your help....
I could not install Gnome-do plugin, Because i don't know how to make theme, I tried hard to do the instructions that site provided but i failed.
They wrote:
> To install plugins system-wide:
$ ./autogen.sh
$ make
& sudo make install

To install plugins locally, open the solution file DoPlugins.mds in MonoDevelop, and build the project. Then copy the dll files of built plugins to

~/.local/share/gnome-do/plugins

In this URL: [http://do.davebsd.com/wiki/index.php?title=Installing_Do#Ubuntu]("http://do.davebsd.com/wiki/index.php?title=Installing_Do#Ubuntu")
I download the package but i don't know how to make the dll files.
I need to use file plugin.
That's all
And thanks in advance

---

### Post by mick222 on 2009-05-31
Gnome do should be installed by default. To install plugins summon gnome do click on the little arrow and go to preferances and find the plugin you want.

---

### Post by AlNaimi on 2009-05-31
There were no plugin In preferances (plugin)... I downlaoded the package but i don't no how to make file plugin to dll.... may you help me with that?

---

### Post by mick222 on 2009-05-31
the gnome do plugins should already be in the repositories search synaptic for them and install from there.

---

### Post by AlNaimi on 2009-05-31
Thaks a lot mick222 
I found it in synaptic....but there were a massage said:
> gnome-do-plugins:
 Depends: libevolution5.0-cil but it is not going to be installed
And i should make sure that all required repositories are added

EDIT:
It's a bug, Fallow this link PLZ:
[https://lists.launchpad.net/do-plugins/msg01293.html]("https://lists.launchpad.net/do-plugins/msg01293.html")

---

### Post by mick222 on 2009-06-01
> In this URL: [http://do.davebsd.com/wiki/index.php...ling_Do#Ubuntu](http://do.davebsd.com/wiki/index.php...ling_Do#Ubuntu)
have you all the ubuntu repositories including mediabuntu enabled if not install them, you don't need the source repositories . If that doesn't work install the ones from the link in your first post. Remember you might have to add the security keys.LOok her for the instructions [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu).
Here's a guide to adding gnome do it includes the new dock which i haven't tried [http://maketecheasier.com/gnome-do-docky-a-new-dock-on-the-block/2009/02/12](http://maketecheasier.com/gnome-do-docky-a-new-dock-on-the-block/2009/02/12)  this is for intrepid.

---


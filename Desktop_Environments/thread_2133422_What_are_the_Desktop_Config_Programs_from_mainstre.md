---
title: "What are the Desktop Config Programs from mainstream Ubuntu?"
date: 2013-04-08
forum: Desktop Environments
---

### Post by cefn on 2013-04-08
I've just switched to Lubuntu 13.04 Beta 2, having experienced too much instability and usability issues in Unity on 12.04 LTS. 

I'm trying to find out the packages used by Ubuntu, so I can install them in my Lubuntu.

Especially I'm interested in those which provide...
* Mouse Configuration GUI (I need to be able to have disable touchpad while typing).
* Multimedia Keys for volume control (keys which worked in 12.04 automatically to navigate music and control the soundcard volume do not work out of the box in Lubuntu, so I'd like to add the package which handles this)

There are a bunch of features from the full Ubuntu desktop which I need to recover, but the actual utilities which provide the interfaces don't seem to be listed anywhere - where referred to in the documentation, they're all called by their names as they appear in the Menu, so they're impossible to trace.

---

### Post by slickymaster on 2013-04-08
Here is a package list of Raring's packages: [Package: ubuntu-desktop (1.298)]("http://packages.ubuntu.com/raring/ubuntu-desktop")

---

### Post by cefn on 2013-04-08
> **slickymaster said:**
> Here is a package list of Raring's packages: [Package: ubuntu-desktop (1.298)]("http://packages.ubuntu.com/raring/ubuntu-desktop")

Thanks for the quick response! I had a look through that list, thanks. 

Looks like the UI for touchpad configuration mousetweaks is indeed installed, a config app which I found previously. It hangs and does nothing visible when invoked from the console.

Regards the volume keys, it's still a mystery which tool is doing that work in Unity/Ubuntu. Tried searching via Sound, Key, Multimedia, Volume and so on as well as a visual scan of the whole list of raring packages. I suppose the feature must be hidden within a collection with a less specific name, like gnome-[something] or ubuntu-settings, but I don't know how hellish it will be to experiment with incorporating whole Ubuntu subsystems within Lubuntu.

---

### Post by vasa1 on 2013-04-08
[https://help.ubuntu.com/community/Lubuntu/Mouse](https://help.ubuntu.com/community/Lubuntu/Mouse) has:

Disable touchpad while typing

@syndaemon -d -t
Optionally add -k to allow for modifer keys so that you can do CTRL-click, for example.

---

### Post by vasa1 on 2013-04-08
In case that doesn't work, see if the posts in this thread bring any joy: [https://lists.ubuntu.com/archives/lubuntu-users/2013-April/003664.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-April/003664.html)

The last post in that thread refers to Jupiter but that seems to need Mono. So I'd suggest trying out Nio's suggestion of the Touchpad-Indicator first ([https://lists.ubuntu.com/archives/lubuntu-users/2013-April/003669.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-April/003669.html)).

---


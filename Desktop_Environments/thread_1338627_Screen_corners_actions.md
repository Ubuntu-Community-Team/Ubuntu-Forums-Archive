---
title: "Screen corners actions"
date: 2009-11-26
forum: Desktop Environments
---

### Post by gooood on 2009-11-26
I am a mac user but I love linux too.
One of the feature that I'd like to have on my gnome desktop is the possibility to perform some actions pointing the mouse on the corners of the screen (for example showing the active virtual desktops).
Is that possible?

---

### Post by scorp123 on 2009-11-26
> **gooood said:**
> I am a mac user but I love linux too.
One of the feature that I'd like to have on my gnome desktop is the possibility to perform some actions pointing the mouse on the corners of the screen (for example showing the active virtual desktops).
Is that possible?
Yes, with Compiz (= Desktop effects). When I point my mouse into the upper right corner I get the "Scale Windows" effect. You Mac people call that "Exposé" I think?

Lower left corner and I get the "Expo" effect. Upper left corner and I get the "Cover Switcher" effect.

If you browse the desktop section of this forum you should find plenty of postings that explain how to configure this ...

---

### Post by gooood on 2009-11-26
thanks, I'll search for that.

---

### Post by Ginsu543 on 2009-11-27
You can also download and install Ubuntu Tweak which will allow you to set the behavior of mouse corner actions using a nice GUI. It also has several other nice tweaking options (if you've ever used TweakUI for Windows XP, you get the idea).

---

### Post by scorp123 on 2009-11-27
> **Ginsu543 said:**
> You can also download and install Ubuntu Tweak +1 on that one

This is the content of my **/etc/apt/sources.list.d/ubuntu-tweak.list** file:

```
# UbuntuTweak
# http://ubuntu-tweak.com/2008/01/22/ubuntu-tweak-has-repository-now.html#more-31
# http://www.howtoforge.com/tweaking-hidden-ubuntu-settings-with-ubuntu-tweak
# 
# apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FE85409EEAB40ECCB65740816AF0E1940624A220
#

deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu karmic main

```

The lines starting with ***#*** are comments and are ignored by the package manager. I always keep comments in my *.list files so I know where I found that repo, how to get the repo GPG keys, and so on.

So you can add that fil and store it as **/etc/apt/sources.list.d/ubuntu-tweak.list** ... Then you'd get the keys with the **"apt-key adv ..."** command described above in the comments. Once you're that far you can then install the software:

```
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

The application should then be reachable via ***Applications > System Tools > Ubuntu Tweak***

---


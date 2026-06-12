---
title: "Unity doesn't show apps!"
date: 2011-05-11
forum: Desktop Environments
---

### Post by K3fka on 2011-05-11
Okay, so here's the gist of what happened: I was annoyed with Unity showing my recent documents when I went to the "Files and Folders" thing on it, so I did a quick Google search to figure out how to disable it. I found [this page](http://linux.aldeby.org/ubuntu-natty-11-04-unity-clear-recent-documents.html) with instructions on how to do so. I ran this code: ```
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace
``` and ```
sudo apt-get remove zeitgeist
```

However, upon restarting my computer, my Unity launcher is now missing the icons to view files and folders and to view all applications. In addition, when I click on the Ubuntu symbol in the corner, I'm presented with the screen offering choices of media apps, internet apps, more apps, and to find files. However, clicking on any of these does nothing.

I have resinstalled zeitgeist and run unity --reset in attempt to fix the issue, but to no avail. I would really appreciate it if someone could help me out here! I really don't want to have to run all my applications through the terminal!

---

### Post by PhantmKllr on 2011-05-11
> **K3fka said:**
> ```
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace
```

This command looks like it purged the Sqlite database that zeitgeist depends on. Unless you find a way to replace/restore this database, your only option is to reinstall Ubuntu.

---

### Post by mc4man on 2011-05-12
> **K3fka said:**
> ```
sudo apt-get remove zeitgeist
```

However, upon restarting my computer, my Unity launcher is now missing the icons to view files and folders and to view all applications. In addition, when I click on the Ubuntu symbol in the corner, I'm presented with the screen offering choices of media apps, internet apps, more apps, and to find files. However, clicking on any of these does nothing.

I have resinstalled zeitgeist and run unity --reset in attempt to fix the issue, but to no avail. I would really appreciate it if someone could help me out here! I really don't want to have to run all my applications through the terminal!
re-install unity-place-applications
When you removed zeitgeist you also removed  it

---


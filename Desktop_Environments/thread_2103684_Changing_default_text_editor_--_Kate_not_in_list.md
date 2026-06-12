---
title: "Changing default text editor -- Kate not in list?"
date: 2013-01-10
forum: Desktop Environments
---

### Post by sabersong on 2013-01-10
I'm having trouble changing my default text editor in Kubuntu. Right now, every document, even simple text documents, open in Libre Office. I much prefer Kate for most of my GUI text needs, but the only option listed in System Settings --> Default Applications is Advanced Embedded Text Editor.

I also tried the CLI command:
```
sudo update-alternatives --config editor
```

But again, Kate isn't in the list -- just nano, ed, vi and vim. And while I'm comfortable with vi, when I'm using the GUI, I really prefer Kate. Is there another way to set the default text editor?

---

### Post by stinkeye on 2013-01-11
In gnome I have 2 editor settings 
```
sudo update-alternatives --config editor
and
sudo update-alternatives --config gnome-text-editor
```

Run
```
sudo update-alternatives --get-selections
```

and see if there is something similar in kde.

Not familiar with kde but it may just be simply associating file types to
kate which in ubuntu I can do buy right clicking on a text file.

---

### Post by sabersong on 2013-01-14
I couldn't find anything about an X- or KDE- editor in the list your first suggestion pulled up.

> Not familiar with kde but it may just be simply associating file types to
kate which in ubuntu I can do buy right clicking on a text file.

This worked for me. Thanks for the help!

---

### Post by mparillo on 2013-01-14
I am glad that you found a pretty painless work-around, but this might be the bug report:
[https://bugs.launchpad.net/ubuntu/quantal/+source/kate/+bug/1062086](https://bugs.launchpad.net/ubuntu/quantal/+source/kate/+bug/1062086)
if you are interested.

---


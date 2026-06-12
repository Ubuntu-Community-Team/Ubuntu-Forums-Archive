---
title: "Compiz and active Windows in Gnome Panel"
date: 2008-02-09
forum: Desktop Environments
---

### Post by sojusnik on 2008-02-09
Hi folks,

Since the implementation of Compiz into Ubuntu the behavior of the opened windows in the Gnome Panel has changed. I'm using now 4 "virtual" Workspaces with Compiz on Ubuntu 7.10.

Nowadays the gnome panel is showing all windows in the panel, from all Workspaces. 

Before Compiz, the gnome panel showed only the windows from the workspace you were working with, so when you worked in "Workspace 1" and had 3 windows opened, you only saw these opened windows in the gnome panel, not all other active windows in other Workspaces. 

Is it possible with Compiz to have this "old gnome panel window behavior" again?

Thx in advance!

---

### Post by sojusnik on 2008-02-09
So no one knows how to configure Compiz and the gnome panel, to show only windows from the workspace you are workin with, instead of all windows in all workspaces?

---

### Post by e-dard on 2008-02-10
I am suffering from the same problem!

Annoying!

Edd

---

### Post by e-dard on 2008-02-10
Hey, 

I just did a more thorough google search and found this bug report 

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156055](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156055)

Basically a window title will appear in the panel on more than one workspace when it overlaps those two spaces.

It seems often that when app's are opened they slightly creep onto the next workspace, causing them to appear in the panel for two adjacent workspaces.

I have found by checking the window is maximized removes this problem (as the window is definatly only in one workspace then.).

Edd

---

### Post by sojusnik on 2008-02-10
Solution:

Well, I managed it to run properly.

In Compiz Config Settings Manager --> general options --> desktop size change the following to:

Number of Desktops: 1 (Before I had 4)
Vertical virtual size: 2
Horizontal virtual size: 2

I don't want to have the desktops in a row, horizontal virtual desktops: 4, so instead I used 2x2 to have a nice square.

Thank you very much!

---

### Post by bumanie on 2008-02-10
Don't know whether this will help, but it seen as one of the formative guides to compiz-fusion
[http://www.stumbleupon.com/demo/?review=1#url=http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://www.stumbleupon.com/demo/?review=1#url=http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---


---
title: "dual monitors, workspaces don't move together"
date: 2012-04-30
forum: Desktop Environments
---

### Post by jamaas on 2012-04-30
I've just installed 12.04 and am using Gnome 3.  I checked and my graphics card is AMD-ATI RV620 Firepro 2260 and I think I'm using something called fglrx drivers configured by something called AMD catalyst.  

I've got a couple of wierd behaviours, wonder if someone could suggest corrections.

1. In catalyst it seems to recognize the two dell monitors as "notebook", and I have no idea why, this is a desktop with two separate displays.  I can't see how to change it.

2. Is rather hard to describe.  Previously on 11.10 if I moved up or down through the workspaces on one display, they moved up and down together on the other.  Now with 12.04 the only one that moves up and down is the left one (primary?) and the right one just sits and doesn't move.  Have I configured something incorrectly, would like them to move together.

Thanks a bunch.

J

---

### Post by danielkraaij on 2012-05-02
This can be fixed by following this page. 
[http://gregcor.com/2011/05/07/fix-dual-monitors-in-gnome-3-aka-my-workspaces-are-broken/](http://gregcor.com/2011/05/07/fix-dual-monitors-in-gnome-3-aka-my-workspaces-are-broken/)

In your case you should be using the following command in a terminal (CTRL+ALT+T)

> gsettings set org.gnome.shell.overrides workspaces-only-on-primary false

---

### Post by jamaas on 2012-05-02
Thanks for this.  The instructions for gconf-editor do not work but it appears that this direct command did.

---


---
title: "I want to block all QT apps"
date: 2010-08-31
forum: Desktop Environments
---

### Post by usagiakumu on 2010-08-31
Perhaps I might be a minority demographic here, but I am. Is there a way and how? Ubuntu Software Center doesn't seem to have this option. I come from a long history of being a Windows power user, and I am picking up pretty quickly with this stuff. I find QT ones leave little screen droppings and it bugs me to no end. Some might not, but I like it to be kind of GTK pure. If I wanted a QT app I would have picked Kubuntu with KDE. I admit that it is kind of cool that you can run an app from another desktop and vice versa. I am not trying to start a flame war, nor am I dissing any of the developers that may have made some awesome QT application I may not know about. Is there another software center like thing I can install that at least combines all the QT and GTK ones into separate groups rather than making me fend for myself?

---

### Post by 3Miro on 2010-08-31
I use KDE, GNOME and XFCE on different machines and in order to get best performance, you should stick with native apps as much as possible. I try to use only GTK apps in Gnome and only QT apps in KDE (whenever possible). Your request is not unreasonable at all.

The only solution that I have to use Synaptic Package Manager. When you find an app that you will want (and it doesn't say QT or GTK in its description), you can go to Synaptic and check for its dependencies. If it requires QT, then don't install it.

The only other option that I can think of, is to somehow block the QT libraries from the repository, but I don't know if this is even possible.

---

### Post by usagiakumu on 2010-09-01
I am sure with time I will use the other desktops, possibly. I am pretty easy to please when it comes to apps. I just don't like the fact that QT apps have a different theme, they seem slower than GTK apps, although this may be different in KDE. They seem out of place even with a Gnome theme applied to them. I know I may sound petty, but it is these petty little differences that unsettle me. I am the same way in Windows, if some random application had it's own theme and would try to sit out of place I would remove it and go look for another app that matched the WinAPI theme. :popcorn:

---

### Post by 3Miro on 2010-09-01
Every app needs a set of libraries to work, Gnome apps use GTK libraries which get loaded by default if you are using Gnome. However, KDE apps depend on QT libraries which need to be loaded in addition to GTK. Hence, KDE apps under Gnome take more resources are are somewhat sluggish, while you have the reverse in KDE. Sticking to one group of apps as much as possible is a good idea.

The only way I know how to distinguish QT and GTK apps is by either reading ht description or checking the dependencies. If anyone knows of another way, I will be glad to read about it.

---

### Post by usagiakumu on 2010-09-01
> **3Miro said:**
> Every app needs a set of libraries to work, Gnome apps use GTK libraries which get loaded by default if you are using Gnome. However, KDE apps depend on QT libraries which need to be loaded in addition to GTK. Hence, KDE apps under Gnome take more resources are are somewhat sluggish, while you have the reverse in KDE. Sticking to one group of apps as much as possible is a good idea.

The only way I know how to distinguish QT and GTK apps is by either reading ht description or checking the dependencies. If anyone knows of another way, I will be glad to read about it.

I figured as much about the first point. The second, however, seems an issue for first time users. It bugs the heck out of me that there isn't some script that checks to see if an application requires what dependencies are needed. .DEB seems to be able to resolve dependencies, but can't somehow, at the very least warn me about putting unwanted trash on my computer? Have a window pop up saying "This requires QT, please check to see if a GTK application can do what you need." and have a check-box for "Never show this window again." Would it really be that hard to code? Once I learn how I might code it I will submit it. I am surprised no body has ever thought of such a time saver. Not a deal killer for me, but definitely an annoyance to me.

---


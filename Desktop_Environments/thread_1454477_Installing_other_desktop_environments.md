---
title: "Installing other desktop environments"
date: 2010-04-14
forum: Desktop Environments
---

### Post by bix15 on 2010-04-14
Just before I log into my account, I notice on the bottom of the screen there's a tool bar that says "Desktop Sessions".
My question is how can I install different desktop environments such as KDE and Xfce, and is there any way to switch between them at login??

Thanks!!

---

### Post by mk1w86 on 2010-04-14
To install the KDE desktop environment run:

```
sudo aptitude install kubuntu-desktop
```

With XFCE you have two options, you can install just the window manager or the XFCE 'desktop environment' you would get with Xubuntu which includes all the applications you get with Xubuntu.

To install just the window manager run:

```
sudo aptitude install xfce4
```

or to install the Xubuntu enviroment run:

```
sudo aptitude install xubuntu-desktop
```

You can choose the desktop to use under the Desktop Sessions you mentioned at login. ;)

---

### Post by bix15 on 2010-04-15
Thanks a lot!!
It worked...
the kubuntu-desktop was a pretty big file!!! But its done and I'm happy as a lark :)

---


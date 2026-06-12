---
title: "[dell] xubuntu-desktop in dell mini 9"
date: 2008-12-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by earthpigg on 2008-12-10
that dell desktop thing keeps screwing it up when i log into an xfce session :(

the dell bar crap wont go away, its using the gnome background image and right click context menu for some reason, and choosing 'classic desktop' makes it even weirder.

anyone encountered this before?

google doesn't seem to be helping me find the answer...

---

### Post by earthpigg on 2008-12-10
uninstalled the dell launcher package and damn near every other package with 'dell' in its name in synaptic... its still loading a bunch of gnome stuff.

:(

---

### Post by anjilslaire on 2008-12-10
I'm getting a mini 9 for Christmas and plan on wiping it and loading vanilla xubuntu, but that's not much help for you now...

I presume you are choosing the XFCE session when logging in, and not logging into gnome with all of the XFCE stuff running also?

---

### Post by earthpigg on 2008-12-10
> **anjilslaire said:**
> I presume you are choosing the XFCE session when logging in, and not logging into gnome with all of the XFCE stuff running also?

correct ;)

---

### Post by earthpigg on 2008-12-10
bump

---

### Post by iggykoopa on 2008-12-10
you can try going into a gnome session and go to preferences->sessions and remove whatever applications from there you don't want started. It may help with some of them.

---

### Post by earthpigg on 2008-12-12
> **iggykoopa said:**
> you can try going into a gnome session and go to preferences->sessions and remove whatever applications from there you don't want started. It may help with some of them.

what application is it in gnome that brings up the gnome right-click-on-the-desktop-backgroun context menu?

its really bizzare :<

---

### Post by iggykoopa on 2008-12-12
I believe that's nautilus, if your still using nautilus for file management it will try to take over your desktop. Either use thunar or launch nautilus with: nautilus --no-desktop . If your not still using nautilus I have no idea why it's doing that.

---

### Post by earthpigg on 2008-12-13
if i install thunar, how do i make that the default file manager instead of nautilus?

---

### Post by iggykoopa on 2008-12-13
did you just install xfce? or did you install xubuntu-desktop?

---

### Post by earthpigg on 2008-12-14
i installed xubuntu desktop... will installing xfce completely replace gnome or can i easily run both side by side?

---

### Post by anjilslaire on 2008-12-14
You can run them side by side, choosing which one at logon via the Sessions menu

---

### Post by earthpigg on 2008-12-14
sooo i SHOULD have installed xfce and not xubuntu-desktop?

reason i ask,

on my vanilla ubuntu 8.10 install, i did 'sudo apt-get install xubuntu-desktop' and everything worked perfectly.

on my _**dell mini 9 with dell's ubuntu remix**_, i did the same thing and got the screwy problem im seeking help for in this thread.

---

### Post by iggykoopa on 2008-12-14
no you did right, it may just be an issue with the dell repo's. Not sure how else to help you. To get right of the gnome right click stuff you could try:
```

killall nautilus

```
but that will only fix it that time, if you reboot you will probably have the same issues.

---


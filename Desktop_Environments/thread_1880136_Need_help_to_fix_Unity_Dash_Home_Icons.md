---
title: "Need help to fix Unity Dash Home Icons"
date: 2011-11-13
forum: Desktop Environments
---

### Post by livedlooz on 2011-11-13
Hi,

I need help to fix this issue. My Dash Home/Lenses icons is having problem. Is there anyway to fix this?

[IMG]http://i55.tinypic.com/2jfnc5z.jpg[/IMG]

---

### Post by AppleWiz on 2011-11-13
Sorry to post a "me too" but I see exactly the same.

Going to the terminal and typing unity --update-icons may work for some, but it locks up here. There are a lot of things installed on our machines, but hardly any of it is accessible!

I got this result after installing the Unity/Gnome desktop option in Kubuntu to try it out. KDE works basically fine. Unity keeps it's secrets for now...

~Rob

---

### Post by BillyBoa on 2011-11-13
Try to reset the icons

```
unity --reset-icons
```

and if not to reset Unity

```
unity --reset
```

If the problem continues try to reset Compiz

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

---

### Post by AppleWiz on 2011-11-13
unity --reset-icons
>
glib.glib-gobject <unknown>:0 invalid cast from BamfWindow to BamfApplication

WARN unity.dash.filesystems.cpp:199 Unable to enumerate child processes in directory usr/share/unity/lenses

Then lock-up :(

Restart...

unity --reset
>
Same result, except exiting terminal is possible.

gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
>
Same result.

Possibly a file missing in usr/share/unity/lenses   ?
I'll have a search for "BamfApplication" now.

Thanks for help,
Rob.

---

### Post by AppleWiz on 2011-11-13
Perhaps the offending package:
[https://launchpad.net/ubuntu/+source/bamf/0.2.104-0ubuntu1](https://launchpad.net/ubuntu/+source/bamf/0.2.104-0ubuntu1)

A related thread:
[http://ubuntuforums.org/showthread.php?t=1859196](http://ubuntuforums.org/showthread.php?t=1859196)

---

### Post by BillyBoa on 2011-11-13
Go to synaptic (if you don't have it install it through Ubuntu Software Center) and search for the packages Unity-lens. There are 3 of them (applications-files-music) and with right click choose to reinstall them.

---

### Post by AppleWiz on 2011-11-13
Thanks BBoa,

The 3 "lens" applications from Ubuntu s/ware centre solved it for me at least!

Hope it works for the original thread poster.

---

### Post by livedlooz on 2011-11-16
Sorry, none of the stated methods work on me..

Here is the process how i got that bugs.
1. reduce font size using text scaling factor.
2. then suddenly the icons on dash home cut into half (almost half actually)

the rest part of the lenses is ok, except the main launcher.

Unity should have a setting to reduce the icons, imo.

off topic: the heck? i didn't receive email notifications for this thread even though I've subscribed it.

---

### Post by BillyBoa on 2011-11-16
Just check the Unity plugin in CompizConfig, if it's selected.

[IMG]http://ubuntuforums.org/picture.php?albumid=2448&pictureid=8289[/IMG]

---

### Post by BillyBoa on 2011-11-16
And the ultimate solution

Reinstall the Unity

```
sudo apt-get install --reinstall ubuntu-desktop 
```

I hope this last one to work

---

### Post by livedlooz on 2011-11-22
Thanks, I'll try it.

---

### Post by livedlooz on 2011-11-22
lolz!! someone please kill me (joke)

There is only one way to fix this, set the scaling to default value (1) and then change all fonts size manually. This will not affect the icon anymore.

Glad the second poster found a way to fix his problem ;)

---


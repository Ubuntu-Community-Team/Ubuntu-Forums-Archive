---
title: "Is it possible to customize the indicator applet?"
date: 2009-10-25
forum: Desktop Environments
---

### Post by leandromartinez98 on 2009-10-25
I wander if is it possible to customize the indicator
applet content, that is, that small envelope that when
clicked show empathy and evolution now. I don't use
evolution at all, so it would be nice to:

1 - Put there a link that automatically opens a web
page in my gmail.

2 - remove the evolution link

3 - add a link to skype, so I can remove the skype tray
icon

and other stuff like this, so one can customize the 
behavior of the envelope that, for me now, is only
a two-click way to empathy.

---

### Post by Javi Pirate on 2009-10-25
Has far I know is not possible right now, maybe in the **future** this *function* this will be implement.

---

### Post by gnuisancev3 on 2009-10-25
> **leandromartinez98 said:**
> I wander if is it possible to customize the indicator
applet content, that is, that small envelope that when
clicked show empathy and evolution now. I don't use
evolution at all, so it would be nice to:

1 - Put there a link that automatically opens a web
page in my gmail.

2 - remove the evolution link

3 - add a link to skype, so I can remove the skype tray
icon

and other stuff like this, so one can customize the 
behavior of the envelope that, for me now, is only
a two-click way to empathy.

Removing the evolution link is simple, just uninstall evolution.  Adding stuff will be harder.

---

### Post by Boondoklife on 2009-10-26
Yea moving skype into the indicator would be nice, as that green circle just kills the pretty mono icons in karmic.

Though since skype is closed source will it be possible is another question. Though I have a few gripes about skypes look in general: use of those tacky popups instead of dbus, ugly tray icon, have it check for an existing instance before launching, etc.

---

### Post by crazy2be on 2009-11-09
It seems the list of applications shown permanently in the applet is from 
```
/usr/share/indicators/messages/applications
```
Each file is a plaintext file that contains the path to a .desktop file where the description and command are loaded from. There's a bit of information about indicators (and their changes in 9.10) [here]("http://blog.garethj.com/2009/10/indicator-applet-api-changes-in-ubuntu-9-10/").

---

### Post by kostkon on 2009-11-09
> **leandromartinez98 said:**
> I wander if is it possible to customize the indicator
applet content, that is, that small envelope that when
clicked show empathy and evolution now. I don't use
evolution at all, so it would be nice to:

1 - Put there a link that automatically opens a web
page in my gmail.

2 - remove the evolution link

3 - add a link to skype, so I can remove the skype tray
icon

and other stuff like this, so one can customize the 
behavior of the envelope that, for me now, is only
a two-click way to empathy.

> **Boondoklife said:**
> Yea moving skype into the indicator would be nice, as that green circle just kills the pretty mono icons in karmic.

Though since skype is closed source will it be possible is another question. Though I have a few gripes about skypes look in general: use of those tacky popups instead of dbus, ugly tray icon, have it check for an existing instance before launching, etc.
Yes. There is already a script that does all these. You can find it in [this thread here]("http://ubuntuforums.org/showthread.php?t=1146775"). Its latest version can be found [in this post]("http://ubuntuforums.org/showpost.php?p=7530321&postcount=12").

Hope that helps.

---


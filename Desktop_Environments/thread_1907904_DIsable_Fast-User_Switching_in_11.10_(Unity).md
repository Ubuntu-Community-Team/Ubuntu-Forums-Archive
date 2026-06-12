---
title: "DIsable Fast-User Switching in 11.10 (Unity)"
date: 2012-01-12
forum: Desktop Environments
---

### Post by ThePol1 on 2012-01-12
[COLOR=black][FONT=Verdana]Does anyone know how to disable fast-user switching in 11.10 (Unity)? I've come across some posts that talk about doing this in Gnome, but nothing related to Unity.[/FONT][/COLOR]

---

### Post by Krytarik on 2012-01-12
> **ThePol1 said:**
> [COLOR=black][FONT=Verdana]Does anyone know how to disable fast-user switching in 11.10 (Unity)? I've come across some posts that talk about doing this in Gnome, but nothing related to Unity.[/FONT][/COLOR]
What exactly do you mean by this?

[LIST]
[*]If you mean removing the related panel item, please see the second option in this post:

[http://www.tuxgarage.com/2011/11/hide-users-name-in-top-panel-ubuntu.html](http://www.tuxgarage.com/2011/11/hide-users-name-in-top-panel-ubuntu.html)

This works for Unity as well as for the Gnome Fallback sessions.
[/LIST]

[LIST]
[*]If you mean disabling that feature completely, it should be the same in all Gnome-based sessions, to which Unity belongs too, but I don't know yet if that is possible, and if so, how.
[/LIST]
Regards.

---

### Post by ThePol1 on 2012-01-12
> **Krytarik said:**
> What exactly do you mean by this?

[LIST]
[*]If you mean removing the related panel item, please see the second option in this post:
 
[http://www.tuxgarage.com/2011/11/hide-users-name-in-top-panel-ubuntu.html](http://www.tuxgarage.com/2011/11/hide-users-name-in-top-panel-ubuntu.html)
 
This works for Unity as well as for the Gnome Fallback sessions.
[/LIST]
[LIST]
[*]If you mean disabling that feature completely, it should be the same in all Gnome-based sessions, to which Unity belongs too, but I don't know yet if that is possible, and if so, how.
[/LIST]Regards.
 
Hi Krytarik -- I mean disabling the feature completely. I thought there may be a setting in [FONT=Courier New]gconf-editor[/FONT] that would disable this functionality. The link you provided discusses removing the panel completely, which is something I don't want to do. Thanks!

---

### Post by Krytarik on 2012-01-12
> **ThePol1 said:**
> I mean disabling the feature completely. I thought there may be a setting in [FONT=Courier New]gconf-editor[/FONT] that would disable this functionality.
I didn't find a respective key in GConf-Editor upon a quick search, the same applies to a quick Google Search. But I suggest also searching in DConf-Editor (package "dconf-tools"), as quite a lot of settings are already migrated to DConf in Oneiric 11.10; I can't do that myself right now as I'm not running it currently (I'm only running a Live-ISO occasionally).

> **ThePol1 said:**
> The link you provided discusses removing the panel completely, which is something I don't want to do.
Nope, it just removes the concerning Indicator, as I mentioned before, but I guess you meant that. ;-)

---

### Post by ThePol1 on 2012-01-12
Found a partial solution. As [Krytarik]("http://ubuntuforums.org/member.php?u=1187548") suggested, I looked in dconf-editor. The required setting is under: org->gnome->desktop->lockdown->disable-user-switching. I also edited: org->gnome->desktop->screensaver->user-switch-enabled. :D

---

### Post by Krytarik on 2012-01-12
> **ThePol1 said:**
> Found a partial solution. As [Krytarik]("http://ubuntuforums.org/member.php?u=1187548") suggested, I looked in dconf-editor. The required setting is under: org->gnome->desktop->lockdown->disable-user-switching. I also edited: org->gnome->desktop->screensaver->user-switch-enabled. :D
And in previous versions of Ubuntu, where that key is still stored in GConf, it's:

"/desktop/gnome/lockdown/disable_user_switching"

Lazy me, only searched for "fast", not even for "switch". [-X :P
(because I was quite sure at that time that you just want to remove that ugly panel item)

Oops, didn't notice the screensaver part after you edited the post. Here you go :P :

"/apps/gnome-screensaver/user_switch_enabled"

---

### Post by ThePol1 on 2012-01-12
> **Krytarik said:**
> And in previous versions of Ubuntu, where that key is still stored in GConf, it's:

"/desktop/gnome/lockdown/disable_user_switching"

Lazy me, only searched for "fast", not even for "switch". [-X :P
(because I was quite sure at that time that you just want to remove that ugly panel item)

Oops, didn't notice the screensaver part after you edited the post. Here you go :P :

"/apps/gnome-screensaver/user_switch_enabled"

Thank you very much  [Krytarik]("http://ubuntuforums.org/member.php?u=1187548")! I know it's probably not possible, but it would be nice to keep the user name indicator in the panel but disable the switching functionality. The computer I'm working on is used by multiple people...

---

### Post by Krytarik on 2012-01-12
> **ThePol1 said:**
> I know it's probably not possible, but it would be nice to keep the user name indicator in the panel but disable the switching functionality.
Is the Indicator disabled automatically then, when you lock down the Switching feature?

---

### Post by ThePol1 on 2012-01-12
> **Krytarik said:**
> Is the Indicator disabled automatically then, when you lock-down the Switching feature?

No, it's not.

Just to make sure I'm not confusing things:
As far as I know, you can use the switching feature from three locations in Unity:
1) Screen lock (after screen saver resume).
2) Top-right 'computer' icon (also allows for logout, screen lock, etc.)
3) Top-right user name indicator.

Dbus-editor allows me to disable user switching in #1 and #2. In terms of #3, using dbus-editor, I have to disable the visibility of the top-right user name indicator (or lock down the Switching feature) in order to restrict user switching. It would be nice to be able to disable user switching without having to completely hide the indicator.

---

### Post by Krytarik on 2012-01-12
> **ThePol1 said:**
> ... I have to disable the visibility of the top-right user name indicator in order to restrict user switching. ...
I thought user switching just wouldn't work when you've locked down the Switching feature and are then trying to use the Indicator to initiate a switch. Not?

---

### Post by ThePol1 on 2012-01-12
> **Krytarik said:**
> I thought user switching just wouldn't work when you've locked down the Switching feature and are then trying to use the Indicator to initiate a switch. Not?

No. When I lock down the Switching feature the Indicator is disabled (hidden).

---

### Post by Krytarik on 2012-01-12
> **ThePol1 said:**
> No. When I lock down the Switching feature the Indicator is disabled (hidden).
Too bad! So it's indeed disabled automatically as soon as the Switching feature is locked down, as I asked before, and what you negated before. ;-)

Maybe you could find an Indicator that simply displays the name of the logged in user; or maybe hack that Indicator so that it doesn't check if switching would actually be possible, if you are skilled to that extent.

---


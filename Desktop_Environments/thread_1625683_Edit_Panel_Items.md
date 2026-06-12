---
title: "Edit Panel Items?"
date: 2010-11-19
forum: Desktop Environments
---

### Post by Mario1776 on 2010-11-19
[IMG]http://img508.imageshack.us/img508/9364/screenshot03.png[/IMG]

The panel items Indicator Applet, Indicator Applet Session and Notification Area seem to display numerous icons, some of which I have no use for. I would like to know if it is possible to get rid of three icons I do not want to display.

In the attached screen shot there is from left to right (1) Volume, (2) Network Connection, (3) Battery, (4) Volume, (5) Email (6) Time and Date, (7) Instant Messaging, (8 ) Shutdown Options.

I would like to get rid of (1) Volume, (5) Email, (7) Instant Messaging.
(1) Volume comes with the Notification Area
(5) Email comes with Indicator Applet
(7) Instant Messaging comes with Indicator Applet Session

Is it possible to edit the panel items Indicator Applet, Indicator Applet Session and Notification Area to eliminate the three unwanted icons? Could I disable or uninstall the applications that correspond to them and make them disappear that way?

EDIT: D'oh. Stupid of me not to mention the version: Ubuntu Desktop 10.10

---

### Post by tom4everitt on 2010-11-19
On my 10.04 I get an option "remove from panel" when I right click on them. I assume that would remove them (I didn't want to try though, as I'm not sure how to get them back).

---

### Post by kerry_s on 2010-11-19
> **Mario1776 said:**
> [IMG]http://img508.imageshack.us/img508/9364/screenshot03.png[/IMG]

The panel items Indicator Applet, Indicator Applet Session and Notification Area seem to display numerous icons, some of which I have no use for. I would like to know if it is possible to get rid of three icons I do not want to display.

In the attached screen shot there is from left to right (1) Volume, (2) Network Connection, (3) Battery, (4) Volume, (5) Email (6) Time and Date, (7) Instant Messaging, (8 ) Shutdown Options.

I would like to get rid of (1) Volume, (5) Email, (7) Instant Messaging.
(1) Volume comes with the Notification Area
(5) Email comes with Indicator Applet
(7) Instant Messaging comes with Indicator Applet Session

Is it possible to edit the panel items Indicator Applet, Indicator Applet Session and Notification Area to eliminate the three unwanted icons? Could I disable or uninstall the applications that correspond to them and make them disappear that way?

yes, you can just uninstall it.
i wish is was like awn, so you can just uncheck. :p

---

### Post by sikander3786 on 2010-11-19
> **kerry_s said:**
> yes, you can just uninstall it.
i wish is was like awn, so you can just uncheck. :p
I know it would be called Thread Hijacking but I want to ask a little question.

I have installed ubuntu-netbook package on Maverick Desktop. It doesn't look like the one in your screenshot. Is there anyway to customize it?

---

### Post by Mario1776 on 2010-11-19
tom4everitt
"Remove From Panel" applies to the panel items Indicator Applet, Indicator Applet Session and Notification Area but each of those panel items displays numerous icons. Using "Remove From Panel" to get rid of one of the unwanted icons would get rid of other wanted icons.

kerry_s
Hey! That is exactly what I am looking for. How did you display the "Indicator Applet Preferences" menu? When I try to right click on icons from the Indicator Applet I do not get an option to edit Indicator Applet Preferences.

sikander3786
Meh, I tried using Ubuntu Netbook Remix 10.10, the user interface seemed so constrained and limited for the sake of simplicity I couldn't stand it. It seemed impossible to access to the file system and difficult to customize the desktop environment. Perhaps it was all simply a matter of me being an extreme amateur with Linux/Ubuntu but when I switched to Ubuntu Desktop 10.10 it as ahellofalot more comfortable, even with my current customization problem.

---

### Post by kerry_s on 2010-11-19
> **sikander3786 said:**
> I know it would be called Thread Hijacking but I want to ask a little question.

I have installed ubuntu-netbook package on Maverick Desktop. It doesn't look like the one in your screenshot. Is there anyway to customize it?


i'm not using netbook, just the standard desktop.
i replaced gnome-panel with awn so all panel's are awn.

> Hey! That is exactly what I am looking for. How did you display the "Indicator Applet Preferences" menu? When I try to right click on icons from the Indicator Applet I do not get an option to edit Indicator Applet Preferences.


i'm using awn indicator applets, they have menus.

you need to use the latest from ppa:
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

### Post by sikander3786 on 2010-11-19
> **kerry_s said:**
> i'm not using netbook, just the standard desktop.
i replaced gnome-panel with awn so all panel's are awn.


Yes I figured it out after I posted :-)

But I might have seen another screenshot featuring netbook in some other thread... Don't remember exactly.

Thanks.

---

### Post by kerry_s on 2010-11-19
> **sikander3786 said:**
> Yes I figured it out after I posted :-)

But I might have seen another screenshot featuring netbook in some other thread... Don't remember exactly.

Thanks.

yeah, i was running netbook before.

off the top of my head:

install dconf-tool & run dconf-editor to change the netbook clock settings.

you can change the panel images in /usr/share/unity

you can use gconf-editor to add launchers that don't have the pin listed.


not really much else you can do it's limited


the way i have it set now is a lot more space.
here's what i see.

---

### Post by sikander3786 on 2010-11-19
> **kerry_s said:**
> yeah, i was running netbook before.

off the top of my head:

install dconf-tool & run dconf-editor to change the netbook clock settings.

you can change the panel images in /usr/share/unity

you can use gconf-editor to add launchers that don't have the pin listed.


not really much else you can do it's limited


the way i have it set now is a lot more space.
here's what i see.
Means I can trust my memory :-)

Ok I'll try those and see what happens.

Thanks for the tips.

---


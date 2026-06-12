---
title: "Installing ubuntu-desktop on top of Kubuntu Quantal"
date: 2012-11-17
forum: Desktop Environments
---

### Post by Erik1984 on 2012-11-17
I know that in general it might not be such a good idea to mix desktop environments. However I like both KDE and Unity and don't mind some extra applications. So I'm willing too accept the extra menu clutter in KDE. But there are a few concerns:

1. Both Kubuntu and Ubuntu use LightDM, should I expect some problems there? Which LightDM theme will be used by default?
2. Should I expect problems with some of the KDE services like Nepomuk and Akonadi when starting a Unity session?
3. Am I overlooking things, are there other known issues with this sort of setup?

Anyone of you who has both KDE and Unity installed and what are your experiences?

---

### Post by Erik1984 on 2012-11-18
*bump*

---

### Post by Erik1984 on 2012-11-22
Ok, I just did it. Well not entirely happy but it could've be worse :P

Starting from a pure Kubuntu I installed:
ubuntu-desktop
xubuntu-desktop
gnome-shell

The LightDM theme remains that of Kubuntu.

[B]Ubuntu
[/B]Receive 'internal error' message after each start. Non-Gnome applications like Firefox and Thunderbird have KDE's color theming. Outside that Unity appears fine. The lack of an application menu is a pro here as you don't notice the 'clutter' from other DEs.

**Xubuntu**
Complete mess. lots of icons on the desktop (mounted drives appear twice). Also KDE-colors in 'neutral' applications. Window borders have gone so Xubuntu-session is unusable. Same error message as Ubuntu session.

**Gnome-Shell**
Quite similar to Unity. Error message is handled nicely by Gnome Shell (less intrusive) and theming is also the same. Ambiance theme for Gnome-applications, KDE colors for other apps.

**Kubuntu** 
Largely unaffected. No error message and the only problem is, as expected, menu clutter.

One other weird thing (or maybe not) is that the splash screen now says "Xubuntu 12.10".

---


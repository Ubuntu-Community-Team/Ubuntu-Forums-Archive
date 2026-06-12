---
title: "Is there any way to turn off the adaptive transparency of the top bar?"
date: 2017-12-05
forum: Desktop Environments
---

### Post by justint15 on 2017-12-05
I am on Ubuntu 17.10. I don't use the Ubuntu Dock (I use Dash to Dock) due to it not being too compatible with my GTK Themes. Now, whenever I use Dash to Dock, my desktop looks weird because the top bar goes fully transparent but Dash to Dock doesn't. Is there any way that I can turn off the Adaptive Transparency? If so, how? If there isn't then I think there should be in the next version of Ubuntu.

---

### Post by again? on 2017-12-06
See if you can override with this extension.
[dynamic-panel-transparency]("https://extensions.gnome.org/extension/1011/dynamic-panel-transparency/")
Allows you to set a custom opacity for max and unmaxed windows.

---

### Post by justint15 on 2017-12-06
I had actually tried that before I posted this thread and it didn't work. I think that Ubuntu just ignores the extensions that try to change the transparency.

---

### Post by mc4man on 2017-12-06
> **justint15 said:**
> I had actually tried that before I posted this thread and it didn't work. I think that Ubuntu just ignores the extensions that try to change the transparency.
Doesn't seem to be the case in 18.04, see screeen
(- fresh install, added dock to dash & the dynamic trans extension, set max & min opacity to highest values..

---

### Post by again? on 2017-12-06
> **justint15 said:**
> I had actually tried that before I posted this thread and it didn't work. I think that Ubuntu just ignores the extensions that try to change the transparency.
May have to logout to see effects.
In the 17.10 Ubuntu session I get a panel shadow gradient with maximized windows.
Using the 17.10 Gnome session with dash-to-dock and dynamic-panel-transparency I don't get the panel shadow gradient.
If you're not using the ubuntu-dock shouldn't be a problem using the Gnome session.
[ATTACH=CONFIG]277757[/ATTACH] [ATTACH=CONFIG]277758[/ATTACH]

**[COLOR="#FF0000"]Edit[/COLOR]**: Seems to work in any session if I enable "Remove excess panel styling" in the dynamic-panel-transparency extension.
[ATTACH=CONFIG]277759[/ATTACH] [ATTACH=CONFIG]277760[/ATTACH]

---

### Post by philhughes on 2017-12-07
The Ubuntu dock has 3 transparency modes:

FIXED: constant transparency
ADAPTIVE: lock state with the top panel
DYNAMIC: dock takes the opaque style only when windows are close to it

You can set with for example:

```
gsettings set org.gnome.shell.extensions.dash-to-dock transparency-mode 'FIXED'

```

or use dconf.

---

### Post by again? on 2017-12-07
> **philhughes said:**
> The Ubuntu dock has 3 transparency modes:

FIXED: constant transparency
ADAPTIVE: lock state with the top panel
DYNAMIC: dock takes the opaque style only when windows are close to it

You can set with for example:

```
gsettings set org.gnome.shell.extensions.dash-to-dock transparency-mode 'FIXED'

```

or use dconf.
First post...
> **justint15 said:**
> I am on Ubuntu 17.10. **I don't use the Ubuntu Dock** (I use Dash to Dock) due to it not being too compatible with my GTK Themes. Now, whenever I use Dash to Dock, my desktop looks weird because the top bar goes fully transparent but Dash to Dock doesn't. Is there any way that I can turn off the Adaptive Transparency? If so, how? If there isn't then I think there should be in the next version of Ubuntu.

---

### Post by philhughes on 2017-12-07
Oops, must read more carefully :). But that setting is also in Dash to Dock I think:
[https://github.com/micheleg/dash-to-dock/commit/87a2357820175b4a1ce57d3822ad5da7a791881a](https://github.com/micheleg/dash-to-dock/commit/87a2357820175b4a1ce57d3822ad5da7a791881a)

---


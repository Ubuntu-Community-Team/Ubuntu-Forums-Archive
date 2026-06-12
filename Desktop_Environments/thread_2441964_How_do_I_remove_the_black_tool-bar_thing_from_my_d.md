---
title: "How do I remove the black tool-bar thing from my desktop?"
date: 2020-04-28
forum: Desktop Environments
---

### Post by j4nd3r53n on 2020-04-28
I upgraded from 18.* to 20.04 today, and I have a black line like a toolbar at the top of my screen, with the text 'Activities' and some other stuff that I don't want or need. Is there a way to remove it?

---

### Post by logix2 on 2020-04-28
The title says Kubuntu... Are you aure you're using KDE Plasma? Because that black bar is specific to Gnome Shell (so Ubuntu with Gnome, not KDE), and you may need it in the future for applications that have a tray icon, because this bar also holds such icons.

If you really qant to remove it: I couldn't find a way to completely remove it, but there's an extension called Dash to Panel that incorporates both Ubuntu Dock (left panel holding application icons) and this black bar (top panel) in a single panel. 

Install that and configure it how you like it: [https://extensions.gnome.org/extension/1160/dash-to-panel/]("https://extensions.gnome.org/extension/1160/dash-to-panel/")

---

### Post by j4nd3r53n on 2020-04-29
Well, I upgraded from kubuntu. What you're saying is that my KDE got replaced by GNOME - that's a bit startling. I'll investigate a bit further and see how I can replace GNOME, which I really deeply dislike. Thank you for pointing me in this direction.

---

### Post by deadflowr on 2020-04-29
> What you're saying is that my KDE got replaced by GNOME 
More likely in addition to rather than outright replaced.
look at what desktop meta-packages are installed
```
dpkg -l *-desktop
```
A good chance you still have kubuntu, but that the login is defaulting to Ubuntu/GNOME.

---

### Post by j4nd3r53n on 2020-04-29
hmm, that is odd:

```
$ dpkg -l *-desktop
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                            Version                       Architecture Description
+++-===============================================-=============================-============-==========================================================
un  djvulibre-desktop                               <none>                        <none>       (no description available)
ii  kubuntu-desktop                                 1.398                         amd64        Kubuntu Plasma Desktop/Netbook system
ii  kubuntu-settings-desktop                        1:20.04.9                     all          Settings and artwork for the Kubuntu (Desktop)
ii  libunity-scopes-json-def-desktop                7.1.4+19.04.20190319-0ubuntu3 all          binding to get places into the launcher - desktop def file
ii  plasma-desktop                                  4:5.18.4.1-0ubuntu1           amd64        Tools and widgets for the desktop
un  plasma-look-and-feel-org-kde-breezedark-desktop <none>                        <none>       (no description available)
ii  slack-desktop                                   4.4.2                         amd64        Slack Desktop
```

But it really seems to be not quite working: screen locking used to, but no longer does, and a number of other things, like virtual desktops. Really strange. Do I need to do a fresh install, simply?

---


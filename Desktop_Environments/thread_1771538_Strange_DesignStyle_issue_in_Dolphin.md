---
title: "Strange Design/Style issue in Dolphin"
date: 2011-05-30
forum: Desktop Environments
---

### Post by hsmcdonald on 2011-05-30
Im new to Ubuntu - loving it!

Using 11.04 and a previous KDE user - im really attached to Dolphin for my day to day file manager.

Installed with no issue, except im finding a strange design issue when I use split pane.

It seems as if in the 'unselected' pane, the background color is not rendering properly.  Stranger still, if you use dolphin as root/sudo, the problem goes away.

Just an annoyance but I wanted to see if anyone knows a solution.  Ive tried re-install and it seems to be happening consistently.

See two attached screenshots.

'root.png' looks fine, loaded using sudo.
'not-ok.png' is the same view, loading dolphin as a normal user.

Maybe there is a permissions issue?

- Steve

---

### Post by Zorael on 2011-05-30
I dearly hope you mean **kdesudo** instead of sudo here. :3

Could this be a clash between GNOME coloring and KDE coloring? You could try renaming **~/.kde/share/config/kdeglobals** and see if Dolphin relies more on GNOME that way. It contains some basic KDE settings like coloring, icons, fonts, emoticons, etc.

Also, when you say you reinstalled, did you keep your home directory? If so, perhaps the consistency of the issue merely stems in that your (possibly borked) color settings get transferred to your new installation. When you run Dolphin as root (real root with kdesudo or via su) it obviously has its own KDE settings under **/root/.kde/**, completely separate from yours.

---


---
title: "New windows appear behind terminal window in 17.10"
date: 2017-10-20
forum: Desktop Environments
---

### Post by waltman on 2017-10-20
I just upgraded to 17.10 this morning, and I'm seeing some unusual behavior in the new window manager. Sometimes when I launch a new application from the command line, the window appears behind the terminal window. I've looked through the settings in Settings, gnome-tweak-tool, and dconf-editor, but I don't see any options to turn this behavior off. I've seen this happen with emacs, gnome-tweak-tool, and dconf-editor.

A related problem is that new apps run from the command line don't get the focus, which they used to with Unity in 17.04 and earlier versions.

Am I missing something, or is this actually a feature in Gnome?

---

### Post by mc4man on 2017-10-21
Not features, more like flaws or deficiencies in Ubuntu's new default window manager (mutter
I'd suggest filing a bug(s) as that's the only purpose of 17.10

---

### Post by waltman on 2017-10-21
As far as I can tell this is the default behavior in Gnome 3. I&#8217;ve seen reports of options to turn it off, but all at least a year old and they don&#8217;t seem to be available in 17.10. I can&#8217;t tell Gnome has removed them from gnome-tweak-tool, or if Ubuntu for whatever reason has decided to not support them.

---

### Post by waltman on 2017-10-26
This continues to be constant source of irritation, and I can't figure out how to change it to the old behavior. Since neither this forum nor the #ubuntu IRC channel has offered much help, I decided to take mc4man's file a bug against mutter: [https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1727868](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1727868)

---

### Post by vanadium on 2017-10-27
As usual in gnome shell, extensions may be needed to fix an undesired design decision. Currently, I use the extension with the unfortunate name "Noannoyance" which takes care of this issue. It immediatelly brings the new Window on the foreground and suspends the "Your window is ready" notification. the other one I used, "Focus my window" currently does not work perfectly anymore on gnome 3.26.

---

### Post by waltman on 2017-10-27
Thanks, that did it! I'd still argue that it's overly complicated to set this up, plus it should be documented in the release notes.

---


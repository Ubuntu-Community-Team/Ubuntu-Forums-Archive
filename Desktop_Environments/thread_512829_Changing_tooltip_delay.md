---
title: "Changing tooltip delay"
date: 2007-07-29
forum: Desktop Environments
---

### Post by dhakir on 2007-07-29
Since I've upgraded from Feisty to Gutsy (always using Gnome), I've noticed my tooltips are taking longer to show up, but I couldn't find any settings to change this delay. I believe there could be some settings (like blocking tooltips, changing their delay, font, etc) in System -> Preferences -> Appearance.

---

### Post by NilsE on 2007-07-29
I have been looking for that myself.  I can't find a delay or sensitivity setting anywhere.  It has to be buried in a config file somewhere.

I noticed the first time you hover over an icon it takes about 4 seconds.  Then after that it is about 2 seconds.  If you go from one icon to the next after it popped up it is almost instantaneous.

---

### Post by drdjr on 2007-08-10
This is VERY annoying, it's happening for all applications, not just the panel.

---

### Post by MikeMLP on 2007-08-13
I'm not sure if my issue is the same, but I've noticed that tooltips will not only be slow in coming up, but also will stay on the screen for a long time, making it difficult to click any button until the tooltip clears on its own or disappears with a click on the tooltip istelf.

Fortunately, this annoying problem seems to have disappeared with todays updates.

Hope everyone else's tooltips are fixed now too.

---

### Post by jim_p on 2007-08-14
You can have them removed by using Advanced GNOME Preferences.
To install it using ```
sudo apt-get install gnome-hideseek
```
Then go to System> Preferences> Hidden Preferences
Click "Panel" From the menu on the left, go to General and untick the option
that says something about tooltips.

---

### Post by cdrom600 on 2007-09-05
> **jim_p said:**
> You can have them removed by using Advanced GNOME Preferences.
To install it using ```
sudo apt-get install gnome-hideseek
```
Then go to System> Preferences> Hidden Preferences
Click "Panel" From the menu on the left, go to General and untick the option
that says something about tooltips.

There's no package called gnome-hideseek than I can find.  What repos have you added?

---

### Post by tribble222 on 2007-09-14
> **cdrom600 said:**
> There's no package called gnome-hideseek than I can find.  What repos have you added?

Here's a deb I found [http://www.getdeb.net/release.php?id=154](http://www.getdeb.net/release.php?id=154)

---

### Post by cdrom600 on 2007-09-14
> **tribble222 said:**
> Here's a deb I found [http://www.getdeb.net/release.php?id=154](http://www.getdeb.net/release.php?id=154)

I installed that, but can't find any preference related to tooltip delay...
Anyone have any other clues?

---


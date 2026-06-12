---
title: "Desktop applets/widgets in Unity?"
date: 2013-01-19
forum: Desktop Environments
---

### Post by IdoSC on 2013-01-19
I absolutely dig many elements in Unity so I can't see myself switching to neither Gnome nor KDE anytime soon. The one thing I miss, though, is the widgets feature that appears in KDE, Windows Vista/7/8, and I'm pretty sure in Gnome too (not 100% sure about that one though).

To avoid any confusion; when I say widgets, or Desktop applets, I talk about those big analog clock apps or a fashioned calender or whatever. So far I've only found a nice app for Postit notes, but even that one looks more like a separate window rather than a desktop applet.

Any ideas for something that might work for me?

---

### Post by Petro Dawg on 2013-01-19
> **IdoSC said:**
> I absolutely dig many elements in Unity so I can't see myself switching to neither Gnome nor KDE anytime soon. The one thing I miss, though, is the widgets feature that appears in KDE, Windows Vista/7/8, and I'm pretty sure in Gnome too (not 100% sure about that one though).

To avoid any confusion; when I say widgets, or Desktop applets, I talk about those big analog clock apps or a fashioned calender or whatever. So far I've only found a nice app for Postit notes, but even that one looks more like a separate window rather than a desktop applet.

Any ideas for something that might work for me?

Conky is great for displaying nearly anything on the desktop, including everything you mentioned in your question and more.  You can take a look at some current screen shots [here]("http://conky.pitstop.free.fr/wiki/index.php5?title=Gallery_2012_%281%29").

It does have a bit of a learning curve to do customization, but its not too difficult if you just want to copy and paste another's code.

You can post [here]("http://ubuntuforums.org/showthread.php?t=281865&page=2150") if you need help getting started.

---

### Post by gifford on 2013-01-19
Screenlets are also available in the Software Center and Synaptic.
Large clocks, calendars, etc.

---

### Post by Cheesehead on 2013-01-19
Most widget and applet use cases have been absorbed into Unity's App Indicators, hiding them among the themed icons along the top bar until needed. Discoverable, and the rest of the screen area should be available for work.

It's not difficult to create a new entry in most existing menus, and not difficult to create a whole new theme menu. Most of the work is done by dbus messages.

If you run across a useful widget for a different desktop environment, feel free to point the developer toward [http://developer.ubuntu.com](http://developer.ubuntu.com) to add it to Unity and get more users.

---


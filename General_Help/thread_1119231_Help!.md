---
title: "Help!"
date: 2009-04-07
forum: General Help
---

### Post by Gomeriffic on 2009-04-07
I have a big problem. Today I installed Gnome-do, hoping to use the docky theme. I got the wrong version, so I wanted to remove the packages and this error came up when I opened Synaptic. I tried terminal, but the same error came up! Now Mozilla won't open either. Any help? Here is the Error:
[IMG]http://fc32.deviantart.com/fs42/i/2009/097/a/c/When_does_that_happen_by_Gomeriffic.png[/IMG]

---

### Post by maheshasolkar on 2009-04-07
The error message suggests you try the following:

```
sudo dpkg --configure -a
```

You should try that out. It may finish the unfinished configuration of the system.

---

### Post by Gomeriffic on 2009-04-07
Now when I start mozilla, a window that says

XML Paring Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 34, Column 1:

[COLOR="Red"]<window id="main-window"
^[/COLOR]

Any help? Mozilla is important for my insanity.

---

### Post by maheshasolkar on 2009-04-07
You might want to try to uninstall firefox package and then install it again. To uninstall it:

```
  sudo apt-get remove --purge firefox
```

And to install it again:

```
  sudo apt-get install firefox
```

Although note that even if this fixes Firefox, it may not fix the root cause of your troubles.

Do you see any broken packages in Synaptic? You can find that if you click on the 'Custom Filters' button in the bottom left corner of the Synaptic Package Manager window, and look for 'Broken' filter. If there are any broken packages/dependencies, you can right-click on them and mark them for removal (or re-installation, if you like).

---

### Post by Gomeriffic on 2009-04-07
I just updated firefox. Seemed to work. And in the future for anyone, I do know how to use terminal.

---


---
title: "Stop Maximus from Maximizing Nautilus?"
date: 2010-02-10
forum: Desktop Environments
---

### Post by skrimpy on 2010-02-10
I like having Maximus working on my netbook for most programs.  There are a few I found it annoying for and I was able to successfully tell Maximus to exclude them (Tomboy and the terminal).

However, I can't figure out what the window name for Nautilus is to tell Maximus to exclude it.  I've tried Nautilus and nautilus (not sure if case matters)... any other suggestions?

---

### Post by null_pointer_us on 2010-06-04
I solved this on my PC using gconf-editor and [a comment]("http://albertsq.blogspot.com/2008/09/maximus-configuration.html?showComment=1224083940000#c8175276465621462352") on [this blog]("http://albertsq.blogspot.com/2008/09/maximus-configuration.html").

Make sure gconf-editor is installed:
```
sudo apt-get install gconf-editor
```

1. Open the window you would like to exclude.

2. Open a terminal and execute this command:
```
xprop | grep WM_CLASS
```

3. The cursor will change; click on the window you wish to exclude.

4. In the terminal, the class name will appear, like so:

```
WM_CLASS(STRING) = "nautilus", "Nautilus"
```

5. Still in the terminal, open gconf-editor:

```
gconf-editor
```

6. Navigate to [COLOR="DarkOrange"]**apps -> maximus**[/COLOR]

7. Double-click on [COLOR="DarkOrange"]**exclude_class**[/COLOR].

8. Add the second string (e.g. Nautilus) without quotes to the list.

This change should take effect immediately, but it might not be applied to windows that are already open.

---


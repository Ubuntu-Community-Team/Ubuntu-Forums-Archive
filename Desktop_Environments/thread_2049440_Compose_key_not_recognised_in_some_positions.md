---
title: "Compose key not recognised in some positions"
date: 2012-08-28
forum: Desktop Environments
---

### Post by Fibonacci on 2012-08-28
Hello.

I've always set my compose key using xmodmap on the shift+<menu key> position, running xmodmap -e 'keycode 135 = Menu Multi_key Menu Multi_key Menu'
I've recently switched to KDE, and noticed that doesn't work. Running xev shows shift+menu is being interpreted as Multi_key, but for some reason it doesn't work at all in Qt apps (it does, however, work everywhere else).
On the other hand, setting it directly on the menu key, e.g. by running xmodmap -e 'keycode 135 = Multi_key', does work on every app.

Is there any way to make it work as shift+menu?

---


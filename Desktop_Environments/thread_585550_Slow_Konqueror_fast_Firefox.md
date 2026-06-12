---
title: "Slow Konqueror fast Firefox"
date: 2007-10-21
forum: Desktop Environments
---

### Post by MrIch on 2007-10-21
Hello I wonder why konqueror needs so much time to access an internet page and firefox is able to load it almost instantly.

I think it might by a dns problem or an missing kde modul (because I have not installed the kubuntu-metapackage).

Any hints would be appreciated...

Btw. what package enables the google search field in konqueror?

---

### Post by Happy_Man on 2007-10-21
Are you on Kubuntu or Ubuntu? If you are using Konqueror on Ubuntu, everything Konq does will be slower than it would be in its native KDE, since the application has to keep loading separate libraries from the shared GTK ones that have been preloaded, but which Firefox can access instantaneously.

I think the search bar may be in the package konq-plugins. Not sure, though.

---

### Post by MrIch on 2007-10-22
I'm using kubuntu, konqueror itself starts very fast... but brwosing is quire slowly.

---

### Post by Happy_Man on 2007-10-22
Hmmm... interesting. Perhaps this is merely a problem with your specs? Konq only loads fast because an instance of it is preloaded every time you log in.

---


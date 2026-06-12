---
title: "Slowness and Multiple icons in Unity Search"
date: 2014-11-01
forum: Desktop Environments
---

### Post by Marzian on 2014-11-01
Hello!

When I search an application in the Unity search bar, I get multiple icons (up to hundreds) of everything, even programs I never used, and the search is extremely slow. This happens for applications, but not for files or folders.

I have Ubuntu 14.10, but the problem persists from the previous edition.

```
 ls ~/.local/share/applications
``` gives a normal output and - as far as I know - I didn't install any third party software creating desktop files

Can you help me? Thanks!

---

### Post by bashiergui on 2014-11-02
The dash is designed to search local and/or remote. Local includes only on your computer and remote includes Ubuntu repositories. This explains it in detail:

[http://developer.ubuntu.com/scopes/overview/](http://developer.ubuntu.com/scopes/overview/)

Files and folders lens searches are local, that's why you don't get a ton of results. When you're searching applications, the lens includes remote and local scopes. You can look into modifying the scope, although I've never done it.

---

### Post by Marzian on 2014-11-03
The online search was already turned off...

---


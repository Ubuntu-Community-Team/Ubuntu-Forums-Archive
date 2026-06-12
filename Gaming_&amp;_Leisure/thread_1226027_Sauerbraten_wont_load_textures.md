---
title: "Sauerbraten wont load textures??"
date: 2009-07-29
forum: Gaming &amp; Leisure
---

### Post by uberlube on 2009-07-29
Has anyone had an issue with this? I can play the game just fine but the textures arent being loaded, which makes it look rather funny i must admit.

---

### Post by noerrorsfound on 2009-07-29
Are you seeing errors about the textures when you load the game?

Make sure you're using the official version from [cubeengine.com]("http://cubeengine.com") or [sauerbraten.org]("http://sauerbraten.org"). Then extract it to your home directory, which is easiest and avoids permission issues. When you start it, don't use *sudo*, just *./sauerbraten_unix* (name might be incorrect since I can't check).

If you got it from GetDeb, make sure you have the **sauerbraten-data** package installed as well. I've never used those packages since they're known to cause issues like this. If you have that package installed and the problem doesn't go away, just get the official version to avoid any permission issues. You could try using *sudo* and see if the game loads the textures then, and if it does then it's an issue with the permissions and a reason you shouldn't use those packages (games don't need root access).

If you got it through Synaptic Package Manager or Add/Remove, you might as well uninstall that version since it's out of date. Old versions have more bugs, are missing features, and are incompatible with servers that are running the latest version. I don't know why that old package even exists; someone should either update it or remove it.

If you've got the real package from the official website (it's a **tar.bz2** archive), and it's extracted in your home directory, but the problem still exists, I guess all you can do is check permissions on the game's data files located in the **packages** directory. For some reason they aren't able to be read by the game, so see that they're owned by you and you have permission to access them.

---


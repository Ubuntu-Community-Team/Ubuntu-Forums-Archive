---
title: "Debug error from wine"
date: 2007-06-18
forum: Gaming &amp; Leisure
---

### Post by cobra351 on 2007-06-18
I am new to Ubuntu and having some success at it.Recently installed Vampire The Masquerade-Bloodlines after reading posts on how to unmount discs.The install itself went well but everytime i try to run  the .exe it  returns an error stating that a debugger is running and to unload it.Any idea on where this debugger is located and how to turn it off.I am not sure if if the error is from wine or from th exe itself.Any help would be appreciated.

---

### Post by Cappy on 2007-06-18
this is a guess but maybe
```

cd /media/cdrom
WINEDEBUG=-all env WINEPREFIX="/home/${USER}/.wine" wine setup.exe
```

If your cdrom isn't located at /media/cdrom you'll need to change that and if the setup isn't setup.exe you'll need to change that.

---

### Post by cogadh on 2007-06-18
You might not want to waste your time, Vampire Bloodlines isn't likely to work with Wine. It will install and you will probably get to the title/launch screen, but the gameplay itself doesn't work. I haven't tried it with Wine 0.9.39 yet, but everyone who has tried with versions all the way up to 0.9.35 has failed to run it. See Wine's AppDB entry: [http://appdb.winehq.org/appview.php?iVersionId=4949](http://appdb.winehq.org/appview.php?iVersionId=4949)

---


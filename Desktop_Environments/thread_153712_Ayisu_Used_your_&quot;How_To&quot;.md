---
title: "Ayisu: Used your &quot;How To&quot;"
date: 2006-04-01
forum: Desktop Environments
---

### Post by phil66 on 2006-04-01
install new firefox-1.5.0.1. 
The mv command would not run due to needing the second command to be a directory.

Continued using console after unpacking Firefox-1.5.01 and entered firefox/firefox and program opened.
Changed launcher accordingly and install orange icon in panel
Imported bookmarks,extensions,theme's all sucessful.

Now the big question how should I remove Firefox-1.07

From synpatic

With rm -r from console

With apt-get remove

Thanks for the help
Ray

---

### Post by dcstar on 2006-04-01
[QUOTE=phil66]install new firefox-1.5.0.1.
.......
Now the big question how should I remove Firefox-1.07

From synpatic

With rm -r from console

With apt-get remove

Thanks for the help
Ray[/QUOTE]
You **DO NOT** remove FF 1.0.7 from a Breezy installation, it is intimately tied into the system.

Just use FF 1.5 and don't worry about the old version.

---

### Post by aysiu on 2006-04-01
[QUOTE=phil66]install new firefox-1.5.0.1. 
The mv command would not run due to needing the second command to be a directory.[/QUOTE] Huh? That doesn't make sense. You're "moving" a file to another file. Can you post the exact command you tried to type and what the exact output was? It's *supposed* to be ```
mv installnewfirefox.sh.txt installnewfirefox.sh
```

And, as dcstar said, you shouldn't remove Firefox 1.0.7.
It is integrally tied to Ubuntu.
It isn't integrally tied to Kubuntu, but if you want your plugins working properly, you should keep 1.0.7 installed still.

---

### Post by phil66 on 2006-04-02
Aysiu

Sorry for the miss spelling!!!

The code was word for word as per your quote.
Error returned was "second mv command has to be a directory."

Double checked the command at Ubuntu and psychopath and it had been entered correctly?

As your batch file never ran is it safe to remove from the desktop?

Do you know if on future Firefox upgrades we will be able to install over existing Firefox (such as windows) by indicating where to install.
Or will we end up with numerous apps on our harddrives.

Thanks
Ray

---


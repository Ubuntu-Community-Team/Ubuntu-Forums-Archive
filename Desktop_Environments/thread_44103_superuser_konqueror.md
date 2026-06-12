---
title: "superuser konqueror"
date: 2005-06-24
forum: Desktop Environments
---

### Post by coolclassic on 2005-06-24
On suse I was able to use konqueror in superuser mode is this available in ubuntu, I don't like the idea of changing permissions every time I move a file into usr.........

---

### Post by SGC on 2005-06-24
**Use the following command:**
```
kdesu konqueror
```

**To make a shortcut for this command, open  your text editor (kwrite or kate) and paste the following:**

```

[Desktop Entry]
Comment=
Comment[en_US]=
Encoding=UTF-8
Exec=kdesu konqueror
GenericName=
GenericName[en_US]=
Icon=konqueror
MimeType=
Name=Konqueror Super user mode
Name[en_US]=Konqueror Super user mode
Path=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DCOP-ServiceType=
X-KDE-SubstituteUID=false
X-KDE-Username=

```

**Save the file as konqueror super user mode.desktop or any other name with .desktop extension**

---

### Post by coolclassic on 2005-06-24
Just what I needed Thanks  :-P  :-P  :-P

---


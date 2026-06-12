---
title: "Running app icon in 18.04 dock is blank"
date: 2018-09-18
forum: Desktop Environments
---

### Post by jimfinnis on 2018-09-18
Hi,
Long-time Ubuntu user, just moved over to Bionic. I run a rather elderly editor, MicroEmacs with some custom stuff (it's fine, so does Linus!)
I can create a .desktop for it, but that just creates a launcher. I typically invoke it from the command line. When I do this (and also with the launcher) the running app just shows as blank in the dock, like this:
[ATTACH=CONFIG]281116[/ATTACH]

It's really annoying, particularly as it's creating a new slot for every instance, cluttering up the dock. Is there any way to tell the dock which icon to show for a running, simple app? 

Thanks,
Jim

---

### Post by deadflowr on 2018-09-18
What does the .desktop look like?

---

### Post by jimfinnis on 2018-09-18
It's pretty minimal.

```

[Desktop Entry]
Comment=Microemacs
Name=Microemacs
Terminal=false
Exec=/home/white/bin/me
Type=Application
Icon=gedit.png

```

So I'm repurposing the gedit icon :)  The file is in my home .local/share/applications folder. Am I missing something?

---

### Post by deadflowr on 2018-09-18
drop the .png in the icon name.

---

### Post by jimfinnis on 2018-09-18
No joy, I'm afraid. I know it's possible because other third-party apps do it (Mendeley, for one). Hm.

---


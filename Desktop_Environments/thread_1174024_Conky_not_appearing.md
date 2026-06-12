---
title: "Conky not appearing"
date: 2009-05-30
forum: Desktop Environments
---

### Post by Iteria on 2009-05-30
I'm running Xubuntu 9.04. I installed Dropbox and after the installation was complete, conky stopped rendering on my desktop for some reason. I check the system monitor and it tells that conky is running and if I run the command for conky again the system monitor show two instances running. it just doesn't appear on my desktop.

I don't know that Dropbox is the cause, but conky did disappear right after the install completed. Has anyone else had this issue? Did you find a fix?

---

### Post by m_duck on 2009-05-30
Have you installed Nautilus to get the dropbox integration? If so it's probably Nautilus taking over the desktop and drawing over XFCE's desktop and conky... Perhaps anyway...

What happens if you run the following from terminal or run dialog (stops nautilus):
```
killall nautilus
```

---

### Post by Iteria on 2009-05-30
It worked! Thank you so much!

---

### Post by Iteria on 2009-05-30
Next Question: Is there anyway to make it stop doing that? Every time Dropbox runs Nautilus overtakes Xfdesktop.

---

### Post by m_duck on 2009-05-30
Yeah, kind of...

When you open Nautilus you need to run it with```
nautilus --no-desktop
```However, when I was trying to run that on XFCE it kept respawning anyway and completely ignoring the --no-desktop bit. I'm not sure if there is a preference in Nautilus somewhere to never draw the desktop?

---


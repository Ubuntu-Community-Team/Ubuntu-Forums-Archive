---
title: "No Icons on Desktop"
date: 2009-11-10
forum: Desktop Environments
---

### Post by nexoncore on 2009-11-10
This isnt a bug, its a request.

I have a drive perminently mounted by the NTFS Config Tool. But I came to reaslise that although I want permiment access at all times, I dont want the icon in my face.

How would I go about disabling icons on the desktop?

---

### Post by Simian Man on 2009-11-10
Fire up gconf-editor.  Look under Apps->Nautilus->Desktop and uncheck the "volumes visible" checkbox.

I am on Xfce now, so that is from memory, hopefully it's close enough :).

---

### Post by nexoncore on 2009-11-10
Nah its not work, changed the setting and nothings happened even after restart. But thanks for letting me know about this feature.

---

### Post by blazemore on 2009-11-10
Icons only appear if it's mounted under /media
Mount it somewhere else, like /windows and all will be well

---


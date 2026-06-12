---
title: "Downloaded files are not showing up"
date: 2009-02-28
forum: General Help
---

### Post by wcleeke on 2009-02-28
Usually when I download a file it shows up on the desktop, but of late they arn't showing up after download. At first I was thinking they were being hidden so I made it to show all hidden files and they still didn't show up. Any help?

---

### Post by NoReflex on 2009-02-28
I suppose you mean files downloaded by Firefox. Maybe they are downloaded to another location (check Firefox Preferences) - or right click on a link to some file and choose Save link as to see where it wants to save the file. Maybe Firefox can't save to the specified location (check permissions).
If this isn't about Firefox try using find to locate the file.
It's also a good ideea to check your home dir.

Best wishes,
NoReflex

---

### Post by wcleeke on 2009-02-28
> **NoReflex said:**
> I suppose you mean files downloaded by Firefox. Maybe they are downloaded to another location (check Firefox Preferences) - or right click on a link to some file and choose Save link as to see where it wants to save the file. Maybe Firefox can't save to the specified location (check permissions).
If this isn't about Firefox try using find to locate the file.
It's also a good ideea to check your home dir.

Best wishes,
NoReflex


No it isn't firefox, it seems that are being downloaded to the desktop, but just not showing up on the desktop. I'm not sure how to make them show up.

---

### Post by cariboo on 2009-02-28
Do the files show up if you go to Places-->Home Folder-->Desktop?

Jim

---

### Post by wcleeke on 2009-02-28
Nope

---

### Post by oldos2er on 2009-02-28
What program are you using to download?

---

### Post by Vaphell on 2009-02-28
how are these files downloaded?

maybe if you know the name try to run terminal and enter
locate <name_to_find>

if they are indeed on desktop it would be in results

---

### Post by taurus on 2009-02-28
Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```
Maybe you should have a look in gconf-editor.

---

### Post by wcleeke on 2009-02-28
I restarted the computer and now there showing up.

---


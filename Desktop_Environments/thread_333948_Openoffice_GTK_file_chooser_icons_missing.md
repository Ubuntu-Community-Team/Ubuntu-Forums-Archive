---
title: "Openoffice GTK file chooser icons missing"
date: 2007-01-08
forum: Desktop Environments
---

### Post by pwest on 2007-01-08
The proper icons in the file chooser for Openoffice aren't shown when using the chooser. (see attached)

I am using the standard openoffice.org on dapper amd86 edubuntu. The openoffice.org-gnome and -gtk are installed. 

I have tried reinstalling the openoffice packages, but no change.
The cancel icons are shown whether you are viewing the extended or compact file browser and also in the open and save as dialogs. 

BTW, all users are having the same problem. 

Has anyone got an idea what could be done?

---

### Post by tseliot on 2007-01-08
try this:
```
sudo aptitude install gnome-icon-theme
```

---

### Post by pwest on 2007-01-08
I tried reinstalling both that and gnome-icon-theme-gartoon and that didn't change anything.
I have tried switching to another icon theme than gartoon and that fixes it, so the problem must somehow involve the gartoon icon theme. I will try logging in using US English rather than German and see if that helps.

---

### Post by pwest on 2007-01-08
I have logged in using US English and no improvement. Gartoon icons still missing in ooo file chooser.

---

### Post by pwest on 2007-01-08
I have discovered the same fault on the gtk dialogs of all the 32bit programs I have installed.

Namely firefox32 and Adobe Reader have the gartoon icons missing.

---


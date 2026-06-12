---
title: "Firefox - always opening save dialog"
date: 2007-05-07
forum: Desktop Environments
---

### Post by theh0g on 2007-05-07
Until recently, everything worked nice. But now, when I click on .torrent file, I ALWAYS get a Save As dialog, there is no way to make it open with Azureus (or any other program). How do I fix that in Firefox?

---

### Post by m0eman on 2007-05-07
What I do is select open with -> other and find the azureus launcher, and then I check Do this automatically. That doesn't work for you anymore?

---

### Post by theh0g on 2007-05-07
No, I did that few times and it ignored it, although Azureus was selected and "open" wqas checked. Now I automaticaly get save dialog for .torrent files. It just changed one day for no obvious reason.

---

### Post by m0eman on 2007-05-07
I remember having this problem before but I installed Feisty so it went away. Maybe under preferences you have 'always ask me where to save files' checked?

---

### Post by metalheart on 2007-05-07
In Firefox go to Edit -> Preferences -> Content -> Manage. Maybe you can delete the wrong association.

---

### Post by m0eman on 2007-05-07
The content manager doesn't work on the firefox in Ubuntu's repositories. If all else fails maybe install the firefox from the Mozilla repositories.

---

### Post by mythik on 2007-05-07
> **m0eman said:**
> The content manager doesn't work on the firefox in Ubuntu's repositories. If all else fails maybe install the firefox from the Mozilla repositories.

Would that explain why EVERY single mpg is played instead of asking me what I want to do with it?  I goto edit -> preferences -> content -> manage (or whatever the correct menu choices are) and no movie files are actually stored there.

It's very aggravating to me.

---

### Post by theh0g on 2007-05-07
Figured it out, somehow. I edited mimeTypes.rdf file in my firefox profile and set NC:alwaysAsk to TRUE. Now it asks if I want it open or saved. Really lame you can't set this in application.

---

### Post by metalheart on 2007-05-07
> **theh0g said:**
> Really lame you can't set this in application.
You actually can by entering url about:config but this is also not very intuitive.

---

### Post by theh0g on 2007-05-07
> **metalheart said:**
> You actually can by entering url about:config but this is also not very intuitive.
Well you can set up things for Firefox, but you can't set this, I've tried it.

---

### Post by mythik on 2007-05-07
> **theh0g said:**
> Well you can set up things for Firefox, but you can't set this, I've tried it.

can you paste what your rfp file contains?  mine seems very very blank.

---

### Post by m0eman on 2007-05-08
Mine contains every file extension type I've ever downloaded (.rar, .iso, .zip ...), it has to be opened in a text editing program like gedit. Thats weird if yours is blank.

---


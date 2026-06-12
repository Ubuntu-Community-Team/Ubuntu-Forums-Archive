---
title: "Removing menu items from the right-click menu"
date: 2008-05-18
forum: Desktop Environments
---

### Post by bgschley on 2008-05-18
Hi,

I'm running ubuntu 8.04 on my inspiron 8600. All is working really well. I have had a few problems with CrossOver office 6.0.1 though.

I have tried installing CX office with all of the available methods but to no avail - it fails and does not create the necessary icons in the applications menu. Thus, I have uninstalled it all. However, it did add right-click menu items for all MSOffice document types but did not remove these when it was uninstalled. Hence, I have menu options that do not point to the correct applications.

To try and get round things, I have installed wine and then MSOffice which went off without a hitch.

What I would like to do is to get the right-click menu items opening the documents with the correct application or at least remove them so that they open with openoffice.

Does anyone know how I can do this?

Cheers

George

---

### Post by NormR2 on 2008-05-18
Good luck getting an answer to this one. I've been asking how to ADD rightclick menu items and haven't gotten any responses and how to tailor nautilus in general.
 I'll keep listening to this thread to see what you find out.

---

### Post by bgschley on 2008-05-19
I'm going to post this on the CX website and see if they have any thoughts... CX Office was able to put it into the menu so they should be able to get rid of it.

I'll post again as soon as I get a response.

George

---

### Post by NormR2 on 2008-05-31
I found files that listed apps and the filetypes that they can process. I wanted to remove an app from a RC menu for a filetype. I remove the filetype for that app from its file and its entry disappeared from the menu.
I think it was /usr/share/applications/ <files>.desktop
In my case the app was geany and the file I changed was geany.desktop

Good luck.

---


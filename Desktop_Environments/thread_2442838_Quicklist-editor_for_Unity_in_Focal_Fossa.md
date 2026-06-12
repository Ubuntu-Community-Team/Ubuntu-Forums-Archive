---
title: "Quicklist-editor for Unity in Focal Fossa?"
date: 2020-05-08
forum: Desktop Environments
---

### Post by modig-lars on 2020-05-08
Hi,

Anyone know about a ppa for a quicklist editor in Focal Fossa, or a a gedit guide for dummies on how to do it text based?

Thanks!!

/Lars

---

### Post by ajgreeny on 2020-05-08
What exactly do you want? I had to search for **quicklist** to figure out what it is and there seem to be several things using that name

---

### Post by modig-lars on 2020-05-08
Sorry to be unclear, quicklist for unity launcher...

---

### Post by deadflowr on 2020-05-08
quicklists are generally .desktop Actions.
look at an app's .desktop file using gedit.
(default app launcher desktop files are in /usr/share/applications)

You'll see a line marked like 
```
Actions=something;something-also;
```
and a the bottom of the file you'll see the action parameter sections for each like
```
[Desktop Action something]
Name=something
Exec=foo

[Desktop Action something-also]
Name=something-also
Exec=foobar
```
 
Best to simply open the desktop file from the /usr/share/applications directory and use save as in gedit to save it to your local home directory inside
~/.local/share/applications. (it's a hidden directory by default so in the save as dialog box you can select show hidden folder/files to have it show.)

The benefit of saving to your home is editing it will not require root.
Any update to application will not overwrite your edits. (Files in Home are generally unaffected by package management, unlike system files)
If by chance you mess up in the edit, you still have the system default untouched in the /usr/share/applications directory.
(Which means if you break all you need to do is move the broken one to trash. And it will default back to the system version)

---

### Post by modig-lars on 2020-05-14
OK thanks, trying it now... Late reply but I missed to turn on notification on replies as it seams... Will let you know how I succeed...

---

### Post by slickymaster on 2020-05-14
*Thread moved to **Desktop Environments**.*

---


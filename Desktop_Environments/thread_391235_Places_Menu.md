---
title: "Places Menu"
date: 2007-03-22
forum: Desktop Environments
---

### Post by Mark Erbaugh on 2007-03-22
Where are the locations in the Places menu (both in the main panel menu and in the sidebar in a Nautilis window) maintained?  I have noticed that if I add a bookmark in Nautilus, that the bookmark shows us 'below the line' in the sidebar places menu and it is added the main panel places menu.

How do I add a place so that it is above the line?

I have installed Dapper on a couple of different computers. On one of them my 'Documents' folder automatically showed up in the places menu, on the other it didn't.

---

### Post by mcduck on 2007-03-23
> **Mark Erbaugh said:**
> Where are the locations in the Places menu (both in the main panel menu and in the sidebar in a Nautilis window) maintained?  I have noticed that if I add a bookmark in Nautilus, that the bookmark shows us 'below the line' in the sidebar places menu and it is added the main panel places menu.

How do I add a place so that it is above the line?

I have installed Dapper on a couple of different computers. On one of them my 'Documents' folder automatically showed up in the places menu, on the other it didn't.

You can't. They appear where they are made to appear. And for your Documents directory, is it named exactly 'Documents' on both computers? Linux is case sensitive and the name is predefined, so for example 'documents' or 'Docs' will not work.

---

### Post by Mark Erbaugh on 2007-03-23
> **mcduck said:**
> You can't. They appear where they are made to appear. And for your Documents directory, is it named exactly 'Documents' on both computers? Linux is case sensitive and the name is predefined, so for example 'documents' or 'Docs' will not work.

Thank you. The folder name on the one computer was documents. Changing it to Documents added it to the places menu.

A followup question. Are there any other 'special' folder names that will appear 'above the line'?

Also, is the behaviour hard-coded, or is it controlled by a script file?  If so, which one?

---

### Post by mcduck on 2007-03-24
> **Mark Erbaugh said:**
> Thank you. The folder name on the one computer was documents. Changing it to Documents added it to the places menu.

A followup question. Are there any other 'special' folder names that will appear 'above the line'?

Also, is the behaviour hard-coded, or is it controlled by a script file?  If so, which one?

As far as I know Documents is the only one, and I believe it's hard-coded.

---

### Post by mgmiller on 2007-03-24
The only other one I know of is the "pictures" directory which must be lower case to be seen by the gnome screen saver if you want to use these images.  It was Pictures until recently, when it was changed to pictures.

---


---
title: "Could not add application to the application database"
date: 2006-08-12
forum: Desktop Environments
---

### Post by stuart_75 on 2006-08-12
Hi all,

Ive just got wine working, so I can have MS office running. Now my problem is when I double click on a .doc openoffice opens and not MS word. Ive tried linking .doc files to the word shortcut ive created but i get the message "Could not add application to the application database"

Any ideas??

Thanks!!!!!!!

---

### Post by jordilin on 2006-08-12
> **stuart_75 said:**
> Now my problem is when I double click on a .doc openoffice opens and not MS word.

If I'm not wrong m$ office can't open openoffice docs. On the other hand OpenOffice can open anything :D

---

### Post by stuart_75 on 2006-08-12
> **jordilin said:**
> If I'm not wrong m$ office can't open openoffice docs. On the other hand OpenOffice can open anything :D

The docs im trying to open are MS word docs. I can open them if I open word first then select open, etc, etc. But not by just double clicking the doc.

---

### Post by jordilin on 2006-08-12
> **stuart_75 said:**
> The docs im trying to open are MS word docs. I can open them if I open word first then select open, etc, etc. But not by just double clicking the doc.

Go to the .doc document, right-click->properties->Open with tab, and you can choose the app.

---

### Post by stuart_75 on 2006-08-12
> **jordilin said:**
> Go to the .doc document, right-click->properties->Open with tab, and you can choose the app.

Thats why ive tried and hence the error "Could not add application to the application database"

---

### Post by jordilin on 2006-08-12
> **stuart_75 said:**
> Thats why ive tried and hence the error "Could not add application to the application database"

I understand, as Office is a foreign app for Linux, you can't add it. Perhaps it can be added through the gconf-editor. I'm not sure though.

---

### Post by Hovang on 2006-08-13
Try this in your home dir (change <your user> to your login name):

sudo chown <your user> -R .local
sudo chgrp <your user> -R .local

---

### Post by snovak on 2007-12-18
THANK YOU!!  Works great now!

---


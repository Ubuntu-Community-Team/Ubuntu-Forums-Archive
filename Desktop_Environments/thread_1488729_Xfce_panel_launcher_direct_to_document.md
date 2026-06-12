---
title: "Xfce panel launcher direct to document"
date: 2010-05-20
forum: Desktop Environments
---

### Post by elmosim2 on 2010-05-20
I'm running xfce and I'm trying to create a launcher on the panel that will open a document directly.  Is there any way to do this?

Do I just need the way to open that document from a terminal?

---

### Post by elmosim2 on 2010-05-20
Nevermind, I was trying to do this using abiword, instead I'll use open office.

openoffice /home/user/document.doc

---

### Post by 3Miro on 2010-05-20
If you put this on the Command line in the create launcher wizard, it should work. Anything that works in a terminal should work in the Launcher.

openoffice /home/user/document.doc

---

### Post by SlidingHorn on 2010-05-20
> **elmosim2 said:**
> Nevermind, I was trying to do this using abiword, instead I'll use open office.

openoffice /home/user/document.doc

If you're looking just to quick open/edit without all the extras that come with OpenOffice, you can use a program like gedit

```
gedit /home/user/document.doc
```

or mousepad (first line is to install)

```
sudo apt-get install mousepad

**then, in the wizard, use the below as your command**

mousepad /home/user/document.doc
```

---


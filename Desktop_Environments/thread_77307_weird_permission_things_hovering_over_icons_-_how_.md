---
title: "weird permission things hovering over icons - how to remove?"
date: 2005-10-16
forum: Desktop Environments
---

### Post by bionnaki on 2005-10-16
see picture:

[IMG]http://www.psidonia.net/host/warning.png[/IMG]

they seem to be icons that hover over icons that display permission settings. how can I disable this?

---

### Post by bionnaki on 2005-10-17
*bump

---

### Post by Dr. Nick on 2005-10-17
Edit - Just re-read your title and I guess you already knew that, You can change ownership by launching nautilus as root or opening a terminal and using chmod (Dont know what parameters to use on chmod though)

Those are their since you dont "own" them I believe, right click to properties and see if your username is the owner under "Permissions" tab

---

### Post by bionnaki on 2005-10-18
so, everyone has these?

I guess I thought I did something wrong or chose some weird setting to enable these...oh well, if it's normal, then I dont mind so much.

---

### Post by migueljacq on 2005-10-18
[QUOTE=bionnaki]so, everyone has these?

I guess I thought I did something wrong or chose some weird setting to enable these...oh well, if it's normal, then I dont mind so much.[/QUOTE]

If you're the only user on your machine then it's just likely that root owns those files, which is normal. If you think you should own them, use chown/chmod. Alternatively if you ever need to edit them, you can just use sudo gedit

---

### Post by bionnaki on 2005-10-18
gotcha thanks.

---


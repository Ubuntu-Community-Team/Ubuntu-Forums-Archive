---
title: "double to open executable text file"
date: 2013-07-08
forum: Desktop Environments
---

### Post by jworr on 2013-07-08
I recently switched to xubuntu and I have one simple issue I can't resolve.  How do I change the default action to open an executable text file instead of executing it in the file manager(thunar)?

---

### Post by ohnonot on 2013-07-10
you can't. if it's executable, double-click will execute it. you can always right-click -> open with. if going down a submenu is too much, you can assign a thunar custom action, e.g. "Edit", so you only have to right-click -> Edit (or whatever you call the action that opens the file in your favorite editor).

---

### Post by Frogs Hair on 2013-07-10
In Thunar under  Edit > Preferences > Advanced you can set to ask each time which displays a dialog to view, run, and so on.

---

### Post by jworr on 2013-07-10
Under Edit > Preferences > Advanced, I only see options for how file permissions are propagated and volume management.

---

### Post by Frogs Hair on 2013-07-10
Excuse me ,  you are correct I get no run dialog in Thunar 1.6.3 . I use the XFCE 4.12 PPA .

[http://askubuntu.com/questions/313547/xfce4-run-program-dialogue-box-does-not-appear-when-double-clicking-script](http://askubuntu.com/questions/313547/xfce4-run-program-dialogue-box-does-not-appear-when-double-clicking-script)

---

### Post by ana551 on 2013-07-11
method of execution is givern here    [http://askubuntu.com/questions/122428/how-to-run-sh-file](http://askubuntu.com/questions/122428/how-to-run-sh-file)

---

### Post by ohnonot on 2013-07-12
dear original poster, i think the last post does not apply to your question.
frogshair already admitted to being wrong, so it comes down to what i said originally.

this is a difference between thunar and nautilus.

i always found the nautilus way confusing (iirc pcmanfm has it too), but if you're used to it...
[for me the best solution would be if double click always opens the file for editing, and i'd have to right click to execute it.]

if you uncheck the executable permission bit on your text file, double click opens it in an editor (or whatever is associated to this kind of file).

---


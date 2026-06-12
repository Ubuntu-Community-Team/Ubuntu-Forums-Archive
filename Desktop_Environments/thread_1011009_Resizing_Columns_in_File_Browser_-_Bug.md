---
title: "Resizing Columns in File Browser - Bug?"
date: 2008-12-14
forum: Desktop Environments
---

### Post by selahlynch on 2008-12-14
The resizing of columns in my file browser acts strangely.  I'm trying to resize column 1 and column 2.  I'm doing it in a typical way, by dragging the right hand side of the column header.  

If I try to resize Column 1, I can't make it any smaller, I can only make it larger.  If I try to resize column 2, it resizes column 2 by moving the left side of column 2, rather than the right, thereby affecting column 1.  So if I make column 2 very large, it will result in column 1 being very small.

Have you experienced this bug?

How can I fix this?  How can I help it be fixed?:confused:
The file browser is such an important thing!

---

### Post by lian1238 on 2008-12-14
Is your file browser Nautilus? Making sure..

---

### Post by logos34 on 2008-12-14
which reminds me of my pet peeve:

nautilus won't save adjusted column layout...or is there a way?

---

### Post by lian1238 on 2008-12-14
> **logos34 said:**
> which reminds me of my pet peeve:

nautilus won't save adjusted column layout...or is there a way?
You can go to Edit->Preferences. Go to List Columns. You can drag and change the order to fit your prefered layout.

---

### Post by logos34 on 2008-12-14
> **lian1238 said:**
> You can go to Edit->Preferences. Go to List Columns. You can drag and change the order to fit your prefered layout.

i should have been clearer--i meant the column widths (i.e. specifically the title width big enough).  I have the columns sorted in order

---

### Post by selahlynch on 2008-12-14
My file browser is Nautilus 2.22.5.1

So has anyone experienced this? 
(the first column wont readjust, and when you adjust the second column it does strange things to the first column)

do you know what I'm talking about?

---

### Post by selahlynch on 2008-12-15
I had better luck researching this column resizing issue when including "Nautilus" in my search rather than "file browser".

What (i think) I understand:
-It is a reported bug that stems from a bug in the gtk+ package
-It is fixed in Ubuntu 8.10 Intrepid

Links to reported bugs:
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/25940](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/25940)
[http://bugzilla.gnome.org/show_bug.cgi?id=316087](http://bugzilla.gnome.org/show_bug.cgi?id=316087)

Now the question for me is, can I fix this in a way that does not involve installing Ubuntu 8.10??

---


---
title: "Kiba-dock problems with feisty"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by Arlanthir on 2007-04-20
[I]I installed the 1.2 .deb package of kiba-dock (the same I used before in edgy) and everything is working except the icon-editor.. When I call it, it gives an output that ends with:

ImportError: No module named SimpleGladeApp

From what I've searched, I have libglade or similar installed, so, it should work.. What's happening?[/I]

**Solution:**
Create a symbolic link to python 2.5 by typing (in the terminal):
> sudo ln -s /usr/lib/python2.4/site-packages/SimpleGladeApp.py /usr/lib/python2.5/site-packages/SimpleGladeApp.py

---

### Post by pt123 on 2007-04-20
where do you get the deb file for edgy?

---

### Post by Arlanthir on 2007-04-20
In some other thread here =/
It's a problem of packages anyway, but I already have python-glade2 and nothing..

---

### Post by antoniorc on 2007-04-22
The script SimpleGladeApp.py is included in package kiba-dock.deb but in dir for python 2.4. Solution is create a symbolic link to python 2.5:

sudo ln -s /usr/lib/python2.4/site-packages/SimpleGladeApp.py /usr/lib/python2.5/site-packages/SimpleGladeApp.py

---

### Post by Arlanthir on 2007-04-22
Worked perfectly, thank you very much!

---

### Post by LaaZ on 2008-03-10
Just want to say thanks. I had the same issue here (7.10 Gutsy) and now everything works fine! :)
Edit: PS: Im using the same .deb package.

---


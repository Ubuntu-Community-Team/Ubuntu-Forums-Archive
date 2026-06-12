---
title: "Opening files in SciTE from Nautilus"
date: 2005-11-21
forum: Desktop Environments
---

### Post by 12quality on 2005-11-21
I really like SciTE and use it to edit ruby, html, php, python, latex, etc. 

My problem occurs when I try to open a file from nautilus.  If I try to open a file in my home directory ("/home/seth/") named "myfile.html", it tries to open a file called "/home/seth/file:/home/seth/myfile.html", which just results in a blank document.  I know it's trying to open the name listed above because that's what appears above the editing window.

Typing "scite myfile.html" at the command prompt works fine and so does a File--> Open...from SciTE's menu. 

Any ideas about what's going on and what I can do to fix it?

---

### Post by Jonathan Wiebe on 2005-12-20
I believe that there is a problem in the SciTE .desktop file.  (Although I am not an expert in this area and I'm not sure who to report the bug to.)

Anyways, here is how I got it to work:

Once SciTE is appearing in your Gnome "Open With..." context menu then look for a scite .desktop file in the following folder:

~/.local/share/applications/

In my case the file was named scite-usercustom.desktop

Edit this file and find a line which reads:

Exec=scite %U

Change it to:

Exec=scite -open:

Save the file then kill all running instances of nautilus using the command:

killall nautilus

Now opening files from nautilus should work (at least it did for me).

Let me know how you make out.

Regards,

Jonathan B. Wiebe

---

### Post by Jonathan Wiebe on 2005-12-21
Greetings,

One quick addition.  I have found that appending "-open:" to the Exec line is not neccessary.

The following works just fine:

Exec=scite

Regards,

Jonathan B. Wiebe

---

### Post by 12quality on 2006-01-12
Leaving "Exec=scite" worked.

Thank you two so much.  I can finally use Scite as my default editor.

---


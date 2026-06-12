---
title: "How can I edit the 'Places' dropdown?"
date: 2005-08-28
forum: Desktop Environments
---

### Post by linuxNewb on 2005-08-28
I want to make Places>Computer open with gksudo, but I can't find the .desktop file. What file do I need to edit? Thanks in advance.

---

### Post by duminas on 2005-08-28
[QUOTE=linuxNewb]I want to make Places>Computer open with gksudo, but I can't find the .desktop file. What file do I need to edit? Thanks in advance.[/QUOTE]
That cannot be edited, as far as I'm aware.
You'd have to add a new .desktop file to do what you want.

---

### Post by linuxNewb on 2005-08-28
Actually I found /usr/share/applications/nautilus-comuter.desktop and I changed

Exec=nautilus computer:

to

Exec=gksudo nautilus computer:

but it causes an error message when I execute it... "Cannot find /home/user/computer...". What is the correct way to do it?

---

### Post by jlacroix on 2005-08-28
Believe it or not the easiest way is to use Firefox. Find a file to download, doesn't matter what it is. Do "Save Link As" in the dialogue that comes up, choose "browse for other folders". Then, highlight the folder you want to add, then click on the button that says "add". It will then appear in Places. Don't ask me why it just does.  :-#

---


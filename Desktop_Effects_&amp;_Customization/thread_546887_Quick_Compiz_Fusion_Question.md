---
title: "Quick Compiz Fusion Question"
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by Drillbit on 2007-09-09
OK, I have searched a lot of threads but can't seem to find an answer to this quick question : how do I autostart this command?

compiz --replace --indirect-rendering

My Compiz works great when I enter this (it kills the black screens) but I have to enter it at every start up and hide the terminal that it's in on Desktop 4.

Thank you in advance.

---

### Post by n3tfury on 2007-09-09
go to System>Preferences>Session. Then click on the New button on the right hand side of the menu. Add compiz --replace --indirect-rendering to your startup.

---

### Post by Drillbit on 2007-09-09
> **n3tfury said:**
> go to System>Preferences>Session. Then click on the New button on the right hand side of the menu. Add compiz --replace --indirect-rendering to your startup.

Thank you for your response.

I have done that but I still have black screen trouble until I put that command directly into the terminal after booting up.

Why might that be?

---

### Post by Drillbit on 2007-09-10
Does anyone have any ideas?

---

### Post by dondad on 2007-09-10
> **Drillbit said:**
> OK, I have searched a lot of threads but can't seem to find an answer to this quick question : how do I autostart this command?

compiz --replace --indirect-rendering

My Compiz works great when I enter this (it kills the black screens) but I have to enter it at every start up and hide the terminal that it's in on Desktop 4.

Thank you in advance.

I don't know about the autostart, but you can do it without hiding the terminal by using the run dialog (alt-f2) to run the command instead of the terminal.

---

### Post by Drillbit on 2007-09-10
> **dondad said:**
> I don't know about the autostart, but you can do it without hiding the terminal by using the run dialog (alt-f2) to run the command instead of the terminal.

Thank you.

I've also noticed that when I check the "current session" that my replace --compiz and my replce --emerald are there. My rendering command isn't.

I'm stumped.

---

### Post by Forlong on 2007-09-10
Create a startscript:
```
gedit start-compiz
```
Paste that into the Texteditor:
```
#!/bin/bash
compiz --replace --indirect-rendering &
sleep 5
emerald --replace
```
Click *Save*.
Make the file executable:
```
chmod +x start-compiz
```
Go to *System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs*
Click on *New* and look for the file *start-compiz* in your home folder.

---


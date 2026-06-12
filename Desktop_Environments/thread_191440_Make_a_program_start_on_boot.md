---
title: "Make a program start on boot???"
date: 2006-06-07
forum: Desktop Environments
---

### Post by shane2peru on 2006-06-07
Ok, I switched over to KDE, and now I don't know how to make a program start on boot.  I know this should be simple, and I'm probably overlooking it.  Any ideas??  Thanks.  (it was simple in Gnome.)

Shane

---

### Post by ajgreeny on 2006-06-07
Just make a link to the prog or drag its menu icon from the K menu to the /~/.kde/Autostart file in your home directory and Bob's your uncle.

---

### Post by shane2peru on 2006-06-07
OK, Thanks!  In Gnome there was an easy GUI way.  

Shane

---

### Post by bleaked on 2006-06-07
**From the KDE Help FAQ:**  (I have highlighted in red what I believe you're after, but included the whole bit since it's probably good to know)

> **[SIZE="1"]How do I run a program at KDE startup?**
  
There are many ways to do that. If what you want to do is to run some scripts that would set some environment variables (for example, to start gpg-agent, ssh-agent and others), you can put these scripts into $KDEHOME/env/ and make sure their names end in .sh. $KDEHOME is usually a folder named .kde (note the period at the beginning) in your home folder. If you want scripts to be executed for all KDE users, you can put them under $KDEDIR/env/, where $KDEDIR is the prefix KDE was installed to (you can find this out using the command kde-config --prefix).


**[COLOR="Red"]If you wish to start a program after KDE has started, you may want to use the Autostart folder. To add entries to the Autostart folder: [/COLOR]**

Open Konqueror.

Select Go->Autostart from the menubar.

Right-click in the window view area and select Create New->File->Link to Application

Click on the Application tab in the window that appears and enter the name of the command to run in the Command text box.[/SIZE]

I hope this helps :D

.:bleaked

---

### Post by shane2peru on 2006-06-07
[QUOTE=bleaked]**From the KDE Help FAQ:**  Select Go->Autostart from the menubar.[/QUOTE]
This part is a little unclear.  I don't see a **Go** anywhere in Konqueror.  I may just be overlooking it, but this sounds like the easiest way to accomplish what I want properly.  Thanks for the info.  

Shane

---

### Post by ajgreeny on 2006-06-08
The konqueror Go as mentioned by bleaked is just the icon to the right of the address box.  You just type Autostart in there hit return and you will be taken to the /home/.kde/Autostart folder. You will still need to drag the K menu item into it, or just make a new link in that folder, as I suggested.

---

### Post by shane2peru on 2006-06-08
Ahhh, ok, that was easy.  Thanks for the info.

Shane

---


---
title: "run terminal command on KDE login"
date: 2012-09-08
forum: Desktop Environments
---

### Post by rybnik on 2012-09-08
I run Lucid Lynx, and I use both Gnome and KDE.  I want the terminal command "nm-applet" (without the quotes) to run automatically once I log into KDE, but I don't want it to run when I log into Gnome.  Is there a way to do this?

Thank you.

---

### Post by 2F4U on 2012-09-09
Did you try running the command through the automatic startup functionality? This should be distinct for Gnome and KDE.

---

### Post by Epodx64 on 2012-09-09
Go to system-settings --> Startup & shutdown --> add script 

That shouldn't mess with you're Gnome installation at all.

---

### Post by rybnik on 2012-09-09
[quote=Epodx]Go to system-settings --> Startup & shutdown --> add script 

That shouldn't mess with you're Gnome installation at all.[/quote]

Thanks; I'll try that.  I'll report back on whether it worked.

---

### Post by rybnik on 2012-09-09
Awesomeness.  It worked!

---

### Post by Epodx64 on 2012-09-10
Good glad to hear it.

---

### Post by rybnik on 2012-09-10
For the edification of anyone else wanting to do this, I hasten to explain that you have to use "add program."  It didn't work as "add script."

---


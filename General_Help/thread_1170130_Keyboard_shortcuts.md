---
title: "Keyboard shortcuts"
date: 2009-05-25
forum: General Help
---

### Post by adnaan on 2009-05-25
Hello, 
 
Is there a way of creating a keyboard shortcut combo (eg Ctrl+Alt+T) to launch an application?
 
Thanks, 
Adnaan

---

### Post by iiska on 2009-05-26
If you are using Gnome, open System -> Preferences -> Keyboard Shortcuts.

In the shortcuts dialog press Add and enter some name and command which launches the application. Click OK and assign keys to the shortcut by clicking "Disabled" text in the Shortcut column and then use the key combo you want.

---

### Post by adnaan on 2009-05-30
Thanks for the reply. We have an application written in XFC (Gtk+) that runs in the background and what we would like is when the user presses a certain keyboard combo it comes to the foreground or invokes a certain action in the application. Is this possible? How would we add such a functionality. 

Thank you, 
Adnaan

---

### Post by iiska on 2009-06-01
You can find the same functionality in XFE also. Look into XFCE's applications menu, and from there Settings -> Keyboard. Keyboard dialog contains tab "Application shortcuts", which is similar to Gnome's shortcut dialog.

Ps. Sorry, I read your post in a little hurry, and didn't answer the right question. :oops:

---

### Post by adnaan on 2009-06-02
Hello, 
 
Thank for you again for replying. We would like to do this programatically, that is within the application make a system call to add this keyboard shortcut. Is such a thing possible? Does an API exist for doing this in XFCE?
 
Thanks, 
Adnaan

---


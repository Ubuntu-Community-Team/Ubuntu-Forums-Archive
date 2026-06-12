---
title: "[SOLVED] keyboard shortcut default web page"
date: 2008-02-06
forum: Desktop Environments
---

### Post by glennric on 2008-02-06
Is there any way to change the default web page that is loaded when the Gnome keyboard shortcut is used to open the web browser?  The default is "file:///home/username/," i.e., the users home directory.  I would rather that this would be the Google search page, which is my home page in Firefox.  Does anyone know how to do this?

---

### Post by cuby on 2008-02-08
You can assing keyboard shortcuts in system->preferences->keyboard shortcuts.
If your **default browser** is firefox, it should open the default webpage.

---

### Post by tcommbee on 2008-02-09
you could also check under system>preferences>preferred applications that the browser command looks right, i.e. if you already got google as homepage, there may be an option there which forces the homepage to the other path

---

### Post by glennric on 2008-02-13
> **tcommbee said:**
> you could also check under system>preferences>preferred applications that the browser command looks right, i.e. if you already got google as homepage, there may be an option there which forces the homepage to the other path

The problem is related to the preferred applications option.  I compile my own firefox build optimized for my processor, and it sets itself as the default browser.  It does so be putting the custom command "/opt/firefox/firefox "%s"" in for the web browser preferred application.  The command that the default Ubuntu install of firefox uses is "firefox "%s"".  I had to tell firefox not to check if it is the default browser, and set the preferred app to the ubuntu firefox option.  Since I use a diversion from /usr/bin/firefox to /opt/firefox/firefox anyway, this still opens my version of firefox, and for some odd reason with the path not included in the command the keyboard shortcut opens to the correct homepage.

---


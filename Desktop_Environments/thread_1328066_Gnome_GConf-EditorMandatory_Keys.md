---
title: "Gnome GConf-Editor/Mandatory Keys"
date: 2009-11-16
forum: Desktop Environments
---

### Post by JustinR on 2009-11-16
Hello,

I've just installed Ubuntu 9.10 to a 16gb flash drive and I've recently stumbled upon Gnome's GConf-editor, and while changing the Login screen (I don't like how the new Ubuntu login screen shows the usernames) back to the Simple Greeter I accidentally set the value (disable_user_list) to mandatory, the application was running in gksudo by the way, and, now I have what I want - it doesn't show the user list, but if now if I try to change it it says that "This Key is Not Writable", and if I try to change it through the command line it says, "Error setting value: Can't overwrite existing read-only value: Value for `/apps/gdm/simple-greeter/disable_user_list' set in a read-only source at the front of your configuration path".

Although I'm happy with what I chose, the simple greeter, I like having control - so if I ever want to change it back what could I do?

Btw, I read the Gnome documentation for setting Mandatory keys in GConf-editor and it doesn't help much in "unsetting" the key (making it un-mandatory).

---

### Post by JustinR on 2009-11-17
Bump

---

### Post by JustinR on 2009-11-18
Bump

---

### Post by JustinR on 2009-11-19
Anyone?

---

### Post by vamped on 2009-11-21
While I don't have a solid reply, I do have some options:

Look in directory .gconf in your home directory.  Maybe you could find a file to change manually.

Also, in root's home directory there is also a .gconf directory.

Disclaimer: this is just a guess, and it's probably easy to mess things up if you play around.

---

### Post by vamped on 2009-11-21
Well I guess I was just curious enough to follow you down your rabbit hole, and I got myself stuck too. Since I prefer the login screen the way it was I had to search for the solution. And I found it.

[http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/)

Just a few paragraphs from the top under heading "Configuration Sources", it states:

```
   xml:readonly:/etc/gconf/gconf.xml.mandatory
   include "$(HOME)/.gconf.path"
   xml:readwrite:$(HOME)/.gconf
   xml:readonly:/etc/gconf/gconf.xml.defaults
```

THE SOLUTION: in directory /etc/gconf/gconf.xml.mandatory is a single file called %gconf-tree.xml

Edit the file (must use sudo) and remove the section with disable_user_list in it (probably deleting every line if this is the only mandatory key). Save file.

Log out and back in for the change to become effective.

---

### Post by JustinR on 2009-11-22
Sweet! Thank you so much 0 I've been searching for the solution for quite some time now, I have yet to test the solution, I'll post back soon - thanks!!!

Edit: Jeez, I've been on that page a couple of times and must have missed the solution!

---

### Post by RKendron on 2011-03-20
I just tried it.  I accidentally made my panel setting mandatory.  It works like a dream.  Thank you!:P

---


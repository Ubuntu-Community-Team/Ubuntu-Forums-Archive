---
title: "only firefox and ica client"
date: 2010-06-22
forum: Desktop Environments
---

### Post by wreg on 2010-06-22
Is it possible to hide the gnome interface?
I'd like gnome to come up with only firefox visible on a certain page. From this page users can login to open a virtual desktop with citrix ica client. 

Basically every other functionality can be blocked. I mean, it doesn't matter if it's available, but I'd like it to be invisible.

The web browser environment (address bar and whatnot) can be visible :)


I figured that by putting gnome-open [http://(ip]("http://%28ip") of xen desktop controller) in the startup script it does open gnome with firefox showing the page I want it to.
Now all I need to do is hide the rest of the interface :)

possible?


Thanks in advance,
Wim

---

### Post by clrg on 2010-06-22
Remove all the panels?
Right-click on it, choose "delete this panel".

---

### Post by Mathieu147 on 2010-06-22
I never tried this, but maybe you can test: 

Open gconf-editor, and navigate to /desktop/gnome/session

There's "required_components_list" key, from which you could try to remove components.

---


---
title: "How do I remove open office?"
date: 2009-01-21
forum: General Help
---

### Post by b3n0 on 2009-01-21
Hey all,

My Open Office is playing up. The language setting is set to 'symbol'. I cant make out a thing. That goes for all menus icons and user inputed text. I've tried reinstalling it through the synaptic package manager. No joy there... 

How can I compeltely remove it so I can install it fresh?

Thanks

---

### Post by fooman on 2009-01-21
have you tried deleting the hidden folder that contains the config settings for open office?  after you delete it...it will be recreated when open office is opened again.  ...that may set it back to default settings.

open your home folder and in the toolbar, click "view" and put a check next to "show hidden files".  then find the .openoffice.org folder,  right click on it and choose "move to trash".

try openoffice again and see if that helps.

could also try upgrading to openoffice 3:

[http://ubuntuforums.org/showpost.php?p=6210799&postcount=1](http://ubuntuforums.org/showpost.php?p=6210799&postcount=1)

---

### Post by Tim Sharitt on 2009-01-21
Open a terminal and do
```
sudo apt-get purge openoffice-common
```
This will remove the application as well as remove any configureation files.

---

### Post by jespdj on 2009-01-21
But it's not necessary to try to remove OpenOffice completely!

Do what fooman says to delete your personal OpenOffice settings information before trying to remove the software itself.

On my system, that directory is called .openoffice.org2. Delete it in a terminal window like this:
```
rm -rf ~/.openoffice.org2
```

---

### Post by vanadium on 2009-01-21
I did not have the problem myself, but it looks as if solutions can be found here:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10183)

---


---
title: "How to recover main gnome panel?"
date: 2005-02-10
forum: Desktop Environments
---

### Post by NicS on 2005-02-10
Hi

Does anyone know how do I recover my main gnome-panel (App, Desktops...) that I accidentally erase?

It seems that you can't reconstruct it with adding applets,

Thanks

---

### Post by domzo on 2005-02-10
You can get back to the default user settings if that's what you want? (i.e. as if you were a new user)

To do this you have to delete some hidden directories (or move them to a different directory for backup just in case...). Next time you log in Gnome will recreate the default settings for you. Unfortunately you will lose any customisation you've done.

To do this you will need to log out of gnome (Ctrl alt del) then open up a virtual terminal (ctrl alt f5)

Log in.
type:

ls -a  (this will list all directories including hidden ones (.somehiddendirectory)

mkdir mytempdir  (makes a new directory)

move the user settings to this temp directory

e.g. 

mv .gnome mytempdir
mv .gconf mytempdir
...

See here for a list of files to move/remove:
[http://www.gnome.org/learn/admin-guide/latest/apa.html](http://www.gnome.org/learn/admin-guide/latest/apa.html)

then

exit (to logout of virtual terminal)

ctrl alt f7 (to get back to gnome login)

login, and you should have a fresh faced gnome.

If you want to try to recover any of your old settings you can then try to move individual files back from mytempdir to your home directory again. (you might have to do this via the virtual terminal again)

hope that helps
domzo

ps Having said all that there may be an easier way just to recover the panel!

---

### Post by NicS on 2005-02-10
thanks for the quick reply

well, I already thought of that method but I hoped there would be something less "brutal"!

Anyway, if anyone knows something "smoother"...;

Cheers

---

### Post by domzo on 2005-02-10
I didn't realise it was a quick reply, I'd just logged on  :-) 

Yeah it's strange you'd think there would be an easy way.
You could try just removing .gnome2??

[I]
 .gnome2
	

Contains user-specific application data that is not stored in the GConf repository. For example, this directory contains the following:

    *

      Keyboard shortcut information.
    *

      Window location information.
    *

      Desktop entry files for panel launchers.

This directory also contains user-specific menu data. If a user modifies menus, the details are stored here. [/I]

---

### Post by NicS on 2005-02-10
Well removing .gnome* and .gconf* doesn't work.

Strange.. that's what I used to do when changing to an newer version of GNome on Debian Sid ;)

---

### Post by domzo on 2005-02-10
wierd.. that normally works for me on Suse too.

you could try reinstalling gnome-panel??

---

### Post by NicS on 2005-02-10
Well you had a good idea, it worked

this is rough though for a so "a priori" simple thing!

Hope developers gonna check that out


Thanks again

---

### Post by domzo on 2005-02-10
Glad it worked!

Yeah, there needs to be an easier way..

---


---
title: "gcursor prob"
date: 2009-03-02
forum: General Help
---

### Post by slim@jim on 2009-03-02
I'm trying to install a cursor theme with gcursor which is an easy thing to do but gcursor won't work at all.

When i click on the "+install themes" nothing happens, no widow pops up or anything.

Same thing with the "go to theme folder" no window pops up, it just does nothing.

I uninstalled gcursor and reinstalled it with no help to the problem.

I ran a bunch of searches and found nothing about gcursor doing this.

any ideas plz ?

---

### Post by LizZardCZ on 2009-03-06
Hi,

i have the same problem on Interpid in Gnome. There are 4 question mark icons in the bottom part of the app window. It seems buggy from the first look.

When I launch it in the console view i get these messages:

> (gcursor:19294): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gcursor:19294): libglade-WARNING **: could not find signal handler 'extract_theme'.

(gcursor:19294): libglade-WARNING **: could not find signal handler 'open_theme_dir'.

(gcursor:19294): libglade-WARNING **: could not find signal handler 'entry_selected'.

(gcursor:19294): libglade-WARNING **: could not find signal handler 'size_changed'.


I will try to figure it out but some help would be appreciated ;)

---

### Post by LizZardCZ on 2009-03-06
The solution can be found [here]("https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491").
> 
- Download the tar-ball from e.g. gnome-look.org
- Extract it as root to /usr/share/icons
- Then edit as root the index.theme file located in usr/share/icons/default
Change the line Inherits= to the name of your new icon theme.
Logout and login again and your new cursor is in use.

Hope it helps :)

---

### Post by slim@jim on 2009-04-13
YO !

that did help thanks a ten million.


dang it took me a whole month to get back to this 

cant wait to see my new cursor flying around :)

---


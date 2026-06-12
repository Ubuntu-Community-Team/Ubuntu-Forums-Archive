---
title: "Help!  New system-wide .desktop not taking effect!"
date: 2006-11-01
forum: Desktop Environments
---

### Post by madscientist on 2006-11-01
Argh!  I have an app and I want to add it to my Applications -> Programming menu.  I want to do this system-wide, not just for myself (so I don't want to just add it with the menu editor--which does work by the way!)

So I created a foo.desktop file and copied it into /usr/share/applications.  I took a copy of another .desktop file from an application (emacs21) that was already in that menu, and modified the name, icon, and exec fields.

But it doesn't take effect!  It's silently ignored.  I see no errors or messages in .xsession-errors or in my system logs.  I tried modifying /usr/share/applications/emacs21.desktop (changed the title) and the change shows up in my menus immediately, but my new app is still not there.  I've also tried installing it using 'sudo desktop-file-install --vendor=foo foo.desktop' and although that didn't fail, my menu item still does not appear ](*,). When I start up the menu editor, the new application is not there either.  I've logged out, rebooted, etc. to no avail.

I've googled and searched and tried lots of things but I can't find a simple explanation of what you must do.  It seems like dropping a .desktop file into the /usr/share/applications directory is NOT enough, although all the documentation I've read describes how to write a .desktop file and doesn't say that there's anything else that needs to be done.

What else do I need to do?  What could be wrong?  How do I go about figuring it out?

---

### Post by CatKiller on 2006-11-01
I can't remember all the ins-and-outs of it, but there's a file in your home folder somewhere called applications.menu. If you have a browse of that, I think it will tell you which directories get scanned for .desktop files to go in the menu.

Hope this helps.

---

### Post by madscientist on 2006-11-01
> **CatKiller said:**
> I can't remember all the ins-and-outs of it, but there's a file in your home folder somewhere called applications.menu. If you have a browse of that, I think it will tell you which directories get scanned for .desktop files to go in the menu.Hi; thanks for the response!

I don't see any applications.menu file anywhere in my home folder.  I found a few system-level ones but they just say they're using the default directories.  I'm fairly confident that I've put the .desktop file in the right place because (a) it's where all the other system-level .desktop files are installed by their packages, and those work, and (b) when I modified the title in the emacs21.desktop file in that directory the change showed up in my menus immediately, so it's definitely using that file to populate the menu.

But, is there more that needs to be done than drop that file in /usr/share/applications?  If not, then how do I go about figuring out why my file doesn't work? :confused:

---

### Post by CatKiller on 2006-11-01
Mine's in ~/.config/menus and appears to include by reference 

/etc/xdg/menus/applications.menu
~/.local/share/applications
/usr/share/gnome/apps/Utilities
/usr/share/gnome/apps/Multimedia
~/.local/share/desktop-directories

And according to that file, you can find more information [here]("http://standards.freedesktop.org/menu-spec/menu-1.0.dtd").

---

### Post by madscientist on 2006-11-02
Hm.  Well, I know about the stuff in my home directory: I've actually added the .desktop file there and modified applications.menu and then it showed up in my menu.  But, I want to add it to the _system_ directories so it shows up in everyone's menus automatically without adding it to every user individually.

I looked at the various applications.menu files on my system including the ones you show above (although my system doesn't have /usr/share/gnome/apps/Utilities), and *none* of those files contain references to all the different things that show up in my menus.  So it can't be the case that I have to edit those files to add my application (that would suck in a major way if I had to do that!)

This is really frustrating.

---

### Post by CatKiller on 2006-11-02
So did you look at the specification? > This DRAFT document defines how to construct a user-visible hierarchy of applications, typically displayed as a menu. It allows third-party software to add menu items that work for all desktops, and allows system administrators to edit menus in a way that affects all desktops.

---

### Post by madscientist on 2006-11-03
I did (although your link pointed me to the DTD, which wasn't quite what I was looking for :)  A little URL-foo and I found the doc).

According to that document, since I'm not creating any new menus I should be able to just plunk a .desktop file down in the standard applications directory and it should just work.

But, it doesn't.

I don't know how to figure out what's wrong.

---

### Post by CatKiller on 2006-11-03
As a quicky before I browse the docs myself, have you checked your menu in Alacarte, just to make sure that it's not been disabled there, or with a different user. Just so that you don't get thrown by some weirdness of your user configuration.

The reason I linked to the file I did was because I haven't read all the documentation myself. In my research to do some stuff previously, I'd got as far as discovering that the applications.menu file was significant, and gave a list of places that the menu looks for entries. That link was the one that that document cited.

You could post the contents of your .desktop file in case there's something wrong with it that someone more knowledgeable than us can spot. That someone may well be our future selves :)

---

### Post by CatKiller on 2006-11-03
I definitely have /usr/share/applications included as a "LegacyDir" in my /etc/xdg/menus/applications.menu, but I don't know if that's something I did myself. I think it might have been. Certainly I did something similar when I was trying to do what you are trying to do. I eventually got it working. Whether the two facts are related, I really couldn't say :)

---

### Post by madscientist on 2006-11-10
I have checked my menus with alacarte.  I even used the alacarte "Revert" button to revert all changes (in theory).  And, I've used find | xargs grep to look for any reference to this new menu item, etc. in my home directory.  Nothing interesting.

However.

I created a new user and that user DOES have this menu item appearing, just as I'd expect!!!  So, there's something, somewhere in my account that is turning this off but I can't find it.  I have no idea what to do next other than delete and recreate my account (which would really be a drag).  What part of Gnome/gconf/whatever should I look at to figure this out?

I even renamed the .desktop file to something different but it still won't appear.

---

### Post by CatKiller on 2006-11-10
> **madscientist said:**
> So, there's something, somewhere in my account that is turning this off but I can't find it... What part of Gnome/gconf/whatever should I look at to figure this out?

```
mv ~/.config/menus/applications.menu applications.menu.backup
``` would be my suggested command for reverting your menu to that of a new user. Other than that, I really don't know.

---

### Post by C Shore on 2006-11-11
You may be having trouble with ~/.cache.  Try removing it, logging out and logging back in.

---


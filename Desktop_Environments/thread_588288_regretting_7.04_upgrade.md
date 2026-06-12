---
title: "regretting 7.04 upgrade"
date: 2007-10-23
forum: Desktop Environments
---

### Post by rlongfield on 2007-10-23
I hope someone can help me out.
After running a flawless upgrade to 7.04 I am faced with this error message when I login.

"There was an error starting the Gnome Settings Daemon"

This only happens on my user. My wifes user seems to not get the error message but suffers other problems that my user experiences.

The second problem which I think my be related to the Gnome Settings Daemon error message is trying to browse any folder on my computer. It takes forever for the File Browser window to even open. Once it opens it takes even longer (in fact I've never waited long enough) for the contents of the folder/directory to display. 

This problem also seems to extend to Terminal and ls. When ls finally returns the directory listing everything seems to work fine at that point in terminal.

If I was on windows I would think that I had a virus and that the real solution would be to reinstall everything. I really don't want to even think of heading that route right now so I would love to get this problem(s) fixed.

-Rob

---

### Post by alastair on 2007-10-23
> **rlongfield said:**
> 
If I was on windows I would think that I had a virus and that the real solution would be to reinstall everything. I really don't want to even think of heading that route right now so I would love to get this problem(s) fixed.

-Rob

Someone might have a better idea but ... in this situation, unless I could find a specific reason online somewhere (searching), I'd probably re-make my home directory. Really, the main thing I'd want to clear out/delete would be the .gnome* folders - probably.

DO THE BELOW AT YOUR OWN RISK!

You could try renaming these first i.e.

- log out
- CTRL+ALT+F1 to a shell and log in
- sudo single (not sure here - but I want to make sure Gnome daemons/programs are not running)

This should put you in single-user mode

Now rename/backup some folders :

Maybe the gconf folders only :

- mv .gconf .gconf.bak
- mv .gconf2 .gconf2.bak

Now ...

- init 5 (back to runlevel 5)

Back to the login screen - login. 

 ... any better?

If not - repeat the above, but try the folders :

- mv .gnome .gnome.bak
- mv .gnome2 .gnome2.bak
- mv .gnome2_private .gnome2_private.bak


If not, or still problems, you could always re-make your home dir - i.e. make a new one and then copy your main folders to it from the original (minus some).


Alastair

---


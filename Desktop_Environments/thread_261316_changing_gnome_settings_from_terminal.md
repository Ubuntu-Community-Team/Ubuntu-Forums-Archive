---
title: "changing gnome settings from terminal"
date: 2006-09-20
forum: Desktop Environments
---

### Post by summersab on 2006-09-20
I would like to specify this as frequently as I can because every time I ask a question like this, I get an answer describing something I already know. I am comfortable with the command prompt. I want to use it to solve this problem. I do not want to even touch a mouse to be able to solve this problem. I want to be able to change these settings entirely from the command prompt.

That being said, if you know the internals of the Gnome interface (perhaps have ever made a skin), you will be able to help me. I want to be able to change three things FROM THE COMMAND PROMPT (not from inside Gnome - remember no mouse clicks). What file contains information regarding default applications? I want to make a system-wide change to alter what files are opened by what program. Second, what files contain the data that controls the contents and appearance of the panels? I want to be able to add/remove applets and launchers from the panels as well as alter the appearance (width, transparency, position, etc) of the panels. Lastly, what file contanins data regarding synchronization of the clock to an ntp server?

The reason I want to be able to do this all from the command prompt is becauase I am trying to set up computers en masse for others. I want to write a bash script that will make these changes for me without me having to manually change settings and perhaps miss something. Thus, I stress again, I don't want to use the mouse. No clicking. No GUI. I want to gedit files and pass commands.

If you can help with ANY of these, you're amazing!

---

### Post by mssever on 2006-09-20
I don't know the specifics, but if you hunt through ~/.gnome and ~/.gnome2, you're bound to find what you're looking for. For system-wide settings, look in /etc/gnome*.

---

### Post by kerry_s on 2006-09-20
I don't use gnome so can't help there, but for the ntp it's " /etc/default/ntpdate " That's 1 of your list ;)

---

### Post by jnoreiko on 2006-09-20
From [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/)

> GConf comes with a command line tool called gconftool-1 (for version 1) or gconftool-2 (for version 2) that you can use to get an idea what's going on. Try this command:

    $ gconftool-2 -R /desktop/gnome


I've not used it, but that might be a good place to start.

---

### Post by summersab on 2006-09-20
Does gconf have a import file type (like Windoze .reg files) to import settings directly? Also, is the gconf stuff controlled by a database file or files in the same manner as the Windoze registry is? I would like to be able to modify gconf settings manually, but I really don't know how to hack at it yet. I've not gotten that far yet with Linux (though it is my very next desired skill to learn).

---

### Post by jnoreiko on 2006-09-20
Looks like the answer to most of those questions is yes.
Here's a better article:

[http://www.gnome.org/learn/admin-guide/latest/gconf-6.html](http://www.gnome.org/learn/admin-guide/latest/gconf-6.html)

(You've got this installed on your ubuntu too, it's the GNOME admin guide.)

---


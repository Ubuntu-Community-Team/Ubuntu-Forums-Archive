---
title: "Mupen64Plus 1.5 installation issues"
date: 2009-06-09
forum: Gaming &amp; Leisure
---

### Post by Jcdlvsrbld on 2009-06-09
I've been having trouble installing mupen64plus on my ubuntu machine (currently using jaunty). Using the documentation provided by the project i need to "su to root and run the provided install.sh script"      So, i do and get this output: 

Installing Mupen64Plus to /usr/local
install: cannot stat `config/*': No such file or directory

the install directory contains only an empty folder named config.
have i done something wrong, or is it an issue with the installation script?

thanks in advance for any help  :confused:

---

### Post by Scouto2 on 2009-06-09
Try logging in as /root/ just to install, and then log off and get onto your normal account.

That might work. Just open the file directly instead of the terminal.

Or better yet, just type the command

gksudo nautilus

That opens the file manager as root, that way you can just install the program directly instead of using the terminal.

---

### Post by Jcdlvsrbld on 2009-06-09
> **Scouto2 said:**
> Try logging in as /root/ just to install, and then log off and get onto your normal account.

That might work. Just open the file directly instead of the terminal.

Or better yet, just type the command

gksudo nautilus

That opens the file manager as root, that way you can just install the program directly instead of using the terminal.

tried this, but for some reason i got this error when running the "gksudo nautilus" command

  (gksudo:6629): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
**Eel:ERROR:eel-preferences.c:107: preferences_gconf_value_get_bool: assertion failed: (value->type == GCONF_VALUE_BOOL)


how can i fix this? ](*,)

---

### Post by Scouto2 on 2009-06-09
Out of my league.
Wait for a person with more experience to come along, and if you need to, bump this thread if it reaches the next page of threads.

In the mean time, read this:
[http://ubuntuforums.org/announcement.php?f=93](http://ubuntuforums.org/announcement.php?f=93)
A list of commands that will bork your system, and can easily be disguised.

---

### Post by Jcdlvsrbld on 2009-06-10
i got it to work using apprunner, i guess i should've tried that at first. and i managed to open nautilus as root, but still cant figure out the source of the error:popcorn:

---

### Post by jyaan on 2009-06-10
I created a .deb file for it a while back, I can send that to you somehow if you like, although it is for 32-bit ONLY. Eventually I'll get around to creating a 64-bit .deb, because I run 64-bit now and can't use the old one I made.

---

### Post by Jcdlvsrbld on 2009-06-10
> **jyaan said:**
> I created a .deb file for it a while back, I can send that to you somehow if you like, although it is for 32-bit ONLY. Eventually I'll get around to creating a 64-bit .deb, because I run 64-bit now and can't use the old one I made.

that would be great, since mupen just stopped working for some reason

edit: managed to get it working again, so nvm the deb package

---


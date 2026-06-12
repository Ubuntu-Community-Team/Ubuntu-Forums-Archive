---
title: "Help, error with msstcorefonts and saving changes to xorg.conf"
date: 2005-11-30
forum: Desktop Environments
---

### Post by s monty on 2005-11-30
I get this error while attemping to install msstcorefonts. I need it for installing tahoma font. Any one know what to do? [http://img295.imageshack.us/my.php?image=error5hr.jpg](http://img295.imageshack.us/my.php?image=error5hr.jpg)


And How to do you save changes to the xorg.conf file? Whenever I close it than log off and back on the things I have changed never worked, so I open the file back up and it resets back to default. Any Ideas as to why it does that?


--I know I have been asking a lot of questions lately, Thanks for the help.

---

### Post by HighPlainsDrifter on 2005-11-30
[QUOTE=s monty]I get this error while attemping to install msstcorefonts. I need it for installing tahoma font. Any one know what to do? [http://img295.imageshack.us/my.php?image=error5hr.jpg](http://img295.imageshack.us/my.php?image=error5hr.jpg)


And How to do you save changes to the xorg.conf file? Whenever I close it than log off and back on the things I have changed never worked, so I open the file back up and it resets back to default. Any Ideas as to why it does that?


--I know I have been asking a lot of questions lately, Thanks for the help.[/QUOTE]

You need the universe repositories enabled to get msttcorefonts.

Your xorg.conf changes are not being saved because you are most likely opening up the file in read only mode. You can either open a terminal and sudo gedit /etc/X11/xorg.conf or do what I do, create a customer launcher on the panel for a gksudo'd version of VIM (or gedit, whatever you prefer)

---

### Post by aysiu on 2005-11-30
[QUOTE=s monty]I get this error while attemping to install msstcorefonts. I need it for installing tahoma font. Any one know what to do? [http://img295.imageshack.us/my.php?image=error5hr.jpg](http://img295.imageshack.us/my.php?image=error5hr.jpg) [/quote] See the first link in my sig.

> 
And How to do you save changes to the xorg.conf file? Whenever I close it than log off and back on the things I have changed never worked, so I open the file back up and it resets back to default. Any Ideas as to why it does that? Alt-F2 ```
gksudo nautilus
``` Control-L
/etc/X11
Right-click xorg.conf and select "copy."
Right-click and empty space and select "paste."
Double-click xorg.conf
[b]
Or...[/b]

Applications > Accessories > Terminal ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
``` You decide which method's better/faster

---


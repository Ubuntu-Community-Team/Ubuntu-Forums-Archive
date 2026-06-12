---
title: "can't login : &quot;can't find /usr/gdm/themes/Industrial/industrial.xml"
date: 2005-06-26
forum: Desktop Environments
---

### Post by venkman on 2005-06-26
hello

i installed  an industrial (bluecurve) theme by using apt-get [ i can't remember the exact name or the page from which I got the install info, i had to add some lines in the apt source.list] 

the theme worked fine (gnome) but after reboot  when I'm at the login screen, this error msg appears: can't find file /usr/share/gdm/themes/Industrial/industrial.xml
 
the buttons for reboot, language etc work fine, but the text box for the user name is locked.
 
what should I do? does somebody has this file (or files?) for download? 
or is there a way to uninstall this theme ?
// and could you please explain it to me ;)

Danke, venkman

---

### Post by cwaldbieser on 2005-06-26
Don't know if this will work, but it might be worth a shot.  Switch to a console by pressing CTRL-ALT-F1.  Log in with your normal username / password.  Now type:

```
$ sudo touch /usr/share/gdm/themes/Industrial/industrial.xml
```

This will create an empty file with that name.  

Log out.  switch back to the graphical display with ALT-F7.  Reboot, and see if it still gives you the same error.

FYI - You could use apt-get to uninstall the industrial theme from the console as well.  Sometimes, though, all you need to get some programs working is to create the configuration file it is looking for.

---

### Post by venkman on 2005-06-26
solved, thanks to a good friend ;)

the faked xml file suggestion didn't work :(
 
I switched to a console, sudo startx -- :2 > and started gdmsetup where I chose another theme for the login screen, now it works fine again!

thank you anyway cwaldbieser  :)

---


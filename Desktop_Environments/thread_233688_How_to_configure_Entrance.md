---
title: "How to configure Entrance?"
date: 2006-08-10
forum: Desktop Environments
---

### Post by super carrot on 2006-08-10
I am trying to configure Entrance as my login manager, but I dont know where to begin. I have searched around but I dont seem to be able to find any manuals, does anyone know how I might go about that?

---

### Post by pksings on 2006-08-10
Menu Drop downs, System>Administration>Login Window.

It's themeable, and pretty configurable.

PK

---

### Post by super carrot on 2006-08-10
Thanks for the reply, the problem is the program that you just mentioned, only configures gdm, it doesnt allow me to change the login manager, for instance I cant use that to change to kdm.

---

### Post by mssever on 2006-08-10
I don't know anything about Entrance, but the default login manager is set in /etc/X11/default-display-manager.

Also, try sudo /etc/init.d/gdm stop(or kdm--whatever you're using right now). Then start Entrance: sudo /etc/init.d/name-of-entrance-script start. This should help you make sure that everything's installed correctly.

---

### Post by super carrot on 2006-08-10
Thanks again for your reply, I think that we are getting there now:

update-rc.d entrance defaults 

should add the entrance startup script so now entrance will start up every time the computer starts up.

I think that you will also have to use:

update-rc.d -f gdm remove

to remove the gdm from the start up.

Now, once started up, how will I properly configure the options so that it knows how to properly start up gnome and kde when it is asked to?

---

### Post by loell on 2006-08-10
from edevelop 
> OK  guys... well it took a few days but I finally got this to work. Here are the steps...

- Download and install KDE using synaptic

- signon as root and modify the following file: /usr/share/entrance/build_config.sh

- Edit this file by removing the # from the lines that point to KDE

- Edit the following line: /session/count -i 2 to 3

- Modify the line that points to /session -s "kde" with the following "/usr/bin/startkde"

- Save your changes and run the file/command build_config.sh

- Copy the entrance_config.cfg to /etc

- Exit enlightenment. You should see the KDE sessio...

This should should work for any desktop environment. You just need to make a couple of changes. Hope this helps some peopl
hope this helps :)

---

### Post by Drone4four on 2008-04-05
To make entrance my default login screen, i just use: ```
sudo dpkg-reconfigure gdm

``` What I want to know is how to change entrance themes because the default one is all messed up.  It's mostly just a white screen.  There is no pointer.  So I figure if I try a different theme, of which there are many on get-e.org, then maybe entrance will work properly.  So how do you change entrance themes?

---

### Post by Drone4four on 2008-04-05
Ah yes, according to get-e.org, it says:> To use these login themes, just put the edj file in a dir of your choice. As there isn't currently a gui for this, you need to run entrance_edit --theme <path to theme file> (or entrance_edit --theme <theme file name> until it's fixed). After that you need to manually restart the daemon or simply reboot your computer.

---


---
title: "minimize,maximize,close"
date: 2016-05-01
forum: Desktop Environments
---

### Post by psfal on 2016-05-01
Ubuntu 14.04
This "gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'" puts all my window controls on the right where I want them, but it has to be done in each account on the system. Is there a way to make it system-wide so that it's unnecessary to do it in a new account?

---

### Post by T.J. on 2016-05-02
> **psfal said:**
> Ubuntu 14.04
This "gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'" puts all my window controls on the right where I want them, but it has to be done in each account on the system. Is there a way to make it system-wide so that it's unnecessary to do it in a new account?

No.  Window manager settings are stored for individual users only, because no single window manager is considered standard.  X11 has no such mandate.  

You can get around it by adding an adduser.local file

From the adduser manual page:
"If  the  file  /usr/local/sbin/adduser.local exists, it will be executed after the user account has been set up  in  order  to  do  any local setup."

There are more details on the man page. I would use that to add your gsettings command to the file, so that you preset the buttons as the new user is created.  You could add it to other places, but what if a user wants to change it?

---

### Post by psfal on 2016-05-04
How do I get it to run that command? the man page for adduser doesn't say how to run a terminal command in adduser.local

---

### Post by T.J. on 2016-05-04
> **psfal said:**
> How do I get it to run that command? the man page for adduser doesn't say how to run a terminal command in adduser.local
       

From the manual page:


  >     If  the  file /usr/local/sbin/adduser.local exists, it will be executed
       after the user account has been set up in order to do any local  setup.
       The arguments passed to adduser.local are:
       username uid gid home-directory
       The  environment  variable  VERBOSE  is  set according to the following
       rule:


       0 if --quiet is specified


       1 if neither --quiet nor --debug is specified


       2 if --debug is specified


              (The same applies to the variable DEBUG, but DEBUG is deprecated
              and will be removed in a later version of adduser.)




In other words, /usr/local/sbin/adduser.local  is a shell script that you make where the following parameters are passed to it in this order: username, GID, UID, home directory.  All you would need to do is write a script to accept those parameters, and have it execute your gsettings command as the username in question, either via su or sudo. It will be automatically run after the user is created.

Do you need help creating it?

---

### Post by psfal on 2016-05-04
@T.J. Yes, I do need help creating it. I'm a mechanic by trade, much of this computer terminology is beyond me.

I am the end-user who guides others onto the path of Linux righteousness, away from the path of evil proprietary software.

I would very much appreciate your assistance on this issue :)

---

### Post by psfal on 2016-05-08
Ok, I created the /usr/local/sbin/adduser.local and put this in:

#!/bin/bash
#min max close
gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'

Then did "sudo chmod 755 /usr/local/sbin/adduser.local"

And I got nothing...what did I do wrong?

---


---
title: "x11vnc - help pls"
date: 2005-08-28
forum: Desktop Environments
---

### Post by master_b on 2005-08-28
HI

I've followed the threads/howtos re VNC and GDm/X11vnc and everything is working fine, except for my File/Print Server, which is not running Ubuntu but is running Mepis SOHO Server beta.

My problem is getting X11vnc to run automatically at boot on the Server.

The x11vnc howto says:-

go to Systems/Preferences/Sessions/Startup and add sharex11vnc.

Mepis SOHO does not have these menu items, and the other option given - add to startup script - is apparently what I need to do.

Where/what is the startup script (for my user I assume)?

Thanks

Bill

---

### Post by master_b on 2005-08-28
Anyone?

Bill

---

### Post by bdamon on 2005-08-29
[QUOTE=master_b]

Mepis SOHO does not have these menu items, and the other option given - add to startup script - is apparently what I need to do.

Where/what is the startup script (for my user I assume)?

Thanks

Bill[/QUOTE]


If you are using KDE which is the Mepis default, look in your home directory for a .kde/Autostart directory. Anything files in there get run on login. You will have to create a script place it in that folder and make it executable.

---

### Post by master_b on 2005-08-29
bdamon,

thanks for the reply, but that doesn't help.

I need x11vnc ( server) to start BEFORE login so that I can access the kdm log-in screen remotely.

I believe that a script in /etc/init.d to start x11vnc on boot is the way to go.

I'm currently "googling" re same and will try modifying an existing /etc/init.d script, perhaps the ssh script.

Thanks

Bill

---

### Post by bdamon on 2005-08-30
[QUOTE=master_b]bdamon,

I believe that a script in /etc/init.d to start x11vnc on boot is the way to go.

[/QUOTE]


Yes this would be the preferred method. I would recommend placing your script in /etc/init.d  then make it executable  chmod +x /etc/init.d/scriptname  then create a link in /etc/rc2.d to the script  ln -s /etc/init.d/scriptname /etc/rc2.d/S99scriptname

The link name will need to be in the format as the other links ex. S99scriptname


Ben

---

### Post by master_b on 2005-08-31
Ben, thanks for the reply and confirmation that I'm heading in the right direction.

I've since learned a bit about ssh and shfs, both of which are loaded as modules in my setups, so I'm leaning more towards these for security reasons, rather than having the vncserver running permanently.

I could use ssh to log into the Server and run x11vnc when needed, and use shfs to log in and mount the Shares and drives on the Server.

So much to learn and so many ways to achieve the desired results. 

Bill

---

### Post by bdamon on 2005-08-31
[QUOTE=master_b]

I could use ssh to log into the Server and run x11vnc when needed, and use shfs to log in and mount the Shares and drives on the Server.

So much to learn and so many ways to achieve the desired results. 

Bill[/QUOTE]

Thats what makes Open Source so great! 

You might also want to look into tunneling vnc through a ssh connection, much more secure.


Ben

---


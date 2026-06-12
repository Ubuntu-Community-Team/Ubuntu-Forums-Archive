---
title: "Root Xserver Problem"
date: 2006-03-03
forum: Desktop Environments
---

### Post by XIII on 2006-03-03
when i try to run applications from root it gives me a message like this:

> root@php:/home/sting# kate /etc/apache/httpd.conf
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
root@php:/home/sting#  

how to configure it to make root able to run applications?

---

### Post by Parkotron on 2006-03-03
Ubuntu and Kubuntu are set up to use [FONT="Courier New"]**sudo**[/FONT] methods, rather than a full root account. Instead try [FONT="Courier New"]**kdesu kate /etc/apache/httpd.conf**[/FONT] while logged in as a regular user.

---

### Post by XIII on 2006-03-04
[QUOTE=Parkotron]Ubuntu and Kubuntu are set up to use [FONT="Courier New"]**sudo**[/FONT] methods, rather than a full root account.[/QUOTE]

On ubuntu i was able to use the full root account, just since i switched to kubuntu i couldn't use it, isn't there any other method to configure Xserver?? :confused:

---

### Post by retsaw on 2006-03-04
As the regular user that owns the X session type into a terminal```
xhost +local:
```that will allow applications started by root (and other users) to connect to your X server.  This is slightly insecure as it will allow other users on your machine to connect to your X session and they could monitor your mouse and what you type on your keyboard.  Presumably this won't be an issue for you, but I should point it out anyway.

Now, you will need to do this everytime you log on to be able to run X applications as root.  It presumably is possible to alter the setup so you don't need to do this, but I don't know what change you need to make, it will surely be in the kdm configuration file though, and it probably is related to the options kdm uses to start X.

---


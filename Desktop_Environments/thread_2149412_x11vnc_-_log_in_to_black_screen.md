---
title: "x11vnc - log in to black screen"
date: 2013-05-28
forum: Desktop Environments
---

### Post by flickerfly on 2013-05-28
I have setup x11vnc and can log in using the command 
sudo x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log -rfbauth .vnc/passwd -rfbport 5900

This machine is a vmware virtual machine. Other machines with a similar setup are RHEL boxes with Xvnc. (Xvnc isn't available on Ubuntu right?)

When I get logged in it drops me to a black screen with a white mouse. It doesn't seem to matter how long I hang around it still won't put anything on the screen.

I have XRDP setup on it and working, but they want VNC instead because they don't know of any RDP clients that automate the SSH tunnel stuff.

What causes the login to go to a black screen? How do I fix it?

---


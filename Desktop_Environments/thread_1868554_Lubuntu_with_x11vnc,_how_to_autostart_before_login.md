---
title: "Lubuntu with x11vnc, how to autostart before login"
date: 2011-10-24
forum: Desktop Environments
---

### Post by sgadecki on 2011-10-24
Hey all,
         For a while now I have been trying to figure out  how to get x11vnc started *Before* logging in to  Lubuntu.  After trying many different things, I have finally figured it  out!  This info can also be used to auto-start other VNC servers as well  (tightVNC, etc.)  This is also good information for how to auto-start  apps in general.  I'm sure there are a few of you out there who have  been trying to figure  this out, and I'm sure I'll want to do this on another machine some  time and by tomorrow I'll forget how I did this, so... here's how it's  done:

In order to get this to work I used X11VNC v0.9.13.  I had trouble getting this to work fully when using v0.9.11 and v0.9.12.  I downloaded v0.9.13 directly from [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/) and then compiled it following the instructions on that same page.

Lubuntu uses LXDM as a desktop manager.

The config files for LXDM are:

/etc/lxdm/default.conf               [default LXDM settings config]
/etc/lxdm/lxdm.conf         [general LXDM settings config]
/etc/lxdm/LoginReady               [runs when LXDM starts, before logging in]
/etc/lxdm/PreLogin          [runs after clicking Login, but before validating credentials]
/etc/lxdm/PostLogin                     [runs after validating credentials]
/etc/lxdm/PostLogout                 [runs after logging out]
/etc/lxdm/PreShutdown    [runs after initiating shutdown, but before shutting down]
/etc/lxdm/PreReboot                   [runs after initiating reboot, but before rebooting]
/etc/lxdm/Xsession                       [X general settings config]


The  descriptions between the brackets [ ] are what I came up with after  some experimenting with these files.  If you have any suggestions or if I  am incorrect with any of these, please let me know.

Depending on when you want your app to auto-start, edit the appropriately named file.

  In this case, since I want to have X11VNC running at the logon screen, I'm going to edit the LoginReady file.

Here I'm assuming that you already have x11vnc installed.  If not installed, install x11vnc using your favorite method.

now that x11vnc is installed open a terminal, we'll get it to auto-run.

Since x11vnc needs X to run, to get x11vnc to run before logon we have to "adjust the XAUTHORITY environment variable to point to the correct MIT-COOKIE auth file while running **x11vnc** as **root**"

at the command prompt, type in: **sudo nano /etc/lxdm/lxdm.conf**

Edit this line:
## set this if you don't want to put xauth file at ~/.Xauthority
**xauth_path=/tmp**

For a single user machine, **xauth_path=****~/.Xauthority** should work

For a multiple user machine like mine, change the xauth_path to a folder that is accessible before login.  I used /tmp

save the change.

at the command prompt, type in: **sudo nano /etc/lxdm/LoginReady**

Change this:
[B]#!/bin/sh
#
# Note: this is a sample and will not be run as is.[/B]

to this:
[B]!/bin/sh
# X11VNC AutoStart
sudo x11vnc -auth /tmp/.Xauth1000 -forever -rfbport 5900[/B]

make  sure you run x11vnc as root (use sudo) otherwise it won't start until  after logging in, which defeats the whole purpose of this setup.

Save  changes, and reboot.  Your x11vnc server should auto-start at the  Lubuntu(LXDM) login screen allowing you to connect to the machine via  VNC and then log on.

You may notice however, that this configuration does not have a password set on the VNC connection.  
[U][B]
To set your VNC server to require a password:[/B] [/U]

in a terminal window type:
[B]sudo x11vnc -storepasswd Password /etc/x11vnc.pass
[/B]but replace "Password" with your password. This saves your password in  a file located at **/etc/x11vnc.pass**

After setting your password with the above, at the command prompt type in: **sudo nano /etc/lxdm/LoginReady** and add **-rfbauth /etc/x11vnc.pass** to your startup string and your VNC server should now require a password.

The startup string that I use in my LoginReady is here:

[B]sudo x11vnc -auth /tmp/.Xauth1000 -forever -rfbauth /etc/x11vnc.pass -rfbport 5900

[/B]

---

### Post by Rob1970 on 2011-12-12
this is brilliant!! i have been trying to fathom out if it is even  possible to remote VNC to a linux box across a LAN/WAN for ages (pre-login).... thank you so much :KS

---

### Post by irvin on 2012-02-11
This works completely !

before login screen, secure, with password and numeric keys are working !

[http://www.dannratemal.de/?p=450](http://www.dannratemal.de/?p=450)

---

### Post by NewUserFF on 2012-02-16
Great! thx a lot !  ive been looking for it for a long time!

---

### Post by BigDogRMF on 2012-02-23
Works great, I configured as shown above. My only problem is that vnc does not ask for my password, it just connects. How would I modify the above so that X11vnc will still ask me for a password?
Thanks!

---

### Post by sgadecki on 2012-02-27
> **BigDogRMF said:**
> Works great, I configured as shown above. My only problem is that vnc does not ask for my password, it just connects. How would I modify the above so that X11vnc will still ask me for a password?
Thanks!

Hey BigDogRMF,
       My instructions for setting the password were very vague.  I just updated the main post.   I hope this helps to clarify!

_**To set your VNC server to require a password:** _
 
 in a terminal window type:
 [B]sudo x11vnc -storepasswd Password /etc/x11vnc.pass
[/B]but replace "Password" with your password. This saves your password in  a file located at **/etc/x11vnc.pass**
 
 After setting your password with the above, at the command prompt type in: **sudo nano /etc/lxdm/LoginReady** and add **-rfbauth /etc/x11vnc.pass** to your startup string and your VNC server should now require a password.
 
 The startup string that I use in my LoginReady is here:
 
 **sudo x11vnc -auth /tmp/.Xauth1000 -forever -rfbauth /etc/x11vnc.pass -rfbport 5900**

Hope this Helps!
                        -sgadecki

---


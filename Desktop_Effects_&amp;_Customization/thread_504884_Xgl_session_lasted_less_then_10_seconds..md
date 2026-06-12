---
title: "Xgl session lasted less then 10 seconds."
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by mobad on 2007-07-19
I've been having this problem since I switched to Feisty, Xgl just doesn't load.
I get the "Your session has lasted for less then 10 seconds" error.  
I run Feisty 64bit with the Ubuntu fglrx drivers installed properly.  
My .xsession-errors reports ```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mobad"
/etc/gdm/Xsession: Beginning session setup...
_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/ubuntu:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6

Fatal server error:
no screens found

(gnome-session:23121): Gtk-WARNING **: cannot open display:  

```
I've searched the forums for various terms included in the .xsessions-errors and found some older posts of people with the same problem but none of them were any help.
The only thing I have found is changing GdmXserverTimeout=10 to GdmXserverTimeout=50 I have tried this both in gdm.conf and gdm.conf-custom but it always times out after ten seconds.  
I even tried "gdmflexiserver --command="UPDATE_CONFIG daemon/GdmXserverTimeout=50" but with no success.  
I think that my solution is completely off track.
If anyone could help me solve this problem that would be great!

Thanks,
Mark

---

### Post by zero244 on 2007-07-20
Have you even had it work right.
I havent seen your problem before with 32 bit Ubuntu.
Are you loading XGL from your xorg.conf file or from a startup script.

---


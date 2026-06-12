---
title: "VNC as different user or as user logged in?"
date: 2009-05-12
forum: General Help
---

### Post by degel3030 on 2009-05-12
I have been going over a few tutorials and I just haven't been able to successfully have the ability to VNC into a users session and also have the ability to VNC into the login menu so I can log in as a different user. 
I am using 8.04 LTS Server

Oh and because I am sure someone is wondering why, I need to be able to support people who are logged in, but also start a few non-headless services from the GUI.

Any help or experience with this would be fantastic

Thanks

---

### Post by dougfractal on 2009-05-12
ssh into server


sudo x11vnc -auth /var/lib/gdm/:0.Xauth -display :0


this will start up a vnc gdm login screen.


from your client 
xtightvncviewer -via HOSTNAME localhost


login and the vnc will close.

on server
If vino-preferences are set to enable remote desktop
you can use ssh -Y  to setup vino-preferences with XForwording
or 

sudo x11vnc -auth /var/lib/gdm/:0.Xauth -display :0

again (not recommended)


client 
xtightvncviewer -via HOSTNAME localhost



SUMMARY  
SERVER: you need to start vnc twice (once to login, then to use; (vino may do this for you))
CLIENT: you need to vncview twice

voila.

---

### Post by krunge on 2009-05-12
> **dougfractal said:**
> 
SERVER: you need to start vnc twice (once to login, then to use; (vino may do this for you))
CLIENT: you need to vncview twice


If you set KillInitClients=false in /etc/gdm/gdm.conf-custom (and possibly gdm.conf too) you should only need to connect once.

More info: [http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

---


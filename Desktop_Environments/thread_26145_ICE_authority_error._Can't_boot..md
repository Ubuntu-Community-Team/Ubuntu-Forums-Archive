---
title: "ICE authority error. Can't boot."
date: 2005-04-12
forum: Desktop Environments
---

### Post by Trickyphillips on 2005-04-12
>  Your session only laster less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.
 

When I click the "View Details (~/.xsession-errors file)" button, I see

> /etc/gdm/PreSession/Default:Registering your session with wtmp and vtmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp /var/run/utmp -x "/var/lib/gdm/:0. Xservers "-h" "-i" ":0" "ron"

**(gnome-session:8209:WARNING**:Unable to read ICE authority file: 23/home/ron/.ICEauthority
 

I've spent the last 3 hours unsucessfully trying to install USB2.0 drivers on Windows (I'm really hating Windows today), so I can move some files to my external HD and get them onto my Linux box, and when I turn on my Ubuntu computer I see this. I'm so frustrated right now. 

If any truster members know how to fix this, could I PM you my login/password and let you telnet in (I've got the telnetd server running right now), then tell me how you fixed it? I really don't have the energy to do anything with my computer right now.  :cry:  :cry:

Thanks.

---

### Post by danip on 2005-04-12
I believe this comes from running k3b.  Easy problem to fix.  Boot up into I think its failsafe terminal and just do what it says here.

[http://www.ubuntuforums.org/showthread.php?t=23752&highlight=.ICEauthority](http://www.ubuntuforums.org/showthread.php?t=23752&highlight=.ICEauthority)

Search is wonderful.

---

### Post by Trickyphillips on 2005-04-12
[QUOTE=danip]I believe this comes from running k3b.  Easy problem to fix.  Boot up into I think its failsafe terminal and just do what it says here.

[http://www.ubuntuforums.org/showthread.php?t=23752&highlight=.ICEauthority](http://www.ubuntuforums.org/showthread.php?t=23752&highlight=.ICEauthority)

Search is wonderful.[/QUOTE]
 Phew... Thanks. I was really frustrated after my Windows problems. I think I'll be alright now.

---

### Post by danip on 2005-04-12
I used to get the error alot.  I got sick of it and uninstalled k3b and found a new burner program called gnomebaker and I haven't had that problem since.  Don't know if that is what fixed it or not but it's worth trying.  Plust gnomebaker is a better burning program anyways.

---

### Post by Trickyphillips on 2005-04-12
[QUOTE=danip]I used to get the error alot.  I got sick of it and uninstalled k3b and found a new burner program called gnomebaker and I haven't had that problem since.  Don't know if that is what fixed it or not but it's worth trying.  Plust gnomebaker is a better burning program anyways.[/QUOTE]
 ```
sudo apt-get remove k3b
sudo apt-get install gnomebaker
```

Done!

Thanks again. :)

---

### Post by wondering_jew on 2005-04-14
I had this error too... didnt know that it had anything to do with k3b. I switched to a console from the gdm  typed "chown (username) .ICEauthority then went back to the login screen and logged in. after that I ran nautilus as a super user and changed the permissions on the ICE authority file and never had a problem since... except k3b hasn't worked in a while and I'm now wondering if the two are related....

---

### Post by thecrimsonking on 2005-04-24
Are you guys running K3B in Gnome?  I use K3B in KDE all the time and have never come across this problem.
Seems strange to only happen by running K3B in Gnome.

---


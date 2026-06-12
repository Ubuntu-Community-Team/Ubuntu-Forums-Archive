---
title: "How can we logout inactive users in Gnome?"
date: 2007-02-07
forum: Desktop Environments
---

### Post by Macchi on 2007-02-07
We are looking for a solution to logout users after a given time period of inactivity on Gnome. It would be nice if anyone you could share their solutions for this simple use case.  

In many cases it is better to terminate the session and return to the main login screen. Observe that this does not exclude the ordinary "screensaver" and lock, but it would be a nice complement. For instance a mandatory policy for:

 1) Power-off the display after 5 minutes, 
 2) Activate screensaver after 8 minutes, 
 3) Logout the inactive user after 20 minutes. 


This is very useful and important for "hotdesks" and shared workstations/desktops in homes or offices, to avoid that distracted users would lock out a common resource. 
Manual rebooting is awkward and even undesirable, since it would interrupt all kinds of useful processes running in the background, such as automatic backup of home directories, etc.

I hope to find a good solution here. Forgetting to logout must be a very common daily situation and would be very useful for professional use of Ubuntu.

---

### Post by kevinlyfellow on 2007-02-09
Setup a user account that you would like the power management features for (for the ss, blank monitor) and just copy this to your new users forlder
```
 sudo cp -R ~/.gconf /home/newuser/
```
You probably want to change the permissions so they can't change the .gconf settings

I'm currently looking into idle logout...

---

### Post by kevinlyfellow on 2007-02-09
from [http://www.derkeiler.com/Mailing-Lists/securityfocus/focus-linux/2004-10/0021.html](http://www.derkeiler.com/Mailing-Lists/securityfocus/focus-linux/2004-10/0021.html)
> > So, my question:
> What are people using these days to log idle users out of their systems?

For shells that read /etc/profile (like bash, ksh, sh) append:
TMOUT=N
export TMOUT

(In Debian you can get away by putting TMOUT=N in /etc/environment).

If you use csh, tcsh, or any in the *csh family, then
edit /etc/csh.cshrc and add:

set autologout = 15 

---

### Post by Macchi on 2007-02-09
Thanks **kevinlyfellow** for your suggestion. 
Manually locking permissions at gconf is indeed a way to go, but I hope to find something at a higher level for Gnome. I hope there are mandatory policies for power management on a specific machine... 

The timeout for command shells can be useful, but in our case it would only apply for the elimination of spurious processes. None of out target users would ever get close to a CLI. The _Autolog_ package could be another solution, I will look at it. 

Our main application for idle logout is on graphical desktops, so I will also look at scripts around _gdm_ or _gnome.session_ or Xsession.options, or $HOME/.xsession (see man xsession). I will try to find a point to insert a gentle logout after some inactivity timeout.

There must be a simple and elegant solution within the linux space.  
Lets keep in touch!

PS: Ideally I would be proud to pursue the problem myself and hack a solution, but right now I can't manage it within a limited time and limited knowledge on the inner mechanisms within Gnome.

---


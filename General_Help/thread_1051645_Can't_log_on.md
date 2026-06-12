---
title: "Can't log on"
date: 2009-01-26
forum: General Help
---

### Post by Worp8d on 2009-01-26
Hi,

I recently installed a program ([VIPM]("http://jkisoft.com/vipm/")) onto my computer (Ubuntu 8.04.1, x64) and it has caused a problem which is preventing me from logging on.  When I try to log on I get an error saying
Your session only lasted less than 10 seconds.  IF you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

When I view the details it says

/etc/gdm: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit.d/all_ALL linked to /etc/x11/xinit/xinput.d/default.
mkdtemp: private socket dir: Perimssion denied.

Does anyone have any ideas as to what is going on and how I might fix the problem?

Thanks,
Glen

---

### Post by Worp8d on 2009-01-26
After trying to log on with using the failsafe GNOME session I get a different error message:

Please contact your system administrator to resolve the following problem:
Could not open or create the file "(null)"; this indicates that there may be a problem with your configuration, as many programs will need to create files in your home directory.  The error was "Failed to create file '/tmp/gconf-test-locking-file-32P1NU': Permission denied" (errno = 13)

and then the login stops and I'm returned to the login screen.

The failsafe terminal session will allow me to start the terminal but I don't know how to go about fixing this problem.

---

### Post by jimmythegeek on 2009-01-31
Couple of things come to mind, all in the nature of experiments.  Apologies in advance if this is insultingly basic or just plain wrong.  

Probably the least potentially wrecking would be to create a new user from the command line and see if you can log in with that user.  

Hitting CTL+ALT+F1 will take you to a command prompt login.  You can use your standard account there, and issue the command 'sudo useradd -m <newuseraccount>'

Then 'sudo passwd <newuseraccount>' and enter the new user's password.

Then hit CTL+ALT+F[7-10] to get back to a GUI login screen.  

If you can log in that tells you it's a session-specific problem and we can dig deeper from there.
--
The other experiments to try would be removing the package (if that's not a deal breaker) via 'apt-get remove VIPM', which should not be very risky; or changing permissions on the files flagged as part of the problem.  I don't like that last one, and suggest it only as a last resort.

---


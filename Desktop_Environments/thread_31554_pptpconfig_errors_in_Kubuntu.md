---
title: "pptpconfig errors in Kubuntu"
date: 2005-05-03
forum: Desktop Environments
---

### Post by jstreed on 2005-05-03
pptpconfig doesn't seem to work in Kubuntu 5.04


when running the program as root (as intended) I get the following errors:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


Fatal error: php-gtk: Could not open display in /usr/bin/pptpconfig.php on line 31





This, coupled with the recent update problems and Kopete being unable to accept incoming messages is seriously making me debate whether installing Kubuntu was a good idea.  I just don't want to go back to Unbuntu, gnome is nasty. 




 :-|

---

### Post by Xtreme it on 2006-10-18
I'm having the same problem in Ubuntu and currently searching for a solution. So, if you by any chances know how to solve it just place the How-To here.

By the little I searched, this is a problem with the user permisisons.
If I use the logged on user to open the application, the application opens with no problems, but states that it is meant to be used by root. If I open it using sudo (or gksudo) I get the same error as you.

Some pages ( as [1]("http://www.experts-exchange.com/Operating_Systems/Linux/Q_20762091.html") or [2]("http://www.ethereal.com/lists/ethereal-users/200309/msg00013.html")) direct the solution to the use of _xhost +_ but I don't think that it is the right solution. Previous to the distro upgrade pptpconfig worked well for all the users of the system.

Some more info would be nice from the people how already solved this issue.

---


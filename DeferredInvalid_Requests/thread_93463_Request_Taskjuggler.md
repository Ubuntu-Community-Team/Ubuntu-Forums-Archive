---
title: "Request: Taskjuggler"
date: 2005-11-22
forum: Deferred/Invalid Requests
---

### Post by greenrenault on 2005-11-22
Can we get Taskjuggler made available for Ubuntu?

[http://www.taskjuggler.org/](http://www.taskjuggler.org/)

Thanks!

---

### Post by MartinG on 2005-11-22
You can always install it via Klik, while waiting:

[http://klik.atekon.de/](http://klik.atekon.de/)

---

### Post by 23meg on 2005-11-22
The klik version seems to be waiting for approval at the moment. BTW, the app isn't in Dapper.

---

### Post by greenrenault on 2005-11-23
I found that using alien I could convert the rpm into a deb and install from there.

Instructions here on how to do this:
[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

Also taskjuggler requires libpng3 libraries to be installed.

Then to list the contents of the deb to find out what the program filename is use:
dpkg -c taskjuggler-kde_2.2.0_beta2-0.1_i386.deb

Which shows that TaskJugglerUI is the command to execute.
/opt/kde3/bin/TaskJugglerUI

Thanks for the above help!

---


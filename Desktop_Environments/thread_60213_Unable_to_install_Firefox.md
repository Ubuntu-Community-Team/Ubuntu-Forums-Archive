---
title: "Unable to install Firefox"
date: 2005-08-26
forum: Desktop Environments
---

### Post by ubuntunewbie on 2005-08-26
I recently installed Kubuntu and am trying to install the mozilla-firefox package. but kynaptic does not allow me to select the package for installation. I read that there is a security issue with this package
[http://www.ubuntulinux.org/usn/usn-149-1](http://www.ubuntulinux.org/usn/usn-149-1)
can anybody let me know whether this package has been discontinued?

Thanks for your time !

Kubuntu ROCKS !

---

### Post by kayas80 on 2005-08-26
try the following command from the terminal: -

sudo apt-get install firefox

---

### Post by k.ODOMA on 2005-08-26
[QUOTE=kayas80]try the following command from the terminal: -

sudo apt-get install firefox[/QUOTE]

I and I think a number of people are being met with this message:

Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate

Any ideas on what happened to the firefox package?

---

### Post by Freddy on 2005-08-26
Try "sudo apt-get update" then "sudo apt-get install firefox" from your terminal.

---

### Post by samwyse on 2005-08-26
[QUOTE=Freddy]Try "sudo apt-get update" then "sudo apt-get install firefox" from your terminal.[/QUOTE]
 It's sudo apt-get install mozilla-firefox, though I don't know why Kynaptic wouldn't let it install.

---

### Post by neroagent on 2005-08-27
The best thing to do is to head over to [www.brunolinux.com](www.brunolinux.com) and follow the instructions on his web page. It worked for me on Kubuntu.

---

### Post by c0rderr0y on 2005-08-27
the "extras" are currently broken until they are fixed you will have to wait.... ](*,)

---

### Post by ubuntunewbie on 2005-08-28
Firefox is available again now.

---

### Post by wspgeek on 2005-10-03
I'm seeing the same exact issues today.

I did a fresh installation of Kubuntu 5.04.  I manually edited the /etc/apt/sources.list to have kynaptic look a the other available sources. Ran kynaptic, refreshed the list of available updates, ran a upgrade-all, then rebooted.

Since then I've been unable to install many "extras", including Firefox.  And I've tried running apt-get from the CLI......nothing.

Any thoughts?

---


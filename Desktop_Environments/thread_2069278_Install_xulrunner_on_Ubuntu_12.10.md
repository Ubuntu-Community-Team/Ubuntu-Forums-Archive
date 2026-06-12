---
title: "Install xulrunner on Ubuntu 12.10?"
date: 2012-10-10
forum: Desktop Environments
---

### Post by Jack Kelly on 2012-10-10
I believe that I need to install xulrunner.  But I'm running 12.10.  When I try to install xulrunner-1.9.2 I get the following error:

```

jack@probook:~$ sudo apt-get install xulrunner-1.9.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xulrunner-1.9.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'xulrunner-1.9.2' has no installation candidate

```

Launchpad does have [xulrunner listed under 12.10]("https://launchpad.net/xulrunner/+packages") but there are no releases available yet.

Do I just need to be patient?

(Why do I need xulrunner?  To [allow Eclipse 4.2.1 to use SWT]("http://www.eclipse.org/swt/faq.php#browserlinux").)

---

### Post by albandy on 2012-10-10
In lauchpad I get this message:

There is no current release of this source package in The Quantal Quetzal. You can still report bugs, make translations, and so on, but they might not be used until the package is published. 

So you can try to install the 12.04 package.

---

### Post by Jack Kelly on 2012-10-10
Thanks for the very quick reply!

I tried to install [the .deb file for xulrunner-1.9.2 for 11.04 (Natty)]("https://launchpad.net/ubuntu/natty/amd64/xulrunner-1.9.2/1.9.2.28+build1+nobinonly-0ubuntu0.11.04.1") but Software Manager complained that there was an unresolved dependency (I couldn't find a version of xulrunner for a more recent Ubuntu release).

So instead I manually downloaded [xulrunner-10.0.2 from mozilla]("http://ftp.mozilla.org/pub/mozilla.org/xulrunner/releases/10.0.2/runtimes/"), extracted it to ~/opt/xulrunner and then added ```
-Dorg.eclipse.swt.browser.XULRunnerPath=/home/jack/opt/xulrunner
```  to my eclipse.ini file (as recommended [here]("http://www.eclipse.org/swt/faq.php#specifyxulrunner")).  This seems to work!

---

### Post by Jack Kelly on 2012-10-10
I've updated the Eclipse page of the Ubuntu Wiki:

[https://help.ubuntu.com/community/EclipseIDE#A.22Failed_to_create_a_browser_control_to_display_diff..22_error](https://help.ubuntu.com/community/EclipseIDE#A.22Failed_to_create_a_browser_control_to_display_diff..22_error)

---


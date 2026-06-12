---
title: "multiple browsers"
date: 2012-03-21
forum: Desktop Environments
---

### Post by Skaperen on 2012-03-21
People say I can have and run both Google-Chrome, and Firefox, at the same time (same user).  Well, that sounds nice.  But is there a way to do that with different versions of Firefox?  I'm on Ubuntu 10.10 waiting for Xubuntu 12.04 (so no system upgrade until then).

---

### Post by PhantomTurtle on 2012-03-21
You could try this - [http://odyniec.net/blog/2010/02/running-multiple-versions-of-firefox-in-ubuntu-9-10/]("http://odyniec.net/blog/2010/02/running-multiple-versions-of-firefox-in-ubuntu-9-10/"). It's for Ubuntu 9.10 but it looks like you could do it with 10.10 as well. Just make sure you change the version numbers of firefox to the ones you want rather than copying and pasting right from the site.

---

### Post by lovinglinux on 2012-03-22
Essentially, you can download any versions you want, extract them to your home and start them with the corresponding path, adding *-no-remote* and the profile name to the command, so each version uses a different profile. You can't start two instances of Firefox using the same profile.

If you want to make it simple get FoxTester extension:

[http://www.webgapps.org/add-ons/foxtester](http://www.webgapps.org/add-ons/foxtester)
[https://github.com/webgapps/foxtester/downloads](https://github.com/webgapps/foxtester/downloads)

---

### Post by Skaperen on 2012-03-22
> **lovinglinux said:**
> Essentially, you can download any versions you want, extract them to your home and start them with the corresponding path, adding *-no-remote* and the profile name to the command, so each version uses a different profile. You can't start two instances of Firefox using the same profile.

If you want to make it simple get FoxTester extension:

[http://www.webgapps.org/add-ons/foxtester](http://www.webgapps.org/add-ons/foxtester)
[https://github.com/webgapps/foxtester/downloads](https://github.com/webgapps/foxtester/downloads)
Is that doable with apt-get?

What I'd like to end up with after that is separate icon on the panel for each version installed.

---

### Post by Frogs Hair on 2012-03-22
Firefox current releases and Nightly worked fine together for me . I am currently using Nightly and Opera. Fox Tester is an add-on installed via Firefox. The different versions will be available on the Firefox menu.

To get icons for each browser and use them at the same time you may have to install them separately . See the first post or so in the Firefox 9 and beyond thread located in the sticky in Absolute Beginner Talk.

---

### Post by Skaperen on 2012-03-22
> **Frogs Hair said:**
> Firefox current releases and Nightly worked fine together for me . I am currently using Nightly and Opera. Fox Tester is an add-on installed via Firefox. The different versions will be available on the Firefox menu.

To get icons for each browser and use them at the same time you may have to install them separately . See the first post or so in the Firefox 9 and beyond thread located in the sticky in Absolute Beginner Talk.
Huh?  That forum was closed before there was Firefox 9.

---

### Post by Frogs Hair on 2012-03-22
The thread name has been changed to reflect the latest release . [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---


---
title: "Tried to uninstall but still shows up"
date: 2009-05-30
forum: General Help
---

### Post by emid on 2009-05-30
I recently upgraded to 9.04.  A while back before the upgrade I believe I installed an SVN snapshot of Ekiga.  Anyways, today I was playing with an Asterisk box I have running and I wanted to connect to it through Ekiga.  I didn't even remember that I had installed the SVN version so I went ahead and installed the version in the repos through Synaptic. I tried to run it and nothing happened.  I uninstalled it, but realized that Ekiga was still showing up in my application menu.  Then I remembered about the SVN installation. I went ahead and tried to remove it, but to no avail, it still remains in the application menu.  Also, if I type Ekiga on the command line it will start to run but then encounter errors.  Unfortunately if I try to uninstall it using apt-get, I get a response saying that Ekiga isn't currently installed.

I'm not really sure what to do.  I want to install the current repo version of Ekiga, but I don't seem to be able to without removing all traces of the other version that I cannot get off my system.

Any advice?

---

### Post by dcstar on 2009-05-31
> **emid said:**
> I recently upgraded to 9.04.  A while back before the upgrade I believe I installed an SVN snapshot of Ekiga.  Anyways, today I was playing with an Asterisk box I have running and I wanted to connect to it through Ekiga.  I didn't even remember that I had installed the SVN version so I went ahead and installed the version in the repos through Synaptic. I tried to run it and nothing happened.  I uninstalled it, but realized that Ekiga was still showing up in my application menu.  Then I remembered about the SVN installation. I went ahead and tried to remove it, but to no avail, it still remains in the application menu.  Also, if I type Ekiga on the command line it will start to run but then encounter errors.  Unfortunately if I try to uninstall it using apt-get, I get a response saying that Ekiga isn't currently installed.

I'm not really sure what to do.  I want to install the current repo version of Ekiga, but I don't seem to be able to without removing all traces of the other version that I cannot get off my system.

Any advice?

Installing things outside of the APT system means the APT system has no knowledge or control of them, you have to find the method **you** used to install it and use whatever uninstall procedure comes with it.

---

### Post by emid on 2009-05-31
I had a feeling about that but was hoping it wasn't the case.  If I re-download the source files can I remove it that way?

---


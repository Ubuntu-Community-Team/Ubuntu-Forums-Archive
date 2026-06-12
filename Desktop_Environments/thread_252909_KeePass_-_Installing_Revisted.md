---
title: "KeePass - Installing Revisted"
date: 2006-09-07
forum: Desktop Environments
---

### Post by lwsiv on 2006-09-07
Greetings,

I am a "coming over to the other side" long-time Fedora user. I have set up Keepass (latest) on at least 3 different version of Fedora, and have not had the issues I am having with Ubuntu.

After searching the forums and googling the web, I see that Ubuntu is not very KeePass friendly (installation wise) and I do not see any resolution to any of the queries associated with installing Keepass.

I am running Ubuntu Dapper and am trying to install the Keepass (XKeyPass 0.2.2 distro). I have installed them, as well as the QT Package (for Ubuntu) on the XKeypass site. I am getting the error loading shared libraries: libpng.so.3 error.

What is up? What do I need to install to get keepass working. I manage so many accounts that keepass is critical, and I will be forced to go back to Fedora, if I can't figure this one out.

Luke Stephens

---

### Post by croak77 on 2006-09-07
For your libpng.so.3 error, do you have libpng3 installed?

---

### Post by lwsiv on 2006-09-07
If you read the previous posts associated with Keepass installations, this is an issue somehow related to how Ubuntu repackages the Qt libs. libpng12 is installed from what apt-get tells me, however, I am guess libpng.so.3 is not a shared lib in that version. There was a lot of discussion around whether it is good mojo or bad mojo to retro install the older libraries (both Qt and libpng) to resolve this, but nothing was finalized in the posts I have found on google or this forum.

Not being a debianite, nor an Ubuntu-ite, I am reluctant to just go slamming libs around.

---

### Post by croak77 on 2006-09-07
There is libpng12 and libpng3 two differnent packages. libpng3 provides libpng.so.3.

Or use an older qt3 version

[http://home.arcor.de/tareks/keepass-0.1.3/keepass_0.1.3_i386.deb](http://home.arcor.de/tareks/keepass-0.1.3/keepass_0.1.3_i386.deb)

---

### Post by pt123 on 2006-09-16
Has anyone got it to work with wine?

---


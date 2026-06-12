---
title: "Matlab Install w/ Root Privilege Issues"
date: 2009-02-17
forum: General Help
---

### Post by Shwefty on 2009-02-17
Howdy,

I'm trying to install Matlab & Simulink Student Edition R2008b.  Now before the "use Octave!" replies start rolling in, I have to use Matlab for a class...but I agree.

Essentially I have a problem creating symbolic links from the GUI installer.

I start the install_unix.sh file (yes, it does install natively into linux).  Click Run - a GUI installer pops up.  I click a couple of yes's for the EULA and such, then it asks for a MATLAB root directory (any suggestions?).  I enter /home/username right now...because that's what I have rights to. It asks me what available software I'd like to install (which is everything available).

Then, it asks me about where it should install symbolic links.  The /usr/bin/local is not writeable because I don't have the proper permissions.  I'm not logged in as root (as I don't know how/bad idea), but would like to authorize this.

Is there some way to authorize a root action from GUI?  The installer doesn't prompt the standard Root Password request like is normal on standard updates and such.  I've tried all the sudo/su commands I could think of.

Thanks in advance

---

### Post by Cesaar on 2009-03-05
When running the installation file run it from Terminal:

```
cd /media/cdrom
```

```
sudo gksu ./install
```

---


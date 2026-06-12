---
title: "Upgraded to 11.04 Classic - Gnome panels broken?"
date: 2011-06-16
forum: Desktop Environments
---

### Post by jbuczek on 2011-06-16
I'm running 11.04 (64 bit AMD ) CLASSIC by upgrade from 10.10.

When I R-click on my gnome panels all I get is [Help,About Panels].  I cannot get [Add To Panel] and the other gnome panel options.

I created a new login and everything works fine there.  

Any clues?

P.S. No, I do not want to run Unity.  I have a lot of work to do and I don't have time to retrain for the sake of "eye candy" or "modernising". Automobile controls and keyboards don't need "modernising" either <G>.

---

### Post by jbuczek on 2011-06-16
Update: After reading a few things I tried:

sudo gnome-panel

I got these messages:

** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:2495): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:2495): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

and it hung, meaning I never got the CLI prompt back....

BUT........ the panels are fixed!
BUT........ only for the current session.  If I log out and back in I'm back where I started.

---

### Post by jbuczek on 2011-06-16
Up-Update: Sorry I should have tested more.

sudo gnome-panel 

fixed the problem with being unable to access gnome panel options such as "Add To Panel" but lost my main menu settings and pretty much all the launchers which I created don't work any more.  System created launchers work.

Log out and Log in still takes me back to where I started.

Guess I'll stay there until 11.10 unless someone knows what the h*** is going on here.

TIA

---

### Post by mcduck on 2011-06-16
Check that the panels aren't locked down through gconf.

Run "gconf-editor", browse to apps/panel/global and make sure the "locked_down" -option isn't enabled.

(by the way, running "sudo gnome-panel" sounds like rather bad idea... you definitely don't want to run your desktop apps as root, and even less through sudo which might result in your normal user's setting files becoming owned by root. Always use gksudo with graphical applications.)

---

### Post by jbuczek on 2011-06-16
That did it!  Thanks.

I didn't understand what the difference between "gnome-panel" and "sudo gnome-panel" would be.  I've run into lots of admin type apps that do one thing without sudo and unlock the useful stuff with sudo.  When I tried to run it without sudo it appeared to do nothing.

BTW - I believe you about gksudo for graphical apps but I remember things better if I understand why.  I've tried some things both ways and it doesn't seem to make any difference.

Thanks again!

---

### Post by mcduck on 2011-06-17
> **jbuczek said:**
> That did it!  Thanks.

I didn't understand what the difference between "gnome-panel" and "sudo gnome-panel" would be.  I've run into lots of admin type apps that do one thing without sudo and unlock the useful stuff with sudo.  When I tried to run it without sudo it appeared to do nothing.

BTW - I believe you about gksudo for graphical apps but I remember things better if I understand why.  I've tried some things both ways and it doesn't seem to make any difference.

Thanks again!

The difference is that sudo doesn't load the root user's environment variables correctly for graphical apps, and instead uses your own user accounts variables. So you end running tha application as root but using your normal user's configuration files. If you then change any setting, it well be written into your config files but as root, overwriting the config file and leaving your normal user without the permissions to alter the file any more.

It doesn't cause problems with every program, but simply learning the habit of always using gksudo with GUI applications is a lot easier than trying to find out and remember which apps work safe with sudo and which require using gksudo.

There is a similar issue when using command like "sudo su" or "sudo -s" in a terminal. The "safe" command for a root session is "sudo i".

For better explanation you might want to check Ubuntu's official root/sudo guide ([https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")), and this nice forum post: [http://ubuntuforums.org/showpost.php?p=6188826&postcount=4]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4")

---


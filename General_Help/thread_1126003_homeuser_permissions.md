---
title: "/home/user permissions"
date: 2009-04-15
forum: General Help
---

### Post by dhysk on 2009-04-15
In my infinite wisdom I managed to change the permissions of my admin account's home directory, and could no longer log into GNOME/KDE.  Fortunately I was able to get it back with chmod 644 on the .drmc and a chmod -R 755 on the /home/user directory.  

***(_NEW GUY INFO_: -R or -r in a command line is normally not a good idea -R or -r generally means recursive and used in combination with chmod, chown, rm, or rmdir could REALLY ruin your day!! more things to not do at this link: [http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54))***

Unfortunately now every single file is now executable.  Is this a major problem that needs fix or should I change the permissions again and only turn on executables as I get errors and such until everything works again?  I have made a tone of modifications to the 'standard 8.04' install and don't really want to start from scratch.  I'm not to fond of giving everyone executable rights within this dir.  

I initially was trying to restrict who could see the admin accounts folder in the first place, however I accidentally applied the new permissions to everything within the /home/user dir.

As a side note I would like to thank Linux for always making a good command shell available even though I couldn't log into my account with a graphical UI I was able to at least get up and running again....I love this OS!!  even though it gives me the power to 'break' things ;).

---


---
title: "Problmes updateing Firefox"
date: 2006-09-23
forum: Desktop Environments
---

### Post by beforewisdom on 2006-09-23
Hi;

A long time back I started with Ubuntu with the Breezy Badger release.  Updates for firefox were lagging so I followed a stick, here, in this forum, for manually upgrading firefox and integrating it into my system.

I have since upgraded my system to Dapper Drake.

This morning the update manager upgraded my firefox with no problems. 

I am still getting the OLD version coming up, even if I drop "firefox" into a command shell.

What should I check to undo this and turn firefox upgrades back over to Ubuntu?

---

### Post by crossedout on 2006-09-23
You'll need to edit your profiles.ini file to have it point to the path where your FF install is.  Just know that by doing that you may have to move your entire profile to that new location.  Having said that, as easy as it is to do, you may want to just create a new profile with profile manager and have it point directly to your new version of FF and import your bookmarks, etc.

-Xout

---

### Post by beforewisdom on 2006-09-24
I ran a "which firefox" command in my shell and saw that firefox the system was using was in /usr/bin

I ran a "ls -l /usr/bin/fire*" command and got listings for two symbolic links, one for "firefox" and one for "firefox.ubuntu".  The former being the old manual install back when Ubuntu was behind on firefox upgrades, the later being Ubuntus install location.

I changed the links so that the "firefox" link now points to Ubuntu's copy of firefox rather than my own.

---


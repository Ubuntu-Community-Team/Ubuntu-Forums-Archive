---
title: "Mapping Samba Shares in Nautilus - Username and Password?"
date: 2006-06-13
forum: Desktop Environments
---

### Post by DarkElf109 on 2006-06-13
The system I'm running relies on users being able to log into a Samba share with their own username and password from an icon on the desktop. In Windows and OSX, it's a simple matter: just map the drive, and they request the credentials. It used to be this same way for Nautilus, but for some reason, with Dapper, it no longer works as expected. If no user name is given when the share is mapped, when the user tries to access their folder on the share (individually access-controlled, while the main share is guest-enabled), Nautilus simply says that it couldn't display the folder contents. This is unacceptable, as the system is meant for use by people with little to no computer knowledge, and mapping the share every time they want to get to their folders is unacceptable.

From the research I've done, it seems that Nautilus isn't requesting login details for directory listings. What I'm wondering is, is there any way to reenable this? If not, are there any other solutions?

---

### Post by DarkElf109 on 2006-06-14
Well, in the interim, I've figured out a way to do it that's less then satisfactory, but it gets the job done. Since console access is disabled for the users, I wrote a C++/GTK application that gets the Samba username from the user, then calls Nautilus using a set of configuration options that emulate having the username pre-configured on the mapped drive. It's not the bext solution, but it works.

The proper way to do this, it would seem, would be to disable guest access in the root of the share. By doing this, Nautilus would never think that it could simply use guest access, and would ask for user credentials (including username) when trying to access the share.

---


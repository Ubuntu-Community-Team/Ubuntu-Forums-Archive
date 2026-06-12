---
title: "Problem with users logging in..."
date: 2009-04-28
forum: General Help
---

### Post by bmturney on 2009-04-28
Let me start by saying I'm fairly new to Linux.. I've messed around with it a little in the past... but now I'm administering an FTP server running on Ubuntu... 

I have setup an FTP server and I have set my users' home directory to be something other then /home/user.. they are actually pointing to a user specific directory but in a different directory... 

Anyway... When I try to log on as one of the users it isn't allowed to log on via FTP... the user gets a non descript permission denied or something... I had originally set the user to have a shell of /bin/false to prevent them from being able to log directly into the server (other than through FTP).  But while troubleshoot I changed one of my users to use /bin/sh

When I try to log in as this user, I get a message that says No Directory, Logging in with HOME=/

I've checked the permissions on the directory that is set as the home directory for the user and the user is the owner of the directory and the owner has RWX to the directory... 

Any ideas as to what my problem might be?  I'm running out of ideas, so any direction would be a great help.

Thanks

---


---
title: "Hard drive help"
date: 2009-03-10
forum: General Help
---

### Post by ThermoGel on 2009-03-10
I had ubuntu 8.10 server installed on a machine with a 120GB drive for the system drive and two 500GB drives for media files and personal files.  The one for media was formatted as ext3 and the other fat32.  Everything worked fine.  The motherboard on my main computer died, and while I wait to replace it I started using the computer that I had 8.10 server installed on as my main machine.  I wiped the 120GB drive clean and installed ubuntu 8.10 desktop and now I can only access the ext3 500GB drive if I use gksudo nautalis.  I have the drive mounted at:

/media/Media 

with the owner and group of that directory as user media.  I have myself in the group media.  As I said if I start nautalis with root permissions I can view the files on that drive, but with my logon I cannot.  In fact in a terminal window if I try

cd Media
from the /media directory I get a permission denied.

Looking for any help.  Thanks in advance.

---

### Post by taurus on 2009-03-10
What is the output of this command from a prompt (or terminal)?

```
sudo ls -la /media/Media
```

Maybe you have the permissions and/or group ownership all wrong.

---

### Post by ThermoGel on 2009-03-15
Hey thanks for the response.  I was away for a few days.  I am a total noob.  I thought that I gave full rwx permissions to everyone, but a look through my bash_history I only gave rwx permissions to the user.  Once again thanks for the help.

---


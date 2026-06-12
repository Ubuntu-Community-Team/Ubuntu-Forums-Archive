---
title: "Default Desktop"
date: 2009-07-24
forum: Desktop Environments
---

### Post by JeeperGeek on 2009-07-24
I would like to create a default desktop for all users who log on.  Desktop background, program startups, panels, etc.  Is this possible?  I'm running Ubuntu 9.04.

Best thing would be to copy one that is setup like copying a profile in Windows and putting it in the default profile.

---

### Post by s3MA00RRNY on 2009-07-24
The default profile folder is in /etc/skel. Everything in that folder is automatically copied to a created user's home folder. Hope that helps you get started. Most of the settings in Linux are hidden files that start with a dot. You'll probably want to copy some of those to /etc/skel.

---


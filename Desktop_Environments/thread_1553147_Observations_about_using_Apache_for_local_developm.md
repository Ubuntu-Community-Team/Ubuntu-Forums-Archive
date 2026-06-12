---
title: "Observations about using Apache for local development with virtual hosts in /home"
date: 2010-08-14
forum: Desktop Environments
---

### Post by shiftbit on 2010-08-14
FYI - if your reading this and having trouble getting virtual hosts to work which point to a location in your home folder, then maybe this will help.  Besides the various config files and their settings, my biggest headache was the folder permissions.  That has been what just spend the last few hours fighting with.  Basically, root will own the home folder, your user will own the [username] folder and then under there, you need to start assigning [www-data] as the group.

So say you have a folder path like so
/home/some-user-name-here/projects/mynewwebsite

notes:
- root will own /home
- start with /projects (and all the way down to your web root path) and assign [www-data] as the group with read access.

---

### Post by infamous-online on 2010-08-14
Yeah, I think I pulled my hair out, trying to use the default build for Apache by Ubuntu and said screw it. I formatted the drive and compiled apache from the source as I've always done, it gives you more control and more importantly less headaches. However, this info should be very useful for those using the default packages that come with Ubuntu.

---


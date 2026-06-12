---
title: "CHMOD problem, won't let me set permissions"
date: 2009-01-19
forum: General Help
---

### Post by jackmacnally on 2009-01-19
Dear all, 

i am a relatively new ubuntu user. much help would be appreciated!

i have a 250gb hard drive on my server in the loft running ubuntu server 8.10, that i wish to make into a backup drive for my pictures, music, etc. i understand that to make the 'backup' folder appear on the network, you have to 'share' it. fair enough, i can see it on my XP computer, but then it says 'you do not have permission to access this resource'. i go to my server, right click on the folder > properties > permissions tab. under the 'others' heading, i select create and delete files for 'folder access'. it waits about a second, then automatically reverts to '---'. it has done this time and time again, seemingly no matter what i do. 

please, if anyone could even possibly point me in the right direction, i would be very appreciative!

Jack Macnally

---

### Post by dcstar on 2009-01-20
> **jackmacnally said:**
> Dear all, 

i am a relatively new ubuntu user. much help would be appreciated!

i have a 250gb hard drive on my server in the loft running ubuntu server 8.10, that i wish to make into a backup drive for my pictures, music, etc. i understand that to make the 'backup' folder appear on the network, you have to 'share' it. fair enough, i can see it on my XP computer, but then it says 'you do not have permission to access this resource'. i go to my server, right click on the folder > properties > permissions tab. under the 'others' heading, i select create and delete files for 'folder access'. it waits about a second, then automatically reverts to '---'. it has done this time and time again, seemingly no matter what i do. 

please, if anyone could even possibly point me in the right direction, i would be very appreciative!

Jack Macnally

You will probably have to manually change the Samba configuration, you can search out HOWTOs or install tools to do this.

---


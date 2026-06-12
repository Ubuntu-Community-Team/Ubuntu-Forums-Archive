---
title: "Valid password don't work on locked screen"
date: 2014-10-27
forum: Desktop Environments
---

### Post by tom144 on 2014-10-27
One of our user made a Ubuntu 14.04 install with Ubuntu desktop (Unity) and choosed a local username that is the same as the persons username in our company database. As we want our users to login with the company username we removed the local user and it's home directory which was created under the installation. Now the user can login with his company user name without any problems. However when the desktop screen gets locked and he tries to unlock it with his password he gets the message that the password is incorrect even though it is correct. I don't know if it's the old user, which we removed, that still messes something up (for example the fact that the old username was the same name as the company username) or if it's something else . Here are some information about files that may have something to do with this:

-rw-------  1 <correct username><some group>    52 okt 27 11:53 .Xauthority

-rw-r----- 1 root shadow  728 okt 27 10:17 /etc/gshadow
-rw------- 1 root shadow  790 okt 24 13:28 /etc/gshadow-
-rw-r----- 1 root shadow 1114 okt 27 10:23 /etc/shadow
-rw------- 1 root shadow 1114 okt 27 10:17 /etc/shadow-

-rwxr-sr-x 1 root shadow 35536 jan 31  2014 /sbin/unix_chkpwd

As of my understanding all this files looks like they have the right ownership. Do anyone know what the problem is and what you can do to fix this?

Kind regards

---


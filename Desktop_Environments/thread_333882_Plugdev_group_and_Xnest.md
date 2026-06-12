---
title: "Plugdev group and Xnest"
date: 2007-01-08
forum: Desktop Environments
---

### Post by Tarkan on 2007-01-08
Hello,

I'm working with a system with many clients and users. All user information is stored in Ldap, so I don't have local accounts and groups (the groups like plugdev exist, but nobody belongs to that groups).

It would be great, if the user in front of the computer was able to mount usbsticks and so on by clicking on the icon, that appears, when you plug in the usbstick. I found a way to add the users who log in with gdm to the plugdev group by adding some lines in /etc/pam.d/ and in /etc/security/groups.conf. 

It works, but if someone is logged in and another user logs in with Xnest, both are in the plugdev group. If the user in front of the computer plugs in a usbstick for example, both users see the Icon and the one who clicks it first has access to the files. 

Of course, I would like only the user in front of the computer being able to do this. Is there any way to forbid mounting usbsticks or whatever, if someone is logged in with Xnest?

Thanks a lot!

---


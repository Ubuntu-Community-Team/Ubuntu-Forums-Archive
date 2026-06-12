---
title: "some help with samba + permission denied messages"
date: 2008-12-25
forum: General Help
---

### Post by geodeath on 2008-12-25
Hi!

I started setting up a samba share with the excellent guide here on ubuntu.
It missed the point where you have to use smbpasswd if you have encryption on but i found it from the samba checklist so the service seems to work fine. However, to setup the service, i created a user account, which is also the owner of the folder that is shared. This user is of course another account and not the account i use to use the ubuntu installation. 

To get to my point:
Having setup the owner as not me, i am having permission denied problems.
I am trying to download something in the shared folder with ktorrent and although it starts, some time later it gives me an error which is no other than permission denied. Also, trying to create a shortcut in my desktop to the shared folder, also gives me permission denied messages. I tried both using nautilus as is and using sudo, without success.

In fear of breaking my samba share, what do i need to do in order to give permission for my other account (the one i am using right now to type this), lets say "george"?

thanks!:guitar:

edit: i forgot to add that if i click on right click->properties of the shared folder i have setup the group sambashare to be able to create & read files & folders and also everyone else to read & write as well. the "george" user is also a member of the sambashare group..

edit no2: from what i can see i can access and read & write to the shared folder, but the ktorrent error still happens. After a small time downloading it gives permission denied errors.

---


---
title: "Problem with 2 ubuntu servers and Active Directory"
date: 2006-06-30
forum: Desktop Environments
---

### Post by countryboy on 2006-06-30
Hi, I have a problem with AD and ubuntu.

I have 2 ubuntu servers, one is running Breezy and the other is running Dapper.

They are both joined to my W2K domain and have the same smb.conf files and have been configured in the same manner. Users from my W2K domain are able to log on to both machines without any problems using their AD accounts.

Now, a user on the Breezy machine wants to mount his home folder on the Dapper machine. No problem...you would think.

The folder can be mounted but all the permissions are stuffed.

- on the actual Dapper machine permissions are user = <AD account>, group = Domain Users

once the folder is mounted to the Breezy machine, the file and folder permissions are now user = <somebody else's AD account or even a machine account, group = Domain Users

So, it seems that somewhere along the line the original permissions are changed to a different user.

I wondered if perhaps it was because on the Dapper machine the persons's AD account was given a certain ID (say 10000) and once this ID was translated to a user account on the Breezy machine, user 10000 was in fact a different user account? (I hope I am explaining myself clearly).

It always seems to be the same accounts that are given the incorrect permissions - eg on the Dapper server JoeSmith always ends up as TheReceptionist (in terms of the file of folder permissions), no matter if a different user account is used to mount that same user account.

Has anybody seen something like this before?

Thanks

---

### Post by countryboy on 2006-07-03
Hello??

I can't believe that no-one else has two ubuntu servers in an Active Directory domain :-?

---

### Post by countryboy on 2006-07-03
Ok, so I've figured out that the problem is that the UID's are different on each machine - when I log on ServerA using my Windows account, it creates a user and assigns it the uid of 10000 (for example). When I log on to ServerB it creates a user and assignes it the uid of 10001 (for example).

Then when I try and mount my home folder on ServerB from ServerA, it thinks I am a different user and gives the mounted files and folders the permissions belonging to the user account on ServerB that has the same uid on ServerA

So, that being the case, has anyone found a fix for this?

Thanks

---


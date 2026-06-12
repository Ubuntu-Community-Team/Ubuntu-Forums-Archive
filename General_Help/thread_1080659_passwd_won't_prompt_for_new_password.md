---
title: "passwd won't prompt for new password"
date: 2009-02-25
forum: General Help
---

### Post by Veyasu on 2009-02-25
I've added a user, but the "adduser" command didn't prompt for a password.

I saw a line when I ran the command before it started prompting me for the full name and all that, and it just said this:

> passwd: password update successfully

I tried doing **sudo passwd <username>** but that gave me the same result. Without prompting me for a new password it just returned **passwd: password update successfully**.

I tried switching to root using **su sudo**, with the same result.

Then I tried **usermod -p <password> <username>** using both sudo and as root, and it just completed with no returnmessage.

When I try **su <username>**, it asks me for the password. I tried blank, and I tried the password I specified with **usermod**, but no luck.

I really have no clue whatsoever what I'm doing wrong, and I tried googling for about an hour, and I didn't find anyone who's had a similar problem.

I'm running Ubuntu Server 8.10.

---

### Post by Veyasu on 2009-02-25
Sorry for bumping my own thread, but this is excruciatingly frustrating.

If its even remotely useful, heres some more info about my system.

The server is a virtual machine running on VMWare server 2.0 with an Ubuntu 8.10 host. It has LAMP, OpenSSH and Samba installed using **tasksel**. There are 2 other VM's on the host, both running Debian 5.0, which has no problems.

Anyone have any clue whatsoever as to what may be causing this?

---


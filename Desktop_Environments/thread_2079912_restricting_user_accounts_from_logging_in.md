---
title: "restricting user accounts from logging in"
date: 2012-11-02
forum: Desktop Environments
---

### Post by insidus on 2012-11-02
Hey,

At my university, ive been creating a LAMP server on Ubuntu Server 12.04. Every users has their own log in information so they can FTP into their OWN directory, and they have their OWN database to work from. But this has left me with a problem, i don't want any users to bee able to log into the physical machine, the desktop. I want to only allow the administrator to be able to log on.
I have disabled all users (except the admin) to log in via ssh, but i also need to remove them from the login screen on the actual server desktop, and stop them from being able to log in.

I don't have a massive ubuntu server experience, and any would be greatly appreciated!

thanks

-- insidus

---

### Post by insidus on 2012-11-02
Update on my post..

I managed to change the .profile file in the home directory for the user to automatically log them out when they log in, but there must be a more secure/better way of doing this?

-- insidus

---


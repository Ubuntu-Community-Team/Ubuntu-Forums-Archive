---
title: "Cannot start kstartupconfig?"
date: 2007-03-07
forum: Debian
---

### Post by Cloudy on 2007-03-07
Hi all,

Recently during my Operating Systems class, we installed Debian on a PC using a Knoppix Live CD. Some of the PCs in the lab already had Debian on them, others didn't. I sit at one of the machines that already had Debian installed, but I didn't have a user account on it. Anyway, after making a new account via the command "useradd" I can't log in to the user I created.

I'll walk you through what I did:

Booted into Debian. There was only one user account on it (from an install done by a prior class) so I pressed ctrl alt f1 to go into a virtual terminal and logged in as root in order to create a new account.

Did useradd <username> and changed the new user's password

then I went back to the login screen and refreshed X. However, whenever I try to log in with my new account I get a little popup error that says "Cannot start kstartupconfig." and I'm thrown back to the login screen.

Can someone help me? :)

---

### Post by AlanB_mg on 2007-12-19
I was loading KDE as  a second desktop on Ubuntu and had the same result. all I did was to load KDE via APT  instead of Synaptic and then altered the permissions of /home/user/.kde to 777 via CHMOD in a terminal hope this is of some use.:smile:

---


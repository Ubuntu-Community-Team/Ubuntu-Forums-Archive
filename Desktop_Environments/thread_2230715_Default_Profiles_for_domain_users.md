---
title: "Default Profiles for domain users"
date: 2014-06-20
forum: Desktop Environments
---

### Post by Zane_Youmans on 2014-06-20
Hey everyone! Feel free to move this thread to a different topic if someone has already done it, but I can't find anyone who has.

I am setting up some machines for a lab at my organization, and I have tied them to our domain so any of our domain users can log in. I want to make it so each new user who logs on gets a customized default profile (i.e. custom background with organization logo, set of programs pinned to start menu) instead of getting the original profile with the purple\orange background. I have tried making a new user account and customizing it to my liking and then changing the /etc/useradd.conf file to point to that users home directory. Every time a new user is made it will copy that custom profile for the new user so they will get the background and color setup. It works, but only for local users. I just want to know how to make the new domain user profiles pull from this custom profile as well. This is in Ubuntu 12.04

Thanks!
Zane

---

### Post by Zane_Youmans on 2014-07-07
Does this even make sense to anybody?

---


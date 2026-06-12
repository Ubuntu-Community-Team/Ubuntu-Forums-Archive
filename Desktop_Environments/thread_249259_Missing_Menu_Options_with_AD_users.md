---
title: "Missing Menu Options with AD users"
date: 2006-09-02
forum: Desktop Environments
---

### Post by ddoctor on 2006-09-02
Hi,

I recently set up my ubuntu 6 machine to log in to my win2k domain controller (using an article on this forum, which worked perfectly). 2 issues 

#1. When I ssh in as a domain user, then vnc, 3/4 of the menu options are missing from the System->Administration menu in Gnome.

Smeg doesn't list options for this menu. I tried Alacarte, which lists the options, but it doesn't bring them back.

I also tried blowing away the /home/(networkusername) folders, copying a local user's profile to /etc/skel, then logging in again with the network user... the hope was that pam_mkhomedir.so would give us the menu options... not to be.

I have these options:
- Device Manager
- Network Tools
- Printing
- System Monitor

I have a feeling I need to do something to my PAM stack, or make my Domain Users group a member of the local Users group (which I don't know how to do). Or, is this a filesystem permission issue?

Help would be greatly appreciated.

Cheers,

D Doctor

---

### Post by ddoctor on 2006-09-02
correction - 1 issue. :-\"

---

### Post by ddoctor on 2006-09-03
Anyone?

---

### Post by ddoctor on 2007-11-02
Also replicating in Gutsy. 
Might be a problem with /etc/skel

---


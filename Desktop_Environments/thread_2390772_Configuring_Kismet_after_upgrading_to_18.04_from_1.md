---
title: "Configuring Kismet after upgrading to 18.04 from 16.04"
date: 2018-05-02
forum: Desktop Environments
---

### Post by madbrido on 2018-05-02
[COLOR=#242729][FONT=Arial]I have the following error when the system is 'setting-up' kismet..[/FONT][/COLOR]
[B]
The provided user list contains invalid usernames.The users to be added 
to the kismet group have to be provided in a space-separated list of 
usernames. It seems that the following usernames are not valid: 
userOne. Please revise the list.
[/B]
[COLOR=#242729][FONT=Arial]Moreover, any installation/removal process is now stuck at this where I can only enter 'ok' but then I am back at the error message.

if I try for example 'sudo apt autoremove', I get "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem" --> which then generates the above issue over and over.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How do I solve this? I thought I could find a list with users but it is not the case, I don't know where it is taking this userOne username.[/FONT][/COLOR]

---

### Post by madbrido on 2018-05-02
Solved removing kismet with

sudo dpkg --remove kismet

---


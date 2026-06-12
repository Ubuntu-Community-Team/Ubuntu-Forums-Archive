---
title: "Can someone please paste me /usr/group"
date: 2005-05-20
forum: Desktop Environments
---

### Post by Xgkkp on 2005-05-20
In trying to add myself to the lp group, in an attempt to run ink-checking programs, I appear to have mistakenly wiped myself off of all other groups. (it seems usermod -G needs an exact list of groups). I noticed this when audio ceased to function.

However, I can't remember which groups that I should be on - would it be possible for someone to past /usr/group or to tell me which groups my user should be a part of?

---

### Post by nad on 2005-05-20
Please see the file /etc/group for all group names installed on your system.

The usermod command with the -G switch will make the user a member of only the groups listed in the command. The adduser command will add an existing user to an existing group.

---

### Post by Xgkkp on 2005-05-20
[QUOTE=nad]Please see the file /etc/group for all group names installed on your system.

The usermod command with the -G switch will make the user a member of only the groups listed in the command. The adduser command will add an existing user to an existing group.[/QUOTE]

yes, I know this... now. I used -G and now I am only listed in one group (well, and ausio because I manaully added it myself). My problem is, I don't know what groups I was originally in, and so I don't know which groups I should be in.

my /etc/group file is effectively empty - it has a list of groups but my user isn't on any of them, so I can't use it as a reference for what I'm supposed to be in.

---

### Post by nad on 2005-05-20
adm disk cdrom floppy audio video plugdev lpadmin scanner

Is my list from a warty install. You certainly do need to use the /etc/group file as a reference! Only you know what software and services you have installed that may require a group permission access.

---


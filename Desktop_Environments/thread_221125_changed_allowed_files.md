---
title: "changed allowed files ?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by chalkedup on 2006-07-22
basicaly i still have sudo but i think i have access to more files than i should?
i followed a how2 for a voyager 105 or 100 modem i think it was part of a wiki 
ive either lost the web page from my bookmarks or its been edited out since  
it told me to edit a file that i was supposed to change back afterwards that gave me more access to files?or something to do with sudo to make it easier but i cant remember/find what file i had to re edit back to the original as i had to do alot of other things to set it up ](*,) 

so i was wondering if theres any files that its likely to be so i can put them right? or do you know of the voyager modem instruction page 

sorry its so vague im pretty certain the original page was edited?
thanks

---

### Post by roostishaw on 2006-07-22
Might the file be /etc/sudoers ?
If so, edit it with:
```

sudo gedit /etc/sudoers

```

---

### Post by ardchoille on 2006-07-22
I was told it's always best to edit the sudoers file with 
```

sudo visudo

```
Is that not the case with Dapper?

---

### Post by chalkedup on 2006-07-23
thanks for that im not sure if that was it or not ? 
heres the output from that file
```
  GNU nano 1.3.10           File: /etc/sudoers.tmp

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


```

does that look right ?

---


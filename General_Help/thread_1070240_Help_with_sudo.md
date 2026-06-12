---
title: "Help with sudo"
date: 2009-02-14
forum: General Help
---

### Post by orc_dragoon on 2009-02-14
Everytime I try to use the sudo command. I enter my password and I get this

<username> is not in sudoers file. This incident will be reported.


How do I fix this?

---

### Post by RedSingularity on 2009-02-14
I am just curious.  I used to get the same thing.  Are you using KDE?

---

### Post by orc_dragoon on 2009-02-14
I just followed the text-mode install. So I don't know. How could i find out?

---

### Post by adult swim on 2009-02-14
you can add yourself to the sudoers file to avoid this error and be able to use sudo by booting  into recovery mode, going to a root terminal and enter in ```
visudo
```  then make sure it looks like this
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
USER    ALL=(ALL) ALL
# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
``` the part you are specifically interested in is ```
# User privilege specification
root	ALL=(ALL) ALL
USER    ALL=(ALL) ALL
``` you may have to add that last line there, changing USER to your username.  once you have made the changes, to save and close the file, hit ctrl+X, and then hit y.  when you reboot you should be added to the sudoers file.

---

### Post by RedSingularity on 2009-02-14
When you boot does it say Ubuntu or Kubuntu?

---

### Post by RedSingularity on 2009-02-14
Ahhhhh that reminds me.....I have to turn on adult swim and watch some superjail!  LOL

---

### Post by orc_dragoon on 2009-02-14
> **Shadow121 said:**
> When you boot does it say Ubuntu or Kubuntu?

ubuntu

---

### Post by RedSingularity on 2009-02-14
Oh your using the Gnome desktop then.  When i had the problem it was with the K desktop environment.  In any case just follow what adult swim is saying.  He knows what he's talking about.  :)

---

### Post by orc_dragoon on 2009-02-14
> **adult swim said:**
> you can add yourself to the sudoers file to avoid this error and be able to use sudo by booting  into recovery mode, going to a root terminal and enter in ```
visudo
```  then make sure it looks like this
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
USER    ALL=(ALL) ALL
# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
``` the part you are specifically interested in is ```
# User privilege specification
root	ALL=(ALL) ALL
USER    ALL=(ALL) ALL
``` you may have to add that last line there, changing USER to your username.  once you have made the changes, to save and close the file, hit ctrl+X, and then hit y.  when you reboot you should be added to the sudoers file.


Im confused with this. I typed that into the termal and I got the etc/sudoers, but what am I supposed to do then?

---

### Post by adult swim on 2009-02-14
if your username is orc_dragoon, youd want it like this
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
orc_dragoon    ALL=(ALL) ALL
# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by orc_dragoon on 2009-02-14
Well I accidently put in th wrong username and save and now I can't acess, so wwhat can I do?

---

### Post by adult swim on 2009-02-15
if you boot into recovery mode, and go to a root terminal, you shouldnt need a password and you should be able to change it from there with ```
visudo
```

---

### Post by orc_dragoon on 2009-02-15
Thanx. You solved my problem and I have many thanx for you

---


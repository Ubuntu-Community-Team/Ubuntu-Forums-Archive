---
title: "sudo command upon startup sessions"
date: 2008-03-06
forum: Desktop Environments
---

### Post by oddworld on 2008-03-06
I keep trying to run a single command at startup, but I am not having any luck:
```
sudo opendchub
```
So bar I have added: sudo opendchub into sessions. Didnt work.
Also edited rc.local to say:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo opendchub

exit 0



```

As well as sudoers.tmp

```
  GNU nano 2.0.6            File: /etc/sudoers.tmp                              

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

%username ALL=(root) NOPASSWD: /path/to/opendchub



```

All I want to do is run sudo opendchub upon startup, if I dont have the sudo then it does not allow the hub to run on port 411.
I may have done something wrong above, if so please let me know.
Thanks!!

---

### Post by tech9 on 2008-03-06
> **oddworld said:**
> I keep trying to run a single command at startup, but I am not having any luck:
```
sudo opendchub
```So bar I have added: sudo opendchub into sessions. Didnt work.
Also edited rc.local to say:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sudo opendchub

exit 0



```As well as sudoers.tmp

```
  GNU nano 2.0.6            File: /etc/sudoers.tmp                              

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

%username ALL=(root) NOPASSWD: /path/to/opendchub



```All I want to do is run sudo opendchub upon startup, if I dont have the sudo then it does not allow the hub to run on port 411.
I may have done something wrong above, if so please let me know.
Thanks!!

You need to use the root account to edit files such as these...

try this

```
sudo kwrite /etc.sudoers
```

then enter your root password and you should be able to modify the file

---

### Post by oddworld on 2008-03-06
I did, I ran the command as:
 sudo visudo

---

### Post by tech9 on 2008-03-06
so it does save your entries then?

---

### Post by oddworld on 2008-03-06
Yea, I typed it and rebooted and it was still there when I opened it up a second time.

---

### Post by tech9 on 2008-03-06
I see what you are trying to do. Is opendchub a program? Why don't you launch opendchub on start up through start up sessions

System>Preferences>Sessions

click add

type

gksu "/path to opendchub"

---

### Post by oddworld on 2008-03-06
This might sound strange, but I cant find where it installed to.
I am also not that comfortable with linux installations.
I know that in my home directory I found .opendchub with a few config files in it
Also in /etc I didnt find anything.
So where would be path be?

---

### Post by tech9 on 2008-03-06
Is the program in the accessories menu, or any menu for that fact? If it is, you want to right-click the application from the menu and select "add this launcher from desktop"

Then goto the desktop and right-click the icon > Select properties, and click the launcher tab.

Then select the information from the Command text box.

This is the information that you want to copy into the new session you create, when adding a new session.

I hope this helps.

---

### Post by YoG%*@ on 2008-03-06
hi,

> **oddworld said:**
> This might sound strange, but I cant find where it installed to.
So where would be path be?

```
 
which $commandname

```

shows where a command is located. 
so, in your case

```
 
which opendchub

```

should point you to its installation location.

hth, 
mux

---

### Post by oddworld on 2008-03-06
Wow thats a very useful command!
I SSH'ed into my home computer to look at the directory /usr/local/bin/ and saw opendchub
I suppose then that I could add this to one of the places suggested earler.
Thanks, when I get back home Ill check it out.

---

### Post by tech9 on 2008-03-06
> **mux said:**
> hi,



```
 
which $commandname

```shows where a command is located. 
so, in your case

```
 
which opendchub

```should point you to its installation location.

hth, 
mux


That is a pretty nice command.

You know what they say... you learn something new everyday ;)

---

### Post by kerry_s on 2008-03-06
well your doing it wrong.

first 1, rc.local is all ready running as root, don't need sudo.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

opendchub &

exit 0
```


the second 1

```
%username ALL=(root) NOPASSWD: /path/to/opendchub
to
"your-name" ALL=NOPASSWD: /path/to/opendchub

```
replace "your-name" with the name you use to log in.
%username would mean you created a "username" group, then added yourself to it.
but your "your-name" is got to be in there, look in /etc/group

here's a pic of mine "user" is my log in name.

---

### Post by oddworld on 2008-03-06
> **kerry_s said:**
> well your doing it wrong.

first 1, rc.local is all ready running as root, don't need sudo.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

opendchub &

exit 0
```


the second 1

```
%username ALL=(root) NOPASSWD: /path/to/opendchub
to
"your-name" ALL=NOPASSWD: /path/to/opendchub

```
replace "your-name" with the name you use to log in.
%username would mean you created a "username" group, then added yourself to it.
but your "your-name" is got to be in there, look in /etc/group

here's a pic of mine "user" is my log in name.

So change it to:
```
  davis ALL=NOPASSWD /usr/local/bin/opendchub 
```

Does my name need quotes or no?

---

### Post by kerry_s on 2008-03-06
you forgot the ":" after nopasswd
davis ALL=NOPASSWD /usr/local/bin/opendchub
to
davis ALL=NOPASSWD: /usr/local/bin/opendchub

---

### Post by oddworld on 2008-03-06
opendchub is still not starting under sudo
heres what I have got so far:

sudo visudo yields:

```
  GNU nano 2.0.6            File: /etc/sudoers.tmp                              

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

%davis ALL=NOPASSWD: /usr/local/bin/opendchub



```

and rc.local is:

```
  GNU nano 2.0.6             File: /etc/rc.local                                

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

opendchub

exit 0



```

and my system -> pref -> sessions says:

```
sudo /usr/local/bin/opendchub
```

But still, it is not working.
Any ideas?

---

### Post by kerry_s on 2008-03-06
drop the "%" not needed.
is the "opendchub" executable?

you also don't need it in both places, only 1. since you all ready have it in the session startup, remove the rc.local 1 & fix that "%" in sudoers.

---


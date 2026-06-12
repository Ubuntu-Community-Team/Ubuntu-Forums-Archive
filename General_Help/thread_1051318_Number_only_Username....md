---
title: "Number only Username..."
date: 2009-01-26
forum: General Help
---

### Post by dernsber on 2009-01-26
We use number only usernames at work, and i want to create one in an Ubuntu environment, but it won't let me:

"
User name has invalid characters

Please set a valid user name consisting of a lower case letter followed by lower case letters and numbers.
"

Is there a way to by-pass that error and get it to accept a numerical username?... Kubuntu and CentOS both allow this, just popping up a possible confusion error when you do that, but i want to use Ubuntu (still new to Linux and so far i like the default Gnome/Ubuntu gui the best)....

Thanks!

---

### Post by bodhi.zazen on 2009-01-26
How did you try to create a new user ?

When the gui tools fail, use the command line (& read error messages) :twisted:

> root@jaunty:~# **[COLOR=red]adduser 007[/COLOR]**
adduser: Please enter a username matching the regular expression configured
via the NAME_REGEX[_SYSTEM] configuration variable.  **Use the `--force-badname'**
option to relax this check or reconfigure NAME_REGEX or NAME_REGEX_SYSTEM.

root@jaunty:~# **[COLOR=green]adduser --force-badname 007[/COLOR]**
Allowing use of questionable username.
Adding user `007' ...
Adding new group `007' (1003) ...
Adding new user `007' (1002) with group `007' ...
Creating home directory `/home/007' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:



---

### Post by dernsber on 2009-01-27
Ok... 2 new problems....

1. not accepting the username i'm trying (007 worked, but 118576 is not...):

~$ sudo adduser --force-badname 118576  
[sudo] password for :   
Allowing use of questionable username.  
Adding user `118576' ...  
Adding new group `118576' (1003) ...  
Adding new user `118576' (1003) with group `118576' ...  
useradd: unknown group 118576  
adduser: `/usr/sbin/useradd -d /home/118576 -g 118576 -s /bin/bash -u 1003 118576' returned error code 6. Exiting.  


2. When i did add 007, i want to duplicate the permissions/groups that my other usernames have... i got it added into the Admin group, but it was missing some other permissions.  Is there a way to copy another user profile/setup, or even change that other users username is what i'm thinking...

And yes, command line, that's why i'm trying to switch to an Ubuntu system.... :D

---

### Post by dernsber on 2009-01-27
sweet.. figured it out.... usermod -l will let you change the login name... :D

THANKS!!!!!

---


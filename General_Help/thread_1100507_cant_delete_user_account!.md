---
title: "cant delete user account!"
date: 2009-03-19
forum: General Help
---

### Post by sdowney717 on 2009-03-19
yes I am the administrator super user.
the account became corrupted
I tried to delete it out of the user list
it always comes back
I removed the home folder of this user by using gksu nautilus and sent it to the trash

when i tried logging into the corrupt account, it always said
/.dmrc file ignored etc....
make sure owned by user and have 644 permissions

this was a test account but I want it out of the list
also when I was in root I could not open root trash?

sudo userdel -r [username]
scott@scott-desktop:~$ sudo userdel -r [tricia]
[sudo] password for scott: 
userdel: user [tricia] does not exist
scott@scott-desktop:~$ 
does not work

---

### Post by sdowney717 on 2009-03-19
well, I fooled it by
copying tricia2 to tricia in /home
then i went thru the remove user and group applet menu 
and it removed it, but it still would not remove from the terminal.
but it is gone,(I think)

---

### Post by fieroboom on 2009-03-19
In order to properly assess the situation, we need more detailed information, such as how you 'deleted it out of the user list'.
Was that in the graphical user panel?

If so, the best way to remove a user is to login as yourself, open a terminal and type:
```
sudo deluser <test_username>
```
That will remove the user from /etc/group, /etc/sudoers, etc, but won't remove the user's home directory, so once that's completed, run this:
```
sudo rm -rf /home/<test_username>
```

Be **very careful** with that last command, and type it ***exactly*** that way, except for substituting <test_username> with the username you want to remove. That command will remove the user's home directory.
Again, be very careful with sudo rm -rf. If you have any questions or are unsure about something, ask first before you run it, and I'll be happy to explain further.
:D
-Paul

---

### Post by sdowney717 on 2009-03-19
thanks, so where did the /home/tricia files go if I was using
gksu nautilus?
I can not see the trash in root using gksu nautilus, (folder contents cant be displayed) and the cursor is endlessy working there.

---


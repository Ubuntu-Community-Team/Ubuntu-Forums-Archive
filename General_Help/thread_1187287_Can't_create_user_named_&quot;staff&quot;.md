---
title: "Can't create user named &quot;staff&quot;"
date: 2009-06-14
forum: General Help
---

### Post by opus_az on 2009-06-14
I'm building Ubuntu computers for a non-profit group and they'd prefer to log on as "staff" like they do on their Windows computers, but Ubuntu won't let me add a user with that name.

Is there some way that's not too convoluted, and wouldn't confuse someone else working on these computers if I'm not there, to add a user named "staff"?

---

### Post by BZF on 2009-06-14
[SIZE=1][COLOR=Blue]when you first put ubuntu on the computer and then you have to enter a name, name it "staff"[/COLOR][/SIZE]

---

### Post by opus_az on 2009-06-14
Oh, OK. I already have a few computers with updates and software and printers, etc. Can I do it after the initial install?

---

### Post by ddrichardson on 2009-06-14
Yes, System->Administration->Users and Groups or from the command line with ```
useradd staff
```
Its in the system help: [http://is.gd/11Mmm](http://is.gd/11Mmm)

---

### Post by MaxIBoy on 2009-06-14
Run the command:
```
sudo adduser staff
```
The adduser program will prompt you for a password and so on.

Then, run the command: 
```
sudo usermod -a -G admin staff
``` (Don't forget the -a or -G!)


Then, run this command:
```
sudo visudo
```
You will be given a file to edit. Make sure you see a line somewhere in the file like this:
```
%admin ALL=(ALL) ALL
``` (If there is no such line, add one.)

---

### Post by opus_az on 2009-06-14
I think the trouble is a group named staff (gid 50) is automatically created during install.

If I add a user "staff" in Users and Groups from the Administration menu I get an error "User name "staff" already exists".

If I do useradd staff I get an error "group staff exists..."

Should I just add my staff user to the existing staff group (useradd -g)? Any bad repercussions?

---

### Post by opus_az on 2009-06-14
I edited /etc/adduser.conf so USERGROUPS=no so new users (added with adduser) are added to group "users" (gid 100).

I guess in hindsight I could have also:
 - done a useradd -g 100 staff
 - added the staff user in the Users and Groups window and changed the 'main group' setting on the advanced tab to Users.


Thanks, all!

---


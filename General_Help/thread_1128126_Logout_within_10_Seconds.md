---
title: "Logout within 10 Seconds"
date: 2009-04-17
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-17
i accidently use the rm -r cd /home/suresh.. after i restart my system go to the Fail safe mode..it is logout the 10seconds..Your session only lastd less than 10 seconds if u have not logged out yourself, this could mean that there is some instalation problem or that maybe out of diskspace. Try logging in with one of the fail safe session see if you can fix this problem
This process is currently running setuid or setgid. i got this error message... how to recover this problem

---

### Post by iponeverything on 2009-04-17
chock this up to a learning experience. 

If you were not superuser, odds are that you only nuked your primary account, not a big deal.  

- Boot single user mode.
- Create a account with different name from the command line.
- Add that new user to the admin group from the command line.
- reboot and log in as the new user.

---

### Post by kirsis on 2009-04-17
Restart computer. Enter the GRUB menu and choose the recovery option for the kernel you use.

When prompted with a menu, choose to "drop to root menu"

Type ```
adduser suresh
```

It will ask you a couple of questions. Answer them.

Then type ```
adduser suresh admin
``` to add this user to the group that can use 'sudo'.

This will reinitialize the user 'suresh', though your files and folders will be lost.

After all this, type ```
exit
``` and resume booting as normal.

---


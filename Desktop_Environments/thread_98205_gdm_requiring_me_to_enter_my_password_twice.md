---
title: "gdm requiring me to enter my password twice"
date: 2005-12-02
forum: Desktop Environments
---

### Post by stevea1210 on 2005-12-02
When I log into my ubuntu file server,  I have to enter my password twice.  I get no error in between the two password prompts, and after entering the password the second time, it does let me in.  If I log in with a domain account, this doesn't happen.  It only happens logging in with the one and only local account.  

process:
enter username 
hit tab or enter
enter password
hit tab or enter
password box pops right up again
enter password
hit tab or enter
login goes through.

Any ideas why this is happening?

---

### Post by Xian on 2005-12-02
I would first search [Ubuntu Bugs](http://bugzilla.ubuntu.com/). However, I have seen this method posted as working for this type of issue:


Create a new user account, logged into the new user account. 
Log out of the user account and log back into the original account.
Log out and reboot.

---

### Post by stevea1210 on 2005-12-03
Thanks xian,  I searched bugzilla unser a few search terms and didn't find any related issues.

I tried your suggestion on creating the new account.  When I logged in with the newly created account, I had to put my password in twice again.  When I logged out of the new account, and back in with the original account, dual password again.

After a reboot, still have to enter the pasword twice. :(

---

### Post by flopsy on 2005-12-03
Log out, go to a console with Ctrl-Alt-F2, log in and enter
```
rm -irf /tmp/orbit-yourusername
```

Logout with Ctrl-D. Alt-F7 will bring you back to the login screen.

It may do the enter-password-twice thing one more time, but it should fine after that.

---

### Post by stevea1210 on 2005-12-04
thanks flopsy, unfortunately that didn't work either.

Dropping to a console I had to enter my password twice.  After making a backup of /tmp/orbit-<user> and deleting it, I went back to gdm, logged in with the dual passwords.

Logged out, back in, dual passwords again.

Did a reboot and still had to enter the password twice.

Two other bits of info:
The new user I created in response to xian's post also has to enter the password twice.  Also I only have to enter my password once when I ssh into the box.

---

### Post by stevea1210 on 2006-01-15
I fixed this issue.  Turns out it was user error.  I had a typo in one of my pam.d configs.  For the record the word PASS has two S's in it.  Go figure.

---

### Post by Draaku on 2006-10-09
which file did you edit? I am having the same problem.

---

### Post by stevea1210 on 2006-10-14
The error I had was a typo in the pam.d/sudo file.  I had entered "pas" instead of "pass".  It took me a while to figure out it was a simpole typo.  I know you have posted on the thread about joining a box to AD, and it was during that process that I made my typo.  I would suggest very carefully looking at all of the pam.d files you edited manually and confirm that there isn't an error in any of them.

---

### Post by Draaku on 2006-10-16
thanks stevea, your reply prompted me to look in the right place:
Here is what I saw/did.
```
fg32@ucc123:/etc/pam.d$ ls
atd                 common-auth~          common-session~    groupmod  sudo
chage               common-auth.bak       cron               login     useradd
chfn                common-pammount       cupsys             newusers  userdel
chsh                common-password       gdm                other     usermod
common-account      common--password      gdm-autologin      passwd
common-account~     common-password~      gnome-screensaver  ppp
common-account.bak  common--password.bak  groupadd           samba
common-auth         common-session 
```

your comment on me trying to add this comp to our domain started me to think. I noticed the files with the ~ on the end and realized these were backups of the originals when I tried joining to the domain, so I simply backed up the originals and then renamed the ones with the ~ back to the original, no more prompt for password twice! thanks for the help.

---

### Post by oxygenws on 2006-10-21
to sovle this problem, edit /etc/pam.d/common-auth file and add "try_first_pass :)
=====================================================
auth     sufficient     pam_ldap.so
auth     required       pam_unix.so nullok_secure **try_first_pass**
=====================================================

---


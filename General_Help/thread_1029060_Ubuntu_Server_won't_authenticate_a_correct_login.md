---
title: "Ubuntu Server won't authenticate a correct login"
date: 2009-01-03
forum: General Help
---

### Post by joshd2189 on 2009-01-03
I have ubuntu server 8.10 installed on an old computer and messed around enough to prevent me from logging in with my username/password from anywhere (ssh/samba/or by booting up the server directly).  The only access I have is through the root shell in the boot recovery console.  I am confident that the user/pass is correct because when I type them correctly, I just get looped back into the login prompt with no error.  However, if I type it in incorrectly, I get a "Login incorrect" error.

This problem came after I rebooted after editing cups.conf so that I could have admin privs from another computer on the network.  I am not 100% sure what I did, and not sure what other information to provide, so just let me know.

oh and i already repaired all packages and updated and upgraded, and removed cups to no avail..  nor have i had any luck finding anything remotely similar on google.

thanks in advance for any assistance.

---

### Post by LateNiteTV on 2009-01-03
login as root and do the following:
```
passwd *username*
```
this will allow you to change the password.

you didnt delete the account did you?

you can check to make sure the acct is still there by:
```
cat /etc/passwd | grep *username *
```

---

### Post by joshd2189 on 2009-01-03
yup, I know that my username is in the /etc/passwd file and I have already taken the step of making a new password for my user.  I even made a password for root (shame on me) and the same thing happens when I use those credentials to log in (ie root).  When I type in a username/password that is listed in the /etc/passwd file, it simply asks me for my user id and pass again with no error message.  If I type in a user/pass thats not listed in the /etc/passwd file, I get a login incorrect..

---

### Post by joshd2189 on 2009-01-03
still havent been able to allow users to login.  I have added new users and they are unable to login.  when I run the following command from the root recovery console I get a segmentation fault after I have entered the password:
```
login username
```


from /var/log/messages (I had to hand copy)
```

selinux: disabled at boot
apparmor: apparmor initialized
....
operation="profile_load" name="/usr/sbin/cupsd" name2=default pid=3479
...
kernel: ecryptfs: unrecognized option 'rw'
kernel: ecryptfs: unrecognized option 'user=josh'
kernel: padlock: VIA PadLock not detected
sudo: pam_sm_authenticate: Called
sudo: pam_sm_authenticate: username = [josh]
sudo: Error attempting to parse .ecryptfsrc file; rc = [-5]
sudo: Unable to read salt value from user's .ecryptfsrc file; using default
sudo: Passphrase key already in keyring
sudo: There is already a key in the user session keyring for the given passphrase.
```

what do i make of all this?

btw, reinstalling is not an option b/c I have no access to a working cdrom and i cant boot from usb/network on this old computer.

---

### Post by joshd2189 on 2009-01-04
yay found the source of the problem and fixed it :).

[HTML]https://bugs.launchpad.net/ubuntu/+source/samba/+bug/260687[/HTML]

---


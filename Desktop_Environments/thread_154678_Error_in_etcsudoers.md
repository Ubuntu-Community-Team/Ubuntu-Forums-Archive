---
title: "Error in /etc/sudoers"
date: 2006-04-03
forum: Desktop Environments
---

### Post by phil66 on 2006-04-03
Ubuntu Breezy 5.10

Installed Firestarter firewall when I started app had to enter password.

Searched forum and found thread to  edit /etc/sudoers

added "username all=nopasswd:  /etc/firestarter" to end of file

Firestarter will not start getting error message

"syntax error line 24" "parse error in /etc/sudoes line 24"

Tried to open file /etc/sudoes and getting the same error

Should ALL=NOPASSWD: been in upper case

How do I correct this error as I cannot enter file with apps to remove what I have entered

Many thanks for your help
Ray

---

### Post by taurus on 2006-04-03
To edit /etc/sudoers, you need to use visudo!!!
```

sudo visudo

```

---

### Post by phil66 on 2006-04-03
Taurus

Sudo visudo returns the same error message as does sudo

Tried different editors they return same error messages

Have also tried changing permissions and it returns the same error message

Is there a way to remove line without opening file??

Thanks for the reply
Ray

---

### Post by taurus on 2006-04-03
If you're completely unable to use sudo, then you need to boot your machine with the LiveCD and mount your harddrive somewhere, like /mnt.  Then, edit your /etc/sudoers...  Otherwise, I see there is no way to edit or remove anything in /etc/sudoers without ever being root!!!

---

### Post by phil66 on 2006-04-04
Taurus

Sorry for the long delay.

Tried the live cd but I did not quite understand how to mount harddrive.

Booted to recovery mode as root and used nano editor to remove script I had inserted earlier. Made corrections to /etc/sudoers and /etc/sudoers.tmp.

I am now able to use sudo. I am still wanting to bypass the password in Firestarter.

According to your previous thread I should use sudo visudo to enter file then add "username ALL=NOPASSWORD: /etc/firestarter" is this correct?

Thanks for the help
Ray

---

### Post by carlosqueso on 2006-04-04
EDIT--I need to read everything before I post...DOH!

---

### Post by elamericano on 2006-04-04
That's why I always create a root password. Then I su root whenever I need to edit /etc/sudoers.

You spelled PASSWD wrong. Your entry should be:
username ALL=NOPASSWD: /etc/firestarter

Remember that sudoers won't work if the permissions aren't 440. So, remember to change it back if you change it for editing. It's best not to change it in the first place. I edit as root in vi and force write with :w! Then I test the change in another terminal window before exiting root.

---


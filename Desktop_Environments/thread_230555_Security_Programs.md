---
title: "Security Programs"
date: 2006-08-06
forum: Desktop Environments
---

### Post by magnoliablossom on 2006-08-06
Okie dokie...I have my system almost set up exactly like I want it and only have one more thing I need to address.  What kind of security programs do I need?  I have kids that like to download a lot of stuff and I send a lot of email.  Specific programs would be a great a help.  Thanks in advance!

~* Ash *~

---

### Post by x64Jimbo on 2006-08-06
Security in Linux is basically a given. If you give each child a user account, all of your information will be secure. Make sure that you log out each time you leave the computer, and you should be OK. All programs (inc. saved passwords, cookies, etc, will be different for each account) should save their settings like passwords and history in their home directory which is similar to Documents and Settings in Windows. 
Just make sure you log out each time you're done using your computer and you'll be fine.
Also, since you're using Linux now, most of the stuff they download will not work, and will not affect your system in a negative way. Even if they do manage to run Windows binaries in a Wine environment, it will be confined to their home directory as mentioned previously. They can't destroy your system like they could in Windows.

---

### Post by ardchoille on 2006-08-06
I recommend the following apps:

rkhunter - Checks for rootkits
chkrootkit - Checks for some rootkits that rkhunter doesn't check for
tripwire - An intrusion detection system


If you have other user accounts on the system, I recommend adding yourself to the wheel group and then doing the following:

```

sudo chown root:wheel /bin/su && sudo chmod 4750 /bin/su

```

What this will do is make it so that normal users, except the administrator, cannot sit there all day long and repeatedly call su to try and brute force the root password.. they'll simply get a "permission denied" error instead of a password prompt.

Remember: Security in Linux is an ongoing process, not a destination.

---


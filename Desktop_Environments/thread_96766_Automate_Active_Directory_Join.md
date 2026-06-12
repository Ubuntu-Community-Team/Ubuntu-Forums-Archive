---
title: "Automate Active Directory Join"
date: 2005-11-29
forum: Desktop Environments
---

### Post by thegnark on 2005-11-29
Is there an existing tool, or has anyone made a wizard to automate configuring and joining a machine to a Active Directory domain? A nice little GUI would of course be superb.

Now, whenever I need to put a machine on a domain, I have to follow a whole series of steps including installing a few packages, modifying some config files and attacking the command line with several attempts to establish connection.

If such a tool does not exists, might anyone have a programming itch to create one? Let the wiki be your guide: [https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto]("https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto")


This would solve one of my major hurdles in deploying more Ubuntu machines. Now if someone can just tell my how to get sudo to recognize %domain\linuxadmins as a valid group (yes, it appears in `groups`).

---

### Post by thegnark on 2005-11-30
bump

---

### Post by thegnark on 2005-12-01
no commentary? no one willing to attempt it? i don't know enough about glade/gtw/whatever to do the interface. maybe i'll work on the backend if i get some spare time at work...

---

### Post by lordeldor on 2005-12-01
Ok I just saw your post on slashdot, not an ubuntu user however. But maybe I can try and help with your issue.... First off a few questions. Are you trying to use the wild card %domain, are you using the short name,  or are you using the FQDN?
Which version of Samba is in the repository?
Also what version kerberos...
What is the exact command you are trying to use w/ sudo?

Oh and mabe even the config file for sudo would be helpful

---

### Post by thegnark on 2005-12-02
**My group (the important one): **TERAMEDIA\linuxadmins
**Sudo line:** %TERAMEDIA\linuxadmins ALL=(ALL) ALL
**Samba version:** 3.0.14a-6ubuntu1
**krb5-user version: **1.3.6-4
**krb5-config version: **1.6
**Sudo command: **Any

---

### Post by lordeldor on 2005-12-02
This is improper, in a typical /etc/groups file you can only use a-z A-Z  - . and _

Dose your groups file actually have a \ in a group name?
Was this a hand edit? Or did you use groupadd/gui equivalent?
Now what you need to have functioning is pam/kerberos. To be honest the kerberos groups should be relevant in the sudoers file as soon as pam recognizes them...You shouldnt need an entry in groups as far as I know.

However a workaround can be to add your user to the local wheel group, and uncomment  
# %wheel        ALL=(ALL)       ALL
in the sudoers file.....


I know I know thats an extra step, and you were looking for automation. But I am not that quick with code, and I can only attempt to ofer any information I have. Check into the Pam and  Kerberos docs, and you may find gold about kerberos groups and pam.




 
Also, from the ubuntu page you referenced, you added to /etc/pam.d/sudo

auth sufficient pam_winbind.so
auth sufficient pam_unix.so use_first_pass
auth required   pam_deny.so

@include common-account

This should make sudo aware of your domain usernames, try ditching the domain prefix, and just use the username in the sudoers file....

---

### Post by thegnark on 2005-12-02
**Dose your groups file actually have a \ in a group name?**
Yes, it's pulled from active directory. And so you see, I have pam/kerberos enabled (I wouldn't be able to authenticate on the machine without using a local account).


[B] Also, from the ubuntu page you referenced, you added to /etc/pam.d/sudo
[/B]Below is my /etc/pam.d/sudo```
 #%PAM-1.0

@include common-auth
@include common-account

auth sufficient pam_winbind.so
auth required pam_unix.so use_first_pass
```

I'm not a pam/kerberos/ad/authentication expert so i'm grey in this area (and mostly followed the guide, trying to understand where i can).
I have tried including just my username in sudo and it didn't work. Below is the result of `users`:
TERAMEDIA\taylorg TERAMEDIA\taylorg TERAMEDIA\taylorg

I thought it might have to do with "\t" being an escaped tab, so I escaped the slash with no avail. Let me knwo if you need anymore info.

Thanks for your help so far!

---

### Post by stevea1210 on 2005-12-02
I have several ubuntu machines joined to my 2k3 domain.  If you are using \ as your winbind seperator, and not the default +, try putting the group name in quotes.  There have been times I have had to do that in other areas due to the interpratation of \ in linux.

---

### Post by thegnark on 2005-12-02
**New sudo line:**
%"TERAMEDIA\linuxadmins" ALL=(ALL) NOPASSWD: ALL


```
TERAMEDIA\taylorg@C-000013:~$ sudo vi /etc/crontab
Password:
TERAMEDIA\taylorg is not in the sudoers file.  This incident will be reported.
```

The very fact that I got prompted for a password (when NOPASSWD: was specified) demonstrates the system doesn't (a) recognize the group or (b) recognize me as part of the group (which `groups` definately demonstrates I am).

I added the windbind seperator line with a "+" (since it was non-existant) and re-logged in (now as teramedia+taylorg). I modified sudo to reflect the new seperator (with no quotes) and it worked like cake!

One down, more to go :( Thanks everyone for your help.

---


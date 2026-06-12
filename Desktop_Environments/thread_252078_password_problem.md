---
title: "password problem"
date: 2006-09-06
forum: Desktop Environments
---

### Post by danielfretto on 2006-09-06
I am fairly new to Ubuntu. I'm running Dapper Drake.  I'm duel booting along side XP pro.
I recently disabled the need for a password on startup for both root and user.
Now when i need to enter my passwords to update or run synaptic or even change to root, the system doesn't recognize the old passwords.
Ubuntu does boot fine with no password.
How do I recover passwords?
Any help would be much appreciated.

---

### Post by taurus on 2006-09-06
Boot into recovery mode (from GRUB menu) and at the prompt, type

```
passwd john
(assuming john is your login name...)
```

---

### Post by danielfretto on 2006-09-07
i assume you wanted me to type that commond into a terminal window after rebooting into recovery mode.

BTW there were two selections in grub menu that had (recovery mode) after.

i chose the first.  at the end of the boot i had to hit Ctrl D.

here's what the terminal looked like:

d@shedd:~$ passwd d
Changing password for d
(current) UNIX password:
passwd: Authentication failure
d@shedd:~$

any auggestions?

---

### Post by danielfretto on 2006-09-07
Boot into recovery mode (from GRUB menu) _and at the prompt, type_

what do you mean by at the prompt?

when recovery boot prompts me to hit Ctrl D i am unable to type text.  i did it anyway and hit enter with no success.

before this password glitch when in user mode and installing applications through terminal i've been prompted to enter password.  when i have typed the password the text does not show in terminal.  it took some figuring out to realize the terminal was actually recognizing the text. again this was before this password problem.

---

### Post by Ramses de Norre on 2006-09-07
Do it in recovery mode, that'll give you a root shell and you wont need the current passwd then.

If you can't find the recovery mode do this: In grub go to the line of your most recent kernel and press 'e', then go to the line starting with 'kernel' and press 'e' again, then delete the words "quiet splash" and add "single" at the end.
Press enter and then 'b' to boot into recovery mode.

---

### Post by danielfretto on 2006-09-07
edited "kernel" line to end with word "single" and booted as suggested.

passwords still won't work for update or synaptic.

any further suggestions?

i will be intermitently at the pc today and will apply any suggestions at earliest convenience.  

thanks a bunch for helping out.

---

### Post by danielfretto on 2006-09-07
d@shedd:~$ passwd d
here is what happened in terminal in recovery mode.

Changing password for d
(current) UNIX password:
passwd: Authentication failure
d@shedd:~$ passwd root
passwd: You may not view or modify password information for root.
d@shedd:~$ sudo passwd d
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts
d@shedd:~$ sudo passwd root
Password:
Sorry, try again.
Password:

---

### Post by Ramses de Norre on 2006-09-07
Do you get a root shell?? So something like this:
```
**root**@hostname:~**#**
```
You should get that when booting with the "single" option..

---

### Post by danielfretto on 2006-09-08
after editing grub lines OS boots into normal user:

d@shedd:~$

---


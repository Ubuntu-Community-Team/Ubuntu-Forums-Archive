---
title: "Help with adduser"
date: 2009-05-22
forum: General Help
---

### Post by Panterix0r on 2009-05-22
Hi, 
how to create user without promt password and chfn??
example:

ubuntu-desktop # adduser user_test
ubuntu-desktop # 

thank!

---

### Post by gradysghost on 2009-05-22
Not sure I understand.  Do you wish to know the command line parameters so that all aspects of the adduser command can be included at once without any additional prompting?  Or do you wish to create an account with no password?  No *nix system will allow you to create a user without a password.  There's this thing called security that we're all pretty proud of, and that means that accounts get passwords, especially administrative ones.

However, if your desire is the first option, you might find that adduser doesn't have a parameter for password.  You can also try manually editing the groups file.  Still, adduser is probably the easiest way to do this on the CLI.  Otherwise, you can use the System -> Administration -> Users and Groups program.

---

### Post by Panterix0r on 2009-05-22
> **gradysghost said:**
> Not sure I understand.  Do you wish to know the command line parameters so that all aspects of the adduser command can be included at once without any additional prompting?  Or do you wish to create an account with no password?  No *nix system will allow you to create a user without a password.  There's this thing called security that we're all pretty proud of, and that means that accounts get passwords, especially administrative ones.

However, if your desire is the first option, you might find that adduser doesn't have a parameter for password.  You can also try manually editing the groups file.  Still, adduser is probably the easiest way to do this on the CLI.  Otherwise, you can use the System -> Administration -> Users and Groups program.

yes, i wanna to create by command line and parameters without any additional prompting

---

### Post by unutbu on 2009-05-22
Is this what you are looking for?
```
% sudo useradd --create-home --user-group --password pea --comment "Sweat Pea" --shell /bin/bash pea
% getent passwd pea   # show /etc/password entry
pea:x:1003:1004:Sweat Pea:/home/pea:/bin/bash
% getent group pea    # show /etc/group entry
pea:x:1004:
```

---

### Post by Panterix0r on 2009-05-22
> **unutbu said:**
> Is this what you are looking for?
```
% sudo useradd --create-home --user-group --password pea --comment "Sweat Pea" --shell /bin/bash pea
% getent passwd pea   # show /etc/password entry
pea:x:1003:1004:Sweat Pea:/home/pea:/bin/bash
% getent group pea    # show /etc/group entry
pea:x:1004:
```

oooo yes,

thank you very much!!!

---

### Post by trench.me on 2009-05-22
Why not use Guest Sessions? As long as you have 8.10 or higher you're good to go. 

Some more information [here]("http://beginlinux.wordpress.com/2008/10/04/ubuntu-810-beta-video-using-guest-session/") & [here]("https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount").

IMHO, Guest Sessions is probably one of Ubuntu's most underrated features. The short story: it creates a temp user inside the /tmp/ directory and completely removes the user upon logout. If you want to keep the Guest Session open just use the User Switcher applet to login to your normal acct and leave the guest open in the background.

Awesome stuff.

Many uses.

---

### Post by unutbu on 2009-05-22
Warning: I just realized that "--password pea" makes the encrypted password equal to "pea". It is literally the string put in /etc/shadow. That means typing "pea" as the password at a login prompt won't work. 

I don't have the solution off-hand. I think you might need to install the mcrypt package, find the command to encrypt "pea", and insert that encrypted string into the useradd command...

PS. It's a pity I don't know how to spell "Sweet" properly...

---

### Post by trench.me on 2009-05-22
I suppose I should have refreshed the thread before posting that, eh? :D

---

### Post by unutbu on 2009-05-22
Okay, I think I have it sorted:

A correct command would be:
```

sudo useradd --create-home --user-group --password $(mkpasswd -s -m md5 2peasNpod) --comment "Sweet Pea" --shell /bin/bash pea
```

This creates a user named "pea" with password "2peasNpod".

---


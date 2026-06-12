---
title: "Can't log in!"
date: 2005-05-05
forum: Desktop Environments
---

### Post by Termina on 2005-05-05
I control+alt+f2, so I can try my xorg.conf w/o interrupting my current X session.

The problem is, it keeps telling me my password is wrong!

What's up with this, and how can I fix it?

---

### Post by nad on 2005-05-06
These may be silly questions, but, where are you going to try your new conf file without interupting X and what keeps telling you that your password is wrong?

---

### Post by lorap on 2005-05-06
hi friend, maybe my question's silly then forgive me, but don't you have your capslock turned on?

---

### Post by Termina on 2005-05-06
Nope, don't have caps on.

The login window (command line) is giving me the password-incorrect message.

I can log in fine with username/pass, but not in the command line.

---

### Post by lorap on 2005-05-06
donno what to say...
i did login many times in terminal window but never had such kind of problem.
i'm completely sure you did everything right,it's probably some kind of a bug.
report ubuntu about it.it'd be nice of you to do that so new newbies would be happier to not encounter this difficulty.

---

### Post by nad on 2005-05-06
This is strange. Have you changed any permissions in your file system other than in /home? Can you switch users in a terminal window then log back in as this user?

I can only suggest that you create a root password and try to log in as root.

---

### Post by Professor X on 2005-05-06
Does your /var/log/messages contain any relevant error messages?

---

### Post by Termina on 2005-05-06
I've tried giving root a password, and no go.

/etc/passwd has /bin/bash as the shell (thought maybe it was a /bin/false issue).

I finnally added a new user (with a short, 5 digit password... all numbers).

My user/root pass were set to the same (9 digits, random number and letters. contained an asterick).

Changing the user that couldn't log in password to the 5 digit one worked.

---

### Post by crazybill on 2005-05-07
Typical reasons for not being able to log in:
1. using wrong username although password is being typed correctly
2. CAPS lock on when typing password.
3. misstyping password
4. typing in wrong password.
5. already logged in
6. finger laying on key too long adding more than one key stroke.
7. key not fully hit down.
8. other keyboard error (some key not recording correctly)

---

### Post by bored2k on 2005-05-07
You could have simply made a root password with the Ubuntu installer disc. It's as easy as *something creative*

[http://ubuntuguide.org/#gainrootwithoutlogin](http://ubuntuguide.org/#gainrootwithoutlogin)
[http://ubuntuguide.org/#gainrootinstallcd](http://ubuntuguide.org/#gainrootinstallcd)

---

### Post by Termina on 2005-05-07
[QUOTE=crazybill]Typical reasons for not being able to log in:
1. using wrong username although password is being typed correctly
2. CAPS lock on when typing password.
3. misstyping password
4. typing in wrong password.
5. already logged in
6. finger laying on key too long adding more than one key stroke.
7. key not fully hit down.
8. other keyboard error (some key not recording correctly)[/QUOTE]

Hey, did you read my post?

The password was entered in correctly, the fact that I could log in after every restart proves that.

Being logged in already shouldn't be a problem:

ulimits -a and /etc/security/limits.conf shows that my max logins are unlimited (or, atleast, no specific limit).

As I said, not a keyboard error. When changing the password to something under 8 chars, it works.

---

### Post by Termina on 2005-05-07
[QUOTE=bored2k]You could have simply made a root password with the Ubuntu installer disc. It's as easy as *something creative*

[http://ubuntuguide.org/#gainrootwithoutlogin](http://ubuntuguide.org/#gainrootwithoutlogin)
[http://ubuntuguide.org/#gainrootinstallcd](http://ubuntuguide.org/#gainrootinstallcd)[/QUOTE]

I mentioned above that I did create a root password (I could log in /w GDM, but not when I switched to ctrl+alt+f#).

It didn't work with the same password my user had (I set it to that), until I changed it to under 8 digits.

---


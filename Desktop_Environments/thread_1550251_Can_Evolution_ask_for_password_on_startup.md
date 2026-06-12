---
title: "Can Evolution ask for password on startup?"
date: 2010-08-10
forum: Desktop Environments
---

### Post by alex_dc on 2010-08-10
Hi,

I was wondering if Evolution had an option to ask for a password every time it started, similar to the way Outlook operates (and I don't mean when you are trying to send/receive mail, I mean when the application first starts). I am moving a user from Windows to Ubuntu and she was wondering if this function could be retained. I didn't see any option in the standard preferences.

Thanks in advance!

---

### Post by Zimmer on 2010-08-10
Do you mean the password for her email  pop or iMap server?
If so, you need only set the preferences to check for mail every N minutes and you will be prompted for the password as soon as Evolution starts....

---

### Post by alex_dc on 2010-08-10
Nope. I mean as Evolution (the program) first starts itself, not the first time it retrieves mail. When Outlook first starts it asks for a password. If you can't enter the correct password Outlook will close itself, keeping unauthorized users from reading your mail.

---

### Post by jcolyn on 2010-08-10
Gnome keyring will do what you want.

Once the account(s) are set up the first time you send and receive mail it will ask for a password both pop and smtp. Gnome keyring will pop up and ask for a password (a new password not the mail password)

Now when you start evolution it will ask for your keyring password and will remember your account(s) password..

---

### Post by Agent ME on 2010-08-11
> **alex_dc said:**
> If you can't enter the correct password Outlook will close itself, keeping unauthorized users from reading your mail.
Why should an unauthorized user even be able to get onto your account in the first place? Each user should have their own account on the system, or have access to a guest account.

---

### Post by alex_dc on 2010-08-11
> **Agent ME said:**
> Why should an unauthorized user even be able to get onto your account in the first place? Each user should have their own account on the system, or have access to a guest account.

Not necessarily. The box is a home computer and everyone uses the same account as, aside from the e-mail, they have no reason to have multiple accounts. In fact it would become rather burdensome to have multiple accounts as each family member is constantly accessing files of the others.

I'm guessing there isn't any way to do this aside from changing the permissions on the executable and setting gksudo to ask for a seperate password on execution. Not really a "secure" fix, but it would probably be enough for low-level competency users.

Then again, even if I did the above, Evolution would execute as root rather than the user, wouldn't it? I guess there isn't any way to solve my issue.

---


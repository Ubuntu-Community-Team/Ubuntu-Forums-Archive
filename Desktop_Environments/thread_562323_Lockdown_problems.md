---
title: "Lockdown problems"
date: 2007-09-28
forum: Desktop Environments
---

### Post by DrNick on 2007-09-28
Hi all

Not entirely sure this is on the correct part of the forums, but here we go.

As an IT admin type person, I've been having a go at trying to lock down GNOME somewhat for use in a school environment.  I've been playing about with GConf and it's associated tools as per the GNOME S.A.G, however I have one problem.  Whenever I set mandatory prefs, (i.e. users can't change them), it applies them to admin users too!  That's just silly, I must be doing something wrong?

Any ideas very much appreciated.  Cheers.

---

### Post by DrNick on 2007-09-29
Bump!  :)

---

### Post by Wicca on 2007-09-29
I am not sure what you did change using gconf-editor, but to my understanding you can only change the settings of the current profile (yours), or am I wrong?

If you want to setup a standard user profile with restrictions, have a look at sabayon:

```
sudo apt-get install sabayon
```

Sabayon provides a sane way to edit GConf defaults and GConf mandatory keys:
the same way you edit your desktop.

Sabayon launches profiles in an Xnest window. Any changes you make in the
Xnest window are saved back to the profile file, which can then be applied
to user's accounts.

---

### Post by DrNick on 2007-10-01
Sounds good, I'll give that a try.  Cheers!:)

---


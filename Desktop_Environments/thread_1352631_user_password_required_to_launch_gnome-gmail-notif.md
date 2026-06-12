---
title: "user password required to launch gnome-gmail-notifier"
date: 2009-12-11
forum: Desktop Environments
---

### Post by osx on 2009-12-11
I installed gnome-gmail-notifier. It works great, but after I restart the computer and launch it, it prompts me for my ubuntu user account password. Not the gmail password, as I have that stored, but the password of the account being used to launch it. I'm trying to launch it from the same account I installed it.

I check the permissions on the /usr/bin/gnome-gmail-notifier file it is set to root:root with 755 permissions.

Any ideas why I need to keep providing my computer password to launch it and how I can change that? I would like to make the program start at boot.

Thanks.

---

### Post by Physical Hook on 2009-12-11
```
%admin ALL=NOPASSWD: /usr/bin/gnome-gmail-notifier

```Add it to /etc/sudoers and it shouldn't ask you for a password anymore.

---

### Post by osx on 2009-12-12
> **Physical Hook said:**
> ```
%admin ALL=NOPASSWD: /usr/bin/gnome-gmail-notifier

```Add it to /etc/sudoers and it shouldn't ask you for a password anymore.

Thanks. I tried that but it didn't work. I didn't explain the problem I am having very well. The problem I am actually having is the same as what has been posted here [http://ubuntuforums.org/showthread.php?t=1335243]("http://ubuntuforums.org/showthread.php?t=1335243").

However, nobody has ever posted a fix at the reference link.

Attached is a screenshot of what happens.

---

### Post by Boondoklife on 2009-12-12
While this is not secure, you can get this to work by changing the default keyrings password to "" (Empty).

This can be done in the passwords and encryption keys section, but this is a big security risk and especially for machines that have multiple logins. This is the only way I have gotten everything to work without being prompted.

---

### Post by osx on 2009-12-12
> **Boondoklife said:**
> While this is not secure, you can get this to work by changing the default keyrings password to "" (Empty).

This can be done in the passwords and encryption keys section, but this is a big security risk and especially for machines that have multiple logins. This is the only way I have gotten everything to work without being prompted.

That's what I was afraid of as that seems to be the only solution I have seen posted for this problem with other applications.

Hopefully there will be a fix for this in future versions of Gnome or a fix through Ubuntu itself.

---

### Post by Boondoklife on 2009-12-12
I really don't think this a gnome or ubuntu issue, sounds more like an issue as to how the applications use the keyrings.

Really you only run into this if you use auto-login, which is a no-no for security anyways!

---


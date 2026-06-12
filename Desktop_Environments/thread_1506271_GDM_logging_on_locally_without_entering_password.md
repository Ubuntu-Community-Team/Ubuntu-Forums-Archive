---
title: "GDM: logging on locally without entering password?"
date: 2010-06-10
forum: Desktop Environments
---

### Post by trusktr on 2010-06-10
Any idea how to log a user in without a password in GDM?

I've found this archived thread but it doesn't appear to do anything when I tried what it says:
[http://ubuntuforums.org/showthread.php?t=12777&page=2](http://ubuntuforums.org/showthread.php?t=12777&page=2)

I'm not looking for auto-login. I'd simply like one user to be able to click on his name and it will log in without prompting for a password.

Thanks!

---

### Post by kerry_s on 2010-06-10
adminstration-> users & group

but, after the last update using it makes the panels take forever to load.

---

### Post by towheedm on 2010-06-10
Set automatic login.  Click on Administration => Login Screen and set the user to be automatically logged in after x seconds.

Oops.  Just read the last part of the post.  There is a way to set a null password for a user.  Search the forums, it's there somewhere.

---

### Post by trusktr on 2010-06-15
> **towheedm said:**
> Set automatic login.  Click on Administration => Login Screen and set the user to be automatically logged in after x seconds.

Oops.  Just read the last part of the post.  There is a way to set a null password for a user.  Search the forums, it's there somewhere.

Hey, thanks Kerry_s, but when i tried this, it didn't work! User and Groups would show "password: not asked at login" but it would still ask me.

Turns out that with my distro (Arch Linux) they have forgotten a line in /etc/pam.d/gdm that tells PAM to skip the password requirement for users who are in the "nopasswdlogin" group:

```

# The following line allows users to log in via GDM, without entering their password, if they are in the nopasswdlogin group. Make sure this comes before the first pam_unix line (needs confirmation)!
auth            sufficient      pam_succeed_if.so  user ingroup nopasswdlogin

```

But yeah, I also noticed that after i fixed it the panels were taking ridiculously long to appear!... They still take the same amount of time to load, but for some reason they won't pop out for a long time. I was able to deduce this because i have compiz enabled with shadows for my panels, so i could see the shadows sticking out from the edges of the screen until the panels finally popped out. 

I'm filing a bug at gnome.org!

---


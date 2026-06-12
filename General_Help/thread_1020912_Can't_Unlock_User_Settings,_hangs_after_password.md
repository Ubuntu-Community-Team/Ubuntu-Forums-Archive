---
title: "Can't Unlock User Settings, hangs after password"
date: 2008-12-24
forum: General Help
---

### Post by nLinked on 2008-12-24
If I go to System, Administration, Users and Groups, and click on the Unlock button (because I need to change some permissions on my account), it asks for my password.

I know I am entering the correct password and although I think it accepts it, the window "Users and Groups" just freezes there. After 20 seconds or so, an error message comes up saying **Could not Authenticate. An unexpected error has occurred**.

I have searched some threads with this error but can't find a working fix. I am able to install programs and use the sudo command with my password just fine by the way. And my user is the first and only user on Ubuntu (Ibex).

---

### Post by Mrs Twaddle on 2008-12-28
i'm having this problem too.

oo this worked for me

[http://ubuntuforums.org/showpost.php?p=6415534&postcount=12](http://ubuntuforums.org/showpost.php?p=6415534&postcount=12)

---

### Post by nLinked on 2008-12-28
Thanks, just tried this and even restarted but same problem :(

---

### Post by randallecook on 2008-12-28
The Users and Groups application is called users-admin. From a terminal you could try this: 'sudo users-admin'. This should launch the app already in superuser mode so you won't need to unlock anything. Hopefully that will allow you to bypass the problem.

Randall

---

### Post by nLinked on 2008-12-28
> **randallecook said:**
> The Users and Groups application is called users-admin. From a terminal you could try this: 'sudo users-admin'. This should launch the app already in superuser mode so you won't need to unlock anything. Hopefully that will allow you to bypass the problem.

Randall

Thanks. Now this works better but if I look at the console window, it gives the following error a number of times:
```
(users-admin:6513): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

```

And ends with this:
```
** (users-admin:6513): CRITICAL **: Unable to lookup session information for process '6513'
```

In the User and Groups window, if I click on my username and then Properties, and then the User Priviliges tab, I can't change anything. It's greyed out tick boxes. The Unlock button in the main window was unlocked however.

There must be something wrong with my installation (Ubuntu 8.10). What could it be? I want to be able to change permissions this way. I could before, don't know what messed it up.

---

### Post by Richard J Moore on 2010-04-05
I had this problem on Karmic. None of the posts seemed to address my  problem then I discovered that when the desktop locks I am sometimes left with the Fn key of my T61p locked. Shitf+Fn unlocks Fn and normal typing resumes.

Anyone using an IBM or Levono laptop with the Fn key might his this.

Occasionally I hold the shft key down too long and the accessibility options kick in, but these are usually accompanied with the popup asking for confirmation that they will be activated.


Richard

---


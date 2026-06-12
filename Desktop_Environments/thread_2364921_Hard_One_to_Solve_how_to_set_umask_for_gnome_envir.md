---
title: "Hard One to Solve: how to set umask for gnome environment in 17.04?"
date: 2017-06-29
forum: Desktop Environments
---

### Post by greg2lapa on 2017-06-29
In the past, I could always set umask at ~/.profile. But in Ubuntu 17.04, this no longer works.

Does anyone know how to change the umask value (which is 022 by default in 17.04) so that documents created in gnome-session using gedit get a different umask?

---

### Post by TheFu on 2017-06-29
17.04 is too new for me, but did you try ~/.bashrc - assuming bash is your shell.  If some other shell has been selected, then you need to use the init file for that specific shell.  

Of course, this assumes a normal login shell is being used.  That might not be the situation if some odd method is being used.

---

### Post by sisco311 on 2017-06-30
I don't fully understand what magic happens when you start an X session, but according to the /etc/X11/Xsession.d/55gnome-session_gnomerc file, ~/.gnomerc is sourced if you are running the GNOME session. So I would try to set it there.

You can try to add the umask command to ~/.xsessionrc if you want it to apply to any x sessions you start.

---

### Post by Morbius1 on 2017-06-30
It's interesting to note that this doesn't happen in Xubuntu 17.04 where the default umask is 0002. Even if I were to install gedit a new file is saved as 664. This seems to be a Gnome thing or at least some part of gnome that Xubuntu doesn’t use.

I had to install ( VBox guest )  Ubuntu 17.04 to verify your symptoms. 

If I find anything actually useful I'll post back.

---

### Post by greg2lapa on 2017-06-30
> **TheFu said:**
> 17.04 is too new for me, but did you try ~/.bashrc - assuming bash is your shell.  If some other shell has been selected, then you need to use the init file for that specific shell.  

Of course, this assumes a normal login shell is being used.  That might not be the situation if some odd method is being used.

Yes I tried ~/.bashrc. And it works if I create doc in nano or vi. But as I said in my OP, I'm looking for a fix for gnome-session when using gnome apps like gedit.

> **sisco311 said:**
> I don't fully understand what magic happens when you start an X session, but according to the /etc/X11/Xsession.d/55gnome-session_gnomerc file, ~/.gnomerc is sourced if you are running the GNOME session. So I would try to set it there.

You can try to add the umask command to ~/.xsessionrc if you want it to apply to any x sessions you start.

Already tried all this before posting.

> **Morbius1 said:**
> It's interesting to note that this doesn't happen in Xubuntu 17.04 where the default umask is 0002. Even if I were to install gedit a new file is saved as 664. This seems to be a Gnome thing or at least some part of gnome that Xubuntu doesn&#8217;t use.

I had to install ( VBox guest ) Ubuntu 17.04 to verify your symptoms. 

If I find anything actually useful I'll post back.

664 is respecting the default umask. In Xubuntu, have you tried changing umask in ~/.profile, say to 077. Then create a new doc in gedit. Do you get permissions of 600 (rw - - - - - - - )?

---

### Post by steeldriver on 2017-06-30
Is your display manager lightdm? if so, I wonder if the "right" way to do it is to add a pam_umask entry to the /etc/pam.d/lightdm file?

```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
auth    optional        pam_kwallet.so
auth    optional        pam_kwallet5.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
#session required        pam_loginuid.so
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
session optional        pam_kwallet.so auto_start
session optional        pam_kwallet5.so auto_start
session required        pam_env.so readenv=1
session required        pam_env.so readenv=1 user_readenv=1 envfile=/etc/default/locale
[COLOR=#0000ff]session optional        pam_umask.so umask=0002[/COLOR]
@include common-password

```

(I also can't test on 17.04 at the moment - sorry)

---

### Post by Morbius1 on 2017-06-30
> 664 is respecting the default umask. In Xubuntu, have you tried changing  umask in ~/.profile, say to 077. Then create a new doc in gedit. Do you  get permissions of 600 (rw - - - - - - - )?                 
Yes I have and yes it does. Xubuntu does exactly what you would expect it to do which is why I said this seems like a Gnome / Unity thing.

[COLOR=#0000cd]**EDIT:**[/COLOR]
Adding [COLOR=#0000ff]session optional        pam_umask.so umask=0002 to [/COLOR]/etc/pam.d/lightdm does not work for me in Ubuntu, Nor does creating a file at /etc/profile.d/umask.sh and setting umask to 0002 there.

---

### Post by TheFu on 2017-06-30
If true, this a sev-1 critical bug, IMHO. If I "login" then a login shell and all that entails should be involved. I think the gnome people are wrong.

[https://bugzilla.gnome.org/show_bug.cgi?id=736660](https://bugzilla.gnome.org/show_bug.cgi?id=736660)

Seems some others have noticed this issue: 
[https://unix.stackexchange.com/questions/254378/how-to-set-umask-for-the-entire-gnome-session](https://unix.stackexchange.com/questions/254378/how-to-set-umask-for-the-entire-gnome-session)

---


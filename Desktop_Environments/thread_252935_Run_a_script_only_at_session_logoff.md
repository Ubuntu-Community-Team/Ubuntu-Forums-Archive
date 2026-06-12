---
title: "Run a script only at session logoff?"
date: 2006-09-07
forum: Desktop Environments
---

### Post by celticmonkey on 2006-09-07
I working on a problem that involves running a script when a user logs into a gnome session and another when the user logs out. The first part is easy. Just add it to the session start up list. The last part I can't figure out. Any hackers got a tip for me?

Added difficulty: it's not the same script for all users of the system.

---

### Post by skymt on 2006-09-07
[COLOR="Silver"]Do you want a quick hack, or an elegant one?[/COLOR]

EDIT: Forget that, I came up with something better than the quick hack I had before. For each user that needs their own logout script, make a script at ~/.xsession. It should start by running 'gnome-session' (do NOT use exec). Follow that with any post-logout code you need to run. Then, from GDM, log in with the System Default session.

This is all assuming you don't need to run anything graphical or interactive from these scripts. It gets harder if you do.

---

### Post by celticmonkey on 2006-09-07
Thanks Skymt. I think that's what I've been looking for. If my scripting works out I'll share it with everyone.

---

### Post by ebash on 2006-09-08
Another solution is to add the code into the file:
/etc/gdm/PostSession/Default

This has the advantage that only one single file needs to be updated. Although if the users are using remote stations to login this approach will not work.

---

### Post by Balau on 2008-06-14
> **ebash said:**
> Another solution is to add the code into the file:
/etc/gdm/PostSession/Default

This has the advantage that only one single file needs to be updated. Although if the users are using remote stations to login this approach will not work.

I need to point out that the Default script runs with root privileges, but the $USER and $HOME variables are still the ones of the user that logged off. Using these variables I did something like that:

```

logoutscript="$HOME/.gdmlogout";
if [ -x "$logoutscript" ] ; then
  su $USER -c "$logoutscript"
fi

```

You can also use $USER to do something different for each one.

---


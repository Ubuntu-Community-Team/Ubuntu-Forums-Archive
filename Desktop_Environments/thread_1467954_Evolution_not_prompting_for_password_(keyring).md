---
title: "Evolution not prompting for password (keyring?)"
date: 2010-05-01
forum: Desktop Environments
---

### Post by summentier on 2010-05-01
I have installed Ubuntu three times now, and I'm running into same problem all the time, both with Karmic Koala (9.10) and now also Lucid Lynx (10.04):

When I configure Evolution for IMAP access to my GMAIL account, it never prompts me for a password. Instead, I guess Evolution tries to connect without any password and fails every time. Switching to Thunderbird didn't do the trick either, so I think it might have something to do with the Keyring daemon. My Internet connection is fine, as I can access my account under other operating systems.

Things I've tried so far:

[LIST]
[*]"Forget passwords" in the evolution menu
[*]Forcing shutdown of evolution and deleting the ~/.evolution folder (as suggested by [https://bugzilla.redhat.com/show_bug.cgi?id=221112](https://bugzilla.redhat.com/show_bug.cgi?id=221112))
[*]Accessing the keyring and deleting the default keyring
[*]Removing the password of the default keyring
[*]Creating new users with or without automatic login (to see if the login keyring might be the problem)
[*]Examining debug console and stdout/stderr of evolution (no entries except for the connection failure)
[/LIST]
This is truly driving me nuts, so any help would be greatly appreciated!

---

### Post by Rodney9 on 2010-05-01
I am haveing the same problem with pop3.
Every time I startup and open evolution it asks for Accessing the keyring password.

---

### Post by summentier on 2010-05-01
@Rodney9: Have you taken a look at the following thread:

[http://ubuntuforums.org/showthread.php?t=832675](http://ubuntuforums.org/showthread.php?t=832675)

In short, you can try:

[LIST]
[*]setting the password of the default keyring to none: go to Accessories > Passwords and Encryption keys
[*]Turn off default login for your user (Administration > Login Screen), or, if this doesn't work, try creating a new user without default login (Administration > Users and groups)
[/LIST]
My problem, however, is exactly the opposite: Evolution *never *prompts me for a password.

Ideas still welcome :)

---

### Post by summentier on 2010-05-01
So, continuing my monologue: I fixed the problem.

It was not the keyring at all, but my configuration was erroneous. Evolution does not ask for a password if it cannot connect at all.

To get Evolution working with GMAIL, do the following:

[LIST=1]
[*]**Try sending an e-mail.** If Evolution prompts you for a password and is successful in sending the mail, it is not a keyring problem (make sure you have the right configuration as well - mostly TLS).
[*]**Review your configuration**. For GMAIL, make sure you have SSL enabled and you're using DIGEST-MD5 as authentication mechanism (i think pretty everything else than the default Password will work)
[*]**Deactivate and reactivate** your account in the preferences menu.
[/LIST]
Hope this helps!

---


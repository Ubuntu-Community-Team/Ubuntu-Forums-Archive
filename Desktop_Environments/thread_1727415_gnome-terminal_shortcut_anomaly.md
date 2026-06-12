---
title: "gnome-terminal shortcut anomaly"
date: 2011-04-12
forum: Desktop Environments
---

### Post by linfidel on 2011-04-12
This is a weird one, I think...   

I use the standard terminal shortcut key from keyboard shortcuts, and all is well.  But, I kinda like to customize the command a little, for example setting the geometry, so I created a 2nd shortcut to gnome-terminal, using the custom shortcuts.  No problem so far.

But there's a problem that doesn't make sense.  I have the SSH agent set up, and when I run ssh from the default terminal shortcut, I get the pop-up keyring dialog to enter my passphrase, and every other ssh session does not require a passphrase.  If I run gnome-terminal from either the run dialog or an existing terminal, same behavior.

**But...**  the terminal I run from the shortcut key, using the same command, and the same default session, acts differently.  It does not popup the dialog, but asks for my passphrase on the terminal itself, and it asks for every ssh session.  Pretty much defeats the purpose of the ssh agent.  Note that it still require my passphrase, **not** the login password for the remote system.

Anyone know how I can make the custom keyboard shortcut work the same as all the other invocations?

I noticed that if I create a shortcut for xterm, it does the same thing.  Running xterm from a terminal will not require the ssh passphrase after I've entered it, but the shortcut does, so it's not gnome-terminal itself.

Thanks for your help, I hope. :)

---


---
title: "keyboard shortcut for ssh"
date: 2010-05-10
forum: Desktop Environments
---

### Post by amastbaum on 2010-05-10
I recently switched from GNOME to xfce, and I can't get working a simple keyboard shortcut to ssh to another machine.

In GNOME, I made a launcher (which gnome-do found); the first time I ran the launcher I'd get an X11 popup asking for by ssh passphrase, and then it would be saved for the rest of the GNOME session, making logins nice and fast.

In xfce, a similar launcher opens a new xfce4-terminal, which asks for the passphrase every time. I made a keyboard shortcut to "ssh -X me@server" -- this open an X11 popup for the passphrase, but no terminal, because there is no "run in terminal" option for keyboard shortcuts.

I'd be okay with running "ssh-add" at every login, but it has to be system-wide, rather than attached to one terminal instance. Passphraseless ssh is an options but a creepy one. I do all my work on this remote computer, so this is very frustrating! Any suggestions?

Thanks,
Andy

---

### Post by Jose Catre-Vandis on 2010-05-10
What's stopping you just typing the passphrase into the terminal or do you mean the passphrase is saved somewhere on your client and appears in your popup?

Have you tried using Zenity?

---

### Post by amastbaum on 2010-05-10
I could type it in the terminal, but I log into this computer very often so it's a huge pain relative to my gnome setup.

In gnome, a launcher that runs ssh in the terminal is smart enough to run a GTK-ified ssh-askpass and save your passphrase in the keyring for the rest of the session. I want to make that happen in xfce.

---


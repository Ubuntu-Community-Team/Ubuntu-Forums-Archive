---
title: "su and sudo dont work no more"
date: 2006-07-31
forum: Desktop Environments
---

### Post by ferrari on 2006-07-31
i have installed ubuntu Desktop and fully updated it i can log in to the Desktop with the root password but i doesnt work in the terminal.

it says:

su: Authenication failure
sorry.


i tried changing the password from System>Preference>About Me, and i did a restart. it logs in the Desktop and the Synaptic works with the password but not the su or sudo in the terminal.

---

### Post by scxtt on 2006-07-31
what specific commands are you running?

---

### Post by ferrari on 2006-07-31
just su

i was trying to sudo apt-get install "anything"

and command "su" alone doesnt work

it asks for password but says its wrong

---

### Post by jasutton on 2006-07-31
Well, 'su' wouldn't work in Ubuntu by default since Ubuntu comes with the root account 'disabled' (no password really).  It would only work if you specifically set a 'root' password (e.g., 'sudo passwd root').

Now, as for why 'sudo apt-get install' doesn't work while synaptic does is another issue.  Try getting a root shell ('sudo -s').

---

### Post by ferrari on 2006-07-31
ok sudo -s worked iam in root. thanks


but it doesnt ask for password iam in root direct :confused:

---

### Post by jasutton on 2006-07-31
If you've used 'sudo' recently with anything else, it might not ask for a password.  To test this theory, you could use 'sudo -k' and the next time you use sudo, it should force you to enter your password.

---


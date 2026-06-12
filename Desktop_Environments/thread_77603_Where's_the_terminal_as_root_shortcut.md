---
title: "Where's the terminal as root shortcut?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by scottylans on 2005-10-17
I know this is likely officially the dumbest question but.....

I just deleted my 5.04 install and installed 5.10.
There used to be an icon under applications / system tools / terminal session (as root)  
or something like that

It's gone - I need it to setup wpa supplicant and ipw2200.

I found a terminal session and then typed "su username" and then password to try and get the same effect but it wouldn't let me run some commands (like ifconfig) for some reason

No doubt this is likely one of the stupidest things ever but can someone give me a hand?

I also found the "run as different user" option too - but I don't know what command to run to execute a terminal session so yeah....

Anyone?

---

### Post by afonic on 2005-10-17
Ubuntu uses sudo:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

To get a "root" terminal you can type "sudo -s" followed by your password.

---

### Post by scottylans on 2005-10-17
[QUOTE=afonic]Ubuntu uses sudo:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

To get a "root" terminal you can type "sudo -s" followed by your password.[/QUOTE]


Thank you  - that seems to be working (I can use "updatedb" to find stuff)

Sorry about being so dumb :(

---

### Post by afonic on 2005-10-17
You're welcome! :-)

---


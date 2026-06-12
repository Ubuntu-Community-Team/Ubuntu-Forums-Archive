---
title: "Login drums"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Charles Hand on 2006-07-07
Can I turn off the login drum sound?

-Charlie

---

### Post by Dr. Nick on 2006-07-07
in Gnome go to System - Preferences - Sound and set login to no sound to stop the chime sound

System - Administration - Login Window / Accessibility Tab and uncheck the 'Login screen ready box ' for the drums

---

### Post by majed on 2006-07-07
Hi, Yes -- you can! :)

I assume you are using the default: GDM to logon. So here are the steps:

[LIST=1]
[*]Open GDM Setup to change Login Window Preferences
   From a terminal, run the below command and enter your password
```
sudo gdmsetup
```
[*]Go to the Accessibility tab on the setup window
[*]Uncheck the "Login screen ready" checkbox or change the wave file to any other sound you would like to play
[/LIST]

Enjoy,
Majed

---

### Post by tonyr on 2006-07-07
What about the longer drumroll as gdm first comes up?

EDIT:  Sorry, my bad. I meant the greeter sound after login and on logout,
that kind of sunrise thing.

---

### Post by tonyr on 2006-07-07
Answerd my own question (asking the right question is half the answer)
In **System->Preferences->Sound->Sounds**, set **Log in:** and
**Log out:** to **No sound**.

---

### Post by autocrosser on 2006-07-07
That is the Gnome-login sound--goto /preferences/sounds to change or remove the sound--you also can set your own custom sounds there--

---


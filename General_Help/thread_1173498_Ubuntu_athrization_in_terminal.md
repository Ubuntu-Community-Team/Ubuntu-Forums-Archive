---
title: "Ubuntu athrization in terminal"
date: 2009-05-29
forum: General Help
---

### Post by ThewhiteLynx on 2009-05-29
I am rather new to Ubuntu just as a warning, I just installed 9.04 a few days ago and as a relatively new computer programmer I am trying to be able to start writing some java programs, however I have been trying to install Java onto my desktop with ubuntu, but following the instructions Sun gives it says i need to first type *su* in the terminal then it will ask for an authorization code, I was thinking this was the login password for the only account I have on the system, which I am assuming makes it admin by default, but when I try entering the password no characters are displayed when I enter, not even the usual black circles that are normally used for passwords.  I assumed this was natural so I just tried typing my passwords a few times but every time I try it says, "Authentication failure."

---

### Post by smo0th on 2009-05-29
use sudo to gain admin priviledges, ubuntu uses sudo instead of su

about the no-circles-appearing thing it is normal in terminal, but terminal gets what you type.

cheers.

---

### Post by ThewhiteLynx on 2009-05-29
Thanks

---

### Post by hayden92 on 2009-05-29
When you type your password into the terminal, the characters are not even echoed on the screen, this is for the sake of security.

Sudo is what I would recommend as well, once you type in and enter your password, you will be granted superuser power for 15 minutes (or something like that)

Sometimes the command-line can be confusing!

---

### Post by Yellow Pasque on 2009-05-29
The latest stable release of Sun's Java JRE is Java 6, update 13 (6u13). This version is included in Jaunty's repos. Always look in the repos/Synaptic first when you need a program. You'll save yourself a lot of time and hassle.

---


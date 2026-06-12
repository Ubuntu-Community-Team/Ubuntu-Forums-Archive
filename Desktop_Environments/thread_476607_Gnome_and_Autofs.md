---
title: "Gnome and Autofs"
date: 2007-06-17
forum: Desktop Environments
---

### Post by jleino on 2007-06-17
Hello.

I have an autofs problem. After accessing a file behind an automounted directory, the directory
does not umount ever. I think could be a Gnome problem because if I do it in command line
everything works ok. I'm using Gnome 2.18.1 (Ubuntu 7.04).

Syslog is just flooded:

Jun 17 20:07:37 mnemonic automount[10245]: expired /purkki/dokumentit
Jun 17 20:07:40 mnemonic automount[4840]: attempting to mount entry /purkki/dokumentit
Jun 17 20:08:56 mnemonic automount[10296]: expired /purkki/dokumentit
Jun 17 20:08:56 mnemonic automount[4840]: attempting to mount entry /purkki/dokumentit

I tried to clear 'most recent documents' folder thinking that perhaps
it polls the directory regularly or something... I didn't help though.

Any ideas are highly appreciated!

With best regards, jleino

---


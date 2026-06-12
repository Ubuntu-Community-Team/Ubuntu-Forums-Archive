---
title: "Environment Variable"
date: 2006-01-02
forum: Desktop Environments
---

### Post by Canellas on 2006-01-02
Hi,


If I define an environment variable, for example: "export MY_VAR=OK", in the '~/.bash_profile' or in the '/etc/profile', when I type 'echo $MY_VAR' in a 'xterm' session, it appears "OK". However, if I try to use this variable in a program, as 'eclipse', it does not exist.

Does anyone know where I must set an environment variable so that graphical programs access it?

TIA,
  Canellas

---

### Post by cwaldbieser on 2006-01-02
[QUOTE=Canellas]Hi,


If I define an environment variable, for example: "export MY_VAR=OK", in the '~/.bash_profile' or in the '/etc/profile', when I type 'echo $MY_VAR' in a 'xterm' session, it appears "OK". However, if I try to use this variable in a program, as 'eclipse', it does not exist.

Does anyone know where I must set an environment variable so that graphical programs access it?

TIA,
  Canellas[/QUOTE]

Try your ~/.bashrc.  The ~/.bash_profile is only sourced for a login shell.

---

### Post by elastomer on 2006-01-06
There has to be a place where the system is setting environment variables. In ordinary unix (including generic Debian), the /etc/profile file is the place this happens. Where is it happening in Ubuntu? I've been running linux systems for more than 15 years--it's frustrating to not be able to administrate a system. Where is the documentation on how the system is set up?

---

### Post by cwaldbieser on 2006-01-06
[QUOTE=elastomer]There has to be a place where the system is setting environment variables. In ordinary unix (including generic Debian), the /etc/profile file is the place this happens. Where is it happening in Ubuntu? I've been running linux systems for more than 15 years--it's frustrating to not be able to administrate a system. Where is the documentation on how the system is set up?[/QUOTE]
It looks like /etc/profile exists in Ubuntu.
For documentation, I would suggest "man bash", as this enumerates all the places a bash shell looks when setting up the environment.

---


---
title: "Even as Root, cannot install SM Alpha Centauri"
date: 2009-06-26
forum: Gaming &amp; Leisure
---

### Post by Quirriff on 2009-06-26
I'm trying to install the Alpha Centauri Planetary pack, since I'm using 64-bit I have IA32 libs and everything, and I typed this in the mounted CD directory:

```
linux32 sh setup.sh
```

and the installation script seems to work until...

> 
Author
======
The Loki update tool was written by Sam Lantinga at Loki Software, Inc.

Please enter the installation path [/usr/local/Loki_Update]             
Please enter the path in which to create the symbolic links [/usr/local/bin] 
[color=red]No write permission to /usr/local/bin[/color]

I'm trying as a normal user, Root and Sudo, same thing every time.

---

### Post by vikkikanhaua on 2009-06-26
please post the "ls -l" output of /usr/local/bin

---

### Post by Quirriff on 2009-06-26
Well, it seems there is no /usr/local/bin
Perhaps that's the problem?

the only things inside /usr/local is:
etc  games  include  lib  man  sbin  share  src

What would the equivilent be on Jaunty?

---

### Post by vikkikanhaua on 2009-06-26
just create a bin directory with root privileges
```
sudo mkdir /usr/local/bin
```

then try to install

---

### Post by Quirriff on 2009-06-26
Yep it installed, new problems now but I'll try to fix 'em myself.

---


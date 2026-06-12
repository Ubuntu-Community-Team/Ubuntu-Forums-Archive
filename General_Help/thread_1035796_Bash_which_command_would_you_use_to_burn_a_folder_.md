---
title: "Bash: which command would you use to burn a folder (&lt;=4Gb)"
date: 2009-01-10
forum: General Help
---

### Post by frenchn00b on 2009-01-10
Hello,

I wanna burn with bash my data (no X). Which command would you use to burn a folder (<=4Gb)?
I am wondering which arguments and program I gonna use... to avoid any crap or burning failures.

Which command would you advice ?
mkisofs, I remind is the worst way :) lol

Cheers

---

### Post by jerome1232 on 2009-01-10
[http://sharkysoft.com/tutorials/linuxtips/cdcommands/](http://sharkysoft.com/tutorials/linuxtips/cdcommands/)

That should help.

---

### Post by frenchn00b on 2009-01-12
> **jerome1232 said:**
> [http://sharkysoft.com/tutorials/linuxtips/cdcommands/](http://sharkysoft.com/tutorials/linuxtips/cdcommands/)

That should help.

thanks

growisofs is one to choose, because it handles more functionality, like you can add it this : 
- a .tmp file where you give path of files to burn

mkisofs cant do that, cant read it this tmp file:( 

k3b uses growisofs... but which argument are favourable ??

---

### Post by heindsight on 2009-01-12
> **frenchn00b said:**
> thanks

growisofs is one to choose, because it handles more functionality, like you can add it this : 
- a .tmp file where you give path of files to burn

mkisofs cant do that, cant read it this tmp file:( 

k3b uses growisofs... but which argument are favourable ??

Yes, you'll want to use growisofs. Have a read through the manual
```
man growisofs
``` to see what options are available and how to use them.

---

### Post by adamlau on 2009-01-12
Or you can install the libburnia libraries and run xorriso through Bash.

---


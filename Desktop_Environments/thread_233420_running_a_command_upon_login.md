---
title: "running a command upon login"
date: 2006-08-10
forum: Desktop Environments
---

### Post by hadian on 2006-08-10
Hi
I want to run the following command (which introduce Intel Fortran Compiler) when i login to the system automatically:
source /opt/intel/fc/9.0/bin/ifortvars.sh
i put this in .bashrc file but in this case it is run when i enter the bash. i want to use this compiler in photran (a plugin of eclipse for fortran) but now it is not accessible by photran.
How can i run the above command that i can use the compiler in any IDE?
Regards,
Hadian

---

### Post by moma on 2006-08-10
What about if you add it to "Startup programs" in 
System -> Preferences -> Sessions  menu (in GNOME desktop).

You may beed to drop the "source" word, run the script only.
------------------------------------------

You can also create a script that runs the  /opt/.../ifortvars.sh and then starts eclipse. Make the script executable.

#!/bin/bash 
/opt/intel/fc/9.0/bin/ifortvars.sh
eclipse

---

### Post by hadian on 2006-08-10
thank you moma
the first method did not work but the second method solved the problem with addind source to the begining of /opt/intel/fc/9.0/bin/ifortvars.sh command. without source command it does not work.
hadian

---


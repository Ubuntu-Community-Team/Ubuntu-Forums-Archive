---
title: "Ubunto had a frontal lobotomy"
date: 2006-08-29
forum: Desktop Environments
---

### Post by DagonX on 2006-08-29
I added 
PATH=/opt/jdk1.5.08/bin:$(PATH)
export PATH
JAVA_HOME=/opt/jdk1.5.08
export JAVA_HOME
to bash.bashrc.

java -version returns the correct version.

I can not change bash.bashrc back because I do not have permission edit the file, restore the backup, or anything else.

Sudo is not recongized, neither is man, ls, or other shell commands.

What is the recovery method? Other than to reinstall ubunto.

---

### Post by Cable on 2006-08-29
Maybe try booting into recovery mode?

---

### Post by DagonX on 2006-08-30
tried that

---

### Post by cptnapalm on 2006-08-31
Assuming you have a bootable CD, boot that and then mount the drive, then change things back to how they were previously and see if that worked.

That be a good first step.

---

### Post by mssever on 2006-08-31
> **DagonX said:**
> I added 
PATH=/opt/jdk1.5.08/bin:$(PATH)
export PATH
JAVA_HOME=/opt/jdk1.5.08
export JAVA_HOME
to bash.bashrc.

java -version returns the correct version.

I can not change bash.bashrc back because I do not have permission edit the file, restore the backup, or anything else.

Sudo is not recongized, neither is man, ls, or other shell commands.

What is the recovery method? Other than to reinstall ubunto.
I believe your PATH should read: ```
PATH=/opt/jdk1.5.08/bin:$PATH
``` Without the parentheses. If you were in a double-quoted string, you would use curly braces {}.

Boot from the live CD, mount the drive, fix your .bashrc and see what happens.

Also, you can probably specify the exact path to your commands:
[LIST]
[*]/usr/bin/sudo
[*]/bin/ls
[*]/bin/nano
[*]/usr/bin/man
[*]/usr/bin/locate
[*]/usr/bin/updatedb[/LIST]

---

### Post by mewray on 2006-09-12
I'm having a similar problem.  I followed a guide on the ubuntu forums (I can't find the link right now, unfortunately) and am able to sudo/etc by using the absolute pathnames...

if I (non-root) did "export blah" where is the file that the variable gets exported to?

---

### Post by mssever on 2006-09-12
It gets exported to the environment, which is stored in RAM. That means that if you log out, everything that you exported disappears. So, if you want persistant exported variables, wither put them in .bashrc or put them in another file that gets sourced from .bashrc.

---


---
title: "C compiler"
date: 2005-11-24
forum: Desktop Environments
---

### Post by derm0 on 2005-11-24
Hi all,
I've only just recently started with Ubuntu and was wondering if there was a way to compile c files in the shell script. The standard Unix cc comand doesn't seem to work. Does anyone know if Ubuntu does have a c compiler & if it does what the shell command is to run it??

Thanks,
Derm

---

### Post by kairu0 on 2005-11-24
[QUOTE=derm0]Hi all,
I've only just recently started with Ubuntu and was wondering if there was a way to compile c files in the shell script. The standard Unix cc comand doesn't seem to work. Does anyone know if Ubuntu does have a c compiler & if it does what the shell command is to run it??

Thanks,
Derm[/QUOTE]

gcc?

---

### Post by GeneralZod on 2005-11-24
A compiler is not installed by default.  Do

```

sudo apt-get install build-essential

```

---

### Post by Knitter on 2005-11-24
Hello!
I know this is a dumb question but have you installed the gcc? it's not installed by default.

use synaptic or apt-get to install "build-essential", i think this is the package.

hope it helps.

---

### Post by Ugeek on 2005-11-24
build essential supplies all the nessesary dependencies. only installing gcc wont help.
so do
    sudo apt-get install build-essential

---


---
title: "No such file or directory"
date: 2009-04-21
forum: General Help
---

### Post by sirus the virus on 2009-04-21
I have just installed UBUNTU on one of my home PC n I have compiled a simple program but the terminal giving me such type of response.

gcc -o prog prog.c

prog:1:19:error:stdio.h:No such file or directory

prog:2:20:error:stdlib.h:No such file or directory

prog:3:23:error:sys/types.h:No such file or directory

n etc

so please tel me what should I do to over come this problem.
And if the answer is to install a certain package than do let me know the name of that package and the name of the website so that I could be able to install it.

---

### Post by mwacky on 2009-04-21
Are you able to find those references from your program, are they in the same directory as the program?  You might need to set environment variables.

---

### Post by codeseer on 2009-04-21
Add /usr/include to your Path.

Open a terminal and type:

```

gedit /home/username/.profile

```

Edit this area:

```

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    **PATH="$HOME/bin:$PATH"**
fi

```

PATH="$HOME/bin:/usr/include:$PATH"

---

### Post by lloyd_b on 2009-04-21
> **sirus the virus said:**
> I have just installed UBUNTU on one of my home PC n I have compiled a simple program but the terminal giving me such type of response.

gcc -o prog prog.c

prog:1:19:error:stdio.h:No such file or directory

prog:2:20:error:stdlib.h:No such file or directory

prog:3:23:error:sys/types.h:No such file or directory

n etc

so please tel me what should I do to over come this problem.
And if the answer is to install a certain package than do let me know the name of that package and the name of the website so that I could be able to install it.

Try this:```
sudo apt-get install build-essential
```

By default, Ubuntu does *not* install a complete build system.  Those errors indicate that you're missing the standard include files, which the build-essential package will install (along with many other things you'll probably need).

Lloyd B.

---


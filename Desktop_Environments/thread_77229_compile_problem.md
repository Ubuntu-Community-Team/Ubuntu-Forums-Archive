---
title: "compile problem"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Iuliux on 2005-10-16
every time when I try to install someting in breezy the output is like these:
[cod]
./configure
[/cod]
> 
...
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

gcc is installed.
any ideeas?

---

### Post by GeneralZod on 2005-10-16
Try:

```

sudo apt-get build-essential

```

---

### Post by Iuliux on 2005-10-16
10q very much.

---

### Post by Iuliux on 2005-10-16
upps ... now it stopes at
> 
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!


---

### Post by Iuliux on 2005-10-17
any ideeas:confused:

---

### Post by GeneralZod on 2005-10-17
[QUOTE=Iuliux]any ideeas:confused:[/QUOTE]

Search Synaptic or Adept for something like:

x11 dev

and install that.  If this is a KDE app you're trying to compile, search for 

qt dev

and install any of those, and the same again for 

kde dev.

---


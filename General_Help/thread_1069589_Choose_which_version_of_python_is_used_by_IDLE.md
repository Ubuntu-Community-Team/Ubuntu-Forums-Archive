---
title: "Choose which version of python is used by IDLE?"
date: 2009-02-14
forum: General Help
---

### Post by mahela007 on 2009-02-14
I have installed IDLE an the package "python3.0 minimal"
however when i start IDLE it uses python 2.5
How do I make it use python 3?

Also what are the names of the correct packages I have to install in order to run python 3 and IDLE? I don't know if the packages I have installed are correct
the ones I installed are
[I]python3.0 minimal
idle[/I]

---

### Post by ianhaycox on 2009-02-14
```

sudo update-alternatives --config python

```

Does this help ?

---

### Post by linux_tech on 2009-02-14
You should just be able to install python 3.  If the interpreter does not use python 3, reinstall the interpreter, and then it should use python 3.

---


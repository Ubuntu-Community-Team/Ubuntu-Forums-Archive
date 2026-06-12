---
title: "Command Line Help"
date: 2010-10-16
forum: Desktop Environments
---

### Post by kushanku on 2010-10-16
I am trying to learn how to use the terminal in Ubuntu 10.10. I am trying to execute a python program using the command './hello.py'.
I am in the correct directory and have changed to permission settings to '755'. 

I can execute the program using the 'python hello.py' command but want to understand why './hello.py' command is not working?

Thanks

---

### Post by luvshines on 2010-10-16
> **kushanku said:**
> 
I can execute the program using the 'python hello.py' command but want to understand why './hello.py' command is not working?

Thanks

By executing it with 'python <program-name>' you are actually telling that the program is a python program, it is to be treated as a python program, it's to be interpreted by a python interpreter.

When you run it as ./hello.py, Linux will try to run it as a bash/sh script if you don't specify the first line in the script, that is the 'shebang' line, as #!<path-to-python-interpreter>, something like #!/usr/bin/python OR #!/usr/bin/env python

What is the first line in your script ?

---

### Post by kushanku on 2010-10-16
> **luvshines said:**
> By executing it with 'python <program-name>' you are actually telling that the program is a python program, it is to be treated as a python program, it's to be interpreted by a python interpreter.

When you run it as ./hello.py, Linux will try to run it as a bash/sh script if you don't specify the first line in the script, that is the 'shebang' line, as #!<path-to-python-interpreter>, something like #!/usr/bin/python OR #!/usr/bin/env python

What is the first line in your script ?

the script is just a hello world script:
```

x = "Hello World!"
Print x

```

Do I need to write something at the start of the script to tell the interpreter to execute it as a python script?

---

### Post by luvshines on 2010-10-16
> **kushanku said:**
> the script is just a hello world script:
```

x = "Hello World!"
Print x

```

Do I need to write something at the start of the script to tell the interpreter to execute it as a python script?

yup!!
Add #!/usr/bin/env python as the topmost line

---

### Post by kushanku on 2010-10-16
Awesome! Thanks a lot. Would you mind just explaining to me how that line works?

---

### Post by luvshines on 2010-10-16
> **kushanku said:**
> Awesome! Thanks a lot. Would you mind just explaining to me how that line works?

Wikipedia will definitely be able to explain better:
[http://en.wikipedia.org/wiki/Shebang_(Unix)](http://en.wikipedia.org/wiki/Shebang_(Unix))

---


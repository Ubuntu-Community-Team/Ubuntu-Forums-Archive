---
title: "making a shortcut to a .py programme"
date: 2009-04-25
forum: General Help
---

### Post by joey-elijah on 2009-04-25
I have some python programmes installed (via bzr) that i can create launchers to via 'main menu' and they launch fine., however other's don't launch at all.

Just curious as to how i go about making a shortcut/what command i should use to launch them..

Example: I downloaded CoverGloobus which comes as a .py file that you give permissions to and then double click and it runs. Just linking the menu shortcut to the .py starts it up fine.

Example: I'm testing out BloGTK!2 via BZR and even though i can do "the double click" on the .py file, if i link to it nothing happens when i click it. 

Example: I'm testing Emesne-Crazy via BZR and i can make a launcher for it by just linking to the .py file. It works fine.

There's some fundamental rule i'm obviously not aware of here... 

:confused:

---

### Post by ddrichardson on 2009-04-25
The ones that don't run are probably missing a shebang: look to see if they have ```
#!/bin/python
```as their first line. I'm pretty sure the DE handles MIME type by extension so would run a double clicked file but to execute directly needs a shebang (unless you type python filename.py).

---

### Post by joey-elijah on 2009-04-25
> **ddrichardson said:**
> The ones that don't run are probably missing a shebang: look to see if they have ```
#!/bin/python
```as their first line. I'm pretty sure the DE handles MIME type by extension so would run a double clicked file but to execute directly needs a shebang (unless you type python filename.py).

The ones that won't launch do have #!/user/bin/env python but adding a shebang/ python file.py   results in an error either about whitespace or can't execute 'process'. I'm doing something wrong here!

What would be the perfect 'command' structure for a .py tucked in a folder?

---

### Post by ddrichardson on 2009-04-26
> **joey-elijah said:**
> The ones that won't launch do have #!/user/bin/env python but adding a shebang/ python file.py   results in an error either about whitespace or can't execute 'process'. I'm doing something wrong here!

What would be the perfect 'command' structure for a .py tucked in a folder?
I don't use the /usr/bin/env approach, its done for portability - if python is installed in /usr/local/bin/python then the script wont run so env is used to run python instead. This has a vulnerability that might elevate authority and I know atleast one system where env is in /bin/env.

The shebang should just be```
#!/usr/bin/python
```If that doesn't work then there is an issue with MIME types.

So a hello world script in bash for example would be```
#!/bin/sh
echo Hello World
```

If you can't run them in the terminal without an error then there's a good chance they're borked - whitespace might be the indentation which is important in Python.

---

### Post by joey-elijah on 2009-04-26
> **ddrichardson said:**
> If you can't run them in the terminal without an error then there's a good chance they're borked - whitespace might be the indentation which is important in Python.

They all run fine through terminal.

I'm lazy and just wanted menu entries instead of having to launch them through the terminal everytime.  :P

Well at least some work via launchers , so it's no big issue having to launch the rest through the terminal really.

---

### Post by robertrej on 2009-04-26
Not sure if this is the place but I am trying to create a
shortcut to a specific directory in terminal which I could
launch from my desktop.any ideas?


                   thanks
                   BJ

---


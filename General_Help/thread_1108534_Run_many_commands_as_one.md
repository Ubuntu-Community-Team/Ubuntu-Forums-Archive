---
title: "Run many commands as one?"
date: 2009-03-27
forum: General Help
---

### Post by valros on 2009-03-27
Is it possible to open almost all of the programs that are in my applications menu, instead of using the shortcuts or each command is there a way I can place all the commands as one and that could be used as a launcher?

---

### Post by mikewhatever on 2009-03-27
Yes, but it's a rather silly thing to do.

---

### Post by valros on 2009-03-27
Well, how do you chain commands as one?

---

### Post by UbuntuNerd on 2009-03-27
I don't recommend it, you might not like the end result.

---

### Post by UbuntuNerd on 2009-03-27
> **valros said:**
> Well, how do you chain commands as one?
You can chain commands together using &&

---

### Post by valros on 2009-03-27
eh, not what I'm looking for in that the next command is only ran once the first is finished, id like to open many programs at once.

---

### Post by mb_webguy on 2009-03-27
Create a script.  Open a text editor, and paste the following.```
#! /bin/sh

program1 &
program2 &
program3 &
```

Replace *program#* with the commands to launch the applications you want.  Save the file as something like ~/bin/runall.  Open the terminal and type "chmod +x ~/bin/runall".  Now you can use the command "runall" to run those applications.  If you run the command from the terminal, the programs will close if you hit Ctrl+C or close the terminal, but you can add it to your startup programs or using Alt+F2.

---

### Post by spcwingo on 2009-03-27
Nevermind, you just posted that you don't want to run one after the other.

---


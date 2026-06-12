---
title: "Put two commands in custom application launcher"
date: 2009-06-20
forum: General Help
---

### Post by Benzjaminz on 2009-06-20
Hi I'm still a bit new to ubuntu.

I've installed a program (Matlab but that's not important) but due to a bug in the program it requires that I type two lines of code in the terminal to launch it correctly.

export AWT_TOOLKIT="MToolkit"
matlab

How do I create an application launcher with these two lines of code in it. In the terminal I can put a semi-colon between them and it will run but I can't seem to make a custom launcher that will work with two lines of code.

Thanks

---

### Post by jerome1232 on 2009-06-20
```
export AWT_TOOLKIT="MToolkit" && matlab
```

Ought to work, the second command only gets executed if the first command succeeds.

---

### Post by paperplate9 on 2009-06-20
Make sure you select the Type as 'Application in Terminal'

then put this as the command:
bash -c 'export AWT_TOOLKIT=MToolkit; matlab'

---

### Post by sdennie on 2009-06-20
The other option would be to just put the "export ..." into ~/.bashrc and never worry about it again.  You would have to log off and then back in for this to take effect at the launcher level though.

---

### Post by geirha on 2009-06-20
You can also put a variable assignment infront of a command. That variable will then be passed to that command (only). No need to export.
```
AWT_TOOLKIT=MToolkit matlab
```

---

### Post by sdennie on 2009-06-20
> **geirha said:**
> You can also put a variable assignment infront of a command. That variable will then be passed to that command (only). No need to export.
```
AWT_TOOLKIT=MToolkit matlab
```

Yes, that's the better way to do it if you don't want it global.  But, launchers don't interpret that syntax right so, you have use:

```

sh -c "AWT_TOOLKIT=MToolkit matlab"

```

---

### Post by geirha on 2009-06-20
> **sdennie said:**
> Yes, that's the better way to do it if you don't want it global.  But, launchers don't interpret that syntax right so, you have use:

```

sh -c "AWT_TOOLKIT=MToolkit matlab"

```

Ah, yes, forgot about that. It's not run by a regular shell. The env command can be used as well. I believe that is more common
```
env AWT_TOOLKIT=MToolkit matlab
```

---

### Post by Benzjaminz on 2009-06-20
Hi Thanks very much for all the help.

At the moment I've used what paperplate9 mentioned which seems to work well. 

bash -c 'export AWT_TOOLKIT=MToolkit; matlab'

But will play around with the other ways when I have a chance to learn a bit more about ubuntu.

---


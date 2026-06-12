---
title: "Why do I need quotes for find?"
date: 2009-04-27
forum: General Help
---

### Post by lavinog on 2009-04-27
Notice if I search for a file without quotes:
```
 sudo find ./ -iname *.m
./mattest.m

```

Then with quotes:
```

sudo find ./ -iname "*.m"
./Desktop/ece2317proj.m
./mattest.m

```

Why would the file on the desktop require quotes to be located?
(This is a Hardy machine)

---

### Post by StuartN on 2009-04-27
> **lavinog said:**
> Notice if I search for a file without quotes:
```
 sudo find ./ -iname *.m
./mattest.m

```

Then with quotes:
```

sudo find ./ -iname "*.m"
./Desktop/ece2317proj.m
./mattest.m

```

Why would the file on the desktop require quotes to be located?
(This is a Hardy machine)

The argument to find is *.m and for this to be preserved it must be quoted. If it is not quoted then the shell expands *.m to ece2317.m mattest.m before passing the result as an argument to find.

---

### Post by Brandon Williams on 2009-04-27
Without the quotes, the *.m in the first command line is being expanded by the shell to match the file in your current working directory. With the quotes, the shell will leave expansion up to find.

---

### Post by Dr_Willis on 2009-04-27
a good way to 'test' these  * 'situations' is to try a simple 'echo' command

```
echo *.m 
```     

would print out the various filenames  that match. If none patch it would print out '*.m' 

The point to learn is the SHELL is expanding the *  with the filenames before the program being ran even sees  the arguments.

ie: the shell expands **echo *.m**       to be

echo foo.m  bar.m whatever.m 

If such files exist.

---

### Post by andrew.46 on 2009-04-27
Hi lavinog,

And I guess strictly speaking you only need *single* quotes not *double*. The doubles are only required to allow variable expansion *by the shell*. The classic demonstration of this is:

```

andrew@skamandros~$ echo '$HOME'
$HOME

```

as opposed to:

```

andrew@skamandros~$ echo "$HOME"
/home/andrew

```

But in the case you demonstrate this is a minor nitpick as the quotes are designed to shield your search from shell expansion and I suspect either type will serve here.

Andrew

---

### Post by RedSquirrel on 2009-04-27
This question is covered in the **find** man page under the heading "NON-BUGS". ;)

```
man find
```

---

### Post by lavinog on 2009-04-28
I like the man page answer to escape the * instead...it is one less keystroke ;)

---


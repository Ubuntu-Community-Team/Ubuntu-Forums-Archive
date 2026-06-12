---
title: "&quot;cd&quot; in bash script"
date: 2005-11-14
forum: Desktop Environments
---

### Post by Huubke! on 2005-11-14
Why am I too stupid to find out how I can "cd" to another directory using bash script? (I want the script to do some stuff and then go to another directory and stay there)

Thanks!

---

### Post by Remmelas on 2005-11-14
most stuff done in a bash script is done using the same syntax as at the command line, so, to cd in your script just put the command on it's own line

cd /some/directory
ls *

would cd to /some/directory and list the files in that directory.

---

### Post by cbkm on 2005-11-14
When you run a bash script it creates a new bash process and does all it's work in there.

Hence even if the last line of your bash script was:
```

cd /

```

When the script exits you'd be returned to the directory you ran the script from.

If you really-really want to change the local environment you could run your script as:
```

source myscript.sh

```

which should do as you want. :)

---

### Post by Huubke! on 2005-11-14
nope doesn't work!
looks like this:

[FONT="Courier New"]#!/bin/bash
cd /home/some_dir/
some_prog &
tail -f some_file &
[/FONT]

---

### Post by kont.raen on 2005-11-14
[QUOTE=Huubke!]nope doesn't work!
looks like this:

[FONT="Courier New"]#!/bin/bash
cd /home/some_dir/
some_prog &
tail -f some_file &
[/FONT][/QUOTE]

Hi,

it might be, that the program you try to execute is not in the path - so in order to make sure, that some_prog (in the current directory) is executed, modfify the line into :

./some_prog &

Hope this helps :)

---

### Post by cbkm on 2005-11-15
If I may ask, why are you running the "tail" in the background?

---


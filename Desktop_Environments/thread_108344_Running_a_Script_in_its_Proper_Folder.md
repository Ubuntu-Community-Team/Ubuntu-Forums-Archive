---
title: "Running a Script in its Proper Folder"
date: 2005-12-25
forum: Desktop Environments
---

### Post by pilaftank on 2005-12-25
When you double-click a shell script from within **File Browser** (*Applications* --> *Accessories* --> *File Browser*), the script is run from the **$HOME** folder instead of the folder where the script resides.  If I have script **xyz.sh** in the **~/apps** folder, that's the folder where I want it to run.

So, how do you launch a script from **File Browser** so that the script runs in the folder where it lives?

---

### Post by Zwack on 2005-12-25
[QUOTE=pilaftank]So, how do you launch a script from **File Browser** so that the script runs in the folder where it lives?[/QUOTE]

Probably not the answer you're looking for (but I don't use the file browser to run scripts...

Easiest way would be to add a line to the script to do a cd to the directory you want to run it in.  If you want to make it universal, something like "cd `dirname $0`" should work for you.

Z.

---

### Post by pilaftank on 2005-12-26
[QUOTE=Zwack]Easiest way would be to add a line to the script to do a cd to the directory you want to run it in.[/QUOTE]
Yeah, but the author of the script does not know where the script will be located at the time the author is writing the script (and even if the author knew, the script would then become hard-coded to a specific location -- very undesirable).


[QUOTE=Zwack]If you want to make it universal, something like "cd `dirname $0`" should work for you.[/QUOTE]
I'm not aware of any way to use **File Manager** to pass a value into a script (and even if there is such an option, it puts an unwieldy burden on the user to type the path of a script just to run it).

---

### Post by Zwack on 2005-12-26
[QUOTE=pilaftank]I'm not aware of any way to use **File Manager** to pass a value into a script (and even if there is such an option, it puts an unwieldy burden on the user to type the path of a script just to run it).[/QUOTE]

$0 is the path/name of the script that is currently running.  It is not a commandline option.  I haven't tested this before, so I don't know what File Manager does...

Here's my test script...

```
#! /bin/sh

echo $0
echo `basename $0`
echo `dirname $0`

sleep 30
```

And here are two sample outputs when "run in terminal" from Nautilus File Browser

```

/home/ubuntu/dummy/testscript.sh
testscript.sh
/home/ubuntu/dummy
```

and 

```

/home/ubuntu/testscript.sh
testscript.sh
/home/ubuntu
```

See, it does exactly what you want... just put 

```
cd `dirname $0`
``` 

at the top of your script and when you run it it will go to the location it is currently in.

Z.

---


---
title: "compile specific source file in Linux coreutils package"
date: 2014-10-26
forum: Education &amp; Science
---

### Post by mahmoud7 on 2014-10-26
I need to compile a specific version of cp (copy) command from the Linux coreutils source file. Instead of compiling the whole package.
iam just add a printf statement at the end of the function.
I am using Ubuntu 14.04, the source code of cp command is exist in the following directory.


/tmp/coreutils/coreutils-8.21/src/cp.c


how to compile it, so when run the cp command i can see the statement that i had added it in the code?

---

### Post by sudodus on 2014-10-26
I would leave the cp command untouched, and use rsync, which can do a lot more than cp. Or if you want some post-processing, you might be able to do it with some command available in the bash shell (make an alias or shell-script file).

Please explain what you want to do (I mean how you want the final output to be modified), there are many people here who can help you. If it is too difficult for me, there are other persons who know more about rsync options and bash commands.

---

### Post by mahmoud7 on 2014-10-26
i need to add a printf statement 
printf("my name");
so after run the command it will print "my name"

---

### Post by sudodus on 2014-10-26
Then you can wrap it in a shell script or alias, that will print "your name"

```

#!/bin/bash

cp  "$*"
echo "your name"

```

Save it to a file for example **mycp** and make it executable

```
chmod ugo+x mycp
```


Example:

```
./mycp file1 "file 2" target-dir
```

Quote filenames with spaces or other special characters.

Output:

```
your name
```

You can also check if the copy process was successful and supply different output text for different cases.

---


---
title: "using *scrot* in a bash script with variables"
date: 2009-06-10
forum: General Help
---

### Post by waspinator on 2009-06-10
Hi,

I'm trying to take a screen shot and then more it to another folder.

It works fine if I do something like this

```

#!/bin/bash
scrot '%T.jpg' -q 50 -e 'mv $f /home/screenshots/'

```

but it doesn't understand this

```

#!/bin/bash
FOLDER="/home/screenshots/"
scrot '%T.jpg' -q 50 -e 'mv $f $FOLDER'

```

Is there any way of making this work?

Thanks,

Waspinator

---

### Post by munky99999 on 2009-06-10
sudo apt-get install scrot

---

### Post by DGortze380 on 2009-06-10
> **waspinator said:**
> Hi,

I'm trying to take a screen shot and then more it to another folder.

It works fine if I do something like this

```

#!/bin/bash
scrot '%T.jpg' -q 50 -e 'mv $f /home/screenshots/'

```

but it doesn't understand this

```

#!/bin/bash
PATH="/home/screenshots/"
scrot '%T.jpg' -q 50 -e 'mv $f $PATH'

```

Is there any way of making this work?

Thanks,

Waspinator

PATH is a system variable, you really shouldn't use it like that, could cause problems.

maybe try something like this (idk if it will solve your problem, can you post the errors you received)?

```

#!/bin/bash
myDir="/home/screenshots/"
scrot '%T.jpg' -q 50 -e 'mv $f $myDir'

```

---

### Post by waspinator on 2009-06-10
> **munky99999 said:**
> sudo apt-get install scrot

did that ... thanks for reading my post

> **DGortze380 said:**
> PATH is a system variable, you really shouldn't use it like that, could cause problems.

maybe try something like this (idk if it will solve your problem, can you post the errors you received)?

```

#!/bin/bash
myDir="/home/screenshots/"
scrot '%T.jpg' -q 50 -e 'mv $f $myDir'

```

Ya, I tried that ... still doesn't understand. It renames the file to myDir instead of moving it to a folder

Thanks anyway

Can I pipeline $myDir in somehow?

This doesn't work:

```

#!/bin/bash
myDir="/home/screenshots/"
echo "'%T.jpg' -q 50 -e 'mv $f $myDir'" | scrot

```

it just produces the standard scrot file name and doesn't move it. it seems to ignore the pipe

---

### Post by DGortze380 on 2009-06-10
> **waspinator said:**
> did that ... thanks for reading my post



Ya, I tried that ... still doesn't understand. It renames the file to myDir instead of moving it to a folder

Thanks anyway

Can I pipeline $myDir in somehow?

I don't have scrot to test with, but try one of the following.

Just use the move command, no quotes.

mv $f $myDir

or

Use accent marks (top left of your US keyboard, under the tilde (~)).

`mv $f $myDir`

Both of those work in bash to move the file held in $f to the directory held in $myDir

---

### Post by waspinator on 2009-06-10
when I try it without quotes I get this error:

```

giblib warning: unrecognised option /home/screenshots

mv: missing file operand
Try `mv --help' for more information.

```

When I try using ` instead of ' I get

```

mv: missing destination file operand after `/home/screenshots'
Try `mv --help' for more information.
scrot: option requires an argument -- 'e'

```

I still don't get why this doesn't work though

```

#!/bin/bash
myDir="/home/screenshots/"
echo "'%T.jpg' -q 50 -e 'mv $f $myDir'" | scrot

```

Oh, and I think you may have misunderstood me about the $f variable. $f is not defined by me. It's a built in function to scrot to get the file name.

Thanks

---

### Post by DGortze380 on 2009-06-10
> **waspinator said:**
> when I try it without quotes I get this error:

```

giblib warning: unrecognised option /home/screenshots

mv: missing file operand
Try `mv --help' for more information.

```

When I try using ` instead of ' I get

```

mv: missing destination file operand after `/home/screenshots'
Try `mv --help' for more information.
scrot: option requires an argument -- 'e'

```

I still don't get why this doesn't work though

```

#!/bin/bash
myDir="/home/screenshots/"
echo "'%T.jpg' -q 50 -e 'mv $f $myDir'" | scrot

```

Thanks

EDIT:

This should work:

```

`mv $f $dir/$f`

```

---

### Post by DGortze380 on 2009-06-10
> **waspinator said:**
> 

Oh, and I think you may have misunderstood me about the $f variable. $f is not defined by me. It's a built in function to scrot to get the file name.


Thanks

I assumed it was defined by scrot.

I'm not sure if you can use it in my above post, I don't know WHEN it's defined by scrot, but give it a try.

---

### Post by waspinator on 2009-06-10
Still doesn't seem to work ... same error as before without the extra /$f ... hmm

It looks like messing with how scrot works is not going to work. the -e is used to execute a command after running scrot, but that command doesn't seem to be 'inside' the bash script, and since $f is a scrot variable I can't use that after the scrot command to move it manually.

I think my best bet would be to pipe in the input, but I don't know how.

This is what I tried but scrot just ignores the pipe.
```

#!/bin/bash
myDir="/home/screenshots/"
echo "'%T.jpg' -q 50 -e 'mv $f $myDir'" | scrot

```

Maybe I don't know how to use pipes properly?

Thanks

---

### Post by DGortze380 on 2009-06-10
> **waspinator said:**
> Still doesn't seem to work ... same error as before without the extra /$f ... hmm

It looks like messing with how scrot works is not going to work. the -e is used to execute a command after running scrot, but that command doesn't seem to be 'inside' the bash script, and since $f is a scrot variable I can't use that after the scrot command to move it manually.

I think my best bet would be to pipe in the input, but I don't know how.

This is what I tried but scrot just ignores the pipe.
```

#!/bin/bash
myDir="/home/screenshots/"
echo "'%T.jpg' -q 50 -e 'mv $f $myDir'" | scrot

```

Maybe I don't know how to use pipes properly?

Thanks

scrot would have to accept the input in that form for it to work. You can't necessarily use a pipe.

you tried the following??

```

#!/bin/bash

dir="/home/screenshots"
scrot '%T.jpg' -q 50 -e '`mv $f $dir\$f`'

```

---

### Post by waspinator on 2009-06-10
> **DGortze380 said:**
> scrot would have to accept the input in that form for it to work. You can't necessarily use a pipe.

you tried the following??

```

#!/bin/bash

dir="/home/screenshots"
scrot '%T.jpg' -q 50 -e '`mv $f $dir\$f`'

```

Ya I tried that. Actually the first time I didn't understand that I was supposed to keep the first ' and just add ` and not replace. Unfortunately Now all it does is rename the image from %T to "dir"

Thanks

---

### Post by DGortze380 on 2009-06-10
> **waspinator said:**
> Ya I tried that. Actually the first time I didn't understand that I was supposed to keep the first ' and just add ` and not replace. Unfortunately Now all it does is rename the image from %T to "dir"

Thanks

Sounds like you're getting closer, it's renaming the file.
Are you sure you didn't forget a $

And you tried the following and got errors?

```

#!/bin/bash

dir="/home/screenshots"
scrot '%T.jpg' -q 50 -e `mv $f $dir\$f`

```



The only real hint I can give you at this point is that you have a problem with the syntax of how scrot is accepting the arguments.

Just going to take trial and error to fix I think.

For reference as you work on it.

The following works and is a valid command
`mv $f $dir\$f`

Not much more I can do without access to scrot at the moment.
Good Luck.

---

### Post by waspinator on 2009-06-10
> **DGortze380 said:**
> Sounds like you're getting closer, it's renaming the file.
Are you sure you didn't forget a $

And you tried the following and got errors?

```

#!/bin/bash

dir="/home/screenshots"
scrot '%T.jpg' -q 50 -e `mv $f $dir\$f`

```



The only real hint I can give you at this point is that you have a problem with the syntax of how scrot is accepting the arguments.

Just going to take trial and error to fix I think.

For reference as you work on it.

The following works and is a valid command
`mv $f $dir\$f`

Not much more I can do without access to scrot at the moment.
Good Luck.

Alright Thanks.

I'm trying to get pipes to work right now.

I thought this would work but it doesn't for some reason ... :

```

FOLDER=/home/user/screenshots
scrot `echo "'%T.jpg' -q 50 -e 'mv \$f $FOLDER'"`

```

I get this error

```

giblib warning: unrecognised option /home/user/screenshots'

giblib error: Saving to file '2009-06-10-17:29:45.jpg' failed

```

Maybe someone can help me out with pipes...

Thanks for your help

---


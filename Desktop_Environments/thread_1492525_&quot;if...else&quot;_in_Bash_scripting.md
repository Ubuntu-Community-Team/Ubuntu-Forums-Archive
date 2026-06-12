---
title: "&quot;if...else&quot; in Bash scripting"
date: 2010-05-24
forum: Desktop Environments
---

### Post by Xafer on 2010-05-24
Sorry for asking questions simultaneously, I just curious with this Ubuntu :)
So, I would like to make a simple Bash code that read the users input.

```

#!/bin/bash
echo "Enter input"
read input 
if [$inputan =1]
        then
                echo "You choose one"
else
        echo "You choose other than one"
fi

```

So, when the users put 1, it will show a text "You choose one"
else, it will show "You choose other than one". The problem is whenever my input is, I always get this output
> Enter input:
5
[: 9: missing ]
You choose other than one

---

### Post by swizman on 2010-05-24
Change the if condition to:

if [ $input = 1 ] 


You need empty space after and before the "[]" and also after the "=". 
The variable containing the input is called $input, not $inputan.

Works fine with those changes.

---

### Post by BoneKracker on 2010-05-24
[http://www.ibm.com/developerworks/library/l-bash.html](http://www.ibm.com/developerworks/library/l-bash.html)

[http://linux.die.net/abs-guide/](http://linux.die.net/abs-guide/)

---

### Post by Xafer on 2010-05-24
> **swizman said:**
> Change the if condition to:

if [ $input = 1 ] 


You need empty space after and before the "[]" and also after the "=". 
The variable containing the input is called $input, not $inputan.

Works fine with those changes.
Thanks, great work, at the first i use 
if[$input=1]
leaving all the spaces, and didnt work. but with spaces it works. thanks

---


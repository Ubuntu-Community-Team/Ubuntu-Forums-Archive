---
title: "Strange error"
date: 2009-06-07
forum: General Help
---

### Post by papabill on 2009-06-07
I'm trying to load a software package (a BBS), and even though I've loaded it before, now I'm getting a strange message at the first part of the load-something I've never gotten before, and I'm at a loss to explain or correct it.

Here is the command:
root@Ubuntu:/home/bill/downloads/temp# ./install.sh

Here is the result:
bash: ./install.sh: /bin/bash^M: bad interpreter:No such file or directory

Anyone have a clue what this message means?

Thanks

---

### Post by papabill on 2009-06-07
Well, I figured out the error myself, but not WHY it gave me the error.

I had modified the file (install.sh is a text file), but for some reason it still wouldn't run. I'd still like to know why.

Thanks

---

### Post by PirateChef on 2009-06-07
The first line of a bash script should read
```

#!/bin/bash
```

So, the interpreter is bash, and what the error is telling you is that the path to the interpreter is wrong. This should be easy to fix. 

I'm wondering about that ^M in the error. I wonder if that's a space or null character or something that accidentally got into the script. Try deleting that first line, typing it in, and then saving it. (There should be no spaces in it, and it should be at the beginning of the script.)

---


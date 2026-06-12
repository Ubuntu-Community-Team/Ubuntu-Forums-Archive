---
title: "Script problem"
date: 2009-03-24
forum: General Help
---

### Post by Davidoff99 on 2009-03-24
Hi,

I writed this simple restarter script, but I got an error. :(
I have Ubuntu 8.10 x64 Server version. This script works on 8.04 version.

#!/bin/bash
while [ 1 ]; do
  cd /opt/wowarsenal/bin
  ./arcemu-world
  sleep 5
done

restarter.sh: 7: Syntax error: end of file unexpected (expecting "do")

Sorry for my english :)

---

### Post by heindsight on 2009-03-24
> **Davidoff99 said:**
> Hi,

I writed this simple restarter script, but I got an error. :(
I have Ubuntu 8.10 x64 Server version. This script works on 8.04 version.

#!/bin/bash
while [ 1 ]; do
  cd /opt/wowarsenal/bin
  ./arcemu-world
  sleep 5
done

restarter.sh: 7: Syntax error: end of file unexpected (expecting "do")

Sorry for my english :)

Well, firstly I'd suggest using:
```
while true; do
```
instead of
```
while [ 1 ]; do
```
It just looks better ;) I don't think it will fix your problem though.

I don't see anything wrong with your script.

The only thing I can think of is that you might somehow have DOS style CRLF line endings instead of Unix style LF line endings.

---

### Post by Davidoff99 on 2009-03-24
I changed it

#!/bin/bash
while true; do
  cd /opt/wowarsenal/bin
  ./arcemu-world
  sleep 5;
done;

I got this error:
Syntax error: "done" unexpected (expecting "do")

---

### Post by heindsight on 2009-03-24
Like I said, your code looks fine to me. The only explanation I can think of is that you have some non-printing characters (like the CR characters of DOS end-of-line sequences) in there that are confusing bash

Could you perhaps run the following command (from the directory containing your script) and post the ouput:
```
hd restarter.sh
```

By the way, if you're posting code or terminal output, please put it in [CODE] tags - it's just a lot easier to read that way...

---

### Post by Davidoff99 on 2009-03-25
```
00000000  23 21 2f 62 69 6e 2f 62  61 73 68 0d 0a 77 68 69  |#!/bin/bash..whi|
00000010  6c 65 20 74 72 75 65 3b  20 64 6f 0d 0a 20 20 63  |le true; do..  c|
00000020  64 20 2f 6f 70 74 2f 77  6f 77 61 72 73 65 6e 61  |d /opt/wowarsena|
00000030  6c 2f 62 69 6e 0d 0a 20  20 2e 2f 61 72 63 65 6d  |l/bin..  ./arcem|
00000040  75 2d 77 6f 72 6c 64 0d  0a 20 20 73 6c 65 65 70  |u-world..  sleep|
00000050  20 35 3b 0d 0a 64 6f 6e  65 3b 0d 0a              | 5;..done;..|
0000005c

```

---

### Post by aeiah on 2009-03-25
it tells you the error is near 'done'. its the ; at the end. its expecting something to follow on from the done because you put a ; in there. just remove it and it should work.

---

### Post by Davidoff99 on 2009-03-25
I wrote with the notepad on windows.
I rewrote the script with "nano" and it works! :popcorn:
Thank you for the help!

---

### Post by heindsight on 2009-03-25
> **aeiah said:**
> it tells you the error is near 'done'. its the ; at the end. its expecting something to follow on from the done because you put a ; in there. just remove it and it should work.

No, the semicolon after **done** is unnecessary, but it won't cause an error. At least, when I tried it, it didn't cause any errors. 

> **Davidoff99 said:**
> 
```
00000000  23 21 2f 62 69 6e 2f 62  61 73 68 **0d 0a** 77 68 69  |#!/bin/bash..whi|
00000010  6c 65 20 74 72 75 65 3b  20 64 6f **0d 0a** 20 20 63  |le true; do..  c|
00000020  64 20 2f 6f 70 74 2f 77  6f 77 61 72 73 65 6e 61  |d /opt/wowarsena|
00000030  6c 2f 62 69 6e **0d 0a** 20  20 2e 2f 61 72 63 65 6d  |l/bin..  ./arcem|
00000040  75 2d 77 6f 72 6c 64 **0d  0a** 20 20 73 6c 65 65 70  |u-world..  sleep|
00000050  20 35 3b **0d 0a** 64 6f 6e  65 3b **0d 0a**              | 5;..done;..|
0000005c

```

That hexdump output confirms my initial suspicion. The lines in your file are all terminated by DOS style CRLF sequences (the parts I made bold in the quote above).

To fix it, you can install tofrodos:
```
sudo apt-get install tofrodos
```
and then run (in the directory containing your script):
```
fromdos restarter.sh
```

---


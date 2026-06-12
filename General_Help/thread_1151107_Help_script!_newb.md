---
title: "Help script! newb"
date: 2009-05-06
forum: General Help
---

### Post by lesodk on 2009-05-06
I have created a script

#!/bin/sh
exec matlab -desktop

but i really don't know where to place it.

Normally when i install programs i do it in the folder 
/opt/
and create a symlink in /usr/local/bin
then i don't need to use "sh".

My question is, should i put the script in /opt/ and make a symlink,
or what is the "normal" procedure for this?

---

### Post by dubhear on 2009-05-06
what is symlink?:confused:

---

### Post by lesodk on 2009-05-06
sorry, i use
"ln -s" to place a shortcut in the /usr/local/bin folder

---

### Post by baseface on 2009-05-06
just put it in /usr/local/bin or /usr/bin or where ever and you dont need to run sh first. just strip off the .sh at the end of the file name and ur good to go. no need for a symlink.

---

### Post by lesodk on 2009-05-06
thanks.
What if i'm noot root user?
Can i do the same some place in my home folder?

---

### Post by StOoZ on 2009-05-06
> **dubhear said:**
> what is symlink?:confused:

FYI --> [http://en.wikipedia.org/wiki/Symbolic_link]("http://en.wikipedia.org/wiki/Symbolic_link")

---

### Post by lesodk on 2009-05-06
strange. I don't know where to put my scripts if i don't have acces to
usr/bin or usr/local/bin

is there any alternative?

---

### Post by dubhear on 2009-05-06
> **StOoZ said:**
> FYI --> [http://en.wikipedia.org/wiki/Symbolic_link]("http://en.wikipedia.org/wiki/Symbolic_link") to be continued...

---

### Post by baseface on 2009-05-07
as long as you put your script somewhere in your $PATH, you will be able to run it without providing a full path name or using sh first.

---


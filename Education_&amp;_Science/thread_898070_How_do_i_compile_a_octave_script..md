---
title: "How do i compile a octave script."
date: 2008-08-22
forum: Education &amp; Science
---

### Post by 7raTEYdCql on 2008-08-22
I use the following method to compile a octave script. 

1)Initiate octave 
2)Type the name of the script.

Another method i use is cat abc.m | octave.

The problem i face is this. The script will run, but i get the following error message.

error: can't perform indexing operations for <unknown type> type

Please help.

---

### Post by rye_ on 2008-08-23
first of all, why use cat instead of echo?
echo mfile.m | octave
        
but regarding the error, I can't see that it affects the running of the m-files.

---

### Post by SkippoGuangiacomo on 2008-08-25
i.mehrzad, take away the extension (the .m) from the extension of the file (i.e. cat abc | octave; or echo abc | octave as rye_ suggested). You won't get the error after.

---

### Post by rahul0159 on 2011-03-25
> **SkippoGuangiacomo said:**
> i.mehrzad, take away the extension (the .m) from the extension of the file (i.e. cat abc | octave; or echo abc | octave as rye_ suggested). You won't get the error after.
Hi,I hv the same problem in compilation but when i use echo command then it throws error  "Invalid call to echo." command i hv used is.....
echo Untitled | octave

---

### Post by Lateralis on 2011-03-26
My knowledge of Octave is practically non-existent.  (I have in fact only just googled what it can do, and now feel miffed I've never used it before!)  But, I would think you could get your scripts to work by making them executable and adding 
```

#!/usr/bin/octave

```
to the top of your scripts (assuming the octave interpreter is located in /usr/bin).


Edit: I meant to make clear you need to ensure the script has execute permissions (chmod +x <filename>) and then you need to execute the script via your preferred method, e.g. ./<filename>.

---


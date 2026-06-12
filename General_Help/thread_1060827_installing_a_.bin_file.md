---
title: "installing a .bin file"
date: 2009-02-05
forum: General Help
---

### Post by hockey9876 on 2009-02-05
I'm trying to install a file ending in .bin

I placed it in the /usr/local directory and did 
a chmod 777 filename.  Then I tried ./filename.bin
I got an error stating that the file could not be
found.  So I tried doing a sudo ./filename.bin.
Same result.  

Am I missing anything important here????  I've installed
these file types before and never had a problem...until
now.

Thanks,

John

---

### Post by kthakore on 2009-02-05
This might be unnecessary but show ls -al line of this file. Also based on what you said u did  chmod on filename not filename.bin. Lastly the error says it can't find the file, so ur working directory might not be in /usr/local. So run this install /usr/local/filename.bin

---

### Post by binbash on 2009-02-05
start it ./usr/local/filenameasda.bin

---

### Post by ibutho on 2009-02-05
> **binbash said:**
> start it ./usr/local/filenameasda.bin

Shouldn't it be just
```
/usr/local/filenameasda.bin
```

---

### Post by Nepherte on 2009-02-05
There's no need to save it in the /usr or /usr/local directory. The easiest way would still be somewhere in the home directory since that's the only place where you can save a file as a user without escalating your privileges. There's also no need to chmod the file unless you are trying to make the file executable. Since you already made it executable (and much more with the chmod 777) you can run it with:
```
sudo /full/path/to/bin/file
```

---

### Post by hockey9876 on 2009-02-06
None of these has worked... regardless of whether I type the full
path /usr/local/servers/file.bin or sudo /usr/local/servers/file.bin
I get the following:

 unable to execute ./server103_linux32.bin: No such file or directory

ARGHHHHHHHH

Any other ideas...?

John

---

### Post by hyper_ch on 2009-02-06
what are you trying to install?

---


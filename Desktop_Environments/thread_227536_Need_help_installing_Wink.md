---
title: "Need help installing Wink"
date: 2006-08-01
forum: Desktop Environments
---

### Post by Panserbjorn on 2006-08-01
I downloaded wink.15.tar.gz, extracted the files to my desktop, navigated to the folder in terminal, but the commands ./configure, make, sudo make install do nothing. Any help?

---

### Post by jasutton on 2006-08-01
might need to do this first:

```
sudo apt-get install build-essentials
```

---

### Post by Panserbjorn on 2006-08-01
That's not it. I have build-essential installed. Thanks though.

---

### Post by jasutton on 2006-08-02
Just wondering...

What exactly do you mean by they 'do nothing?'  What fails? ./configure? make? make install?

---

### Post by Panserbjorn on 2006-08-02
./configure outputs ```
bash: ./configure: No such file or directory
```

make outputs ```
make: *** No targets specified and no makefile found.  Stop
```

make install outputs ```
make: *** No rule to make target `install'.  Stop.
```

---

### Post by jasutton on 2006-08-02
can you do an 'ls -la' in that folder and give the output?

---

### Post by Panserbjorn on 2006-08-02
```
total 16
drwxr-xr-x  3 mark mark 4096 2006-08-01 21:47 .
drwxr-xr-x  3 mark mark 4096 2006-08-01 22:00 ..
drwxr-xr-x 11 mark mark 4096 2006-08-01 21:47 installdata.tar.gz_FILES
-rwxr--r--  1 mark mark 2294 2005-06-20 03:15 installer.sh
```

---

### Post by etank on 2006-08-02
Try ```
sudo sh ./installer.sh
```

---

### Post by Panserbjorn on 2006-08-02
That did the trick. Thanks so much, etank and jasutton!

---


---
title: "Open .tar.gz"
date: 2010-10-15
forum: Desktop Environments
---

### Post by shadowfax1 on 2010-10-15
Can someone give me the commands to open Floola-linux.tar.gz.  For those that might be interested this program apparantly supports ipod nano 5g....Thankyou

---

### Post by luvshines on 2010-10-15
Does this work:
```
tar -xzvf <file-name>
```

---

### Post by 3Miro on 2010-10-15
This is an archive (like rar or zip). You can extract the files by double-click. However, it probably has just the source-code for the program, which means that you will have to compile it yourself. Usually that is done with a terminal, cd into the folder with the extracted files and then type ./configure, make, make install. However, you should check for a README or INSTALL files for detailed instructions. Also, check their web-page to see if they have any info.

---

### Post by shadowfax1 on 2010-10-15
It's source code...no installation instructions on the read me txt.  This is where I get confused...can you give it to me in laymen's language as to 'make cd and directory?

---

### Post by nothingspecial on 2010-10-15
```
./configure
make
sudo make install 
```

Most of the time, but not always. Do you have a link to where you got it from, maybe the instructions are there?

btw, gtkpod works fine with nano 5g

---

### Post by shadowfax1 on 2010-10-15
Wish it did but the drop down box only goes to 4g and I'm pretty sure I got the latest version.  System recognizes the pod but there's nothing there after transferring the files.

---

### Post by nothingspecial on 2010-10-15
Are you on 10:10?

Because if you are using an earlier version of ubuntu, patches need to be applied.

---

### Post by shadowfax1 on 2010-10-15
Yes

---

### Post by nothingspecial on 2010-10-15
[U]I got to go. They work for me. I`ll check your post tommorow.

Good luck 
[/U]

---

### Post by shadowfax1 on 2010-10-15
I must be missing something....I extracted the file simply by right clicking and choosing extract here
I then moved the folder into the following directory...

usr/local/src

Does the ./configure go before or after the directory info?

---

### Post by luvshines on 2010-10-15
> **shadowfax1 said:**
> I must be missing something....I extracted the file simply by right clicking and choosing extract here
I then moved the folder into the following directory...

usr/local/src

Does the ./configure go before or after the directory info?

I just downloaded Floola to check what you are missing here, but actually , I think it is too simple:
1. After you do extract here, you'll see a new directory name Floola-linux
2. Open that directory, select Floola and press enter.

That's it. No installation, nothing

---

### Post by shadowfax1 on 2010-10-15
I guess I was making mountains out of a mole-hill....lol
Thanxs

---


---
title: "Batch into Bash File"
date: 2009-02-19
forum: General Help
---

### Post by Riley2 on 2009-02-19
Hi, I just got a great new Linux VPS with Ubuntu 7.10. So I have a batch file I wanted to run through SSH, but I found that only bash files work. Could someone please turn this batch files into a bash as I have never worked with them before :)
```
@echo off
title servername
cd Source/Bin
java -Xmx1024m -cp .; Server
pause
```

---

### Post by dcstar on 2009-02-19
> **Riley2 said:**
> Hi, I just got a great new Linux VPS with Ubuntu 7.10. So I have a batch file I wanted to run through SSH, but I found that only bash files work. Could someone please turn this batch files into a bash as I have never worked with them before :)
```
@echo off
title servername
cd Source/Bin
java -Xmx1024m -cp .; Server
pause
```

Essentially both are just two flavours of the same thing, the best thing is to have a look at what is already in your Linux system (plenty of scripts in the /etc tree to look at) and then you can see the differences.

---

### Post by mikewu on 2009-02-19
```
#!/bin/sh
uname -n
cd Source/Bin 
java -Xmx1024m -cp .:Server
read -p "Press Any Key To Continue"
```

This assumes Source/Bin is in your home directory and that Server is a subdirectory in there.

---


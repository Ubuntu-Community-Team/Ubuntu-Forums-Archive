---
title: "[SOLVED] where do I place files in ubunu so I can extract it through the terminal ?"
date: 2008-03-12
forum: Desktop Environments
---

### Post by amlife on 2008-03-12
Hello I'm very very new to Linux word, I'm windows person :confused:

if I downloaded a compressed file, where do I place it so I can extract it from the terminal. 
I have a .tar file sitting on my desktop when i try to extract it it won't let me .. 

any idea's ? 

Thank you

---

### Post by Whiffle on 2008-03-12
Should be able to do it right there.  How are you going about it?  It should be something like:

```

cd ~/Desktop
tar xvf file.tar

```

Or, you should be able to right click it.

---

### Post by Dark Star on 2008-03-12
You can extract file anywhere . .What you need to do is to change the path .. to change path

```
cd /path/of/the/file/
```

---

### Post by aysiu on 2008-03-12
That's odd that you wouldn't be able to extract it if it's on your desktop.

By the way, what is the tar file?

---

### Post by bharadwaj on 2008-03-12
the default location of all files in terminal is home. So try placing the file in your home dir and then > tar xvf file.tar

---

### Post by amlife on 2008-03-12
Thanks for the help I got it working by doing cd command and navigate to desktop.

I applicate the support and help. the tar file belongs to vmware workstation.

Thanks again

---


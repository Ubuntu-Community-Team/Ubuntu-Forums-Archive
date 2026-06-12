---
title: "Squelching Terminal Output"
date: 2009-02-23
forum: General Help
---

### Post by leachja on 2009-02-23
I'm in the process of writing a program in C. I'm making some system calls and calling functions like stty and setserial. I am wondering if there is a way of not displaying this in the terminal. Hopefully it would be selective. I don't want to lose all output, just the output of the commands that are intermediary.

Thanks

---

### Post by mb_webguy on 2009-02-23
Prefacing the command with "nohup" will send all output to the file "nohup.out" in your current directory. or your home directory if you don't have write access to the current directory.  You could do the same basic thing by piping the output to a file, such as "*command* >> output.txt".  If you don't want to see any output at all, you could pipe it to /dev/null (i.e. "*command* >> /dev/null").

If you know that the messages you want to see contain a certain word or phrase, you can pipe the output to grep, e.g. "*command* | grep Error" to show all lines containing "Error".

Some commands have an option to limit the output given.

---

### Post by leachja on 2009-02-23
Thanks alot, that helps me greatly.

---


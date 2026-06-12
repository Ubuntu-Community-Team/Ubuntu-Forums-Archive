---
title: "running c++ binaries from same directory"
date: 2009-05-19
forum: General Help
---

### Post by iochinome on 2009-05-19
Hey guys, so i have a total beginner question here... i have just made do without this information for a while and figured it was time i knew. so i am programming in c++, i compile the program successfully, and it spits out a binary, lets call it "helloworld"

is there a way to run "helloworld" from the directory it is in? for instance, say that it is on the desktop. instead of doing
gcc -o helloworld helloworld.c
cd
Desktop/helloworld

why can i not just do
gcc -o helloworld helloworld.c
helloworld

?

it gives me a "command helloworld not recognized" type error... it would just be easier for fast debugging, you know. thanks! much appreciated.

---

### Post by chiefbutz on 2009-05-19
First you will need to check to be sure that it has executable permissions. If you can already run the file then I assume that it does but here is the command for it anyways (assuming you are in the same file and the binary)

```
chmod +x helloworld
```

If you are in the directory with the binary you need to run it like this:
```
./helloworld
```

The reason is that the computer looks in certain places for executable files. Since the desktop is not one of those places by default you have to say "./" which means the current directory.

I hope this helps.

---


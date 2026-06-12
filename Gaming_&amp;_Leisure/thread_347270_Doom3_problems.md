---
title: "Doom3 problems"
date: 2007-01-27
forum: Gaming &amp; Leisure
---

### Post by will61 on 2007-01-27
I'm trying to install the doom3 binary files for Linux without much luck 
when I follow the code stated in the ubuntu help page I get the following output

"will@black:~$ sudo ./doom3-linux-1.3.1302.x86.run
sudo: ./doom3-linux-1.3.1302.x86.run: command not found"

Am I missing something ??

on the help page it says that the code is "./doom3-linux-1.3.1302.x86.run" , but that gives a "permission denied" response 

So to get permission I add "sudo" before it and it gives me a "command not found"

What gives ??? can anybody help

---

### Post by kvonb on 2007-01-27
Hello,

Assuming that you DID actually download the file "doom3-linux-1.3.1302.x86.run", and that it is actually in your home folder (the ~/ part), you will first have to make it executable like so:

```
chmod +x doom3-(press the TAB key to autocomplete)
```then type:

```
./doom3-(TAB)
```In the above codes, don't actually type the (), but press the tab key, this is just in case it is a different filename to the example you were following.

Hope that helps :)

EDIT:  you might have to install it as root, so put "sudo" in front of the last command, ie:

```
sudo ./doom3-(TAB)
```

---

### Post by Dritzen on 2007-01-27
If all else fails, you can use:

```

sudo sh doom3-linux-1.3.1302.x86.run

```

Essentially what is happening is that you are trying to run a file that isn't marked as executable.  When you chmod +x filename , it sets that file as executable.

Typing the command above runs the .run script whether it is marked as executable or not.

---

### Post by will61 on 2007-01-27
Thanks for the helps it worked and doom3 is up and running now I did have a few Audio probs but thats also worked out

---


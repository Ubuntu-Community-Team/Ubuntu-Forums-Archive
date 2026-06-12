---
title: "Running a .bat"
date: 2007-06-18
forum: Desktop Environments
---

### Post by HcoJustin on 2007-06-18
I was wondering if there was an easy way to run .bat files on Ubuntu 7.04....I know my friend has made his recognize all file extensions, and he has tried to help me, i just can't understand.
So if anyone could help me out, i would appreciate it.
 Thanks,
  ~HcoJustin

---

### Post by eentonig on 2007-06-18
A .bat file won't work if you're talking about a windows .bat file.  

But you can make just about any tekst file run as a little script.

What you need to do is open yuor preferred tekst editor and enter

> #!/bin/bash
# Some explanation on what you want to accomplish
# This line isn't read by the interpreter/Commandline
# because it has a '#' in front of it.

<replace this with your command>
# In example
ls --all --human-readable    # It is wise to include the full options when writting scripted commands




And then make this text file executable with

> chmod +x tekstfile

If you place this under **~/your_username/bin** it will be available everywhere

---

### Post by HcoJustin on 2007-06-18
uhhhmmm ok....i will try to do what you just posted...with the text file, what to i make the extension as?   .sh? or leave it as a text

EDIT: this is in my .bat 
```
javac *.java

pause
```

EDIT: this is in another one.
```
@echo off

title Run

java -Xmx500m client 0 live live lowmem members english

pause
```

---

### Post by vanadium on 2007-06-18
A "linux bat file", ak a shell script, can have any name you like. You just need to make sure the file is executable (right-click in Nautilus, properties).

b.t.w., you should post questions regarding basic stuff in the Absolute Beginners forum.

---

### Post by eentonig on 2007-06-18
As said, you don't need a file extension. Allthough I usually name my shell scripts .sh. But that's just for clarity if I want to review something later.

What is it that you want to accomplish?

PS. You will need the > #!/bin/bash on the first line of your scripts (assuming you use the default shell that is). This is called the "Sha-bang" Google around for 'shell scripting' if you need some guidance.

---

### Post by HcoJustin on 2007-06-18
i need 2 basic layouts...one to compile .java files and another to that basically makes this...
```
@echo off
title Run

java -Xmx500m client 0 live live lowmem members english

pause
``` work for linux...they don't even have to be exact, just give me enough info to make it work.


EDIT: i need some help still....i have
> #!/bin/sh and stuff, I just need help writing the command.

---


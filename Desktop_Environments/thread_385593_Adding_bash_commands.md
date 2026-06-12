---
title: "Adding bash commands"
date: 2007-03-15
forum: Desktop Environments
---

### Post by Gorbachev on 2007-03-15
So, I how would I add a command, where i just open terminal and type, for example

program

and it launches a program called program.

I searched, but didnt know exactly what to put, or even how to explain this to people in this thread.. so, hopefully someone can help.

---

### Post by taurus on 2007-03-15
Do you mean how can you run a program from a terminal?  Click Applications, Accessories, then Terminal.  Then, at the prompt, type

```
firefox
```

---

### Post by Gorbachev on 2007-03-15
No, I mean, how do I add a new application which can be launched from terminal by merely typing "blahblah" or whatever it might be?

For instance, I have an executable that I want to be able to launch by merely typing a word into terminal.

Also, I don't know why/how I posted this here, can a mod move it to general help? Thanks.

---

### Post by lloyd_b on 2007-03-16
What you need to do either put the executable in a directory that's in your PATH, or add the directory that the executable is in to you PATH.

In a terminal window, type "env | grep PATH", and you'll see a line like:
```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/home/lloyd/bin:

```
This is a list of directories that the computer searches for executables.  So if "program" is in one of those locations, bash will find it.  Copying "program" to one of those locations will make things work the say your want.

Alternately, you can add new directories onto that path.  Note the last directory in the PATH listed above: "/home/lloyd/bin".  This is a directory I've set up for my "private" executables.  To add this to my PATH, I edited the file ".bashrc", and added the following line
```
export PATH=$PATH:/home/lloyd/bin:
```
So now when I make a shell script or something, I put it in that directory and I don't have to worry about the system finding it.

Finally, if you include the full path to an executable, you can run it regardless of where it it:
```
/home/lloyd/test/someprog
```
Will run the program "someprog" in the directory "/home/lloyd/test".

Lloyd B.

---

### Post by Gorbachev on 2007-03-16
Ah, thank you ever so kindly! Very thorough answer.

Thank you! :)

Edit: Now, how would I remove a directory? Thanks again.

---

### Post by lloyd_b on 2007-03-16
> Now, how would I remove a directory? Thanks again.

If you mean "remove a directory that you've added via .bashrc", just edit that line out and exit the current terminal window - the next time you start a terminal window, you'll no longer get that additional directory in the path.

If you mean removing a directory that the system had placed in the PATH - you have to replace the entire PATH.  For example:
```
export PATH=$PATH:/home/lloyd/bin:
```
In this case, the "$PATH" means "the current value of PATH".  This results in "/home/lloyd/bin" being appended onto the existing PATH.  By contrast:
```
export PATH=/bin:/usr/bin:/usr/local/bin:/home/lloyd/bin
```
doesn't reference $PATH - it completely replaces PATH with a new set of directories

Be cautious with removing the directories that the system placed in your path.  If you remove, for example, "/bin", you'll find that the some common commands (such as "ls") no longer work. 

A useful hint: to find out which directory a command is in, type "which {command}" in a terminal window.

Lloyd B.

---

### Post by Gorbachev on 2007-03-16
Well, bash is still looking for a directory which no longer exists (the old location of Wolfenstein ET) and, even though the new location is added, terminal keeps saying file not found directory doesnt exist (something similar to that) everytime i type "et" terminal. if I type et.x86, it launches fine, though.

---

### Post by lloyd_b on 2007-03-16
> Well, bash is still looking for a directory which no longer exists (the old location of Wolfenstein ET) and, even though the new location is added, terminal keeps saying file not found directory doesnt exist (something similar to that) everytime i type "et" terminal. if I type et.x86, it launches fine, though.
 
That directory has to have been added to your PATH somewhere.
1.  Read through the entire .bashrc.  That is the most likely place for such a change to have been made.

2.  Look in your home directory for a file called ".profile".  If one is found, check it to see if it's adding that PATH.

3.  Check the file "/etc/bash.bashrc".  Note: it's owned by root, so you'll need a "sudo" or  a "gksudo" to edit it.

4.  Check the file "/etc/profile".  Same note as #3.

Lloyd B.

---

### Post by Gorbachev on 2007-03-17
Hmm, neither make mention of even $PATH or PATH, or the directory which no longer exists, bizarre. :confused:

---


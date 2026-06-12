---
title: "Starting an application from a &quot;Custom Application Launcher&quot; doesn't work"
date: 2010-03-27
forum: Desktop Environments
---

### Post by andy80 on 2010-03-27
Hi,

I'm trying to create a "Custom Application Launcher" for Team Speak VOIP client. I've unpacked it into /home/andrea/TS/ and I can start it from command line using:

andrea@centurion:~/TS$ ./ts3client_runscript.sh

I've created a normal "Custom Application Launcher" for this application, but clicking on it doesn't work :\
Maybe there is some PATH error, but I cannot see the error since there's no output.

If it can help, here you can find the script: [http://pastebin.com/09YPgJkY](http://pastebin.com/09YPgJkY)

How can I make it work? Thanks!

---

### Post by ajgreeny on 2010-03-27
I think you may need the full pathway to the script, ie ```
/home/andrea/TS/ts3client_runscript.sh
```in the command box of the launcher.  Don't forget you must make the script executable as well for it to work from the launcher.

---

### Post by efflandt on 2010-03-28
Starting a path with "./" runs it from the current directory, which from a terminal is your home dir, but from a desktop launcher may be your Desktop dir.  So you may either need to use "~/" if that script is in your home directory, or the full path starting with "/home/andrea/".  If in doubt, it is best to use a full path.

---

### Post by andy80 on 2010-03-28
> **efflandt said:**
> Starting a path with "./" runs it from the current directory, which from a terminal is your home dir, but from a desktop launcher may be your Desktop dir.  So you may either need to use "~/" if that script is in your home directory, or the full path starting with "/home/andrea/".  If in doubt, it is best to use a full path.

Hello,

I even tried using absolute path too, but I think that the problem is that it cannot find some libraries in PATH, available only in /home/andrea/TS/ folder. But I really don't know how to fix this.

---

### Post by ajgreeny on 2010-03-28
Did you actually make the script file executable, as I said is needed?  If not, I don't think it will ever work.

---

### Post by andy80 on 2010-03-28
> **ajgreeny said:**
> Did you actually make the script file executable, as I said is needed?  If not, I don't think it will ever work.

of course it's executable.. how could I execute it from command line if not?

---

### Post by ajgreeny on 2010-03-29
You _can_ execute a .sh file even if it's not executable in command line with ```
sh filename.sh
```so you could still be using, or trying to use a non executable file. I admit I didn't really notice the actual command you used in terminal, which I now see, having looked closer, would need executable permissions.

---

### Post by DomRepDave on 2010-05-04
I have exactly the same problem.  When I click on the launcher you can tell something is happening but there is no output.  I am a complete Ubuntu novice, is it easy to add the locations/libraries in $PATH?  I imagine I have to make available the directory in which the application was created.

---


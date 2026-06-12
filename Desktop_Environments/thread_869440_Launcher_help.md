---
title: "Launcher help"
date: 2008-07-24
forum: Desktop Environments
---

### Post by jeffbray on 2008-07-24
I've done some research on how to format launchers and everything, but I'm having a hard time with it. There are a few things that I'd like to have launchers for, especially including Neverwinter Nights.

The way I have to initialize NWN now is to open the terminal, navigate to the NWN directory and type ./nwn (which starts NWN... somehow.)

How can I get this all to happen with one command in the "Launcher"?

A little explanation of the commands would be appreciated, because all of the straight-from-Ubuntu definitions of the %.. commands were pretty confusing.

Thanks in advance =D

---

### Post by scragar on 2008-07-24
make a list of the commands you run in order, eg:
```
cd /usr/local/games/nwn
./nwn
```
then remove all the new lines and replace then with " && " like so:
```
cd /usr/local/games/nwn && ./nwn
```
save and test.

---

### Post by Tim Sharitt on 2008-07-24
Just use the full path to the program. ./ just uses the working directory to run the program as if you did type in the full path.

---

### Post by DoktorSeven on 2008-07-25
> **Tim Sharitt said:**
> Just use the full path to the program. ./ just uses the working directory to run the program as if you did type in the full path.

However, sometimes a program will expect the current directory to be where the executable is, and if you type in a command using the full path, the "current directory" will be elsewhere, and the program won't work properly.

It's always best to do the cd /path/to/executable && ./executable commands.

---

### Post by jeffbray on 2008-07-25
Okay, in the command line I typed the following:
> cd ~/Desktop/nwn && ./nwn
and I get this when I try to launch:
> 
Details: Failed to execute child process "cd" (No such file or directory)

What am I doing wrong?

---

### Post by jeffbray on 2008-07-28
bump. please.

---

### Post by jeffbray on 2008-08-05
anybody?

---

### Post by apmcd47 on 2008-08-05
> **scragar said:**
> make a list of the commands you run in order, eg:
```
cd /usr/local/games/nwn
./nwn
```
then remove all the new lines and replace then with " && " like so:
```
cd /usr/local/games/nwn && ./nwn
```
save and test.
> **jeffbray said:**
> Okay, in the command line I typed the following:
> cd ~/Desktop/nwn && ./nwn
and I get this when I try to launch:
[quote]Details: Failed to execute child process "cd" (No such file or directory)

What am I doing wrong?[/QUOTE]
Presumably the path ~/Desktop/nwn is your nwn launcher? It is definitely not a directory, because that is what the error message is telling you. As Scragar says above it should be the path to the actual nwn program directory, eg if it is in /usr/local/games you use Scragar's example. If it is in ~/NWN you type ```
cd ~/NWN && ./nwn
```
Andrew

---

### Post by Chris Pine on 2008-08-08
I was having a similar problem, and it wasn't that the paths were wrong.  It's that "cd" is not recognized by the launcher.  Assuming your paths are correct, try this:

```
sh -c "cd ~/Desktop/nwn && ./nwn"
```

So I'm wondering, why isn't the launcher command wrapped like that by default?

---

### Post by jeffbray on 2008-08-08
Yeah, it was the sh -c "_____" that worked for me.

It is silly that it's not pre-wrapped.

---


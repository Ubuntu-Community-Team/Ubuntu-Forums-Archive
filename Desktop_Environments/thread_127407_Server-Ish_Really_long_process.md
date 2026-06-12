---
title: "Server-Ish Really long process"
date: 2006-02-08
forum: Desktop Environments
---

### Post by Steve132 on 2006-02-08
I am a little bit of a developer, and I have written a program that runs into a bit of a problem.

The program is written to run for a very long time and process a huge amount of data, because it is designed to reprocess a wikipedia data dump into a new format...

However, when I run the program for long periods of time, say, overnight, the program itself runs for about 2 hours and I wake up the next morning to a log that looks something like...
```

processing : 5%
processing : 5%
processing : 5%
processing : 5%
processing : 5%
processing : 5%
Killed
$>

```

My program does not output the message "Killed" anywhere in the source, and my only guess is that for some reason or another, the system is killing the process.

My question is this:  Does anyone know what a program does, if anything, that the OS responds by killing the process and sending "Killed" to stderr?

Based on what my program does, Possibilities I have come up with are as follows, but seeing as fixing any of these problems might take weeks, I don't want to go fixing all of them and rewriting the program logic if it isn't necessary.

--1)  **Memory leak**.  My program does have several minor memory leaks that might eat up system memory to the point where the system might be forced to shut down if left over a long period of time, I guess

--2)  **Security shutdown**.  Does the desktop version of Ubuntu have some sort of security feature where it interprets a resource intensive, long-running process to be malware?  I doubt this is true, because it would be a very silly design decision, (try running a server of some kind with any reliability) but I cannot discount everything.

--3)  **Filesystem Thrashing**.  My program is reading and writing files on a 160 GB FAT32 filesystem.  Being wikipedia, there is a lot of data to process.. and my program converts each article into a separate file inside a folder.  given [The limitations of the FAT32 Filesystem]("http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkc_fil_tdrn.asp") ,especially the limitations on the number of files, it would make sense that my program would override that limit, causing errors that might trigger the death of the process I am seeing.  However, my attempts to fix this problem (by having each new file be written into a catagorized folder by first letter), had no visible effect on the amount of data that could be processed before a kill.

I am out of ideas, and would really like someones help attempting to rectify this problem, or even just speculate with me.

---

### Post by cwaldbieser on 2006-02-08
[QUOTE=Steve132]I am a little bit of a developer, and I have written a program that runs into a bit of a problem.

The program is written to run for a very long time and process a huge amount of data, because it is designed to reprocess a wikipedia data dump into a new format...

However, when I run the program for long periods of time, say, overnight, the program itself runs for about 2 hours and I wake up the next morning to a log that looks something like...
```

processing : 5%
processing : 5%
processing : 5%
processing : 5%
processing : 5%
processing : 5%
Killed
$>

```

My program does not output the message "Killed" anywhere in the source, and my only guess is that for some reason or another, the system is killing the process.

My question is this:  Does anyone know what a program does, if anything, that the OS responds by killing the process and sending "Killed" to stderr?

Based on what my program does, Possibilities I have come up with are as follows, but seeing as fixing any of these problems might take weeks, I don't want to go fixing all of them and rewriting the program logic if it isn't necessary.

--1)  **Memory leak**.  My program does have several minor memory leaks that might eat up system memory to the point where the system might be forced to shut down if left over a long period of time, I guess

--2)  **Security shutdown**.  Does the desktop version of Ubuntu have some sort of security feature where it interprets a resource intensive, long-running process to be malware?  I doubt this is true, because it would be a very silly design decision, (try running a server of some kind with any reliability) but I cannot discount everything.

--3)  **Filesystem Thrashing**.  My program is reading and writing files on a 160 GB FAT32 filesystem.  Being wikipedia, there is a lot of data to process.. and my program converts each article into a separate file inside a folder.  given [The limitations of the FAT32 Filesystem]("http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkc_fil_tdrn.asp") ,especially the limitations on the number of files, it would make sense that my program would override that limit, causing errors that might trigger the death of the process I am seeing.  However, my attempts to fix this problem (by having each new file be written into a catagorized folder by first letter), had no visible effect on the amount of data that could be processed before a kill.

I am out of ideas, and would really like someones help attempting to rectify this problem, or even just speculate with me.[/QUOTE]

If I run a command from a bash shell and send it a KILL signal, "Killed" is printed to the terminal.  E.g.
Terminal 1
```

$ watch ls

```

Terminal 2
```

$ ps x | grep watch
27462 pts/5    S+     0:00 watch ls
$ kill -KILL 27462

```

Terminal 1
```

Killed

```

---

### Post by Steve132 on 2006-02-08
Ok then, so my question is, what is my program doing that is triggering the OS to kill it?

I mean, I know this seems like a debugging responsibility, I of all people know what's best for my own code, but is anyone who is familar with the inner workings of the OS have a hint as to what might a process do to offend the OS enough that the OS decides to kill it?

---

### Post by cwaldbieser on 2006-02-09
[QUOTE=Steve132]Ok then, so my question is, what is my program doing that is triggering the OS to kill it?

I mean, I know this seems like a debugging responsibility, I of all people know what's best for my own code, but is anyone who is familar with the inner workings of the OS have a hint as to what might a process do to offend the OS enough that the OS decides to kill it?[/QUOTE]
Is there anything useful in dmesg or the system logs?  I can't think of any reason the OS would just blithely kill your process-- unless you have a cron job that reboots the system every night or something like that.  You could check your uptime and see.

Maybe some sort of logging to find out when your program is killed could also shed some light on the problem.  If it happens after a regular amount of time, or at the same time, that could be a clue.

---


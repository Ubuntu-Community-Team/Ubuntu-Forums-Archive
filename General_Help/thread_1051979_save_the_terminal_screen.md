---
title: "save the terminal screen"
date: 2009-01-27
forum: General Help
---

### Post by lmuri on 2009-01-27
Hello, everyone,

I am writing a console program in Linux. It is necessary for this program to kill the terminal after every run. However, I would like to have the message on the terminal recorded in a file (only the information just before the end of the program is needed).

How can I do that with some bash command, or program code (I use C)?

Thank you in advance.

Sincerely yours
Ming

---

### Post by mobilediesel on 2009-01-27
> **lmuri said:**
> Hello, everyone,

I am writing a console program in Linux. It is necessary for this program to kill the terminal after every run. However, I would like to have the message on the terminal recorded in a file (only the information just before the end of the program is needed).

How can I do that with some bash command, or program code (I use C)?

Thank you in advance.

Sincerely yours
Ming

If you're running the program from the terminal you can redirect it's output. Like this:```
command > file.txt
```
Then whatever message your program outputs will be in the file.txt or whatever filename you use.
Or if you run the program several times, like this:```
command >> file.txt
```
So it appends the latest message to the end of the file instead of overwriting the file every time.

---

### Post by lmuri on 2009-01-27
Thank you.

Your recommendations are really helpful. However, my problem is a little tricky here.

I made my program to autostart after booting using

Exec = xfc4-terminal --working-directory = /path/to/file ./file

When the program is ended unexpectedly, the terminal is ended with it, and I lost all the debug information on the screen. Because there are quite a lot of output and debug information, a log file for all of them is not a practical option since I do not have space to save it. Unfortunately, I do not know where the problem is, so I can not decide where the program will end.

Above is the reason that I am looking for a solution to just record the output of the program just before the termination of the program.

Sincerely yours
Ming

---

### Post by heindsight on 2009-01-27
If you only want the last few lines of output from your program, you could pipe the output through the tail command. For example, if you want the last 40 lines you can do:

```
command | tail -n 40 > output.txt
```

---

### Post by mobilediesel on 2009-01-27
> **lmuri said:**
> Thank you.

Your recommendations are really helpful. However, my problem is a little tricky here.

I made my program to autostart after booting using

Exec = xfc4-terminal --working-directory = /path/to/file ./file

When the program is ended unexpectedly, the terminal is ended with it, and I lost all the debug information on the screen. Because there are quite a lot of output and debug information, a log file for all of them is not a practical option since I do not have space to save it. Unfortunately, I do not know where the problem is, so I can not decide where the program will end.

Above is the reason that I am looking for a solution to just record the output of the program just before the termination of the program.

Sincerely yours
Ming

> **heindsight said:**
> If you only want the last few lines of output from your program, you could pipe the output through the tail command. For example, if you want the last 40 lines you can do:

```
command | tail -n 40 > output.txt
```

I was going to point **[COLOR="Red"][here]("http://www.linuxcommand.org/wss0150.php")[/COLOR]** but tailing the last 40 lines would probably be easier.

---


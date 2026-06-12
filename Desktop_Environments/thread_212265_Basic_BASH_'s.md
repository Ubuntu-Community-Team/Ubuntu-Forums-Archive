---
title: "Basic BASH ?'s"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Kurt_Alan on 2006-07-09
[SIZE="5"]****[/SIZE]

My thread was dropped, so I'm starting again.

I am doing my first shell tutorial from the newly published book by Apress: Keir Thomas's BEGINNING UBUNTU LINUX.

Problem #1

I'm supposed to practice the *less* command with the openoffice readme by entering:

```
 less /usr/lib/openoffice2/README

```

but this fails and I get "No such file or directory."

Question: Exactly what do I enter at the terminal to find this readme??  Did the author make a mistake??

Problem #2

I want to learn how to control jobs.  The author says: "You can see which jobs are running at any one time by typing the following at the shell prompt:

```
jobs
```

It doesn't work.  I just get a repeated prompt when I press ENTER.  And I know I have a job running in Processes: Folding at Home.

How do I access jobs?  Is the author wrong? Why doesn't the command show me jobs?

---

### Post by taurus on 2006-07-09
Maybe you have OpenOffice installed somewhere else instead of in /usr/lib/openoffice2/!!!  

Since you don't have any job running, of course you get a prompt back when you run that command, jobs!!!  Try something like
```

xmms &
jobs

```

---

### Post by jpkotta on 2006-07-09
If you're running Dapper, OO.o is no longer called "2", it's just plain OpenOffice again.  So the file you're trying to open is not there anymore.  Try this command to locate it:
```
locate openoffice | grep -i readme
```
Do these commands to learn what the above means:
```
man locate
man grep
```
You will learn to love grep.

For job control, you can only manipulate jobs that are running in the current shell.  The Folding@Home process is running in a different shell.  Try this:
```
sleep 60 &
jobs
```

---

### Post by Max Luebbe on 2006-07-09
You can use any file in place of that readme.
Download a text file from somewhere and try less on that.

Jobs is the method for doing job control in Linux.
when you type a & after a command, it tells the system to run that command in the background.

to learn more about this, at the prompt type: man jobs
This will bring up a manual page on its usage, you can scroll up and down in.
When you are done, type the q key to return to the prompt.

Hope this helps.

---


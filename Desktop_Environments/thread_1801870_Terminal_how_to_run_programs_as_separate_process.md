---
title: "Terminal: how to run programs as separate process?"
date: 2011-07-11
forum: Desktop Environments
---

### Post by Luke M on 2011-07-11
I want to run programs from Terminal as a separate process, so that for example

gedit file

will launch gedit and return to the terminal prompt (so no need to open up another terminal).

---

### Post by drmrgd on 2011-07-11
You can run the process in the background by appending the command with an "&".  So, to run that, it would look like:

```
gedit <file> &
```

---

### Post by Luke M on 2011-07-11
Thank you! I don't suppose there is any way to do this automatically (for non-console programs)?

---

### Post by Lars Noodén on 2011-07-11
You have to add the ampersand (&) manually each time.

---

### Post by psusi on 2011-07-11
Programs are always run in their own, separate process.  Normally the shell waits for the program to finish before returning to the prompt.  You can run the program in the background, causing the prompt to return immediately by appending  an &, or you can force the current foreground process to the background by hitting ctrl-Z.  This also will suspend the background job, so you may want to allow it to continue to run in the background with the bg command.  When you press ctrl-Z you should see "[n]+ stopped".  The n is the job number, which you can pass to bg as %n.  You can also use the %n as an argument to the kill command.

Jobs running in the background will still spew their output to the terminal, getting it mixed up with whatever else is being output there at the time.  If you are running a gui program, you probably should run it with Alt-F2 instead of from a terminal, so that its output won't be mixed into the terminal window.

---

### Post by Luke M on 2011-07-11
> **psusi said:**
> 
Jobs running in the background will still spew their output to the terminal, getting it mixed up with whatever else is being output there at the time.  If you are running a gui program, you probably should run it with Alt-F2 instead of from a terminal, so that its output won't be mixed into the terminal window.

But alt-F2 loses the current directory.

---

### Post by MG&amp;TL on 2011-07-11
Although I don't understand it totally, I understand that you can 'tweak' the grub commands as shown here:

[http://linuxcommand.org/wss0020.php#aliases]("http://linuxcommand.org/wss0020.php#aliases") (specifically the section under aliases)

If this was not what you were after, I apologize.

Incidentally, this site is particularly good for learning the terminal commands, and makes it almost fun.

---

### Post by Krytarik on 2011-07-11
Luke M, I usually use "setsid" in those occasions, in your example like this:
```
setsid gedit FILENAME
```
But there is also the command "disown", to separate the new process from its parent process after it is started, applied similar to the "&":
```
gedit FILENAME &disown
```
Grettings.

---

### Post by Lars Noodén on 2011-07-11
> **Krytarik said:**
> ...But there is also the command "disown"...

Can you point to some documentation for that one?

EDIT: Never mind.  I see now that "disown" is a built-in part of bash.

---


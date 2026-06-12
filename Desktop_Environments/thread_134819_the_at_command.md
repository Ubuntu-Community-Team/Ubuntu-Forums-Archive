---
title: "the at command"
date: 2006-02-22
forum: Desktop Environments
---

### Post by bortizc on 2006-02-22
I'm trying to work some alarms using the at command and zenity. however the at command doesn't seem to run. It schedules my commands, but it doesn't seem to run them, or at least the zenity window doesn't show up. Is there some setting I have to modify?

---

### Post by BeatBoxRocker on 2006-02-22
I havent used Zenity, but maybe you are not running "at" properly. Try to make a file  and write the command you want to execute with at.  Then execute at (for example):

at 20:00 <createdfile

This will make "at" to run the command that you wrote inside createdfile.  I hope this help you.

Saludos!

---

### Post by bortizc on 2006-02-22
it didn't work.
there is no error message and the command is scheduled, or at least there is a message saying so. However when it is time to run it doesn't. I even tried a simple echo "message" to test, and still it doesn't work.

---

### Post by cwaldbieser on 2006-02-22
[QUOTE=bortizc]it didn't work.
there is no error message and the command is scheduled, or at least there is a message saying so. However when it is time to run it doesn't. I even tried a simple echo "message" to test, and still it doesn't work.[/QUOTE]
What you are trying to do is probably not working because the "at" command, like cron, executes asynchronously, without being attached to a terminal or display.  For your "at" command, try
```

at> echo hello > ~/hello.txt

```
That will likely work, because it creates a file.

For a typical setup, the following "at" command might be similar what you are trying to achieve.
```

$ at '8:55pm'
at> zenity --calendar --display=:0.0
>

```
I specified the value of my $DISPLAY environment variable for the zenity command.  That way, it knows to run attached to my display.

---

### Post by dcstar on 2006-02-23
[QUOTE=bortizc]it didn't work.
there is no error message and the command is scheduled, or at least there is a message saying so. However when it is time to run it doesn't. I even tried a simple echo "message" to test, and still it doesn't work.[/QUOTE]
Install the mailx package, and then in a terminal run "mail" as 'at' should send error messages there.

---

### Post by bortizc on 2006-02-24
thank you so much!!!
it works like a charm now.

---


---
title: "Cron and Konsole"
date: 2009-01-29
forum: Desktop Environments
---

### Post by zzzuppermen on 2009-01-29
Hello!

I manage a small community radio station and we're streaming our shows to a remote IceCast 2 server, too. We use cron to schedule liveice to run at given times. Because the main staff should not need to do a 

```
ps ax | grep liveice
```

I want a simple visual indication that liveice is running. If I run it by hand (typing 'liveice' in the Konsole) I get a nice Peak Level Meter, showing Audio IO, but ran from cron, it sits in the background and possibly dumps everything in /dev/null (or a log file, if given).

My question is: How can I make cron to open up Konsole and run a command?

Any help is appreciated!

T.;)

---

### Post by zzzuppermen on 2009-02-07
Just in case you wondered in. I still can't figure out how to do it. It seems cron is handicapped for background operations. Btw, I abandoned the idea that the streaming server should run on X in terminal, so I installed Ubuntu Server 8.10 and ran everything from CLI.

It's now more a question of console redirection. How to make cron run something in the foreground? Redirection to /dev/tty1 (or any other number) does not work, no matter how many ">" I use. The output is dumped somewhere, so how can I catch it?

---

### Post by mikjp on 2009-02-07
[http://ubuntuforums.org/showthread.php?p=6676512#post6676512](http://ubuntuforums.org/showthread.php?p=6676512#post6676512)

---

### Post by zzzuppermen on 2009-02-10
Thanks! Great thread!

Eventually did the other way around. Since I don't necessarily need use input, I just dumped the output to a tty. The catch with ncurses is that:

> If  standard  output from a ncurses program is re-directed to something which is not a tty, screen  updates  will  be directed to standard error.  This was an undocumented feature of AT&T System V Release 3 curses.

So I needed to specify:

```
liveice &> /dev/tty1
```

All because the beautiful interface went to, you've guessed, stderr. Also, to avoid the "Error opening terminal: unknown" error, I set first:

```
export TERM=linux
```

Note again that I needed merely a visual indication that the stream is running, so the inability to shut it down by pressing "+" can be neglected. For interactivity, see the post above! ;)

Cheers!

---


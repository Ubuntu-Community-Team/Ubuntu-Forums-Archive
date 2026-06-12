---
title: "sending CTRL+BREAK in terminal"
date: 2009-04-27
forum: General Help
---

### Post by gunga-din on 2009-04-27
I am currently using expect to auto-configure some cisco routers via /dev/ttys0 which is working great, trouble is I need to break in to rommon so I can make it load an IOS file from an tftp server, how do I send a CTRL+break in a terminal session, ie is there an ascii code for it or something?

regards


Jason

---

### Post by Arndt on 2009-04-27
> **gunga-din said:**
> I am currently using expect to auto-configure some cisco routers via /dev/ttys0 which is working great, trouble is I need to break in to rommon so I can make it load an IOS file from an tftp server, how do I send a CTRL+break in a terminal session, ie is there an ascii code for it or something?

regards


Jason

Do you need an actual break? It doesn't have an ASCII code, but consists of setting the line to zero for more than the duration of an ordinary character.

Often, however, an ASCII Nul (code 0) will work just as well. You send that by doing Ctrl-@ (and Ctrl-space often works too).

The program you use for connecting ought to have some command to send an actually break, using first an escape character to enter the program's command level.

---

### Post by mixmastamyk on 2011-05-23
Ctrl+\  (backslash) is the closest I believe.

I assume you tried Ctrl+C as well.

---


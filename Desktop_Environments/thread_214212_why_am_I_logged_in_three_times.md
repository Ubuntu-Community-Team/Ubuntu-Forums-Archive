---
title: "why am I logged in three times?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by tefflox on 2006-07-12
I'm learning to write scripts from linuxcommand.org, and one of them calls for the uptime command, which i run and says 3 users, and they are all me when i enter 'users'.  what does this mean?

---

### Post by philippe_carlo on 2006-07-12
Every time you open a terminal window, (a virtual tty), the system considers this to be a separate login. So, opening two terminal windows gives three logons, one for the X-session and two for the terminal windows. Other programs may cause additional logins too.

---

### Post by tefflox on 2006-07-12
how can i tell which programs are using my login?  none of the tty1-6 have me logged in. they all say "login: "

---

### Post by Dubbayoo on 2006-07-12
graphic login is on F7.

---

### Post by philippe_carlo on 2006-07-12
The closest thing I know is to run 'ps -efH'  which shows all process trees and from which you can probably figure out what processes are keeping you logged in. Usually you will find something like this:

xxx 28850  5244  0 17:08 pts/2    00:00:00     bash
xxx 19982 28850  0 19:44 pts/2    00:00:00       ps -efH

this means 'bash' is the root process. So the bash shell counts as a separate login. I know it's not very practical but it should give you what you need.

---


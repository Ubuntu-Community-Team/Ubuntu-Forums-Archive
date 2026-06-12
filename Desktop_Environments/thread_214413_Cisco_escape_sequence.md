---
title: "Cisco escape sequence"
date: 2006-07-12
forum: Desktop Environments
---

### Post by boozer_2 on 2006-07-12
Hello,

  On a cisco device when pinging, tracerouting, etc... one can hit ctrl-shft-6 on a windows box to quit out of the process.  However, this does not work on Ubuntu.  How do I make it so ctrl-shft-6 in ubuntu is the same as it is windows?

Thanks!

---

### Post by jazzmuzik on 2006-07-12
At the command line you can type 'ps aux' and find the process id (pid) of the program you want to kill. Then type something like:

kill -9 <pid>

or 

sudo kill -9 <pid> 

if the program is running as another user.

---

### Post by boozer_2 on 2006-07-21
Thanks for the reply, but its not a process on the linux box I want to kill.  I want to sent the ctrl-shift-6 sequence via the terminal to a remote device.  The problem is that the sequence is ctrl-shift-6 on a windows box, I need to find out how to send the same sequence on a linux box by either:
1. Modifying the ubuntu keymap to send the sequence the same way windows does
2. Modifying the terminal so it sees the sequence and sends it like windows does
3. Finding the key sequence in ubuntu that would be equivilant to the sequence in windows.
4. Some other way :)

Any ideas?

---

### Post by boozer_2 on 2006-07-25
Anyone?

---

### Post by boozer_2 on 2006-08-03
Final bump :-|

---

### Post by boozer_2 on 2006-10-16
Found the answer in case anyone else is curious...

It's ctrl-alt-6 instead of ctrl-shift-6

---


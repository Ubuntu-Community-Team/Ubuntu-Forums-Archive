---
title: "Network printing using a different login name"
date: 2010-07-19
forum: Desktop Environments
---

### Post by leekyuh on 2010-07-19
Hello everyone,

I need to print a document from my Ubuntu machine via network on college's printer server. The printer is correctly found and configured.
To submit a job, it requires that I need to login on my machine using the same ID as my college web ID.
However, I've been using a different login name on my machine for long time and it is very cumbersome to login again to another name only to print stuffs.

So my question is:
Is it possible to submit a printing job as a different user name?
Suppose I use AAA for my machine and BBB is my college ID.
While logged in as AAA, I'd like to print stuffs as a user BBB.
And of course, I could add a user BBB on my machine.

Any ideas?

Thanks,
LQ.

---

### Post by byStanderone on 2010-07-19
...there are admin secutity routines that are implemented in shared printers, bbb will have to be acknowledge by the system before you can access the shared printer...bbb is not listed among the allowed users.

---

### Post by leekyuh on 2010-07-19
> **byStanderone said:**
> ...there are admin secutity routines that are implemented in shared printers, bbb will have to be acknowledge by the system before you can access the shared printer...bbb is not listed among the allowed users.

Thanks for the reply.
Yes, BBB, which I'm assuming to be my college user name, is already allowed on the printer server. (I can print if I log in as BBB.)
Currently, I am logged in as AAA on my local machine. I want to submit a print job as if I were logged in as BBB on my machine, because my local user name AAA is not recognized by the printer server.

I've found a relevant option on printer settings, but it doesn't make any sense to me.
On Printer Properties - Printer Options - Job Storage, I see a "User Name" option which has choices of "System user name" and "Custom". However, there's no text field that I can actually set the value of "Custom", which I want it to be "BBB".

Any ideas?

---

### Post by leekyuh on 2010-07-19
I found that it works at least in Windows 7.

In printer preferences - Job Storage, I changed the Job mode to "Quick Copy" and selected User name to "Custom".
The menus in Windows were almost the same as those in Ubuntu, except that there IS a text box next to the "Custom" option that I can write something on.
I typed my college ID and it worked perfectly!

Now I have to suspect that it is a bug in printer setting menu in Ubuntu where there's no available text box.
I'm using Lucid 10.04 btw.

---

### Post by byStanderone on 2010-07-20
...sorry, got the id's the other way around, anyway am not sure if w7 allows that to be so...seems a security risk if it does.

---

### Post by leekyuh on 2010-07-20
Yeah, it could be, but since it only allows to change "who" submitted the job, I guess it might not be a serious one.
(It requires a student card to be swiped on the printer before printing.)

---


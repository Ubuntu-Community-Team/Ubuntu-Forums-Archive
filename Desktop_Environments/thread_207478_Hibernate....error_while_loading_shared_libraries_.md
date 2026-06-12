---
title: "Hibernate....error while loading shared libraries: libpam.so.0"
date: 2006-07-01
forum: Desktop Environments
---

### Post by javapda on 2006-07-01
Last week I installed Dapper Drake (Ubuntu 6.06) Gnome on my notebook computer.  I had already loaded it on several desktop computers and I LOVE Ubuntu.\\:D/ 

However, today I was going from one office to another and decided to use Hibernate to suspend my computer while traveling.  ~1 hour later I hit the power button to bring the machine out of hibernation....this seemed to take forever.  I could see a mouse cursor...even something that looked like a screensaver but after 20 minutes of nothing I shutdown the computer.

When I brought it back up I was provided a text-mode login.  I entered my user id and I received the message:

[B]/bin/login: error while loading shared libraries: libpam.so.0: cannot open shared object file: Input/output error
[/B]

I tried several logins but each time the same result.  I brought the machine up in recovery mode...but sadly, I am clueless as to how to proceed.  

Any help would be greatly appreciated. :oops: 

Below is what I see on a boot up.  Please help...thanks in advance.
--------------------------------------------------------
[FONT="Courier New"]Ubuntu 6.06 LTS machinename tty1

machinename login:  userid
/bin/login: error while loading shared libraries: libpam.so.0: cannot open shared object file: Input/output error


Machine:  Gateway notebook computer (600YGR) with Pentium 4, 500M memory

Just installed Dapper Drake and all was well.

Had some applications running and put the computer into Hibernate (System => Quit => Hibernate)
[/FONT]

---

### Post by javapda on 2006-07-05
No worries, I used the nuclear option and **rebuilt the system**.

It would have been nice to see some responses though.

All the best.

---


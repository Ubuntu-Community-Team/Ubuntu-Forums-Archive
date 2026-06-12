---
title: "gksu does not appear to enter password"
date: 2007-07-11
forum: Desktop Environments
---

### Post by Lex Luthor on 2007-07-11
Sometimes, when I open an application that requires gksu to operate, the application freezes waiting for the return of gksu, but gksu does not even appear to ask for a password.
The only way is to open a terminal and kill the gksu process or the application. 

Example: 
[LIST=1]
[*]I opened Add/Remove programs
[*]Selected some appls to include/exclude
[*]Clicked the Apply button
[*]the application turns all disabled, waiting for gksu to asks for the password
[*]nothing happens. the application remains that qway until gksu returns, it is in memory, but it did not appear for the user to enter the pass.
[/LIST]

Sometimes it happens, sometimes it does not.

---

### Post by orb9220 on 2007-07-11
> Sometimes, when I open an application that requires gksu to operate, the application freezes waiting for the return of gksu, but gksu does not even appear to ask for a password.

I use gksudo not gksu to open gui apps such as in **gksudo nautilus** not **gksu nautilus** don't know the difference I just never have gksu.

---

### Post by fjgaude on 2007-07-12
I wonder what happens if you sudo the root password, like so:

 sudo passwd root

My gksu and gksudo both work as they should. But I did do the sudo root long ago.

Try it and see if your issues go away.

frank

---

### Post by spinstartshere on 2008-05-25
I'm having the same problem.  I noticed it every once in a while from when I first started using Ubuntu, but at the moment it happens every time something calls gksu.  It appears in the system monitor, but it does nothing.

---

### Post by oct on 2008-06-08
I had the same problem after upgrading from gutsy to hardy. I noticed that when runing any sudo command from the terminal I got a "sudo: unable to resolve host <hostname>". I edited /etc/hosts and modyfied the second line that was 

127.0.1.1 <hostname>.<workgroup_name>

to

127.0.1.1 <hostname>

Now everything seems to work fine. Can you verify if it's the same problem?

Oct

---


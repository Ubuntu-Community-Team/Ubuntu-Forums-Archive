---
title: "electronic circuit simulation software"
date: 2008-11-30
forum: Education &amp; Science
---

### Post by arunkumar413 on 2008-11-30
[SIZE="5"]hey guys is there any one using Oregano 0.69.0, Schematic capture and circuit simulation software.When i try to simulate it's giving an error as 
"[COLOR="Red"]can't open /usr/share/oregano/models/LM555.model, No such file or directory[/COLOR]"
"[COLOR="Red"][COLOR="Red"]### Too few or none analysis found ###[/COLOR][/COLOR]"
please help me.[/SIZE]

---

### Post by dbodden on 2009-01-29
I just tried this last night (I hope you hadn't given up).

I'm not sure exactly what your problem is, but I can tell you that the directory you mention is where oregano keeps some of the metadata about different circuits.

In my /usr/share/oregano/models directory I have the following:

$ ls -l /usr/share/oregano/models/
total 32
-rw-r--r-- 1 root root  276 2007-08-14 02:05 12AX7A.model
-rw-r--r-- 1 root root   67 2007-08-14 02:05 1N4148.model
-rw-r--r-- 1 root root  207 2007-08-14 02:05 1N750.model
-rw-r--r-- 1 root root  125 2007-08-14 02:05 DiodeBridge.model
-rw-r--r-- 1 root root   31 2007-08-14 02:05 NPN.model
-rw-r--r-- 1 root root   31 2007-08-14 02:05 PNP.model
-rw-r--r-- 1 root root  919 2007-08-14 02:05 TLC555.model
-rw-r--r-- 1 root root 1176 2007-08-14 02:05 UA741.model


Did you possibly try to fiddle with the name of the 555 chip to get different behaviour?  I'm not sure how to change the models (yet), but perhaps you could try a basic circuit without that particular component. If it's a component problem, you may need to create a model for it.

You may also benefit from trying to open one of the examples in /usr/share/oregano/examples.

-Doug

---

### Post by john_g8gik on 2009-02-22
Hi Posters out there,

I was wondering if you fixed your Oregano "problem" ?

I am looking to use a linux application to draw some circuit diagrams (schematics) and Oregano looks like an easy way forward.
Some years back I used Orcad SDT ver 3.1 (I think) where we had to build most of our own components using a library editor.

I have played by generating one empty library, by editing the XML in Gedit, but not yet managed to build the DIN41612 connector which would be my first step.

Seems like the user info is difficult to find, how might I go about "posting" my own notes as an "simple user's guide" - after all I'm a "simple" user;)

Best regards to everyone,
Any helpful comments will be most welcome

---

### Post by MySchizoBuddy on 2010-11-28
Is this project dead. the website doesn't exist anymore.

---

### Post by Chronon on 2010-11-28
[COLOR="LemonChiffon"]Probably so.  It isn't in the repositories anymore either.  There are other front-ends for spice.  Search your package manager for "spice" and you should find some.
[/COLOR]
It's in the repositories and mentioned on the ngspice sourceforge page. It's likely that there's just some trouble with the server.

---


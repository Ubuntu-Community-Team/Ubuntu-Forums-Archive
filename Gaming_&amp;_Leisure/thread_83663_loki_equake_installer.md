---
title: "loki equake installer"
date: 2005-10-29
forum: Gaming &amp; Leisure
---

### Post by MarkUK on 2005-10-29
Hi all , 
bit off a noob question here , i'm trying to install the abopve but i think i'm missing something .


from terminal 

mark@mark:~$ sudo sh equake_1.1.0_rcl-english.run
Password:
sh: equake_1.1.0_rcl-english.run: No such file or directory
mark@mark:~$

it asks for password but i cant type anything it then says the file dont exist 
/user/mark/ file name !!

---

### Post by aljones15 on 2005-10-29
chmod +x filename.run

then run it.

peace,
A

---

### Post by aljones15 on 2005-10-29
btw after chmod +x
just down ./filename.run

should work.

peace,
A

---

### Post by MarkUK on 2005-10-29
ok i think i'm still doing something wrong

mark@mark:~$ sh chmod +x equake_1.1.0_rcl-english.run
/bin/chmod: /bin/chmod: cannot execute binary file
mark@mark:~$ sudo sh equake_1.1.0_rcl-english.run
sh: equake_1.1.0_rcl-english.run: No such file or directory
mark@mark:~$

Not having much luck here

---

### Post by themacmeister on 2005-10-30
Hi there,

There is a trick involved here...

make sure you type sudo chmod, not sh chmod

you can also type:

sh filename.run

or

./filename.run

but if it is not a binary executable, ./filename.run does nothing...

Make sure you type sudo ./filename.run (note the ./)

I usually try sh first, and then ./ second

Hope this helps...

themacmeister

---


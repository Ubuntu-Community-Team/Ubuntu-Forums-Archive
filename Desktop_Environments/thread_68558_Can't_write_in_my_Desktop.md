---
title: "Can't write in my Desktop"
date: 2005-09-23
forum: Desktop Environments
---

### Post by engkeboy on 2005-09-23
this is my prob.. 

when im trying to make a folder or put something in desktop.. this error appears...

it says.. 

[B]"Error creating new folder."
"You do not have permissions to write to the destination."[/B]

it means i can't put anything in m desktop..
but im  the only user in this box.. i dont think i dont have permission..

how can i fix this?

any help...

---

### Post by dbott67 on 2005-09-23
[QUOTE=engkeboy]this is my prob.. 

when im trying to make a folder or put something in desktop.. this error appears...

it says.. 

[B]"Error creating new folder."
"You do not have permissions to write to the destination."[/B]

it means i can't put anything in m desktop..
but im  the only user in this box.. i dont think i dont have permission..

how can i fix this?

any help...[/QUOTE]

Check the ownership & permissions on your Desktop folder (~/Desktop or /home/user/Desktop).

[[IMG]http://leovilletownsquare.com/uploads/med_1127495286-permissions.jpg[/IMG] ](http://leovilletownsquare.com/uploads/1127495286-permissions.jpg) 

-Dave

---

### Post by engkeboy on 2005-09-23
[QUOTE=dbott67]Check the ownership & permissions on your Desktop folder (~/Desktop or /home/user/Desktop).

[[IMG]http://leovilletownsquare.com/uploads/med_1127495286-permissions.jpg[/IMG] ](http://leovilletownsquare.com/uploads/1127495286-permissions.jpg) 

-Dave[/QUOTE]


THIS IS WHY I LOVE UBUNTU!!! they are helping.. : )

but, when i go to dekstop-properties.. It says **"You are not the owner, so you can't change these permissions"**

[IMG]http://www.geocities.com/engkeb0i/prm2.jpg[/IMG] 

also, in the icon of my **Desktop** there's somethin.. what that icon means?

[IMG]http://www.geocities.com/engkeb0i/dsk2.jpg[/IMG]

---

### Post by dbott67 on 2005-09-23
You'll have to use the command "chown" (change ownership) of the Desktop folder.

Type "man chown" from the command line to get the full details.

Good luck!

-Dave

---

### Post by engkeboy on 2005-09-23
gotcha! hehehe.. i should read guides.. 
thanx for the help!

---


---
title: "useradd username  not reflected in gnome &quot;users and groups&quot;"
date: 2007-03-19
forum: Desktop Environments
---

### Post by Badwulf on 2007-03-19
Running edgy ubuntu

Added a user 'oracle' using standard command useradd etc .  Since this user is to own the oracle software it is dynamically built using a standardised script.  All well and good, the user was built.  Password added and I can log in as oracle on the command line correctly. 

I wished to add an auxiliary group to this user, so created the group librarian on the command line.  Again all has worked OK as you would expect. Assigned the group to the user no problem.  In command line world all is well.

The issue for me is that when on my desktop i fire up the "user and groups" program.  the user name oracle is NOT visible in the list of users whilst the group i created IS

Why is this, makes no logical sense to me. 

Probably missing something obvious but i don't know what it is  ... surely the fact that the user 'oracle' home directory is not hanging of /home cant be relevant?

Is there some procedure that needs to be followed having manually added a user? thank you for your thoughts in advance.

John

---

### Post by zvacet on 2007-03-19
I hope this will help.

---

### Post by Badwulf on 2007-03-19
thank you for taking the time to answer :)   i am aware of the user/group graphical tools though ....  My issue is that having created a user in the command line using useradd  (a requirement for what I am doing)  the user does not then show up in the graphical tool "user and groups" list of users.

However groups i have created do show up in the graphical list of groups..

is this a bug or by design?  Or is there a further action i need to take.

---

### Post by Badwulf on 2007-03-22
BUMP ...

surely this is a simple problem?

---

### Post by Badwulf on 2007-03-27
A week ago i posted this and nobody has an opinion??.  seems quite a major issue to me if the graphical tool for displaying/modifying users, does not display all of the users!

---

### Post by Badwulf on 2007-04-09
Got to say that I am not wildly impressed with the response on this issue, i.e none.

Found out the solution, the graphical User maintenance tool in gnome only displays users with an ID higher than 1024, my oracle user i was creating with an ID in the 200's

Hopefully this will be useful to somebody else on here :

John

---

### Post by sadris on 2008-01-07
"graphical User maintenance tool in gnome only displays users with an ID higher than 1024

Is this a hard-coded setting?

I lowered the number FIRST_UID in /etc/adduser.conf to 500 and uid-min in /etc/gnome-system-tools/users/profile to 500 as I have a user at id=507 but said user still does not show up in the graphical Administration > Users and Groups tool.

---


---
title: "How to connect to a specific network location"
date: 2009-05-27
forum: General Help
---

### Post by sudoomar on 2009-05-27
hello

i used to work on vista...our universitty provides us with a wireless internet connection (using a certificate)...

now to connect to the printer of the university i used to digit a command like this in run in windows :
\\dimiwinserver.ing.university.it
then a login screen appears and i login with my university password

how to do this in ubuntu?

---

### Post by sudoomar on 2009-05-27
now i can see the printer but how to set the user and pass?

---

### Post by s.fox on 2009-05-27
Hi,

Can you please tell us which version of ubuntu you are using.

Thanks,

-Ash R

EDIT:  Ninjad :D

---

### Post by HereInOz on 2009-05-27
That looks like you are connecting to a print server of some description.  Ordinarily when you enter a command like that, you are looking to open a folder on a networked host, so I guess that is the sort of thing that you are doing, only accessing a shared printer instead (bit of a guess here).

Linux generally does not work all that well with Windows NETBIOS names, so I am thinking that if you can get hold of the actual IP address of the print server (\\dimiwinserver.ing.university.it) and use the connect to server function in Places, and connect to it as a Windows share, you might (I repeat, MIGHT) get lucky and see what you need to see.

Other than that, you may need to get more information from the Uni IT people and give that information here.  

What happens after you enter your username and password? How then do you print?

---

### Post by s.fox on 2009-05-27
Hey,

[This]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu") piece of documentation should be of some use to you.

-Ash R

---

### Post by sudoomar on 2009-05-27
> **Ash R said:**
> Hi,

Can you please tell us which version of ubuntu you are using.

Thanks,

-Ash R

EDIT:  Ninjad :D

i am using ubuntu 8.10

---

### Post by sudoomar on 2009-05-27
> **HereInOz said:**
> That looks like you are connecting to a print server of some description.  Ordinarily when you enter a command like that, you are looking to open a folder on a networked host, so I guess that is the sort of thing that you are doing, only accessing a shared printer instead (bit of a guess here).

Linux generally does not work all that well with Windows NETBIOS names, so I am thinking that if you can get hold of the actual IP address of the print server (\\dimiwinserver.ing.university.it) and use the connect to server function in Places, and connect to it as a Windows share, you might (I repeat, MIGHT) get lucky and see what you need to see.

Other than that, you may need to get more information from the Uni IT people and give that information here.  

What happens after you enter your username and password? How then do you print?

thanks your reply sounds helpfeul

when i used my printer ip it prompted me to the normal login page
but it says password incorrect
the shared computer is visible in my printers.. but i just need to access it now

---


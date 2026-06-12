---
title: "Not as lost as some...but need an answer"
date: 2009-05-17
forum: General Help
---

### Post by Irishe on 2009-05-17
):P Everyone,
i Have ubuntu 8.04 and Love it and really enjoy the KDE desktop too.
Compiz is Soo cool too. i also use Build 9.04 on my Laptop in virtualbox,
but i'm very new to ubuntu. 

Anyways, what i'm curious about is How can i get Root Permissions?
i want to be able to move/delete/edit whatever file i feel like and
i can't figure out how to get root permissions..Globally :(

i set me a user Pw when i installed it but don't know how to get
Root Permissions.

---

### Post by Carl Hamlin on 2009-05-17
If you preface your commands with 'sudo', they'll run as root without exposing you to the potential security hazards associated with running as a user with permanent root privileges.

---

### Post by geirha on 2009-05-17
One way is to run the file explorer (nautilus in gnome) as root. You do that by hitting Alt+F2 to get the run dialog, and type ```
gksudo nautilus
``` The password it asks for is the same password you use to log in with your user.

Another option is to install the package [nautilus-gksu](apt:nautilus-gksu). If you install it, log out and log back in again for it to load. After that, you can right click a file or folder and choose "Open as Administrator".

---

### Post by Irishe on 2009-05-17
Thanks,
i've Done a little work in Dos before and
 Get the idea behind the Terminal.
now just to learn the commands. 
Thanks for your idea [geirha]("http://ubuntuforums.org/member.php?u=243323"), Nautilus
might be a better option for me.

again, Thanks. i'll let ya know how it goes.
i just want to be able to remove the 3rd party
software that i can't remove through the 
add/remove panel.

---

### Post by geirha on 2009-05-17
How did you install the third party software? If you installed it via a .deb-file or third-party repository, then you should uninstall it using synaptic or apt-get.

---

### Post by Irishe on 2009-05-17
> **geirha said:**
> One way is to run the file explorer (nautilus in gnome) as root. You do that by hitting Alt+F2 to get the run dialog, and type ```
gksudo nautilus
``` The password it asks for is the same password you use to log in with your user.

Another option is to install the package [nautilus-gksu]("apt:nautilus-gksu"). If you install it, log out and log back in again for it to load. After that, you can right click a file or folder and choose "Open as Administrator".


That Option Worked Perfect.


Again Thanks Loads

---

### Post by Irishe on 2009-05-17
well after-the-fact i did find it within the synaptic pkg manager.
i guess just for future reference i should check both.
Thanks though. i did need that answer as well.

i'm not familar with the commands for the terminal.
is there a place i can get a copy of the most used ones?

---

### Post by bacardiandwatermelon on 2009-05-17
First thing that came up on google.. :-)

[]("http://www.ss64.com/bash/")[http://www.reallylinux.com/docs/basic.shtml](http://www.reallylinux.com/docs/basic.shtml)

---


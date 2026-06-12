---
title: "Root password does not work"
date: 2005-05-08
forum: Desktop Environments
---

### Post by PaulSauer on 2005-05-08
When ever I try to run update or synaptic it gives me a WRONG PASSWORD error.
But I can SU in a terminal , no problem.
I,m not new to Linux , but this is my first Ubuntu install.
It looks great .
Can anyone help ?
Thanks Paul

---

### Post by dave9191 on 2005-05-08
Are you sure that its asking you for the root password and not your user password. Ubunutu doesnt set a root password during install and wants you to use sudo all the way through. Menu items like synaptic will expect you password and not the root one that you may have set yourself. 

Dave

---

### Post by PaulSauer on 2005-05-08
Thanks , I tryed my user password, but nothing launches.
If I try it again , I get an error " child terminated with 1 status"

---

### Post by bored2k on 2005-05-08
[QUOTE=PaulSauer]Thanks , I tryed my user password, but nothing launches.
If I try it again , I get an error " child terminated with 1 status"[/QUOTE]
 Try
sudo passwd 
to reset your root password.

If problems persist, run apps like synaptic via sudo synaptic.

---

### Post by PaulSauer on 2005-05-08
What is this sudo stuff ?
Do I use a terminal ?

---

### Post by dave9191 on 2005-05-08
in ubunutu you dont get a root account to play with (unless u set the pass yourself). 

You can run root commands using the sudo prefix and entering your own password. Any additional users can also get sudo privalages if they are added into the sudo-er list. You add the sudo prefix b4 any command in the console that you wish to run as root.

---

### Post by bored2k on 2005-05-08
[QUOTE=PaulSauer]What is this sudo stuff ?
Do I use a terminal ?[/QUOTE]
 Yes.
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---


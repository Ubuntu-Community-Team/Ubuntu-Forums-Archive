---
title: "Backing up Cedega, important if you no longer subscribe !!!"
date: 2006-05-02
forum: Gaming &amp; Leisure
---

### Post by handy on 2006-05-02
I had a quick search & could not find, what I know is there: 

My question:

Do I only have to backup the /home/.cedega/ directory to have a Cedega that I can restore if needs be in the future?

Thanks for your time! :KS

---

### Post by Perfect Storm on 2006-05-02
Aye. Backup all of it, if you gonna clean install ubuntu.

---

### Post by handy on 2006-05-02
[QUOTE=Artificial Intelligence]Aye. Backup all of it, if you gonna clean install ubuntu.[/QUOTE]

Thanks AI,

I just have to verify, that there are no other cedega files anywhere else on the system, apart from those in ** /home/.cedega/** ??

I am not doing a fresh install, I just want to be able to reinstall cedega from backup if I have to, without being forced to take out a new subscription!

When I understand how cedega installs itself, meaning, when I know where all of its files go, then I will know what I have to do!

So, hopefully, **ALL** the files required for cedega to run are in the /home/.cedega directory?

Any input on this will be most welcome... :KS

---

### Post by Perfect Storm on 2006-05-02
Also .trasgaming_global because it contains fonts and moz-controller plus misc.

---

### Post by handy on 2006-05-02
[QUOTE=Artificial Intelligence]Also .trasgaming_global because it contains fonts and moz-controller plus misc.[/QUOTE]

Thanks AI, looks like that covers it!

Cheers! :KS

---

### Post by ubuntu_demon on 2006-05-05
[QUOTE=handy]Thanks AI, looks like that covers it!

Cheers! :KS[/QUOTE]
try this to be sure you have found all : (I don't have cedega installed so I don't know where it stores all it's stuff)

$ locate cedega

---

### Post by handy on 2006-05-05
[QUOTE=ubuntu_demon]try this to be sure you have found all : (I don't have cedega installed so I don't know where it stores all it's stuff)

$ locate cedega[/QUOTE]

[B]
Thanks Ubuntu_Demon![/B]

That is a good command to know.  It showed me that there is only one directory called **cedega**, & that it is the hidden  **/home/.cedega**

A most interesting & useful thing happened as the **locate** command was searching, I saw another path flash by, which was not listed in the results:

**/usr/lib/transgaming_cedega**

*So, my backup list has now grown to include the following:*

[B]/home/handy/.cedega

/home/handy/.transgaming_global

/usr/lib/trangaming_cedega[/B]

I have to wonder if there are any other related files hiding in the system somewhere?

At least it's nothing like the windoze mess usually is, with .dll (dill), .ini & other arcane files spread all over the place, with the registry created to be as complicated as possible, just to insure that no one can back up an individual application!

---

### Post by ubuntu_demon on 2006-05-06
to update the database where locate gets it's information do this :
$ sudo updatedb 

now try locate once again (edega to capture Cedega and cedega) :
$ locate edega

try searching in (online) cedega documentation about where stuff gets installed.

Also if you have multiple pc's you could try to copy the files to another Ubuntu box and see if cedega still works on that pc. Or you could do the same on a different Ubuntu installation on a different partition(if you know how to install another Ubuntu installation next to this one).


If you installed application by installing a .deb you still have you can see where everything gets installed by doing this command : dpkg -c applicationx.deb

the executable is probably :
/usr/bin/cedega

the man page is probably :
/usr/share/man/man1/cedega.1.gz

documentation is probably in this directory :
/usr/share/doc/cedega/

---


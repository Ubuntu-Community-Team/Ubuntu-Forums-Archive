---
title: "How to find specific code inside files with &quot;find&quot;"
date: 2009-03-12
forum: General Help
---

### Post by mirkko22 on 2009-03-12
Hi all

I would like to know how to find a specific piece of code inside all files of my PC with command find...

In fact actually if I need to find for example the term "myterm" located in one or more files (like html, php,...) I use the following command:

find /home/user/folder -name "*.*" -execdir egrep -H '.*myterm.*' '{}' ';' -execdir pwd ';' 

This command will list all files with any extension where inside are located the term "myterm" and this command work very well...But if I want find the same term writted "Myterm" what kind of command I must use ?? When using a term starting with a CAPS character this command don't find nothing...

any idea ?

thanks in advance...

---

### Post by &amp;wP*!) on 2009-03-12
> **mirkko22 said:**
> Hi all

I would like to know how to find a specific piece of code inside all files of my PC with command find...

In fact actually if I need to find for example the term "myterm" located in one or more files (like html, php,...) I use the following command:

find /home/user/folder -name "*.*" -execdir egrep -H '.*myterm.*' '{}' ';' -execdir pwd ';' 

This command will list all files with any extension where inside are located the term "myterm" and this command work very well...But if I want find the same term writted "Myterm" what kind of command I must use ?? When using a term starting with a CAPS character this command don't find nothing...

any idea ?

thanks in advance...

You can use "ignorecase" feature of grep:
```
find /home/user/folder \( -name '*.*' \) -exec grep -il myterm {} \;
```
-i stands for ignorecase.
-l gives the filename which includes the string "myterm" with ignore case.

HTH.

---

### Post by mirkko22 on 2009-03-12
thanks for your help...

Anyway I have find another very nice and simple command:

grep -rli Myterm /home/user/folder

this command permit me to find any term with or without uper/lower case and in any files....It is exactly what I need...cool :-)

---

### Post by mirkko22 on 2009-03-12
In fact the command

```
grep -rli myterm /home/user/myfolder
```

don't take care to uper or lower case...It is because in my files the 2 terms exist and I have think it is correct like that....

So for resume and be clear=>

For search "myterm" and/or "Myterm" the command are:

```
find /home/user/myfolder -name "*.*" -execdir grep -Hi 'myterm' '{}' ';' -execdir pwd ';'
```


For search only "Myterm" the command are:

```
find /home/user/myfolder -name "*.*" -execdir grep -H 'Myterm' '{}' ';' -execdir pwd ';'
```


For search only "myterm" the command are:

```
find /home/user/myfolder -name "*.*" -execdir grep -H 'myterm' '{}' ';' -execdir pwd ';'
```

thank to all for your help and patience....that very hard to be a newbie  :oops:  :lol:  :D

---


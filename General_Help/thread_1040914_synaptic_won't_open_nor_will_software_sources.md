---
title: "synaptic won't open nor will software sources"
date: 2009-01-16
forum: General Help
---

### Post by tomkacz on 2009-01-16
As the title says, Synaptic won't open nor will software sources in administration. Add/remove programs just hangs when I try and use it and the update manager does the same. Using command line seems to work.  I've used 
sudo apt-get -f install 

with success.  No error messages seem to be displayed. When I try and open synaptic and software sources the computer just thinks about it and then does nothing. 
I'm running Ubuntu 8.04 Hardy.

Any ideas out there?

---

### Post by ajcham on 2009-01-16
Could you try:
```
gksu synaptic
``` from the terminal, and seeing if that gives any errors?

---

### Post by tomkacz on 2009-01-16
> **ajcham said:**
> Could you try:
```
gksu synaptic
``` from the terminal, and seeing if that gives any errors?

funny.....just tried that and no errors I'm downloading as we speak

---

### Post by ajcham on 2009-01-16
But it still won't open from the menu?

Could you right-click on Applications, and select 'Edit Menus'.  Scroll down to find System » Administration.  Highlight Synaptic in the list and click Properties to find out what command it is trying to run.

---

### Post by tomkacz on 2009-01-16
> **ajcham said:**
> But it still won't open from the menu?

Could you right-click on Applications, and select 'Edit Menus'.  Scroll down to find System » Administration.  Highlight Synaptic in the list and click Properties to find out what command it is trying to run.

It's trying to run:

gksu /usr/sbin/synaptic

---

### Post by Zack McCool on 2009-01-16
First thing: Check the information in your /etc/hosts file.  You should have a line that looks something like this:

```

127.0.1.1       barada.griffincs.local barada

```

But with your fully qualified domain name, followed by your machine name.  If this has been messed up, it can cause the symptom you are having...

---

### Post by blazemore on 2009-01-16
Clarification:

To output the contents of a file, use the cat command
```
cat /etc/hosts
```

To edit a file, you can use gedit
```
gedit /etc/hosts
```

If you were wondering.

---

### Post by tomkacz on 2009-01-16
> **Zack McCool said:**
> First thing: Check the information in your /etc/hosts file.  You should have a line that looks something like this:

```

127.0.1.1       barada.griffincs.local barada

```

But with your fully qualified domain name, followed by your machine name.  If this has been messed up, it can cause the symptom you are having...

Ok here is the line....127.0.1.1 tomkacz-desktop.local anything missing?

---

### Post by tomkacz on 2009-01-16
thanks for those command lines.....still a bit rusty in that world

---

### Post by tomkacz on 2009-01-16
ok.....all is good....that was the issue.  the computer's name was not repeated on in the line of code. Thank you all for your help and patience!!

---


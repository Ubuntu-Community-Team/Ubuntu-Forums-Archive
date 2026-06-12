---
title: "From kubuntu to Ubuntu [SOLVED]"
date: 2009-02-04
forum: General Help
---

### Post by nikolaiortiz on 2009-02-04
Please.. i want to change Kubuntu 8.10 to Ubuntu..
whit out reinstall all.

i mean, i want gnome desk.
why?
because kde 4. is terrible some help please

---

### Post by blazemore on 2009-02-04
just run from a terminal
```
sudo apt-get install ubuntu-desktop
```

Then log out, click the Sessions menu and choose Gnome.
Let it be set as your default.

Then go through and uninstall all the kde stuff.

---

### Post by tmcarson1 on 2009-02-04
Start up the Synaptic Package Manager, and do a search for
ubuntu-desktop

This will install all you need to use ubuntu instead, then next time you log into kubuntu, there will be an option there to use ubuntu/gnome.

Good luck!

---

### Post by mmitt on 2009-02-04
I think you can just install gnome like this:
```
sudo apt-get install ubuntu-desktop
```
And log out when it has completed and go to settings > sessions > GNOME.

---

### Post by OrangeCrate on 2009-02-04
> **nikolaiortiz said:**
> Please.. i want to change Kubuntu 8.10 to Ubuntu..
whit out reinstall all.

i mean, i want gnome desk.
why?
because kde 4. is terrible some help please

In addition to what the others have said, here's the instructions to remove all the KDE stuff, after you've added the Gnome desktop:

[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by blazemore on 2009-02-04
I think the Psychocats thing is out of date, as Kubuntu now uses KDE4 and a lot of different packages.

---

### Post by OrangeCrate on 2009-02-04
> **blazemore said:**
> I think the Psychocats thing is out of date, as Kubuntu now uses KDE4 and a lot of different packages.

I'll give Asiyu a heads up, and have him take a look...

:)

---

### Post by blazemore on 2009-02-04
It will take a bit of effort.

It will involve looking at the contents of kubuntu-desktop, and removing everything that's not also in ubuntu-desktop.

---

### Post by aysiu on 2009-02-04
It's updated now.

---

### Post by nikolaiortiz on 2009-02-20
thanx i will try now.. 
i been away to much time ...
i will post the results..

---

### Post by nikolaiortiz on 2009-02-27
all works ..
thanx!!!
how i mark this as solved?

---


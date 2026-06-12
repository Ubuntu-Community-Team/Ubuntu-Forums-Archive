---
title: "how do i tell add/remove that it should look at the install cd for the program?"
date: 2009-02-07
forum: General Help
---

### Post by Frogster on 2009-02-07
I am having a nightmare getting my wmp54g working reliably. 

So i removed ndiswrapper the nm applet with the intention of reinstalling them. 

My problem is that Add/remove will not look to the cd to reinstall these apps. How do i force it to check the cd rather than telling me it cant fetch them from the internet????

---

### Post by 2hot6ft2 on 2009-02-07
System>Administration>Software sources>Third-Party Software tab
Add CD-ROM

---

### Post by Frogster on 2009-02-07
Hmmmm I would have thought so as well but all i get told is that the list of applications is unavailable

---

### Post by editrix on 2009-02-08
As I understand it, you can only use the CD rom to install individual programs if it's the *alternate* install CD.

If you need a particular package, you should have a package search option in your Firefox search engine menu (at the top right). If not, [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by drs305 on 2009-02-08
There are a couple of things to keep in mind about CD sources. First, the CD listed in the Ubuntu Software tab is the CD that was used to originally install the system. If you installed *gutsy* but then did a *dist-upgrade* to *hardy* online, the CD would still be the listed as the *gutsy* CD. You should look at the CD listing in "sources.list" to make sure you are inserting the correct CD. For instance, I keep my computer up-to-date, but the CD listing is still for the beta disk with which I installed *intrepid*
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta amd64 (20081001)]/ intrepid main restricted

```

I can add the latest *intrepid* LiveCD to the list without problems.

Also, you can't just add any CD with packages on it. The file structure must be one known to ubuntu, similar to the way the packages are stored in the repositories ( for instance: .../dists/intrepid/main ). That is one of the reasons you need something like *APTonCD* to build CD repositories.

---

### Post by Frogster on 2009-02-08
Thanks everyone. Still scratching my head with this one.

I am using the initial install CD but when I go to use it ubuntu tries to download an updated list. Then just closes *shrugs shoulders*

I will just get everything in tar form and reinstall

Cheers for your help

---

### Post by oldos2er on 2009-02-08
Did you try disabling all repositories while enabling the CD?

---


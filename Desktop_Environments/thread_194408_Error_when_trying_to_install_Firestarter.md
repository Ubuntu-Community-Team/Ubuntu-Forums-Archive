---
title: "Error when trying to install Firestarter"
date: 2006-06-11
forum: Desktop Environments
---

### Post by kingedwin on 2006-06-11
A couple days ago, while trying to set up a wifi network, I installed Firestarter without any difficulty, but uninstalled it later.

Now when try to install Firestarter, I get the error

E: firestarter: subprocess post-installation script returned error exit status 3

I can run Firestarter from the terminal, but I get an error window saying that a proper configuration has not been found, and then it exits.  The only differences are that my wifi network is up, and I've updated my computer with Update Manager and Synaptic.

What is this error, and how can I fix it?

---

### Post by goodfella on 2006-06-13
I had the same problem when I updated to 6.06.  I seemed to have solved it by selecting to remove the package completely from the synaptic package manager and then reinstalling.  Now I have no trouble running firestarter.

---

### Post by scxtt on 2006-06-13
yeah, if you don't "remove completely" it will leave config files behind - and it would seem that the re-install didn't like the existance of those 'left overs' ...

---

### Post by kingedwin on 2006-06-14
Aha!  Fixed.  Thank you.

---


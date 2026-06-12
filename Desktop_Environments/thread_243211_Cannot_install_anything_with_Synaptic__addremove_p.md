---
title: "Cannot install anything with Synaptic / add/remove programs"
date: 2006-08-24
forum: Desktop Environments
---

### Post by GUIPEnguin on 2006-08-24
I can sudo apt-get update file...I can get out to the internet and reach the repositories.

I can ping out fine, as well as surf the internet with firefox, my internet connection is fine.

When using add/remove programs, every package that would have to be downloaded via the internet, I get : 'packagename' is not avalible in any software channel: The application might not support your system.

this is incorrect, because I am running an Intel x68 Pentium 4. I have not had a problem with this utility a few months ago.

When I launch Synaptic package manager, and select to install a package from the internet, I get: You should check that you have a valid internet connection.

I am assuming that I am getting the arch issue because the add/remove programs cant contact the internet.  What is up with this?

---

### Post by apjone on 2006-08-25
try sudo apt-get install -f , this should fix your problem

---


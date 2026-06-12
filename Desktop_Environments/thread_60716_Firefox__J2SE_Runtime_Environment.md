---
title: "Firefox / J2SE Runtime Environment"
date: 2005-08-29
forum: Desktop Environments
---

### Post by Aniquibobo on 2005-08-29
Hi

Try to install J2SE Runtime Environment on Firefox, but not working.
I use this:

sudo apt-get install sun-j2re1.5

and i get this:

E: Couldn't find package sun-j2re1.5

Any tips ?

Many thanks.

---

### Post by snpz on 2005-08-29
What does sudo apt-cache search sun-j2re1.5 say?
I think that there is no repository listed in your sources.list file that contains sun-j2re1.5

---

### Post by wellery on 2005-08-29
Make sure you add the extra repositories:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

The ubuntu guide will also tell you how to install and configure other things"

 [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by Aniquibobo on 2005-08-29
[QUOTE=snpz]What does sudo apt-cache search sun-j2re1.5 say?
I think that there is no repository listed in your sources.list file that contains sun-j2re1.5[/QUOTE]

Hi
I get this
...
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_d ists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or dir ectory)
...

---

### Post by snpz on 2005-08-29
U fallowed instructions from [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories) ?
After editing sources.list file do sudo apt-get update and then try to search j2se one more time!

---

### Post by Aniquibobo on 2005-08-29
[QUOTE=wellery]Make sure you add the extra repositories:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

The ubuntu guide will also tell you how to install and configure other things"

 [http://www.ubuntuguide.org](http://www.ubuntuguide.org)[/QUOTE]

Hi

Yes i have made this changes...

Still trying... :)

---

### Post by snpz on 2005-08-29
There is no error message when doing sudo apt-get update ?

---

### Post by Aniquibobo on 2005-08-29
[QUOTE=snpz]There is no error message when doing sudo apt-get update ?[/QUOTE]
No...update works nice...

---

### Post by snpz on 2005-08-29
Tryed the same using Synaptic?

I installed j2se from package provided in java.com

---

### Post by Aniquibobo on 2005-08-29
[QUOTE=snpz]Tryed the same using Synaptic?

I installed j2se from package provided in java.com[/QUOTE]


Synaptic = ???

sorry
(newbie)

---

### Post by Aniquibobo on 2005-08-29
Hi

It works now.... :smile: 

Many thanks for all tips/help.

Thank you.

---

### Post by snpz on 2005-08-29
Synaptic = package management software!;)
[http://www.ubuntuguide.org/#synaptic](http://www.ubuntuguide.org/#synaptic)

---

### Post by Aniquibobo on 2005-08-29
> **snpz]Synaptic = package management software! said:**
> http://www.ubuntuguide.org/#synaptic[/url]

Many thanks...nice...

---


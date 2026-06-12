---
title: "Backing up downloaded repositories"
date: 2009-01-24
forum: General Help
---

### Post by josamoto on 2009-01-24
Hi all!

Bandwidth is expensive in South Africa, so my question is as follows; is it possible to make a backup of the repositories downloaded by things like "apt-get update" and downloads made by the Update Manager.

Let's say I have to reinstall Ubuntu, coz I did something really stupid, I have to format my harddrive and lose all the updates I made, right!

Can I put make my own repository on for example my external harddrive?

Do excuse the noob questions...

:)

---

### Post by bgerlich on 2009-01-24
The packages apt-get downloads are stored in /var/cache/apt/archives/ . You can copy them from there. You can also use [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) or remastersys to create your own customised install disk using your current system as a base.

---

### Post by josamoto on 2009-01-25
Wow!
Ubuntu is soooo cool!
Thanks!

:)

PS: Windows sucks!

---


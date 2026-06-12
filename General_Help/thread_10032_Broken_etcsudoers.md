---
title: "Broken /etc/sudoers"
date: 2005-01-04
forum: General Help
---

### Post by rolando on 2005-01-04
Oh dear

I installed the firestarter firewall and was happily adding a line to allow me to start it as sudo without entering the password

The silly thing I did was edit /etc/sudoers in ScITE and not visudo and now whenever I run sudo I get a parse error.

The problem is I cannot edit it unless I have super user privileges, 

What can I do?

I have spent ages refining my desktop and adding programs so that my system is just so.

Can I run the installation CD and pick a certain option to enable myself to boot as root with a command line and re-install the file /etc/sudoers to its original format.

Any sensible suggestions greatly appreciated.

---

### Post by jbh on 2005-01-04
yep

[http://ubuntuguide.org/#rescuemode](http://ubuntuguide.org/#rescuemode)

or you could pop in a live CD like Ubuntu Live or Knoppix and do it.

---

### Post by rolando on 2005-01-04
Thanks, ill try that when I get home.  Better get on with some work now!!

---

### Post by jbh on 2005-01-04
i'd better get on with some sleep now. it's 4:00am here. o_O

---

### Post by rbran100 on 2005-01-04
Arn't they both the same anyway? Hope you don't have to wake up as early as i do!

---

### Post by rolando on 2005-01-04
Thanks that worked a treat!!

bit scary how easy it is to get root access tho, maybe I should password grub.

Thanks again

Rolando

---


---
title: "Help, I need help fixing my Ubuntu installation. I am new to Ubuntu."
date: 2009-05-15
forum: General Help
---

### Post by DerPoltergeist13 on 2009-05-15
I followed the instructions here trying to get the old Amarok
[http://helpforlinux.blogspot.com/2009/05/get-amarok-14-in-kubuntu-904.html](http://helpforlinux.blogspot.com/2009/05/get-amarok-14-in-kubuntu-904.html)

After I completed that operation I went to install some software in the add/remove programs and this error message pops up

----
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
---
--
I follow those instructions, but they do not work. I get this error message in the terminal
----
---
E: Type 'sudo' is not known on line 6 in source list /etc/apt/sources.list.d/amarok.list
---

What can I do to fix this? I can't delete those amarok files in the /etc/apt folder because it says permission denied. I use the newest Ubuntu 9.04

---

### Post by kanikilu on 2009-05-15
Open a terminal (Applications > Accessories > Terminal) and type ```
gksu gedit /etc/apt/sources.list.d/amarok.list
``` You should now have access to fix that file and save it.

If you don't know how to fix it, just copy and paste the contents of that file into a reply here, and we should be able to tell you what's wrong...

If you just want to delete it, you can open a root file browser with ```
gksu nautilus
```

Take care when using sudo (or gksu) because you are elevating your permissions to root and can damage your install if you don't know what you are doing...

---

### Post by DerPoltergeist13 on 2009-05-15
Thank you very much!

---

### Post by michy99 on 2009-05-15
Never mind already corrected.

---


---
title: "Order of execution of startup scripts"
date: 2009-02-12
forum: General Help
---

### Post by Tony Flury on 2009-02-12
Can someone point me to a definiitve statement on the order in which the various start up scripts on Ubuntu are executed, and specifcially the context in which they are educated.

Thanks.

---

### Post by Slim Odds on 2009-02-12
not to be stupid, but /etc/init.d/

I has all the scripts. You can look at them and see how they work.

Was there a specific question that you had?

---

### Post by Tony Flury on 2009-02-12
and what about /etc/rc.local ? - which clearly is not in that directory.

---

### Post by Slim Odds on 2009-02-12
Try this: [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

or this: [http://www.linux.com/feature/125977?theme=print](http://www.linux.com/feature/125977?theme=print)

---

### Post by Tony Flury on 2009-02-13
Thanks slim - but again both of these describe the init scripts (primarily i think used to initialise deamons) - which is not the full range of scripts this is exexcuted - for instance where/when is /etc/rc,local run - what happens before and after it ?

---

### Post by Tony Flury on 2009-02-16
Can anyone assist me - sorry for bumping, but i have absolutely no luck tracking down the information i need.

Specifically - i want to know when in the boot up sequence is /etc/rc.local run, and what else runs before and after it.

---

### Post by railrodder on 2009-02-22
When the system starts the scripts are executed from /etc/rc.n where n is the run level.

if you look in there you will find these are all links to /etc/init.d/

I believe that they are executed in sequence from the rc.n directory.

rc.local is executed after all other scripts are executed.

---

### Post by Tony Flury on 2009-02-25
railrodder : thank you - one last question then - what is "run level" and how do i determine what mine is ?

---


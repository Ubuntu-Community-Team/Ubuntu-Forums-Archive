---
title: "SAS License"
date: 2010-01-16
forum: Education &amp; Science
---

### Post by shaunsmith_99 on 2010-01-16
I'm doing some research and getting ready to apply for a PhD program in Statistics. I'm kind of in Limbo right now and maybe some folks have been in smilar experiences and can offer some pointers.

   Basically, I need access to SAS but have none. I can use it on the school's public computers during normal business hours, but I'd like to be able to run it at home.

 I can't get a SAS license from the Statistics departement because I'm technically in the Quality Department, and the quality dept won't give me a license because even though they bought 25 and have issued none of them, nobody seems to know where they are or who is in charge of them.  I called SAS and they don't issue any licenses to students, although I CAN purchase an independent license for $9,500 (Yeah freakin' right). 

  Does anybody know a 3rd party where I can buy or lease a SAS license on a years term?

---

### Post by cybergalvez on 2010-01-16
can you ssh in to one of the campus computers and use sas from the shell account?

---

### Post by shaunsmith_99 on 2010-01-17
> **cybergalvez said:**
> can you ssh in to one of the campus computers and use sas from the shell account?

 
 Thats an option, but my problem is that even for ssh they shut the server down at 5:00. It's a problem I've had before when I ran SAS from home. :(

---

### Post by earlycj5 on 2010-01-19
> **shaunsmith_99 said:**
> Thats an option, but my problem is that even for ssh they shut the server down at 5:00. It's a problem I've had before when I ran SAS from home. :(

You're here at K-State?

K-State Unix (the default if you just SSH in) has SAS installed.  You can use a ssh -X session and launch SAS.  That server is never shut down, or at least certainly not at 5:00.

```

localcomputerprompt:~> ssh -X username@unix.ksu.edu

pub1% sas

```

That should get you up and running.

---

### Post by shaunsmith_99 on 2010-01-20
> **earlycj5 said:**
> You're here at K-State?

K-State Unix (the default if you just SSH in) has SAS installed.  You can use a ssh -X session and launch SAS.  That server is never shut down, or at least certainly not at 5:00.

```

localcomputerprompt:~> ssh -X username@unix.ksu.edu

pub1% sas

```That should get you up and running.


HOLY COW it's working!!! THANK YOU THANK YOU!

---

### Post by earlycj5 on 2010-01-20
> **shaunsmith_99 said:**
> HOLY COW it's working!!! THANK YOU THANK YOU!

Glad I could help. :)

---


---
title: "lost without a traces..."
date: 2006-08-15
forum: Desktop Environments
---

### Post by klgsx on 2006-08-15
I downloaded the Sun Java System Active Server Pages 4.0.2 and i am going out of my mind trying to install this thing without a clue.

First, this is what i am trying to do.  I have installed the apache2 and rebooted pc. dont ask me why- old windows habits.

After that i browsed my local host to see if the site(apache) was working? (see image attached)

Since i am a GUI kind of guy (aleast for the time been) i dowloaded the Sun Java System ASP to allow me to manage Apache.  i followed the instruction there which ask me to create a directory and copy the .tar file to that directory.  After that, it asked me to run type  ./install.sh and this where hell is freeeeezzzzeeeiiing over.


anthony@ALPHA:~/sun$ ls
EULA        package     README                 THIRDPARTYLICENSEREADME.txt
install.sh  QuickStart  sjsasp402-sol-x86.tar
anthony@ALPHA:~/sun$

anthony@ALPHA:~/sun$ ./install.sh
bash: ./install.sh: /bin/ksh: bad interpreter: No such file or directory
anthony@ALPHA:~/sun$

What am i doing wrong?

Any suggestions is welcome

thanks

](*,)

---

### Post by -deadcats on 2006-08-15
Try "sudo ./install.sh" or "sudo sh install.sh" but first make the file executable.

regards,
-dc

---

### Post by llamakc on 2006-08-15
Are you only looking for a gui-based administration program for apache2? How about webmin instead?

---

### Post by klgsx on 2006-08-15
even more lost.. try every single "sudo" command i have learned in the last 3 days.

and this is what i get..

---

### Post by llamakc on 2006-08-15
To start, instead of posting images of screenshots just copy/paste the terminal output here. You can wrap them in the [ code ] tags.

2nd: you would have wanted to to do this:

sudo ./install.sh

and not the permutations you kept trying.

Last, do you realize you downloaded a Solaris package? What architecture are you on, and once more, what is your goal?

Why do you need this package installed? If apache2 is running what can this software offer you?

---

### Post by klgsx on 2006-08-15
:-(

Sorry about the post, just getting getting frustrate... so here is what i am trying to do.   :-({|= 

1)  Looking for a GUI program that will allow me to configure/manage my Apache Server.

2)  I am also looking for a "software" solution that will allow me to host "ASP" pages in my apache.

Any suggestions?

---

### Post by fluffnik on 2006-08-15
Is the first line of ./install.sh this?
```
#!/bin/ksh
```

Solaris uses ksh rather than bash as its default *interactive* shell - someone at Sun has been sloppy, they should have used /bin/sh.

I have both AT&T ksh and the public domain pdksh available in Synaptic - I suspect ksh is multiverse - installing one of those should help.

---

### Post by klgsx on 2006-08-15
yes.. first line is

#!/bin/ksh

---

### Post by fluffnik on 2006-08-16
> **klgsx said:**
> yes.. first line is

#!/bin/ksh

```
sudo apt-get install ksh

```
should get you up and running then.  :)

---


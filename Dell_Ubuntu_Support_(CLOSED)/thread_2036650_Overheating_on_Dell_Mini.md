---
title: "Overheating on Dell Mini?"
date: 2012-08-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Janeleaper on 2012-08-02
We have a Dell Inspiron Mini running Ubuntu 10.04.  I loaded the 10.04 last year after the previous version of Ubuntu it had been running was obsolete, but the Dell hadn't been used since.

My OH took the Dell to Vienna to do research in an archive, and found it kept freezing and the file he was working on would be lost or corrupted.  He also noted it was very hot.  He was working in hot weather, and the machine had usually been switched on for an hour or two.  

Since he got back, I've tried out the Dell myself and found that 10.04 seems to be working fine, except that the machine does get very hot, even in a normal ambient temperature.

I'm considering loading a more recent version of Ubuntu.  What do forum members think the cause of the problem is?

---

### Post by ugm6hr on 2012-08-03
The Mini 9 gets hot under normal conditions. Are you sure it is different than before?
Run a vacuum over the fan vents to remove accumulated dust, just to be sure.
But intermittent freezing sounds like a software issue / shortage of RAM rather than overheating to me.

---

### Post by Janeleaper on 2012-08-05
Thanks for the reply.  You are probably right, but I don't see how it can be shortage of RAM either.  It's only used for word processing (Open Office), email and Skype.  

When my OH was using it at the Austrian State Archive, he would not have had any applications open other than Open Office.  

I'm going to update it to 12.04 and Libre Office, then use it myself for a while and see how it goes.

---

### Post by Janeleaper on 2012-08-05
Thanks for the reply.  You are probably right, but I don't see how it can be shortage of RAM either.  It's only used for word processing (Open Office), email and Skype.  

When my OH was using it at the Austrian State Archive, he would not have had any applications open other than Open Office.  

I'm going to update it to 12.04 and Libre Office, then use it myself for a while and see how it goes.

---

### Post by mikewhatever on 2012-08-05
Try running 'top' in a terminal window to make sure nothing is stuck with 100% CPU usage (press 'q' to quit).

After that, can you post the output of lspci.

---

### Post by ugm6hr on 2012-08-06
Just so you are aware, Ubuntu 12.04 does run on Mini 9, but I found it very slow - a substantial change from 10.04.
I am now running Lubuntu 12.04 on mine, which is perhaps not as good for ease of use with some things, but is very quick if you don't need to plug into other monitors / projectors etc.

---


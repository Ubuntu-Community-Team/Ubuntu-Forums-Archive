---
title: "terminal emulator for ubuntu &quot;hyper term&quot; for configuring switches"
date: 2009-06-05
forum: General Help
---

### Post by luke0927 on 2009-06-05
OK i had to configure some brocade switches today and for the basic first config you have to connect serial cable and console in.  I have always used hyper term for this in Windows.  I downloaded mini com but im not sure how to configure the settings.  For example when connecting in windows its 9600 baud, flow control and parity settings etc....the command it had for linux in the guide is a TIP command which is not recognized in ubuntu.  Hows the best way to do this in Ubuntu

---

### Post by jonobr on 2009-06-05
Hello

If you have minicom installed, you should be able to run it from the terminal by typing minicom

WHen the modem is initialised,
you need to hit control - a , that will show you your current settings

see attached pics for the default settings of minicom
Pic Number 1 shows the current settings on my machine ( the bottom shows the parameters)

Notice mine is on 115 with 8N1

You can change this to whatever you need 
by hitting z

see second attachment 

Hit P for comm parameters, here you need to select 9600 or whatever you need.

See attached again.

Once you have that setup the trick is finding what tty your on,
If you find one that has junk on it, and if your used to hyperterm, you know thats the one you need and its settings are wrong.

Play around until you get the right settings
[ATTACH]116545[/ATTACH]

[ATTACH]116546[/ATTACH]

[ATTACH]116547[/ATTACH]

---

### Post by luke0927 on 2009-06-06
Thanks!  just what i needed.

---

### Post by jonobr on 2009-06-06
excellent.

Best of luck with config

---


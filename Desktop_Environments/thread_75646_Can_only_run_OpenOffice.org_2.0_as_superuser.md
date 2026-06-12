---
title: "Can only run OpenOffice.org 2.0 as superuser"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Scoodaddy on 2005-10-14
Just upgraded from Hoary to Breezy, and having OpenOffice problems (I uninstalled the old version and installed version 2):

I cannot start OpenOffice.org 2.0 from my ordinary user account.  If I click on the "OpenOffice.org2 Writer" menu choice, I get a bar on the bottom screen panel reading "Starting OpenOffice.org2 Writer" for a few seconds, then it disappears without starting the program or generating any error message.

If I run "ooffice2 -writer &" in a terminal, absolutely nothing appears on screen, but when I check I see that there are processes running for soffice and soffice.bin.

If instead I run "sudo ooffice2 -writer &" then OpenOffice starts just fine.

How do I get OpenOffice to run normally, without using sudo?  How did this get screwed up?  The old version worked fine under Hoary.

Thanks,
Tom

---

### Post by buldir on 2005-10-14
Since you installed it as root (I assume), it's a permissions problem:

```
cd /your_openoffice_install_location/program
sudo chmod 755 soffice
```

My OO directory is /opt/openoffice.org1.9.125/

---

### Post by Scoodaddy on 2005-10-14
[QUOTE=buldir]Since you installed it as root (I assume), it's a permissions problem:

```
cd /your_openoffice_install_location/program
sudo chmod 755 soffice
```

My OO directory is /opt/openoffice.org1.9.125/[/QUOTE]

Thanks buldir, I'll give it a try when I get home tonight.  If I installed it as root I did it unintentionally (and I'm not sure how I did it).  I upgraded to Breezy using apt-get, after which I noticed that I still had the older OpenOffice version installed, so I used Synaptic to uninstall it and to install version 2.  I never entered my root password until well after I had experienced the problem, at which time I used su in a terminal window to see if I could run OO as root, which indeed I could.  So AFAICT all the installing was done through my regular user account.  But (if you couldn't tell) I'm pretty much a newbie about all this, so maybe I'm missing something obvious.

---

### Post by buldir on 2005-10-14
You may also find that the owner and group for the soffice program are listed as "nobody". If so, in the program directory of your OO install location, do:  

```
sudo chown root soffice
sudo chgrp root soffice
```
Also check the permissions and owner of your .openoffice2 directory in your home directory, if its been created. In your home directory:

```
ls -al
```

There seems to be problems with the Ubuntu forums at the moment, this may get posted twice. A lot of users now that Breezy is out.

---

### Post by Scoodaddy on 2005-10-14
Thanks for all the info, buldir!  I'll see what I can do with it tonight.  I know little enough about all this that I'm probably posting in the wrong forum, so I appreciate your help.

---


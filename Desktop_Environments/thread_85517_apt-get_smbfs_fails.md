---
title: "apt-get smbfs fails"
date: 2005-11-02
forum: Desktop Environments
---

### Post by dgermann on 2005-11-02
Hi--

OK, I have done as suggested here to get my sources.list up to date: [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")

But when I do apt-get install smbfs, I get this: > smbfs:
  Depends: samba-common (=3.0.10-1ubuntu3) but 3.0.14a-3ubuntu3~5.04ubp1 is to be installed

Anybody got any great ideas for how to solve this dependency? 

I supposed I could uninstall samba-common, and the see what happens. However, when I select that for removal in Synaptic, it says the Ubuntu Desktop is to be removed as well. That does not sound like a good thing to do....

---

### Post by teaker1s on 2005-11-02
install the dependency first then it will install okay
sudo apt-get samba-common

---

### Post by dgermann on 2005-11-03
teaker1s--

OK, I tried that, and got this: >  # sudo apt-get install samba-common
Reading package lists... Done
Building dependency tree... Done
samba-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Looks to me like the first message I got, last night, was telling me that the dependency that smbfs calls for is incorrect in some way. Makes no sense to me, given the version numbers.

Do you see anything else to try here?

---

### Post by teaker1s on 2005-11-03
I think I see the problem, being new to ubuntu  too I can suggest the issue but I'm not 100% on how to sort it and possible risks-someone else will know more than me

the issue appears to be that the samba-common in repositories different version to the one  smbfs wants- now as I understand it smbfs is specifying 3.0.10 
normally a higher version wouldn't cause program to complain-i'd look at
[http://samba.org/samba/smbfs/](http://samba.org/samba/smbfs/)
either download and ./configure make make install the latest version
or contact the person maintaining it and see what they say

sorry I can't suggest more but I know very little more on dependencies etc

---

### Post by schdefan on 2005-11-05
Did you run also an apt-get dist-upgrade or an apt-get uprade to upgrade your packages because on the link they only describe how to update the sources.
If you don't want to upgrade your entire ubuntu just reinstall samba-common with apt-get --reinstall install samba-common


schdefan

---

### Post by dgermann on 2005-11-05
schdefan--

Thanks!

```

 # apt-get --reinstall install samba-common
Reading package lists... Done
Building dependency tree... Done
Reinstallation of samba-common is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

It really sounded like a wonderful idea. Thanks for your help.

I think I will try to do a dist upgrade and hopefully that will solve it. I do have smbfs on a Breezy box.

I also tried notifying the person who maintains smbfs, but the e-mail bounced, with a message that the host was not accepting e-mail at that address. <sigh>

Thanks for your help. I will report back.

---

### Post by schdefan on 2005-11-06
try to remove the samba-common package with apt-get remove samba-common and reinstall it.

---

### Post by dgermann on 2005-11-06
schdefan--

OK, as you sagely suggested, I upgraded the box to Breezy and seem to have it going now.

Thanks for all your help. You have given me more confidence!

---


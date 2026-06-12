---
title: "upgrade from 8.04 to 9.04"
date: 2009-05-07
forum: General Help
---

### Post by Tarmalo on 2009-05-07
I'm trying to upgrade from 8.04 to 9.04 but my update manager dosent give me the option to upgrade my version of ubuntu. How do i upgrade it? Can someone please help?

---

### Post by Tarmalo on 2009-05-07
I also tried using the terminal but all i got was this:
> josh-n-megan@josh-n-megan-laptop:~$ sudo do-release-upgrade
[sudo] password for josh-n-megan: 
Checking for a new ubuntu release
No new release found


---

### Post by Tarmalo on 2009-05-07
I'm trying to upgrade from 8.04 to 9.04 but my update manager dosent give me the option to upgrade my version of ubuntu. How do i upgrade it? Can someone please help?

---

### Post by Tarmalo on 2009-05-07
I also tried using the terminal to upgrade but all I got was this:
> josh-n-megan@josh-n-megan-laptop:~$ sudo do-release-upgrade
[sudo] password for josh-n-megan:
Checking for a new ubuntu release
No new release found 

Any help?

---

### Post by darkstaar on 2009-05-07
Doing a fresh installation of 9.04 would be faster than upgrading from 8.04 anyway...assuming that you have a separate /home partition.

---

### Post by raymondh on 2009-05-07
> **Tarmalo said:**
> I'm trying to upgrade from 8.04 to 9.04 but my update manager dosent give me the option to upgrade my version of ubuntu. How do i upgrade it? Can someone please help?

Upgrading thru the network .... you've got to bump up to 8.10 ibex first then bump up again to 9.04.

If willing, do a fresh install

---

### Post by colau on 2009-05-07
> **Tarmalo said:**
> I also tried using the terminal to upgrade but all I got was this:


Any help?
[html]
aptitude safe-upgrade
[/html]

---

### Post by Tarmalo on 2009-05-07
this is what i got when I entered that in aptitude safe-upgrade:
```
josh-n-megan@josh-n-megan-laptop:~$ sudo aptitude safe-upgrade
[sudo] password for josh-n-megan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  
```

Also, if i have to upgrade to 8.10 then how can I do it without a using a cd or using a usb?

---

### Post by colau on 2009-05-07
> **Tarmalo said:**
> this is what i got when I entered that in aptitude safe-upgrade:
```
josh-n-megan@josh-n-megan-laptop:~$ sudo aptitude safe-upgrade
[sudo] password for josh-n-megan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  
```

Also, if i have to upgrade to 8.10 then how can I do it without a using a cd or using a usb?
Go to System>Administration>Update Manager
See ubuntu 9.04 release is available or not.
If it is available click upgrade.

---

### Post by Acapulco on 2009-05-07
I had this same problem. All you have to do is go to System, Administration (or Preferences, I can't remember) then Sources. There you should check something along the lines of "show full distribution upgrades" or similar.

Sorry to be so vague but you will recognize it easily. You basically have to tell the Upgrade Manager to show every type of update, and not only the ones for your version.

Cheers.

---

### Post by Tarmalo on 2009-05-08
problem solved! thank you Acapulco!

---

### Post by raymondh on 2009-05-08
Glad you got that solved.

It'll help forum members/posters if you could mark the thread solved.  Some day, a poster may have the same problem as you had, will search the forum and will see how you managed to solve it.  :)

Go to your first post > edit > advanced > click on the beginning of the thread title > type solved > save

Again, glad you got your dilemna solved.

---

### Post by bapoumba on 2009-05-08
Threads merged.

---


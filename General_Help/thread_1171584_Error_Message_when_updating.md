---
title: "Error Message when updating"
date: 2009-05-27
forum: General Help
---

### Post by harecanada on 2009-05-27
Hello,

Would anybody know why I get this error message when I am updating or checking for updates in Jaunty?

Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages)  404 Not Found [IP: 212.72.53.130 80]
Some index files failed to download, they have been ignored, or old ones used instead.

harecanada

---

### Post by ActiveFrost on 2009-05-27
Your url is dead - it does not exist ( open it manually and you'll see a nice 404 /welcome message/ ).

AMD64 Skype:
```
http://www.skype.com/go/getskype-linux-ubuntu-amd64
```

---

### Post by taurus on 2009-05-27
Maybe because the repo is dead.  So, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and either remove that line or put a # in front of it to comment it out.  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by harecanada on 2009-05-28
Thanks for the help .
I tried your suggestion Active Frost but it didn't work(yet)
taurus I did what you suggested and it seemed to work. not getting errors but there is still something I want to try. I really appreciate the help you guys.
Thanks,
harecanada

---

### Post by harecanada on 2009-05-29
Here is what I get at the end when I sudo update:

harecanada@harecanada-desktop:~$ sudo apt-get update
[sudo] password for harecanada: 

Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources
Hit [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Packages
Hit [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources                                        
Fetched 9157B in 6s (1443B/s)                                                  
Reading package lists... Done
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
harecanada@harecanada-desktop:~$ 

I don't know what this all means of course.
harecanada

---

### Post by harecanada on 2009-06-01
I don't understand what Ign , Hit and the rest of the stuff means. Can someone help me out? I tried sudo apt-get update to correct these problems and it didn't change anything. Are they really problems to be concerned about?


Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Packages
Get:13 [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources
Ign [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources
Hit [ftp://ftp.mysql.com](ftp://ftp.mysql.com) binary/ Packages
Hit [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources 
Fetched 9157B in 6s (1443B/s) 
Reading package lists... Done
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems




harecanada

---


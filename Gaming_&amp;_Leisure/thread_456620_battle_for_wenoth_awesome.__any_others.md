---
title: "battle for wenoth: awesome.  any others?"
date: 2007-05-27
forum: Gaming &amp; Leisure
---

### Post by antiemptyv on 2007-05-27
so, my girlfriend and i just got into playing battle for wesnoth, and think it's pretty awesome.  what are some other games that are on par with that one?  i can't seem to find another one quite as good.  thanks.

---

### Post by rufius on 2007-05-27
Its easily one of the best. I really like it. I'd say scorched3d and bzflag are two classics. Both excellent.

---

### Post by jacksaff on 2007-05-28
Neverball
Fillets ng
Supertux
Pingus
Liquid war (looks crap but cool game)
Nexuiz and Saurbraten if you're into fps
and of course the most important of all, kpat

---

### Post by antiemptyv on 2007-05-31
thanks!  yeah those are some great suggestions, and i've played a few of them.  BUT are there any that are the same kind of rpg/adventure style as wesnoth AND as good?  i'm beginning to think not.

---

### Post by hikaricore on 2007-05-31
Wesnoth isn't really an RPG.

However, Hero of Allacrost is, and seems to be coming together quite nicely. [http://www.allacrost.org/](http://www.allacrost.org/)
At the moment it's only out in demo form, but the next release is just around the corner from what I hear.

If you feel like surfing around, I suggest checking out the native game database on gwos: [http://doc.gwos.org/index.php/Native_Games](http://doc.gwos.org/index.php/Native_Games)
You might find something of interest there.  ^_^

--Aaron :: UGA

---

### Post by jacksaff on 2007-05-31
Falcon's Eye - lots of other nethack clones too...
Egoboo
lgeneral

---

### Post by KingHanco on 2007-07-19
Hero of Allacrost - How I install this? [http://www.allacrost.org/](http://www.allacrost.org/)

I done this and I can't install it.

```
mitchell@pc-desktop:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
OK
mitchell@pc-desktop:~$ sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
--16:19:10--  http://medibuntu.sos-sts.com/sources.list.d/feisty.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving medibuntu.sos-sts.com... 81.169.138.125
Connecting to medibuntu.sos-sts.com|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

100%[====================================>] 233           --.--K/s             

16:19:10 (15.44 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [233/233]

mitchell@pc-desktop:~$ deb http://debian.ettin.org/allacrost etch-backports main
bash: deb: command not found
mitchell@pc-desktop:~$ wget http://debian.ettin.org/key.gpg -O - | sudo apt-key add -
--16:19:42--  http://debian.ettin.org/key.gpg
           => `-'
Resolving debian.ettin.org... 208.113.179.173
Connecting to debian.ettin.org|208.113.179.173|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,945 (2.9K) [text/plain]

100%[=================================================================================================================>] 2,945         --.--K/s             

16:19:42 (62.55 KB/s) - `-' saved [2945/2945]

OK
mitchell@pc-desktop:~$ apt-get update && apt-get install allacrost-demo
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
mitchell@pc-desktop:~$
```

Ubuntu 7.04

---

### Post by cogadh on 2007-07-19
Your last command was incorrect, you forgot the "sudo". It should be:
```
sudo apt-get update && apt-get install allacrost-demo
```
BTW - Next time, instead of resurrecting an old, dead thread that really has nothing to do with the problem you are having, you should probably start a new thread specifically for your problem.

---

### Post by zekopeko on 2007-07-19
> **KingHanco said:**
> Hero of Allacrost - How I install this? [http://www.allacrost.org/](http://www.allacrost.org/)

I done this and I can't install it.

```
mitchell@pc-desktop:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
OK
mitchell@pc-desktop:~$ sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
--16:19:10--  http://medibuntu.sos-sts.com/sources.list.d/feisty.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving medibuntu.sos-sts.com... 81.169.138.125
Connecting to medibuntu.sos-sts.com|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

100%[====================================>] 233           --.--K/s             

16:19:10 (15.44 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [233/233]

mitchell@pc-desktop:~$ deb http://debian.ettin.org/allacrost etch-backports main
bash: deb: command not found
mitchell@pc-desktop:~$ wget http://debian.ettin.org/key.gpg -O - | sudo apt-key add -
--16:19:42--  http://debian.ettin.org/key.gpg
           => `-'
Resolving debian.ettin.org... 208.113.179.173
Connecting to debian.ettin.org|208.113.179.173|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,945 (2.9K) [text/plain]

100%[=================================================================================================================>] 2,945         --.--K/s             

16:19:42 (62.55 KB/s) - `-' saved [2945/2945]

OK
mitchell@pc-desktop:~$ apt-get update && apt-get install allacrost-demo
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
mitchell@pc-desktop:~$
```

Ubuntu 7.04

you have to put ```
 sudo
``` in front of the last command. and you have to add this line to your System>Administration>Software Sources

```
http://debian.ettin.org/allacrost etch-backports main
```

---

### Post by KingHanco on 2007-07-19
Heh.

```
mitchell@pc-desktop:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
OK
mitchell@pc-desktop:~$ sudo apt-get update && apt-get install allacrost-demo
Get:1 http://debian.ettin.org etch-backports Release.gpg [189B]
Ign http://debian.ettin.org etch-backports/main Translation-en_US              
Hit http://debian.ettin.org etch-backports Release                             
Ign http://debian.ettin.org etch-backports/main Packages                       
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Hit http://debian.ettin.org etch-backports/main Packages                       
Get:3 http://wine.budgetdedicated.com feisty Release.gpg [191B]                
Ign http://wine.budgetdedicated.com feisty/main Translation-en_US              
Get:4 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US 
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release               
Get:5 http://packages.medibuntu.org feisty Release.gpg [189B]                  
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Get:6 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B] 
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Hit http://wine.budgetdedicated.com feisty Release                   
Hit http://us.archive.ubuntu.com feisty Release                                
Hit http://security.ubuntu.com feisty-security/main Packages                   
Ign http://packages.medibuntu.org feisty/free Translation-en_US                
Ign http://packages.medibuntu.org feisty/non-free Translation-en_US            
Hit http://us.archive.ubuntu.com feisty-updates Release              
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://security.ubuntu.com feisty-security/main Sources                    
Hit http://security.ubuntu.com feisty-security/restricted Sources    
Ign http://wine.budgetdedicated.com feisty/main Packages                       
Hit http://packages.medibuntu.org feisty Release                               
Hit http://us.archive.ubuntu.com feisty/main Packages                          
Hit http://us.archive.ubuntu.com feisty/restricted Packages          
Hit http://us.archive.ubuntu.com feisty/main Sources                 
Hit http://us.archive.ubuntu.com feisty/restricted Sources           
Hit http://security.ubuntu.com feisty-security/universe Packages     
Hit http://security.ubuntu.com feisty-security/universe Sources      
Hit http://security.ubuntu.com feisty-security/multiverse Packages   
Hit http://security.ubuntu.com feisty-security/multiverse Sources    
Hit http://wine.budgetdedicated.com feisty/main Sources              
Ign http://packages.medibuntu.org feisty/free Packages               
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources         
Hit http://wine.budgetdedicated.com feisty/main Packages             
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources   
Ign http://packages.medibuntu.org feisty/non-free Packages
Ign http://packages.medibuntu.org feisty/free Sources
Ign http://packages.medibuntu.org feisty/non-free Sources
Hit http://packages.medibuntu.org feisty/free Packages
Hit http://packages.medibuntu.org feisty/non-free Packages
Hit http://packages.medibuntu.org feisty/free Sources
Hit http://packages.medibuntu.org feisty/non-free Sources
Fetched 194B in 2s (90B/s)
Reading package lists... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mitchell@pc-desktop:~$
```

There is noway this will work. Unless it will not work on 7.04

---

### Post by cogadh on 2007-07-19
Try running that last command as two separate commands. First run:
```
sudo apt-get update
```
and after the update finishes, run this:
```
sudo apt-get install allacrost-demo
```
As long as the repository is correctly added and you have the correct package name, this will work.

---

### Post by KingHanco on 2007-07-19
Thanks

---


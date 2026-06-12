---
title: "I need your help- install XGL"
date: 2007-03-03
forum: Desktop Environments
---

### Post by Treeckcold57 on 2007-03-03
Read this: [http://www.rage3d.com/board/showthread.php?t=33883960](http://www.rage3d.com/board/showthread.php?t=33883960)

```
elitex455@elitex455-desktop:~$ wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
--17:16:48--  http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
           => `-'
Resolving ubuntu.beryl-project.org... 195.114.19.35, 64.15.154.150, 80.77.247.17, ...
Connecting to ubuntu.beryl-project.org|195.114.19.35|:80... Password:connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,415 (2.4K) [application/octet-stream]

100%[====================================>] 2,415         --.--K/s            

17:16:49 (209.37 MB/s) - `-' saved [2415/2415]






Sorry, try again.
Password:
OK
elitex455@elitex455-desktop:~$ # Treviño's Beryl-SVN Ubuntu Repository
elitex455@elitex455-desktop:~$    # GPG key: 81836EBF
elitex455@elitex455-desktop:~$    deb http://3v1n0.tuxfamily.org dapper beryl-svn
bash: deb: command not found
elitex455@elitex455-desktop:~$ #Beryl Repositories for Edgy Eft (Ubuntu 6.10)
elitex455@elitex455-desktop:~$ deb http://ubuntu.beryl-project.org/ edgy main
bash: deb: command not found
elitex455@elitex455-desktop:~$ wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add - root@lupine.me.uk.
--17:42:45--  http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
           => `-'
Resolving ubuntu.beryl-project.org... 195.114.19.35, 64.15.154.150, 80.77.247.17, ...
Connecting to ubuntu.beryl-project.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,415 (2.4K) [application/octet-stream]

100%[====================================>] 2,415         --.--K/s            

17:42:45 (1.09 MB/s) - `-' saved [2415/2415]

OK
elitex455@elitex455-desktop:~$ wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add - KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
--17:43:57--  http://www.beerorkid.com/compiz/quinn.key.asc
           => `-'
Resolving www.beerorkid.com... 208.113.136.19
Connecting to www.beerorkid.com|208.113.136.19|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,692 (1.7K) [text/plain]

100%[====================================>] 1,692         --.--K/s            

17:43:58 (18.37 KB/s) - `-' saved [1692/1692]

OK
gpg: directory `/home/elitex455/.gnupg' created
gpg: new configuration file `/home/elitex455/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/elitex455/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/elitex455/.gnupg/secring.gpg' created
gpg: keyring `/home/elitex455/.gnupg/pubring.gpg' created
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
elitex455@elitex455-desktop:~$

```what?

EDIT: Update....

```
elitex455@elitex455-desktop:~$ wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add - KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
--17:43:57--  http://www.beerorkid.com/compiz/quinn.key.asc
           => `-'
Resolving www.beerorkid.com... 208.113.136.19
Connecting to www.beerorkid.com|208.113.136.19|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,692 (1.7K) [text/plain]

100%[====================================>] 1,692         --.--K/s            

17:43:58 (18.37 KB/s) - `-' saved [1692/1692]

OK
gpg: directory `/home/elitex455/.gnupg' created
gpg: new configuration file `/home/elitex455/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/elitex455/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/elitex455/.gnupg/secring.gpg' created
gpg: keyring `/home/elitex455/.gnupg/pubring.gpg' created
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
elitex455@elitex455-desktop:~$    wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
--17:50:57--  http://www.beerorkid.com/compiz/quinn.key.asc
           => `-'
Resolving www.beerorkid.com... 208.113.136.19
Connecting to www.beerorkid.com|208.113.136.19|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,692 (1.7K) [text/plain]

100%[====================================>] 1,692         --.--K/s            

17:50:58 (17.94 KB/s) - `-' saved [1692/1692]

OK
elitex455@elitex455-desktop:~$ KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
gpg: requesting key 81836EBF from hkp server subkeys.pgp.net
gpg: /home/elitex455/.gnupg/trustdb.gpg: trustdb created
gpg: key 81836EBF: public key "Treviño (3v1n0) <trevi55@gmail.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
OK
elitex455@elitex455-desktop:~$    sudo apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Get:2 http://us.archive.ubuntu.com edgy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release
Hit http://security.ubuntu.com edgy-security/main Packages          
Hit http://us.archive.ubuntu.com edgy-updates Release              
Hit http://security.ubuntu.com edgy-security/restricted Packages    
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://us.archive.ubuntu.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Fetched 3B in 0s (5B/s)  
Reading package lists... Done
elitex455@elitex455-desktop:~$ sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-themes
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Note, selecting libgl1-mesa-glx instead of libgl1-mesa
libgl1-mesa-glx is already the newest version.
xserver-xorg is already the newest version.
E: Couldn't find package beryl
elitex455@elitex455-desktop:~$

```it say cant find package beryl

what give?


thanks


sorry, my english is bad.

EDIT: also see my last post.

---

### Post by lukem on 2007-03-03
If you have not done so already, you might try adding additional repositories in Synaptic Package Manager.  I have added everything availaable and I see beryl when I search for it.

Good Luck

Luke

---

### Post by Treeckcold57 on 2007-03-03
I did add repos in synaptic package manager and then I run terminal ( I did follow in [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Adding_the_Beryl_Project_repositories](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Adding_the_Beryl_Project_repositories) )

like this:

```
elitex455@elitex455-desktop:~$  sudo apt-get update
Password:
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Get:2 http://us.archive.ubuntu.com edgy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US        
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US  
Get:3 http://ubuntu.beryl-project.org edgy Release.gpg [191B]        
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release                
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US    
Get:4 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]  
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release                      
Ign http://ubuntu.beryl-project.org edgy/main Translation-en_US                
Hit http://us.archive.ubuntu.com edgy-updates Release                
Hit http://security.ubuntu.com edgy-security/main Packages                    
Hit http://us.archive.ubuntu.com edgy/main Packages                            
Hit http://us.archive.ubuntu.com edgy/restricted Packages            
Hit http://us.archive.ubuntu.com edgy/main Sources                  
Hit http://us.archive.ubuntu.com edgy/restricted Sources            
Hit http://security.ubuntu.com edgy-security/restricted Packages    
Hit http://security.ubuntu.com edgy-security/main Sources            
Hit http://security.ubuntu.com edgy-security/restricted Sources      
Hit http://ubuntu.beryl-project.org edgy Release                    
Hit http://security.ubuntu.com edgy-security/universe Packages      
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://ubuntu.beryl-project.org edgy/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Fetched 194B in 0s (310B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
elitex455@elitex455-desktop:~$ /var/lib/dpkg/
bash: /var/lib/dpkg/: is a directory
elitex455@elitex455-desktop:~$ $ sudo apt-get update
bash: $: command not found
elitex455@elitex455-desktop:~$  sudo apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US                        
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]                                                                                    
Ign http://security.ubuntu.com edgy-security/main Translation-en_US                                                                                  
Get:2 http://us.archive.ubuntu.com edgy Release.gpg [191B]                                                                                            
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US        
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US  
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release                
Get:3 http://ubuntu.beryl-project.org edgy Release.gpg [191B]        
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US    
Get:4 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]  
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release                      
Ign http://ubuntu.beryl-project.org edgy/main Translation-en_US                          
Hit http://us.archive.ubuntu.com edgy-updates Release                
Hit http://security.ubuntu.com edgy-security/main Packages                                
Hit http://us.archive.ubuntu.com edgy/main Packages                                      
Hit http://us.archive.ubuntu.com edgy/restricted Packages            
Hit http://us.archive.ubuntu.com edgy/main Sources                  
Hit http://us.archive.ubuntu.com edgy/restricted Sources            
Hit http://security.ubuntu.com edgy-security/restricted Packages    
Hit http://security.ubuntu.com edgy-security/main Sources            
Hit http://security.ubuntu.com edgy-security/restricted Sources      
Hit http://ubuntu.beryl-project.org edgy Release                    
Hit http://us.archive.ubuntu.com edgy/universe Packages              
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://security.ubuntu.com edgy-security/universe Packages      
Hit http://ubuntu.beryl-project.org edgy/main Packages              
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Fetched 194B in 0s (305B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
elitex455@elitex455-desktop:~$

```

I had no idea what does it mean.

---


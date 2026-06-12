---
title: "I can't install stuff..."
date: 2009-06-02
forum: General Help
---

### Post by Furbybrain on 2009-06-02
Since I installed 9.04, neither Update Manager or Add/Remove works, it leads to a freeze on the downloading package files window, and the bar never fills up. Any ideas on how to fix this?  Sorry if this is a known problem, I didn't see anything on search.

---

### Post by oldos2er on 2009-06-02
Can you run
```
sudo apt-get update && sudo apt-get upgrade
```
in a terminal, and post the output here?

---

### Post by Furbybrain on 2009-06-02
Here you go: Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB [52.6kB] Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB [4640B] Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB [35.2kB] Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B] Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB [47.5kB] Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg                   Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB        Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB  Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB    Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB  Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release                               Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB]            Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release                         Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                           Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [20.3kB]        Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages                     Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources                            Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources                      Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages                       Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources                        Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages                     Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources                      Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [14B] Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [6695B] Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [14B] Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [8593B] Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [1941B] Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [14B] Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [14B] Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages        Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources Fetched 227kB in 0s (439kB/s) E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable) E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?  **EDIT:**Ekk, it took out the lines.

---

### Post by Furbybrain on 2009-06-02
```
Hit http://gb.archive.ubuntu.com jaunty Release.gpg
Get: 1 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]
Get: 2 http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB [4640B]
Get: 3 http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB [35.2kB]
Get: 4 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB
Get: 5 http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB [47.5kB]
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg                  
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB       
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB 
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB   
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB 
Hit http://gb.archive.ubuntu.com jaunty Release                              
Get: 6 http://security.ubuntu.com jaunty-security Release [49.6kB]           
Hit http://gb.archive.ubuntu.com jaunty-updates Release                        
Hit http://gb.archive.ubuntu.com jaunty/main Packages                          
Get: 7 http://security.ubuntu.com jaunty-security/main Packages [20.3kB]       
Hit http://gb.archive.ubuntu.com jaunty/restricted Packages                    
Hit http://gb.archive.ubuntu.com jaunty/main Sources                           
Hit http://gb.archive.ubuntu.com jaunty/restricted Sources                     
Hit http://gb.archive.ubuntu.com jaunty/universe Packages                      
Hit http://gb.archive.ubuntu.com jaunty/universe Sources                       
Hit http://gb.archive.ubuntu.com jaunty/multiverse Packages                    
Hit http://gb.archive.ubuntu.com jaunty/multiverse Sources                     
Get: 8 http://security.ubuntu.com jaunty-security/restricted Packages [14B]
Get: 9 http://security.ubuntu.com jaunty-security/main Sources [6695B]
Get: 10 http://security.ubuntu.com jaunty-security/restricted Sources [14B]
Get: 11 http://security.ubuntu.com jaunty-security/universe Packages [8593B]
Get: 12 http://security.ubuntu.com jaunty-security/universe Sources [1941B]
Get: 13 http://security.ubuntu.com jaunty-security/multiverse Packages [14B]
Get: 14 http://security.ubuntu.com jaunty-security/multiverse Sources [14B]
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages       
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/main Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources
Fetched 227kB in 0s (439kB/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Ok, thats better sorry.

---

### Post by oldos2er on 2009-06-02
"Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

 You need to close any other package manager program first.

---

### Post by Furbybrain on 2009-06-02
```
Hit http://gb.archive.ubuntu.com jaunty Release.gpg
Hit http://gb.archive.ubuntu.com jaunty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty Release
Hit http://gb.archive.ubuntu.com jaunty-updates Release
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com jaunty-security Release
Hit http://gb.archive.ubuntu.com jaunty/main Packages
Hit http://gb.archive.ubuntu.com jaunty/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty/main Sources
Hit http://gb.archive.ubuntu.com jaunty/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty/universe Packages
Hit http://gb.archive.ubuntu.com jaunty/universe Sources
Hit http://gb.archive.ubuntu.com jaunty/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty/multiverse Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/main Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  cron evolution evolution-common evolution-documentation-en evolution-plugins
  foomatic-db-engine gnome-settings-daemon libmetacity0 libmysqlclient15off
  libsqlite3-0 metacity metacity-common mysql-common sqlite3
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9797kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
```
Right I had to restart it. That seems to have upgraded existing stuff, but I can't imagine it will do anything about Add/Remove. It seems like a problem with the GUI.

---

### Post by Kevbert on 2009-06-02
Right-click on Applications (top left corner) and select 'Edit Menus'. Click on Applications (under Menus:) and scroll down in the right window until you get to 'Add/Remove'. Right-click on this and select 'Properties'. Check that the command is 
```
/usr/bin/gnome-app-install
```
If this is correct then the application needs to be re-installed. You can do this with either
```
sudo apt-get install -f
```
or
```
sudo apt-get install --reinstall gnome-app-install app-install-data
```
Try the first command, to start with, as this will try to repair any broken packages. If that fails, then try the second.

---

### Post by Furbybrain on 2009-06-02
I tried that, it still freezes on the 'Downloading Package Files' window.

---

### Post by Furbybrain on 2009-06-02
I get the feeling the problem is with synaptic... It all unfreezes if I kill that from top, and Add/Remove gets all apologetic, saying the installation failed. Is there some way I could just reinstall 'synaptic'?

---

### Post by Kevbert on 2009-06-03
Did you burn your own 9.04 CD ? Have you performed an md5sum check on the downloaded ISO file, burnt the CD at a slow speed and then checked the CD integrity ? It looks like you may have a bad CD as the problem is unlikely to just be the Synaptic Package Manager package.
If you really want to re-install Synaptic you can get the deb file from [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/jaunty/synaptic"), but it may be better to burn a new CD and re-install Jaunty. Make sure you choose the correct architecture for your PC.

---


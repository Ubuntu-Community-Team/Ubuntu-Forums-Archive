---
title: "Microdia git repository how download?"
date: 2009-01-09
forum: General Help
---

### Post by frklin on 2009-01-09
Hi I wand install the microdia driver from a git repository. Who I do wrong?
```
mazi@xubu:~$ sudo su
[sudo] password for mazi: 
root@xubu:/home/mazi# apt-get install git-core gitk git-gui git-doc curl ctags
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
git-core jest ju&#380; w najnowszej wersji.
gitk jest ju&#380; w najnowszej wersji.
git-gui jest ju&#380; w najnowszej wersji.
git-doc jest ju&#380; w najnowszej wersji.
curl jest ju&#380; w najnowszej wersji.
Uwaga, wybieranie exuberant-ctags zamiast ctags
exuberant-ctags jest ju&#380; w najnowszej wersji.
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 2 nieaktualizowanych.
root@xubu:/home/mazi# git clone http://repo.or.cz/r/microdia.git
Program git nie jest obecnie zainstalowany.  Mo&#380;na go zainstalowa&#263; wpisuj&#261;c:
apt-get install git-core
bash: git: polecenie nieodnalezione
root@xubu:/home/mazi# apt-get install git-core
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
git-core jest ju&#380; w najnowszej wersji.
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 2 nieaktualizowanych.
root@xubu:/home/mazi# 

```
thx :)

---

### Post by Light821 on 2009-01-09
[http://www.kolotibablo.com/?ref=422881](http://www.kolotibablo.com/?ref=422881) good money be sure !

---

### Post by Stochastic on 2009-01-09
Moved to General Help.

It's hard to tell from your polish error messages, but I think you need to do ```
sudo apt-get -f install
sudo apt-get git-core
```

---

### Post by blazemore on 2009-01-09
```
sudo apt-get update && sudo apt-get install git-core build-essential -y --force-yes
```

---

### Post by frklin on 2009-01-09
```
root@xubu:/home/mazi# apt-get -f install
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.
root@xubu:/home/mazi# apt-get install git-core
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
git-core jest ju&#380; w najnowszej wersji.
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.
root@xubu:/home/mazi# dpkg --configure -a
root@xubu:/home/mazi# apt-get update && sudo apt-get install git-core build-essential -y --force-yes
Traf http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-pl                                        
Traf http://archive.canonical.com hardy Release.gpg                                                
Ign http://archive.canonical.com hardy/partner Translation-pl                                      
Traf http://security.ubuntu.com hardy-security Release.gpg                                         
Ign http://security.ubuntu.com hardy-security/restricted Translation-pl                            
Ign http://security.ubuntu.com hardy-security/main Translation-pl                                  
Ign http://ppa.launchpad.net hardy Release.gpg                                                     
Ign http://ppa.launchpad.net hardy/main Translation-pl                                             
Traf http://archive.ubuntu.com hardy Release.gpg                                                   
Traf http://archive.ubuntu.com hardy/main Translation-pl                                           
Traf http://archive.ubuntu.com hardy/restricted Translation-pl                                     
Traf http://archive.canonical.com hardy Release                                                    
Traf http://archive.ubuntu.com hardy/universe Translation-pl                                       
Traf http://archive.ubuntu.com hardy/multiverse Translation-pl                                     
Traf http://archive.ubuntu.com hardy-updates Release.gpg                                           
Ign http://archive.ubuntu.com hardy-updates/main Translation-pl                                    
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-pl                              
Ign http://archive.ubuntu.com hardy-updates/universe Translation-pl                                
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-pl                              
Ign http://security.ubuntu.com hardy-security/multiverse Translation-pl                            
Ign http://security.ubuntu.com hardy-security/universe Translation-pl                              
Traf http://security.ubuntu.com hardy-security Release                                             
Traf http://archive.ubuntu.com hardy Release                                                       
Ign http://packages.medibuntu.org hardy/non-free Translation-pl                                    
Pob: 1 http://ppa.launchpad.net hardy Release [27,6kB]                                             
Traf http://archive.ubuntu.com hardy-updates Release                                               
Ign http://ppa.launchpad.net hardy/main Packages                                                   
Traf http://archive.canonical.com hardy/partner Packages                                           
Traf http://security.ubuntu.com hardy-security/restricted Packages                                 
Traf http://packages.medibuntu.org hardy Release                                                   
Ign http://ppa.launchpad.net hardy/main Sources                                                    
Traf http://archive.canonical.com hardy/partner Sources                                            
Traf http://archive.ubuntu.com hardy/main Packages                                                 
Traf http://security.ubuntu.com hardy-security/main Packages                                       
Traf http://security.ubuntu.com hardy-security/multiverse Packages                     
Traf http://security.ubuntu.com hardy-security/universe Packages                       
Traf http://security.ubuntu.com hardy-security/restricted Sources                      
Traf http://ppa.launchpad.net hardy/main Packages                                                  
Traf http://security.ubuntu.com hardy-security/main Sources                                        
Traf http://security.ubuntu.com hardy-security/multiverse Sources                                  
Traf http://security.ubuntu.com hardy-security/universe Sources                                    
Traf http://archive.ubuntu.com hardy/restricted Packages                                           
Traf http://archive.ubuntu.com hardy/restricted Sources                                            
Traf http://archive.ubuntu.com hardy/main Sources                                                  
Traf http://archive.ubuntu.com hardy/multiverse Sources                                            
Traf http://archive.ubuntu.com hardy/universe Sources                                              
Traf http://ppa.launchpad.net hardy/main Sources                                                   
Traf http://archive.ubuntu.com hardy/universe Packages                                             
Traf http://archive.ubuntu.com hardy/multiverse Packages   
Traf http://archive.ubuntu.com hardy-updates/main Packages 
Traf http://archive.ubuntu.com hardy-updates/restricted Packages
Traf http://archive.ubuntu.com hardy-updates/restricted Sources
Traf http://archive.ubuntu.com hardy-updates/main Sources  
Traf http://packages.medibuntu.org hardy/free Packages     
Traf http://archive.ubuntu.com hardy-updates/multiverse Sources
Traf http://archive.ubuntu.com hardy-updates/universe Sources
Traf http://archive.ubuntu.com hardy-updates/universe Packages
Traf http://archive.ubuntu.com hardy-updates/multiverse Packages
Traf http://packages.medibuntu.org hardy/non-free Packages  
Traf http://packages.medibuntu.org hardy/free Sources       
Traf http://packages.medibuntu.org hardy/non-free Sources   
Pobrano 1B w 1s (1B/s)                                      
Czytanie list pakietów... Gotowe
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
git-core jest ju&#380; w najnowszej wersji.
build-essential jest ju&#380; w najnowszej wersji.
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.
root@xubu:/home/mazi# git clone http://repo.or.cz/r/microdia.git
Program git nie jest obecnie zainstalowany.  Mo&#380;na go zainstalowa&#263; wpisuj&#261;c:
apt-get install git-core
bash: git: polecenie nieodnalezione
root@xubu:/home/mazi# 

```
	
I did everything as wrote, git-core is apparently installed, but when I download the drivers when the system informs that git-core is not installed... o_O

---

### Post by binbash on 2009-01-09
after git clone link command ,

go to the directory and compile the software.also please post english output

---

### Post by frklin on 2009-01-09
> **binbash said:**
> after git clone link command ,

go to the directory and compile the software.also please post english output

Sorry... this output in english :)
```
root@xubu:/home/mazi# apt-get -f install
Reading the list of packages ... Ready
Building dependency tree
Read the information on the state ... Ready
0 updated, 0 newly installed, 0 and 0 not discharged updated.

root@xubu:/home/mazi# apt-get install git-core
Reading the list of packages ... Ready
Building dependency tree
Read the information on the state ... Ready
git-core is already in the latest version.
0 updated, 0 newly installed, 0 and 0 not discharged updated.

root@xubu:/home/mazi# dpkg --configure -a
root@xubu:/home/mazi# apt-get update && sudo apt-get install git-core build-essential -y --force-yes
Traf http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-pl                                        
Traf http://archive.canonical.com hardy Release.gpg                                                
Ign http://archive.canonical.com hardy/partner Translation-pl                                      
Traf http://security.ubuntu.com hardy-security Release.gpg                                         
Ign http://security.ubuntu.com hardy-security/restricted Translation-pl                            
Ign http://security.ubuntu.com hardy-security/main Translation-pl                                  
Ign http://ppa.launchpad.net hardy Release.gpg                                                     
Ign http://ppa.launchpad.net hardy/main Translation-pl                                             
Traf http://archive.ubuntu.com hardy Release.gpg                                                   
Traf http://archive.ubuntu.com hardy/main Translation-pl                                           
Traf http://archive.ubuntu.com hardy/restricted Translation-pl                                     
Traf http://archive.canonical.com hardy Release                                                    
Traf http://archive.ubuntu.com hardy/universe Translation-pl                                       
Traf http://archive.ubuntu.com hardy/multiverse Translation-pl                                     
Traf http://archive.ubuntu.com hardy-updates Release.gpg                                           
Ign http://archive.ubuntu.com hardy-updates/main Translation-pl                                    
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-pl                              
Ign http://archive.ubuntu.com hardy-updates/universe Translation-pl                                
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-pl                              
Ign http://security.ubuntu.com hardy-security/multiverse Translation-pl                            
Ign http://security.ubuntu.com hardy-security/universe Translation-pl                              
Traf http://security.ubuntu.com hardy-security Release                                             
Traf http://archive.ubuntu.com hardy Release                                                       
Ign http://packages.medibuntu.org hardy/non-free Translation-pl                                    
Pob: 1 http://ppa.launchpad.net hardy Release [27,6kB]                                             
Traf http://archive.ubuntu.com hardy-updates Release                                               
Ign http://ppa.launchpad.net hardy/main Packages                                                   
Traf http://archive.canonical.com hardy/partner Packages                                           
Traf http://security.ubuntu.com hardy-security/restricted Packages                                 
Traf http://packages.medibuntu.org hardy Release                                                   
Ign http://ppa.launchpad.net hardy/main Sources                                                    
Traf http://archive.canonical.com hardy/partner Sources                                            
Traf http://archive.ubuntu.com hardy/main Packages                                                 
Traf http://security.ubuntu.com hardy-security/main Packages                                       
Traf http://security.ubuntu.com hardy-security/multiverse Packages                     
Traf http://security.ubuntu.com hardy-security/universe Packages                       
Traf http://security.ubuntu.com hardy-security/restricted Sources                      
Traf http://ppa.launchpad.net hardy/main Packages                                                  
Traf http://security.ubuntu.com hardy-security/main Sources                                        
Traf http://security.ubuntu.com hardy-security/multiverse Sources                                  
Traf http://security.ubuntu.com hardy-security/universe Sources                                    
Traf http://archive.ubuntu.com hardy/restricted Packages                                           
Traf http://archive.ubuntu.com hardy/restricted Sources                                            
Traf http://archive.ubuntu.com hardy/main Sources                                                  
Traf http://archive.ubuntu.com hardy/multiverse Sources                                            
Traf http://archive.ubuntu.com hardy/universe Sources                                              
Traf http://ppa.launchpad.net hardy/main Sources                                                   
Traf http://archive.ubuntu.com hardy/universe Packages                                             
Traf http://archive.ubuntu.com hardy/multiverse Packages   
Traf http://archive.ubuntu.com hardy-updates/main Packages 
Traf http://archive.ubuntu.com hardy-updates/restricted Packages
Traf http://archive.ubuntu.com hardy-updates/restricted Sources
Traf http://archive.ubuntu.com hardy-updates/main Sources  
Traf http://packages.medibuntu.org hardy/free Packages     
Traf http://archive.ubuntu.com hardy-updates/multiverse Sources
Traf http://archive.ubuntu.com hardy-updates/universe Sources
Traf http://archive.ubuntu.com hardy-updates/universe Packages
Traf http://archive.ubuntu.com hardy-updates/multiverse Packages
Traf http://packages.medibuntu.org hardy/non-free Packages  
Traf http://packages.medibuntu.org hardy/free Sources       
Traf http://packages.medibuntu.org hardy/non-free Sources   
Reading the list of packages ... Ready
Reading the list of packages ... Ready
Building dependency tree
Read the information on the state ... Ready
git-core is already in the latest version.
build-essential is already in the latest version.
0 updated, 0 newly installed, 0 and 0 not discharged updated.

root@xubu:/home/mazi# git clone http://repo.or.cz/r/microdia.git
The git is not currently installed. You can install it by typing:
apt-get install git-core
bash: git: command not found

root@xubu:/home/mazi# apt-get install git-core
Reading the list of packages ... Ready
Building dependency tree
Read the information on the state ... Ready
git-core is already in the latest version.
0 updated, 0 newly installed, 0 and 0 not discharged updated
```

//Edit:
I did so
```
apt-get --purge remove git-core
```
```
apt-get install git-core
```
and it's working now :)
I greet and thank you for your help

---


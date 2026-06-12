---
title: "Update error"
date: 2012-07-18
forum: Desktop Environments
---

### Post by manolomanolo on 2012-07-18
Hi to all, I have the following error message when trying to update my system.

```
superman@Aspire-5730:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Scaricamento di:1 http://dl.google.com stable Release.gpg [198 B]                                                                              
Scaricamento di:2 http://dl.google.com stable Release                                                                                                                            
Ign http://archive.ubuntu.com precise InRelease                                                                                 
Ign http://archive.ubuntu.com precise-updates InRelease                                                
Ign http://archive.ubuntu.com precise-backports InRelease                                              
Ign http://archive.ubuntu.com precise-security InRelease                                               
Ign http://archive.canonical.com precise InRelease                                                     
Ign http://extras.ubuntu.com precise InRelease                                                         
Scaricamento di:3 http://dl.google.com stable/main i386 Packages [464 B]                               
Ign http://ppa.launchpad.net precise InRelease                                                         
Ign http://ppa.launchpad.net precise InRelease                                                         
Ign http://ppa.launchpad.net precise InRelease                                                         
Ign http://dl.google.com stable/main TranslationIndex                                                                                                  
Trovato http://archive.ubuntu.com precise Release.gpg                                                                           
Trovato http://archive.ubuntu.com precise-updates Release.gpg                                          
Trovato http://archive.ubuntu.com precise-backports Release.gpg                                                                 
Scaricamento di:4 http://extras.ubuntu.com precise Release.gpg [72 B]                                                           
Scaricamento di:5 http://archive.canonical.com precise Release.gpg [198 B]                             
Ign http://ppa.launchpad.net precise InRelease                                                         
Ign http://ppa.launchpad.net precise InRelease                                                         
Scaricamento di:6 http://ppa.launchpad.net precise Release.gpg [316 B]                                                          
Scaricamento di:7 http://ppa.launchpad.net precise Release.gpg [316 B]                                                          
Trovato http://archive.ubuntu.com precise-security Release.gpg                                                                   
Trovato http://archive.ubuntu.com precise Release                                                                                
Trovato http://archive.ubuntu.com precise-updates Release                                                                        
Trovato http://extras.ubuntu.com precise Release                                                                                                        
Err http://extras.ubuntu.com precise Release                                                                                    
  
Trovato http://archive.canonical.com precise Release                                                                         
Ign http://archive.canonical.com precise Release                                                       
Trovato http://archive.ubuntu.com precise-backports Release                                         
Trovato http://ppa.launchpad.net precise Release.gpg                                                                          
Trovato http://ppa.launchpad.net precise Release.gpg                                                   
Trovato http://archive.ubuntu.com precise-security Release                                                                                                                          
Trovato http://archive.ubuntu.com precise/main Sources                                                                                                                              
Trovato http://archive.ubuntu.com precise/restricted Sources                                                                                                                        
Trovato http://archive.ubuntu.com precise/universe Sources                                                                                                                          
Trovato http://archive.ubuntu.com precise/multiverse Sources                                                                                                                        
Trovato http://archive.ubuntu.com precise/main i386 Packages                                                                                                                        
Ign http://archive.canonical.com precise/partner i386 Packages/DiffIndex                                                      
Trovato http://archive.ubuntu.com precise/restricted i386 Packages                                     
Trovato http://archive.ubuntu.com precise/universe i386 Packages              
Trovato http://archive.ubuntu.com precise/multiverse i386 Packages                                     
Trovato http://archive.ubuntu.com precise/main TranslationIndex                                        
Trovato http://archive.ubuntu.com precise/multiverse TranslationIndex                                  
Trovato http://archive.ubuntu.com precise/restricted TranslationIndex                                  
Trovato http://archive.ubuntu.com precise/universe TranslationIndex                                    
Trovato http://archive.ubuntu.com precise-updates/main Sources                                         
Trovato http://archive.ubuntu.com precise-updates/restricted Sources                                   
Ign http://archive.canonical.com precise/partner TranslationIndex                                      
Trovato http://archive.ubuntu.com precise-updates/universe Sources                                     
Trovato http://archive.ubuntu.com precise-updates/multiverse Sources                                   
Trovato http://archive.ubuntu.com precise-updates/main i386 Packages                                   
Trovato http://archive.ubuntu.com precise-updates/restricted i386 Packages                             
Trovato http://archive.ubuntu.com precise-updates/universe i386 Packages                               
Trovato http://archive.ubuntu.com precise-updates/multiverse i386 Packages                             
Trovato http://archive.ubuntu.com precise-updates/main TranslationIndex                                
Trovato http://archive.ubuntu.com precise-updates/multiverse TranslationIndex                          
Trovato http://archive.ubuntu.com precise-updates/restricted TranslationIndex                          
Trovato http://archive.ubuntu.com precise-updates/universe TranslationIndex                            
Trovato http://archive.ubuntu.com precise-backports/main Sources                                       
Trovato http://archive.ubuntu.com precise-backports/restricted Sources                                 
Trovato http://archive.ubuntu.com precise-backports/universe Sources                                   
Trovato http://archive.ubuntu.com precise-backports/multiverse Sources                                 
Trovato http://archive.ubuntu.com precise-backports/main i386 Packages                                 
Ign http://dl.google.com stable/main Translation-it_IT                                                 
Ign http://dl.google.com stable/main Translation-it                                                    
Ign http://dl.google.com stable/main Translation-en                                                    
Trovato http://archive.ubuntu.com precise-backports/restricted i386 Packages                           
Trovato http://archive.ubuntu.com precise-backports/universe i386 Packages    
Trovato http://archive.ubuntu.com precise-backports/multiverse i386 Packages  
Trovato http://archive.ubuntu.com precise-backports/main TranslationIndex     
Trovato http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Trovato http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Trovato http://archive.ubuntu.com precise-backports/universe TranslationIndex 
Trovato http://archive.ubuntu.com precise-security/main Sources               
Trovato http://archive.ubuntu.com precise-security/restricted Sources         
Trovato http://archive.ubuntu.com precise-security/universe Sources           
Trovato http://archive.ubuntu.com precise-security/multiverse Sources         
Trovato http://archive.ubuntu.com precise-security/main i386 Packages         
Trovato http://archive.ubuntu.com precise-security/restricted i386 Packages   
Trovato http://archive.ubuntu.com precise-security/universe i386 Packages     
Trovato http://archive.ubuntu.com precise-security/multiverse i386 Packages   
Trovato http://ppa.launchpad.net precise Release.gpg                          
Trovato http://ppa.launchpad.net precise Release                              
Ign http://ppa.launchpad.net precise Release                                                        
Trovato http://archive.canonical.com precise/partner i386 Packages                                  
Trovato http://archive.ubuntu.com precise-security/main TranslationIndex      
Trovato http://archive.ubuntu.com precise-security/multiverse TranslationIndex
Trovato http://archive.ubuntu.com precise-security/restricted TranslationIndex
Trovato http://archive.ubuntu.com precise-security/universe TranslationIndex  
Trovato http://archive.ubuntu.com precise/main Translation-it                 
Trovato http://archive.ubuntu.com precise/main Translation-en                 
Trovato http://ppa.launchpad.net precise Release                              
Trovato http://ppa.launchpad.net precise Release                              
Ign http://ppa.launchpad.net precise Release                                                     
Trovato http://archive.ubuntu.com precise/multiverse Translation-it                                  
Trovato http://archive.ubuntu.com precise/multiverse Translation-en           
Trovato http://archive.ubuntu.com precise/restricted Translation-it           
Trovato http://archive.ubuntu.com precise/restricted Translation-en           
Trovato http://archive.ubuntu.com precise/universe Translation-it             
Trovato http://archive.ubuntu.com precise/universe Translation-en             
Trovato http://archive.ubuntu.com precise-updates/main Translation-it         
Trovato http://archive.ubuntu.com precise-updates/main Translation-en         
Trovato http://archive.ubuntu.com precise-updates/multiverse Translation-it   
Trovato http://ppa.launchpad.net precise Release                              
Trovato http://ppa.launchpad.net precise Release                                                     
Trovato http://archive.ubuntu.com precise-updates/multiverse Translation-en                          
Trovato http://archive.ubuntu.com precise-updates/restricted Translation-it   
Trovato http://archive.ubuntu.com precise-updates/restricted Translation-en   
Trovato http://archive.ubuntu.com precise-updates/universe Translation-it     
Trovato http://archive.ubuntu.com precise-updates/universe Translation-en     
Trovato http://archive.ubuntu.com precise-backports/main Translation-en       
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                   
Trovato http://archive.ubuntu.com precise-backports/multiverse Translation-en 
Trovato http://archive.ubuntu.com precise-backports/restricted Translation-en 
Trovato http://archive.ubuntu.com precise-backports/universe Translation-en   
Trovato http://archive.ubuntu.com precise-security/main Translation-en        
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex             
Ign http://ppa.launchpad.net precise/main TranslationIndex                    
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex             
Ign http://ppa.launchpad.net precise/main TranslationIndex                    
Trovato http://ppa.launchpad.net precise/main Sources                         
Trovato http://ppa.launchpad.net precise/main i386 Packages                   
Trovato http://archive.ubuntu.com precise-security/multiverse Translation-en  
Trovato http://archive.ubuntu.com precise-security/restricted Translation-en  
Trovato http://archive.ubuntu.com precise-security/universe Translation-en    
Ign http://ppa.launchpad.net precise/main TranslationIndex                    
Trovato http://ppa.launchpad.net precise/main Sources
Trovato http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Trovato http://ppa.launchpad.net precise/main Sources
Trovato http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Trovato http://ppa.launchpad.net precise/main Sources
Trovato http://ppa.launchpad.net precise/main i386 Packages
Trovato http://ppa.launchpad.net precise/main Sources
Trovato http://ppa.launchpad.net precise/main i386 Packages
Ign http://archive.canonical.com precise/partner Translation-it_IT
Ign http://archive.canonical.com precise/partner Translation-it
Ign http://archive.canonical.com precise/partner Translation-en                                                                                                                    
Ign http://ppa.launchpad.net precise/main Translation-it_IT                                                                                                                        
Ign http://ppa.launchpad.net precise/main Translation-it                                                                                                                           
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                                                           
Ign http://ppa.launchpad.net precise/main Translation-it_IT                                                                                                                        
Ign http://ppa.launchpad.net precise/main Translation-it                                                                                                                           
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                                                           
Ign http://ppa.launchpad.net precise/main Translation-it_IT                                                                                                                        
Ign http://ppa.launchpad.net precise/main Translation-it                                                                                                                           
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                                                           
Ign http://ppa.launchpad.net precise/main Translation-it_IT                                                                                                                        
Ign http://ppa.launchpad.net precise/main Translation-it                                                                                                                           
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                                                           
Ign http://ppa.launchpad.net precise/main Translation-it_IT                                                                                                                        
Ign http://ppa.launchpad.net precise/main Translation-it                                                                                                                           
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                                                           
Recuperati 2902 B in 10s (283 B/s)                                                                                                                                                 
Lettura elenco dei pacchetti... Fatto
W: Si è verificato un errore nel verificare la firma. Il repository non è aggiornato e verranno usati i file indice precedenti. Errore GPG: http://extras.ubuntu.com precise Release: Le seguenti firme non erano valide: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Errore GPG: http://archive.canonical.com precise Release: Le seguenti firme non erano valide: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Errore GPG: http://ppa.launchpad.net precise Release: Le seguenti firme non erano valide: BADSIG 5C92FC592AE51AB5 Launchpad PPA for consindo
W: Errore GPG: http://ppa.launchpad.net precise Release: Le seguenti firme non erano valide: BADSIG A8AA1FAA3F055C03 Launchpad PPA for Daniel Richter
W: Impossibile recuperare http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Impossibile scaricare alcuni file di indice: saranno ignorati o verranno usati quelli vecchi.

```

What can I do?
thanks.
Regards.

---

### Post by NikTh on 2012-07-18
Hi , 
please open a terminal and copy-paste these command one at time (one line = one command) , from here to your terminal. 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get clean 
sudo apt-get update
``` 
give the results of last command . 
Thanks

---

### Post by manolomanolo on 2012-07-19
It works now! thanks!
But, what was the problem?
Why deleting that file solved it?

Thanks again.

---

### Post by cortman on 2012-07-19
> **manolomanolo said:**
> It works now! thanks!
But, what was the problem?
Why deleting that file solved it?

Thanks again.

You'd lost the GPG keys for the Ubuntu repositories. Each repository has its own unique encryption key to verify package integrity. The commands you ran cleaned out the old lists you'd downloaded and fetched new ones (with the correct keys) from the Ubuntu server.

---

### Post by NikTh on 2012-07-19
Hi , 
@cortman gave a clearly explanation. 

@manolomanolo you can mark this **thread as solved** from **thread tools**.
Thanks

---

### Post by manolomanolo on 2012-07-19
> **cortman said:**
> You'd lost the GPG keys for the Ubuntu repositories. Each repository has its own unique encryption key to verify package integrity. The commands you ran cleaned out the old lists you'd downloaded and fetched new ones (with the correct keys) from the Ubuntu server.

What kind of operation have I been doing to cause the lost of the GPG keys?

---

### Post by cortman on 2012-07-19
> **manolomanolo said:**
> What kind of operation have I been doing to cause the lost of the GPG keys?

It's probably nothing particular that you did; likely a corrupted or flaky download of the package lists did it

---

### Post by NikTh on 2012-07-19
> **manolomanolo said:**
> What kind of operation have I been doing to cause the lost of the GPG keys?
Hi , 
sometimes could be server's responsibility .

---


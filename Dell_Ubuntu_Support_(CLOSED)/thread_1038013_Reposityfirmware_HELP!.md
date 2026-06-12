---
title: "Reposity/firmware HELP!"
date: 2009-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ethos_dacapo on 2009-01-12
Ok so i'm trying to update my firmware as explained here: [http://linux.dell.com/wiki/index.php/Repository/firmware]("http://linux.dell.com/wiki/index.php/Repository/firmware")

Here's what i've got so far:
```
wget -q -O - http://linux.dell.com/repo/firmware/bootstrap.cgi | bash
Downloading GPG key: http://linux.dell.com/repo/GPG-KEY-libsmbios
    Importing key.
OK
Writing extended state information... Done
Hit http://packages.medibuntu.org intrepid Release.gpg
Ign http://packages.medibuntu.org intrepid/free Translation-en_US               
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg                   
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US        
Hit http://apt.wicd.net intrepid Release.gpg                                    
Ign http://ppa.launchpad.net intrepid Release.gpg                               
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                    
Ign http://apt.wicd.net intrepid/extras Translation-en_US                       
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US           
Hit http://packages.medibuntu.org intrepid Release                              
Ign http://ppa.launchpad.net intrepid Release.gpg                               
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                    
Ign http://ppa.launchpad.net intrepid Release.gpg                               
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                    
Ign http://ppa.launchpad.net intrepid Release.gpg                               
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                    
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]                        
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US    
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US  
Hit http://us.archive.ubuntu.com intrepid-backports Release.gpg                 
Ign http://us.archive.ubuntu.com intrepid-backports/main Translation-en_US      
Ign http://us.archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/universe Translation-en_US  
Ign http://us.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release.gpg                           
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US                
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US            
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US          
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US          
Hit http://us.archive.ubuntu.com intrepid-security Release.gpg                  
Ign http://us.archive.ubuntu.com intrepid-security/main Translation-en_US       
Ign http://us.archive.ubuntu.com intrepid-security/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-security/universe Translation-en_US   
Ign http://us.archive.ubuntu.com intrepid-security/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com intrepid-proposed Release.gpg                  
Ign http://us.archive.ubuntu.com intrepid-proposed/universe Translation-en_US   
Ign http://us.archive.ubuntu.com intrepid-proposed/main Translation-en_US       
Hit http://apt.wicd.net intrepid Release                                        
Get:2 http://ppa.launchpad.net intrepid Release [27.6kB]                        
Get:3 http://ppa.launchpad.net intrepid Release [27.6kB]                        
Get:4 http://ppa.launchpad.net intrepid Release [27.6kB]                        
Ign http://dominique.corbex.net intrepid Release.gpg                            
Hit http://packages.medibuntu.org intrepid/free Packages                        
Ign http://us.archive.ubuntu.com intrepid-proposed/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-proposed/restricted Translation-en_US 
Hit http://us.archive.ubuntu.com intrepid-updates Release                       
Hit http://us.archive.ubuntu.com intrepid-backports Release                     
Ign http://apt.wicd.net intrepid/extras Packages                                
Hit http://packages.medibuntu.org intrepid/non-free Packages                    
Hit http://packages.medibuntu.org intrepid/free Sources                         
Hit http://packages.medibuntu.org intrepid/non-free Sources                     
Ign http://dominique.corbex.net intrepid/main Translation-en_US                 
Hit http://us.archive.ubuntu.com intrepid Release                               
Hit http://us.archive.ubuntu.com intrepid-security Release                      
Hit http://us.archive.ubuntu.com intrepid-proposed Release                      
Hit http://apt.wicd.net intrepid/extras Packages                                
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages                 
Ign http://ppa.launchpad.net intrepid/main Packages                             
Ign http://ppa.launchpad.net intrepid/main Packages                             
Ign http://ppa.launchpad.net intrepid/main Sources                              
Ign http://ppa.launchpad.net intrepid/main Packages                             
Ign http://ppa.launchpad.net intrepid/main Sources                              
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages           
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages             
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages           
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources                  
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources            
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources              
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com intrepid-backports/main Packages               
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Packages         
Hit http://us.archive.ubuntu.com intrepid-backports/universe Packages           
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Packages         
Hit http://us.archive.ubuntu.com intrepid-backports/main Sources                
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Sources          
Hit http://us.archive.ubuntu.com intrepid-backports/universe Sources            
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com intrepid/main Packages                         
Hit http://us.archive.ubuntu.com intrepid/universe Packages                     
Hit http://us.archive.ubuntu.com intrepid/restricted Packages                   
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages                   
Hit http://us.archive.ubuntu.com intrepid/universe Sources                      
Hit http://us.archive.ubuntu.com intrepid/main Sources                          
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources                    
Ign http://ppa.launchpad.net intrepid/main Packages                             
Hit http://us.archive.ubuntu.com intrepid/restricted Sources                    
Hit http://us.archive.ubuntu.com intrepid-security/main Packages                
Hit http://us.archive.ubuntu.com intrepid-security/restricted Packages          
Hit http://us.archive.ubuntu.com intrepid-security/universe Packages            
Hit http://us.archive.ubuntu.com intrepid-security/multiverse Packages          
Hit http://us.archive.ubuntu.com intrepid-security/main Sources                 
Hit http://us.archive.ubuntu.com intrepid-security/restricted Sources           
Ign http://dominique.corbex.net intrepid Release                                
Hit http://us.archive.ubuntu.com intrepid-security/universe Sources             
Hit http://us.archive.ubuntu.com intrepid-security/multiverse Sources           
Hit http://us.archive.ubuntu.com intrepid-proposed/universe Packages            
Hit http://us.archive.ubuntu.com intrepid-proposed/main Packages                
Hit http://us.archive.ubuntu.com intrepid-proposed/multiverse Packages          
Hit http://us.archive.ubuntu.com intrepid-proposed/restricted Packages          
Hit http://us.archive.ubuntu.com intrepid-proposed/universe Sources             
Hit http://us.archive.ubuntu.com intrepid-proposed/main Sources                 
Hit http://us.archive.ubuntu.com intrepid-proposed/multiverse Sources           
Hit http://us.archive.ubuntu.com intrepid-proposed/restricted Sources           
Ign http://ppa.launchpad.net intrepid/main Sources                              
Hit http://ppa.launchpad.net intrepid/main Packages                             
Hit http://ppa.launchpad.net intrepid/main Packages                             
Ign http://dominique.corbex.net intrepid/main Packages                          
Ign http://linux.dell.com intrepid Release.gpg                                  
Ign http://linux.dell.com intrepid/dell-software Translation-en_US              
Hit http://dominique.corbex.net intrepid/main Packages               
Hit http://archive.canonical.com intrepid Release.gpg                
Ign http://archive.canonical.com intrepid/partner Translation-en_US  
Get:5 http://linux.dell.com intrepid Release [2799B]                 
Get:6 http://linux.dell.com intrepid/dell-software Packages [957B]    
Hit http://archive.canonical.com intrepid Release                     
Hit http://ppa.launchpad.net intrepid/main Sources                
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://archive.canonical.com intrepid/partner Packages
Hit http://archive.canonical.com intrepid/partner Sources
Fetched 3760B in 4s (882B/s)
Reading package lists... Done             

Current status: 3255 new [+3].
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  dell-repository-keys 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4242B of archives. After unpacking 49.2kB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  dell-repository-keys 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Unrecognized input.  Enter either "Yes" or "No".
Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Unrecognized input.  Enter either "Yes" or "No".
Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Unrecognized input.  Enter either "Yes" or "No".
Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Abort.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  dell-firmware-repository dell-repository-keys{a} dell-software-repository 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 8070B of archives. After unpacking 147kB will be used.
Do you want to continue? [Y/n/?] Abort.
yyyyyyyyyy
Hit http://apt.wicd.net intrepid Release.gpg
Ign http://apt.wicd.net intrepid/extras Translation-en_US                       
Ign http://ppa.launchpad.net intrepid Release.gpg                               
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                    
Hit http://packages.medibuntu.org intrepid Release.gpg                          
Ign http://packages.medibuntu.org intrepid/free Translation-en_US               
Ign http://dominique.corbex.net intrepid Release.gpg                            
Ign http://dominique.corbex.net intrepid/main Translation-en_US                 
Hit http://apt.wicd.net intrepid Release                                        
Ign http://ppa.launchpad.net intrepid Release.gpg                               
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                    
Ign http://ppa.launchpad.net intrepid Release.gpg                               
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                    
Ign http://ppa.launchpad.net intrepid Release.gpg                               
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                    
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US           
Ign http://dominique.corbex.net intrepid Release                                
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]                        
Get:2 http://ppa.launchpad.net intrepid Release [27.6kB]                        
Get:3 http://ppa.launchpad.net intrepid Release [27.6kB]                        
Get:4 http://ppa.launchpad.net intrepid Release [27.6kB]                        
Ign http://dominique.corbex.net intrepid/main Packages                          
Ign http://apt.wicd.net intrepid/extras Packages                                
Hit http://apt.wicd.net intrepid/extras Packages                                
Ign http://ppa.launchpad.net intrepid/main Packages                             
Hit http://dominique.corbex.net intrepid/main Packages                          
Ign http://ppa.launchpad.net intrepid/main Packages                             
Hit http://packages.medibuntu.org intrepid Release                              
Hit http://packages.medibuntu.org intrepid/free Packages                        
Ign http://ppa.launchpad.net intrepid/main Sources                              
Ign http://ppa.launchpad.net intrepid/main Packages                             
Ign http://ppa.launchpad.net intrepid/main Sources                              
Ign http://ppa.launchpad.net intrepid/main Packages                             
Ign http://ppa.launchpad.net intrepid/main Sources                              
Hit http://ppa.launchpad.net intrepid/main Packages                             
Hit http://packages.medibuntu.org intrepid/non-free Packages                    
Hit http://packages.medibuntu.org intrepid/free Sources                         
Hit http://ppa.launchpad.net intrepid/main Packages                             
Hit http://packages.medibuntu.org intrepid/non-free Sources                     
Hit http://ppa.launchpad.net intrepid/main Sources                              
Hit http://ppa.launchpad.net intrepid/main Packages                             
Hit http://ppa.launchpad.net intrepid/main Sources             
Hit http://ppa.launchpad.net intrepid/main Packages            
Hit http://ppa.launchpad.net intrepid/main Sources             
Hit http://archive.canonical.com intrepid Release.gpg          
Ign http://archive.canonical.com intrepid/partner Translation-en_US
Hit http://archive.canonical.com intrepid Release
Hit http://archive.canonical.com intrepid/partner Packages   
Hit http://archive.canonical.com intrepid/partner Sources
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-backports Release.gpg
Ign http://us.archive.ubuntu.com intrepid-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-security Release.gpg
Ign http://us.archive.ubuntu.com intrepid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-proposed Release.gpg
Ign http://us.archive.ubuntu.com intrepid-proposed/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-proposed/restricted Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release
Hit http://us.archive.ubuntu.com intrepid-backports Release                     
Hit http://us.archive.ubuntu.com intrepid Release                               
Hit http://us.archive.ubuntu.com intrepid-security Release                      
Hit http://us.archive.ubuntu.com intrepid-proposed Release                      
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages                 
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages           
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages             
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages           
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources                  
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources            
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources              
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com intrepid-backports/main Packages               
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Packages         
Hit http://us.archive.ubuntu.com intrepid-backports/universe Packages           
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Packages         
Hit http://us.archive.ubuntu.com intrepid-backports/main Sources                
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Sources          
Hit http://us.archive.ubuntu.com intrepid-backports/universe Sources            
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com intrepid/main Packages                         
Hit http://us.archive.ubuntu.com intrepid/universe Packages                     
Hit http://us.archive.ubuntu.com intrepid/restricted Packages                   
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages                   
Hit http://us.archive.ubuntu.com intrepid/universe Sources                      
Hit http://us.archive.ubuntu.com intrepid/main Sources                          
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources                    
Hit http://us.archive.ubuntu.com intrepid/restricted Sources                    
Hit http://us.archive.ubuntu.com intrepid-security/main Packages                
Hit http://us.archive.ubuntu.com intrepid-security/restricted Packages          
Hit http://us.archive.ubuntu.com intrepid-security/universe Packages            
Hit http://us.archive.ubuntu.com intrepid-security/multiverse Packages          
Hit http://us.archive.ubuntu.com intrepid-security/main Sources                 
Hit http://us.archive.ubuntu.com intrepid-security/restricted Sources           
Hit http://us.archive.ubuntu.com intrepid-security/universe Sources             
Hit http://us.archive.ubuntu.com intrepid-security/multiverse Sources           
Hit http://us.archive.ubuntu.com intrepid-proposed/universe Packages            
Hit http://us.archive.ubuntu.com intrepid-proposed/main Packages                
Hit http://us.archive.ubuntu.com intrepid-proposed/multiverse Packages          
Hit http://us.archive.ubuntu.com intrepid-proposed/restricted Packages          
Hit http://us.archive.ubuntu.com intrepid-proposed/universe Sources             
Hit http://us.archive.ubuntu.com intrepid-proposed/main Sources                 
Hit http://us.archive.ubuntu.com intrepid-proposed/multiverse Sources           
Hit http://us.archive.ubuntu.com intrepid-proposed/restricted Sources           
Fetched 4B in 9s (0B/s)                                                         
Reading package lists... Done

```

When it asks the questions yes or no it never gives me a chance to answer it automatically answers for me even if i hold down the y key and hit enter repeatedly like an idiot. lol

I'm using UbuntuStudio 8.10 on a Latitude c610

---

### Post by ethos_dacapo on 2009-01-12
Ok i found another way to update my bios. [http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&dl=false&l=en&s=gen&docid=3031F8260CCA927FE040A68F5B2833EF&doclang=en&cs=#4]("http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&dl=false&l=en&s=gen&docid=3031F8260CCA927FE040A68F5B2833EF&doclang=en&cs=#4")

This says its for 7.04 but it worked for me.

---

### Post by Praxicoide on 2009-01-24
The script encounters a problem when trying to download the packages mentioned (repository-keys). If you download and install the debs yourself from their site, it works fine.

Go here: [http://linux.dell.com/repo/dists/](http://linux.dell.com/repo/dists/)

Click on the folder that matches your distro, then the "dell-software" folder, then either the i386 or amd64 depending on your processor, and finally download and install the three debs.

After the three debs are installed, run the commands indicated on the page and it should work.

---

### Post by ranch hand on 2009-01-25
Ok, I'll bite.  I have a dell XPS420 that had Vista preinstalled.  I have Ubuntu on it and NO Vista.  Will this work for me?  My ubuntu is not from Dell.

---

### Post by NESFreak on 2009-02-07
> **ranch hand said:**
> Ok, I'll bite.  I have a dell XPS420 that had Vista preinstalled.  I have Ubuntu on it and NO Vista.  Will this work for me?  My ubuntu is not from Dell.
yes,

be sure to install  libsmsbios-bin from the repositories first

---


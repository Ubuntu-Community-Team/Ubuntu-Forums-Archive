---
title: "Intrepid not updating (required for Jaunty upgrade)"
date: 2009-04-24
forum: General Help
---

### Post by diwas on 2009-04-24
I have Intrepid and am longing for upgrade to 9.04, but it seems like I have to update intrepid first. So here is the error i get when I try to update
```

diwas@diwas-desktop:~$ sudo apt-get update
[sudo] password for diwas: 
Ign http://np.archive.ubuntu.com intrepid Release.gpg
Ign http://np.archive.ubuntu.com intrepid/main Translation-en_US               
Ign http://np.archive.ubuntu.com intrepid/restricted Translation-en_US         
Ign http://np.archive.ubuntu.com intrepid/universe Translation-en_US           
Ign http://np.archive.ubuntu.com intrepid/multiverse Translation-en_US         
Ign http://np.archive.ubuntu.com intrepid-updates Release.gpg                  
Ign http://np.archive.ubuntu.com intrepid-updates/main Translation-en_US       
Ign http://np.archive.ubuntu.com intrepid-updates/restricted Translation-en_US 
Ign http://np.archive.ubuntu.com intrepid-updates/universe Translation-en_US   
Ign http://np.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US 
Ign http://np.archive.ubuntu.com intrepid Release                              
Ign http://np.archive.ubuntu.com intrepid-updates Release                      
Ign http://np.archive.ubuntu.com intrepid/main Packages                        
Ign http://np.archive.ubuntu.com intrepid/restricted Packages                  
Ign http://np.archive.ubuntu.com intrepid/universe Packages                    
Ign http://np.archive.ubuntu.com intrepid/multiverse Packages                  
Hit http://packages.medibuntu.org intrepid Release.gpg                         
Ign http://packages.medibuntu.org intrepid/free Translation-en_US              
Hit http://wine.budgetdedicated.com intrepid Release.gpg                       
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_US            
Ign http://np.archive.ubuntu.com intrepid-updates/main Packages                
Ign http://np.archive.ubuntu.com intrepid-updates/restricted Packages          
Ign http://np.archive.ubuntu.com intrepid-updates/universe Packages            
Ign http://np.archive.ubuntu.com intrepid-updates/multiverse Packages          
Err http://np.archive.ubuntu.com intrepid/main Packages                        
  404 Not Found
Err http://np.archive.ubuntu.com intrepid/restricted Packages                  
  404 Not Found
Hit http://archive.canonical.com intrepid Release.gpg                          
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Err http://np.archive.ubuntu.com intrepid/universe Packages                    
  404 Not Found
Err http://np.archive.ubuntu.com intrepid/multiverse Packages                  
  404 Not Found
Err http://np.archive.ubuntu.com intrepid-updates/main Packages                
  404 Not Found
Err http://np.archive.ubuntu.com intrepid-updates/restricted Packages          
  404 Not Found
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US          
Hit http://wine.budgetdedicated.com intrepid Release                           
Hit http://archive.canonical.com intrepid Release                              
Err http://np.archive.ubuntu.com intrepid-updates/universe Packages            
  404 Not Found
Err http://np.archive.ubuntu.com intrepid-updates/multiverse Packages          
  404 Not Found
Ign http://wine.budgetdedicated.com intrepid/main Packages                     
Hit http://wine.budgetdedicated.com intrepid/main Packages                     
Ign http://archive.canonical.com intrepid/partner Packages                     
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Hit http://archive.canonical.com intrepid/partner Packages                     
Hit http://packages.medibuntu.org intrepid Release                             
Ign http://dl.google.com stable/non-free Translation-en_US                     
Hit http://packages.medibuntu.org intrepid/free Packages             
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Get:2 http://dl.google.com stable Release [1300B]                              
Hit http://security.ubuntu.com intrepid-security Release                       
Hit http://packages.medibuntu.org intrepid/non-free Packages                   
Ign http://ppa.launchpad.net intrepid Release.gpg                    
Get:3 http://dl.google.com stable/non-free Packages [954B]           
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Hit http://security.ubuntu.com intrepid-security/main Packages        
Get:4 http://ppa.launchpad.net intrepid Release.gpg [307B]
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Hit http://ppa.launchpad.net intrepid Release.gpg
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Hit http://ppa.launchpad.net intrepid Release.gpg
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Get:5 http://ppa.launchpad.net intrepid Release [27.6kB]
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Get:6 http://ppa.launchpad.net intrepid Release [46.7kB]
Ign http://ppa.launchpad.net intrepid Release
Hit http://ppa.launchpad.net intrepid Release
Hit http://ppa.launchpad.net intrepid Release
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Fetched 2752B in 5s (501B/s)
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
W: Failed to fetch http://np.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://np.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://np.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://np.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://np.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://np.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://np.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz  404 Not Found

W: Failed to fetch http://np.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Please help

-------
Diwas

---

### Post by ranch hand on 2009-04-24
Did you update your /etc/apt/sources.list?  You need to do that or you will get that very error.

---

### Post by ibuclaw on 2009-04-24
Your sources server is down for the current time.

In the meantime, go to **System->Administration->Software Sources** and change server.
It will be shown by the **download from** dropdown box.

Then run, in the following order.
```
sudo apt-get update
sudo apt-get upgrade
sudo update-manager -d
```

Regards
Iain

---

### Post by diwas on 2009-04-24
> **tinivole said:**
> Your sources server is down for the current time.

In the meantime, go to **System->Administration->Software Sources** and change server.
It will be shown by the **download from** dropdown box.

Then run, in the following order.
```
sudo apt-get update
sudo apt-get upgrade
sudo update-manager -d
```

Regards
Iain
Thank you...it helped :D

---


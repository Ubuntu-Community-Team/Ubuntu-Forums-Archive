---
title: "apt-get problem"
date: 2009-06-10
forum: General Help
---

### Post by civillian on 2009-06-10
I tried to open synaptic to do some installing of applications following my reading of some reviews in magazines etc. and when I opened, it closed unexpectedly. The error that synaptic reported was as follows:
```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

I tried again, to install abiword from the command line (apt-get install) and a similar error message accourred:
```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

I had a synaptic related error occur recently which was resolved by running [code]sudo rm /var/cache/apt/*.bin[.code], the error message was regarding a different error however, so it is possibly unrelated.

I tried google and it pulled up only two entries, one a bug report (which I can't make head nor tail of) and the other unrelated as far as I can tell.

Any help you can give would be much appreciated.

---

### Post by Yellow Pasque on 2009-06-10
Try:
```
sudo apt-get update
```

Also, a link to the bug report you found would be nice.

---

### Post by civillian on 2009-06-10
the output of ```
sudo apt-get update
``` is ```
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_GB                     
Get: 1 http://security.ubuntu.com jaunty-security Release.gpg [189B]           
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB          
Hit http://gb.archive.ubuntu.com jaunty Release.gpg                            
Hit http://gb.archive.ubuntu.com jaunty/main Translation-en_GB                 
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB    
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_GB                
Hit http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB           
Hit http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB           
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB   
Hit http://ppa.launchpad.net jaunty Release                                    
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB     
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB   
Get: 2 http://security.ubuntu.com jaunty-security Release [49.6kB]             
Hit http://le-web.org stable Release.gpg                                       
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_GB            
Hit http://packages.medibuntu.org jaunty Release                               
Hit http://gb.archive.ubuntu.com jaunty Release                                
Hit http://ppa.launchpad.net jaunty/main Packages                              
Hit http://gb.archive.ubuntu.com jaunty-updates Release                        
Hit http://ppa.launchpad.net jaunty/main Sources                               
Hit http://packages.medibuntu.org jaunty/free Packages                         
Hit http://gb.archive.ubuntu.com jaunty/main Packages                          
Hit http://gb.archive.ubuntu.com jaunty/restricted Packages                 
Hit http://gb.archive.ubuntu.com jaunty/main Sources                        
Hit http://gb.archive.ubuntu.com jaunty/restricted Sources                  
Hit http://gb.archive.ubuntu.com jaunty/universe Packages                      
Hit http://gb.archive.ubuntu.com jaunty/universe Sources                       
Hit http://gb.archive.ubuntu.com jaunty/multiverse Packages                    
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Hit http://packages.medibuntu.org jaunty/free Sources                          
Hit http://packages.medibuntu.org jaunty/non-free Sources                      
Hit http://gb.archive.ubuntu.com jaunty/multiverse Sources                     
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/main Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Sources            
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Packages             
Get: 3 http://security.ubuntu.com jaunty-security/main Packages [28.9kB]       
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Sources               
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages            
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources             
Get: 4 http://security.ubuntu.com jaunty-security/restricted Packages [14B]    
Get: 5 http://security.ubuntu.com jaunty-security/main Sources [9325B]
Ign http://le-web.org stable/main Translation-en_GB                      
Get: 6 http://security.ubuntu.com jaunty-security/restricted Sources [14B]
Get: 7 http://security.ubuntu.com jaunty-security/universe Packages [8823B]
Get: 8 http://security.ubuntu.com jaunty-security/universe Sources [1941B]
Get: 9 http://security.ubuntu.com jaunty-security/multiverse Packages [14B]
Get: 10 http://security.ubuntu.com jaunty-security/multiverse Sources [14B]
Hit http://le-web.org stable Release               
Ign http://le-web.org stable/main Packages
Hit http://le-web.org stable/main Packages
Fetched 98.9kB in 1s (51.4kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

the bug report was this one [https://bugs.launchpad.net/ubuntu/+bug/371191](https://bugs.launchpad.net/ubuntu/+bug/371191)

many thanks



[edit]
according to the tray icon that pops up when I try to open synaptic, I have unmet dependencies for installed apps...
[/edit]

---

### Post by civillian on 2009-06-10
---solved---

by changing my repos to main instead of GB

dunno what this changed, but it will be a fix for now.

---


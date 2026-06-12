---
title: "Can't Run updates."
date: 2014-09-29
forum: Debian
---

### Post by Noldoran on 2014-09-29
Hello guys. Today I tried to update but it's pop out this message.
```
Ign http://repo.mate-desktop.org wheezy Release.gpg
Hit http://security.debian.org wheezy/updates Release.gpg                      
Ign http://repo.mate-desktop.org wheezy Release                                
Hit http://packages.crunchbang.org waldorf Release.gpg                         
Hit http://security.debian.org wheezy/updates Release                          
Ign http://repo.mate-desktop.org wheezy/main amd64 Packages/DiffIndex          
Hit http://packages.crunchbang.org waldorf Release                             
Hit http://security.debian.org wheezy/updates/main amd64 Packages              
Ign http://repo.mate-desktop.org wheezy/main i386 Packages/DiffIndex           
Hit http://packages.crunchbang.org waldorf/main amd64 Packages                 
Hit http://security.debian.org wheezy/updates/main i386 Packages               
Hit http://dl.google.com stable Release.gpg                                    
Hit http://http.debian.net wheezy Release.gpg                                  
Hit http://packages.crunchbang.org waldorf/main i386 Packages                  
Hit http://security.debian.org wheezy/updates/main Translation-en              
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://http.debian.net wheezy Release                            
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://http.debian.net wheezy/main amd64 Packages                          
Hit http://http.debian.net wheezy/non-free amd64 Packages                      
Hit http://http.debian.net wheezy/contrib amd64 Packages                       
Hit http://http.debian.net wheezy/contrib i386 Packages                        
Hit http://http.debian.net wheezy/main i386 Packages                           
Hit http://http.debian.net wheezy/contrib Translation-en                       
Hit http://http.debian.net wheezy/non-free i386 Packages                       
Ign http://packages.crunchbang.org waldorf/main Translation-en_US              
Hit http://http.debian.net wheezy/non-free Translation-en                      
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://http.debian.net wheezy/main Translation-en                          
Ign http://packages.crunchbang.org waldorf/main Translation-en       
Ign http://dl.google.com stable/main Translation-en                  
Ign http://repo.mate-desktop.org wheezy/main Translation-en_US
Ign http://repo.mate-desktop.org wheezy/main Translation-en
Err http://repo.mate-desktop.org wheezy/main amd64 Packages
  404  Not Found
Err http://repo.mate-desktop.org wheezy/main i386 Packages
  404  Not Found
W: Failed to fetch http://repo.mate-desktop.org/debian/dists/wheezy/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://repo.mate-desktop.org/debian/dists/wheezy/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Please Help Me.

---

### Post by ian-weisser on 2014-09-29
'404 Not Found' means exactly the same thing as on a web page that doesn't exist (anymore).
Comment out or otherwise disable that source.

---

### Post by buzzingrobot on 2014-09-29
The Debian and Ubuntu repos maintained by the MATE team at mate-desktop.org have been taken down.

More here: [http://mate-desktop.org/blog/2014-09-25-debian-and-ubuntu-repositories-removed/](http://mate-desktop.org/blog/2014-09-25-debian-and-ubuntu-repositories-removed/)

---

### Post by Noldoran on 2014-09-29
what should i do now? should i remove them?

---

### Post by Noldoran on 2014-09-29
buzzingrobot i read the link by the way the line says > [COLOR=#666666][FONT=Open Sans]If you require MATE packages for Debian or Ubuntu then the package repositories above are the official repositories to use.[/FONT][/COLOR] i want mate packages for debian but i don't know which is what could you help me pls? i really dont know much about these stuff i dont want to screwed up.

---

### Post by buzzingrobot on 2014-09-29
> **Noldoran said:**
> buzzingrobot i read the link by the way the line says  i want mate packages for debian but i don't know which is what could you help me pls? i really dont know much about these stuff i dont want to screwed up.

The Mate 1.8 packages for Debian stable are in the Debian backports repo. There's a link in that post.  If it was me, I'd edit /etc/apt/sources.list to remove the defunct mate-desktop.org entries, enable the Debian backports repo, and do an update and dist-upgrade, while crossing my fingers. 

As I recall, the 1.8 Ubuntu/Debian repos maintained at mate-desktop.org were never considered "official" and never actually migrated into their offical repos. That post notes some packages were unsigned and/or unmaintained.

---

### Post by QIII on 2014-09-29
As you are requesting help for Debian, moved to Other Operating Systems and Projects

---

### Post by Habitual on 2014-09-29
anybody else notice:
```
Hit [http://packages.crunchbang.org](http://packages.crunchbang.org) waldorf Release.gpg                         
Hit [http://packages.crunchbang.org](http://packages.crunchbang.org) waldorf Release                             
Hit [http://packages.crunchbang.org](http://packages.crunchbang.org) waldorf/main amd64 Packages                 
Hit [http://packages.crunchbang.org](http://packages.crunchbang.org) waldorf/main i386 Packages                  
Ign [http://packages.crunchbang.org](http://packages.crunchbang.org) waldorf/main Translation-en_US              
Ign [http://packages.crunchbang.org](http://packages.crunchbang.org) waldorf/main Translation-en
```, or is that not an issue?

---


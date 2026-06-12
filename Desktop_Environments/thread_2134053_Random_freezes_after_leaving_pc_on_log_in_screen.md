---
title: "Random freezes after leaving pc on log in screen"
date: 2013-04-10
forum: Desktop Environments
---

### Post by Zdechlak on 2013-04-10
Hello
I have a problem since beginning of using Kubuntu:
After I lock my PC with alt+crtl+L and leave it for a night, I can't wake it up sometimes. As I observed it happens randomly (sometimes 1 time in a month, sometimes 3 times per week). The screen is black and there is no response for keyboard or mouse. I tried a lot of shortcuts, but non of them worked.

Last log in syslog before last 'hang out':
09/04/2013 20:17:01    <pc name>    CRON[4119]    (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

System info:

**cat /etc/*-release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
NAME="Ubuntu"
VERSION="12.04.2 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian                                                                                                                                               
PRETTY_NAME="Ubuntu precise (12.04.2 LTS)"                                                                                                                   
VERSION_ID="12.04"                    
                                                                                                                       
**lsb_release -a **                                                                                                                   
No LSB modules are available.                                                                                                                                
Distributor ID: Ubuntu                                                                                                                                       
Description:    Ubuntu 12.04.2 LTS                                                                                                                           
Release:        12.04                                                                                                                                        
Codename:       precise          
                                                                                                                            
**uname -a**                                                                                                                          
Linux <pc name> 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux   

Anyone have an idea why it is happening?
(sorry for my english)

---

### Post by Zdechlak on 2013-04-25
Nobody can help with this problem?

---


---
title: "mini 9,Jaunty Jacklope UNR, how do i make firefox open a pdf file within the browser?"
date: 2009-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shiningkenmonster on 2009-05-08
I have dell mini 9, running on the new Jaunty Jacklope Ubuntu Netbook remix.

someone told me about this website:
[https://help.ubuntu.com/community/SettingUpUbuntu]("https://help.ubuntu.com/community/SettingUpUbuntu")

I did the majority of the command lines. On the part:

To install Adobe Reader

At a terminal, type in:
```
sudo apt-get install acroread acroread-plugins mozilla-acroread
```

it didn't work. It says packages could not be found.

I have installed xpdf on the terminal, but it didn't open a pdf file within firefox. It just says "would you like to open/download the pdf file everytime?"

do the majority of linux users just download the pdf separately from firefox or just have the pdf files load within the firefox broswer?

---

### Post by cggaret on 2009-05-09
I believe these packages are in the medibuntu repo, so you need to have those enabled. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)  will show you how.

---

### Post by Brandon Williams on 2009-05-09
Go to 'Administration->Software Sources', click on the 'Third-Party Sources' tab, and check the box next to 'http://archive.canonical.com/ubuntu jaunty partner'. Close the app, which should run 'apt-get update' for you.

Now you can install both acroread and adobe-flashplugin, which are in the partner repository.

---

### Post by dwightpaige79 on 2009-05-09
> **Brandon Williams said:**
> Go to 'Administration->Software Sources', click on the 'Third-Party Sources' tab, and check the box next to 'http://archive.canonical.com/ubuntu jaunty partner'. Close the app, which should run 'apt-get update' for you.

Now you can install both acroread and adobe-flashplugin, which are in the partner repository.

In Kubuntu Jaunty amd64 enabling those resources does not result in installing acroread for me.

```
$ cat /etc/apt/sources.list                 
# deb cdrom:[Kubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to                         
# newer versions of the distribution.                                                             


## Major bug fix updates produced after the final release of the
## distribution.                                                

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse

deb http://security.ubuntu.com/ubuntu/ jaunty-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ jaunty-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe main multiverse restricted

$ sudo aptitude update && sudo aptitude install acroread
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Hit http://archive.ubuntu.com jaunty Release.gpg                               
Ign http://archive.ubuntu.com jaunty/main Translation-en_US                    
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Hit http://archive.canonical.com jaunty Release                                
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US                
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US              
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US              
Hit http://archive.ubuntu.com jaunty-updates Release.gpg                       
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US            
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US      
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US      
Hit http://archive.ubuntu.com jaunty Release                                   
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US               
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US               
Hit http://security.ubuntu.com jaunty-security Release                                    
Ign http://archive.canonical.com jaunty/partner Packages                                  
Hit http://archive.ubuntu.com jaunty-updates Release                                      
Hit http://security.ubuntu.com jaunty-security/universe Packages                          
Ign http://archive.canonical.com jaunty/partner Sources                                   
Hit http://archive.ubuntu.com jaunty/main Packages                                        
Hit http://archive.ubuntu.com jaunty/universe Packages                                    
Hit http://archive.ubuntu.com jaunty/restricted Packages                                  
Hit http://archive.ubuntu.com jaunty/multiverse Packages                                  
Hit http://archive.ubuntu.com jaunty/main Sources                                         
Hit http://security.ubuntu.com jaunty-security/main Packages                              
Hit http://security.ubuntu.com jaunty-security/multiverse Packages                        
Hit http://security.ubuntu.com jaunty-security/restricted Packages                        
Hit http://security.ubuntu.com jaunty-security/universe Sources                           
Hit http://archive.canonical.com jaunty/partner Packages
Hit http://archive.ubuntu.com jaunty/universe Sources
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://archive.ubuntu.com jaunty/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/main Packages
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.ubuntu.com jaunty-updates/main Sources
Hit http://archive.canonical.com jaunty/partner Sources
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates/restricted Sources
Reading package lists... Done

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No candidate version found for acroread
No candidate version found for acroread
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
```

I wish it did because some where in 'http://archive.canonical.com/ubuntu' there IS a 9.1 version of acroread. The version in medibuntu is I believe 8.1. What do I need to do to get the 'http://archive.canonical.com/ubuntu' version of acroread installed in amd64? Is there some other repo or package needed?

---

### Post by ugm6hr on 2009-05-09
> **dwightpaige79 said:**
> I wish it did because some where in 'http://archive.canonical.com/ubuntu' there IS a 9.1 version of acroread. 

The package search only finds the Dapper 7.0 acroread package.

Perhaps if you post a link to the 9.1 version you found?

---

### Post by dwightpaige79 on 2009-05-09
> **ugm6hr said:**
> The package search only finds the Dapper 7.0 acroread package.

Perhaps if you post a link to the 9.1 version you found?

Thanks. And here is what I found:

[http://archive.canonical.com/ubuntu/pool/partner/a/acroread/](http://archive.canonical.com/ubuntu/pool/partner/a/acroread/)

---

### Post by ugm6hr on 2009-05-09
Looks like it is 32-bit only.

32-bit applications can be installed on Ubuntu 64-bit, but I haven't done it for a while.

This might help: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

EDIT: realised OP is running 32-bit, in which case downloading the i386 .deb and double-clicking will install it.

---

### Post by jyaan on 2009-06-02
There is _no_ reason to go through all that. You don't even need _any_ of Adobe's proprietary programs. Just install mozplugger and you'll be set. That will embed Ubuntu's default document reader into the browser window when you click on a link to a PDF. It's in the repos and it works just as well in 64 as it does in 32. I use it all the time. You can still save the PDF if you want to by saving the page.

---


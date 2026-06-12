---
title: "Wrong sources.list?"
date: 2007-11-26
forum: Desktop Environments
---

### Post by Exonimus on 2007-11-26
Wasn't sure if this is in the right section, if it's not, feel free to move it.

I have the following problem: I updated my feisty release to gutsy RC and kept updating it. However, I recently noticed(and it has been the case for longer, that when I update, I get the following error:
(you might see some dutch text. Genegeerd=ignored ophalen=fetching ophalen... is mislukt=fetching...has failed
```
sroelof@roelof-desktop:~$ sudo apt-get update
Ophalen:1 http://archive.canonical.com gutsy Release.gpg [191B]
Genegeerd http://archive.canonical.com gutsy/partner Translation-nl            
Genegeerd http://ppa.launchpad.net gutsy Release.gpg                           
Genegeerd http://ppa.launchpad.net gutsy/main Translation-nl                   
Genegeerd http://download.skype.com stable Release.gpg                         
Genegeerd http://download.skype.com stable/non-free Translation-nl             
Genegeerd http://ppa.launchpad.net gutsy/universe Translation-nl               
Geraakt http://archive.canonical.com gutsy Release                             
Geraakt http://ppa.launchpad.net gutsy Release                                 
Ophalen:2 http://nl.archive.ubuntu.com feisty-backports Release.gpg [191B]     
Genegeerd http://nl.archive.ubuntu.com feisty-backports/main Translation-nl    
Genegeerd http://nl.archive.ubuntu.com feisty-backports/restricted Translation-nl
Ophalen:3 http://archive.ubuntu.com gutsy Release.gpg [191B]                   
Genegeerd http://archive.ubuntu.com gutsy/web Translation-nl                   
Genegeerd http://nl.archive.ubuntu.com feisty-backports/universe Translation-nl
Genegeerd http://nl.archive.ubuntu.com feisty-backports/multiverse Translation-nl
Genegeerd http://archive.ubuntu.com gutsy/multiverse Translation-nl            
Genegeerd http://archive.ubuntu.com gutsy/restricted Translation-nl            
Geraakt http://archive.ubuntu.com gutsy/universe Translation-nl                
Geraakt http://archive.ubuntu.com gutsy/main Translation-nl                    
Ophalen:4 http://archive.ubuntu.com gutsy-security Release.gpg [191B]          
Genegeerd http://archive.ubuntu.com gutsy-security/web Translation-nl          
Genegeerd http://archive.ubuntu.com gutsy-security/multiverse Translation-nl   
Genegeerd http://archive.ubuntu.com gutsy-security/restricted Translation-nl   
Genegeerd http://download.skype.com stable Release                             
Genegeerd http://ppa.launchpad.net gutsy/main Packages                         
Genegeerd http://archive.canonical.com gutsy/partner Packages                  
Geraakt http://nl.archive.ubuntu.com feisty-backports Release                  
Genegeerd http://archive.ubuntu.com gutsy-security/universe Translation-nl     
Genegeerd http://archive.ubuntu.com gutsy-security/main Translation-nl         
Ophalen:5 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]         
Genegeerd http://archive.ubuntu.com gutsy-backports/web Translation-nl         
Genegeerd http://archive.ubuntu.com gutsy-backports/multiverse Translation-nl  
Genegeerd http://archive.ubuntu.com gutsy-backports/restricted Translation-nl  
Genegeerd http://archive.ubuntu.com gutsy-backports/universe Translation-nl    
Genegeerd http://archive.ubuntu.com gutsy-backports/main Translation-nl        
Ophalen:6 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]           
Geraakt http://download.skype.com stable/non-free Packages                     
Genegeerd http://ppa.launchpad.net gutsy/universe Packages                     
Genegeerd http://ppa.launchpad.net gutsy/main Sources                          
Geraakt http://archive.canonical.com gutsy/partner Packages                    
Geraakt http://nl.archive.ubuntu.com feisty-backports/main Packages            
Genegeerd http://ppa.launchpad.net gutsy/universe Sources                      
Genegeerd http://archive.ubuntu.com gutsy-updates/web Translation-nl           
Geraakt http://ppa.launchpad.net gutsy/main Packages                           
Geraakt http://ppa.launchpad.net gutsy/universe Packages                       
Geraakt http://nl.archive.ubuntu.com feisty-backports/restricted Packages      
Geraakt http://nl.archive.ubuntu.com feisty-backports/universe Packages        
Geraakt http://nl.archive.ubuntu.com feisty-backports/multiverse Packages      
Geraakt http://nl.archive.ubuntu.com feisty-backports/main Sources             
Geraakt http://nl.archive.ubuntu.com feisty-backports/restricted Sources       
Geraakt http://nl.archive.ubuntu.com feisty-backports/universe Sources         
Geraakt http://nl.archive.ubuntu.com feisty-backports/multiverse Sources       
Genegeerd http://archive.ubuntu.com gutsy-updates/multiverse Translation-nl    
Genegeerd http://archive.ubuntu.com gutsy-updates/restricted Translation-nl
Genegeerd http://archive.ubuntu.com gutsy-updates/universe Translation-nl
Genegeerd http://archive.ubuntu.com gutsy-updates/main Translation-nl
Geraakt http://ppa.launchpad.net gutsy/main Sources        
Geraakt http://archive.ubuntu.com gutsy Release            
Geraakt http://archive.ubuntu.com gutsy-security Release   
Geraakt http://archive.ubuntu.com gutsy-backports Release  
Geraakt http://archive.ubuntu.com gutsy-updates Release    
Geraakt http://ppa.launchpad.net gutsy/universe Sources    
6B opgehaald in 1s (4B/s)                           
Ophalen van http://archive.ubuntu.com/ubuntu/dists/gutsy/Release Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?) is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?) is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?) is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?) is mislukt
Pakketlijsten worden ingelezen... Klaar
E: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.(fetching of some index files has failed. These are either ignored, or older versions have been used)
roelof@roelof-desktop:~$ 

```

in other words, it seems I can't get updates from some sources properly. I have no idea what the problem is, might be with me having done something wrong, or that something went wrong with updating awhile ago. FYI, here is my sources .list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy web multiverse restricted universe main

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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
deb http://nl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-security web multiverse restricted universe main
deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports web multiverse restricted universe main
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates web multiverse restricted universe main
# deb http://wine.budgetdedicated.com/apt gutsy main
# deb-src http://wine.budgetdedicated.com/apt gutsy main
deb http://ppa.launchpad.net/zachtib/ubuntu gutsy main universe
deb-src http://ppa.launchpad.net/zachtib/ubuntu gutsy main universe

```

any help would be appreciated. Also: if I messed something up, sorry :P

---

### Post by PeterJS on 2007-11-26
Nope, that's perfectly normal. the ones that it appears to be having trouble pulling are the translation repositories. I've never seen those work right in english, and never had any language problems, if that's your only issue I think you're fine.

---

### Post by rsambuca on 2007-11-26
> **PeterJS said:**
> Nope, that's perfectly normal. the ones that it appears to be having trouble pulling are the translation repositories. I've never seen those work right in english, and never had any language problems, if that's your only issue I think you're fine.

I am afraid I definitely disagree with this.  You have mixed Feisty and Gutsy repos.  I strongly suggest getting rid of the Feisty entries.

---

### Post by Exonimus on 2007-11-26
good. But I'll tell you the whole story then. I was trying to get compiz working properly, and I tried getting the compiz settings manager(gnome-compiz-manager) and it was not there.I couldn't apt-get it even though I enabled universe,multiverse,main and restricted. It just told me: couldn't find package gnome-compiz-manager. Because one of my friend did have the package in it's repository, and because I got those: couldn't find packages, I figured one could be related to the other...
Anyway, if it's not, can you tell me why that package is not there? :/

edit: read the second post. Removed the fesity backports parts.

edit: because I was following a tutorial to install the advanced compiz settings(cube and some other stuff) properly. I tried compizconfig-settings-manage,emerald. It said they didn't have an installable candidate.

---

### Post by PeterJS on 2007-11-26
> **rsambuca said:**
> I am afraid I definitely disagree with this.  You have mixed Feisty and Gutsy repos.  I strongly suggest getting rid of the Feisty entries.

You're right, my bad, I just glossed right over that :(

---

### Post by rsambuca on 2007-11-26
What happens now when you run

sudo apt-get update && sudo apt-get upgrade

---

### Post by jonhaun on 2007-11-26
I'm having the same issue. I've tried uncommenting all of paths in the source.list file and I've run the sudo apt-get upgrade && sudo apt-get update.

For some reason I get the updates available popup and it executes fine, but when I try to update manually or install a new app (Bluefish in this case) I get the same error as above.

---

### Post by rsambuca on 2007-11-26
> **jonhaun said:**
> I'm having the same issue. I've tried uncommenting all of paths in the source.list file and I've run the sudo apt-get upgrade && sudo apt-get update.

For some reason I get the updates available popup and it executes fine, but when I try to update manually or install a new app (Bluefish in this case) I get the same error as above.

Post your sources list.```
cat /etc/apt/sources.list
```

---

### Post by jonhaun on 2007-11-26
Thanks for taking the time to help on this and for the quick response. Here is my source.list

<code>
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted web
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted web
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
</code>

In trying to track down the problem, I put the Release path into the browser and it gave me the file that I think describes the files in updates. I noticed that there was no " web/binary-i386" anywhere in either the Gusty or Feisty versions. Is this an incorrect setting on my end?

---

### Post by rsambuca on 2007-11-26
Have you tried using the Software Sources?  Go to the top menu bar and select "System -> Administration -> Software Sources".  Make sure the repositories are checked.  For the mirror, select "Other".  In the window that opens, select "find the best" (or something like that - I am not on my linux box at the moment).  It will test all the mirrors and then pick the best one.

Then update and upgrade and see if that works.

---

### Post by jonhaun on 2007-11-26
I just deleted the "web" at the end of the first two path definitions and I was able to update the OS and install Bluefish. Do you have any guess on why the "web" was on there?

"deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted web" ->
"deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted"

And am I going to break something if I leave it off?

Also I just updated to the best server as the app found.

---

### Post by rsambuca on 2007-11-26
I don't have it in mine, but I have seen it in others.  I don't know where it is coming from or what it does, to be honest.

---

### Post by jonhaun on 2007-11-26
Thanks again for helping me track this down. I'm going to do some more research and find out if I messed something up. But atleast for now I have it working again. 

From what I can tell the arguments after the path specify the sub-group/folder for the update manager to search under. I don't see a "web" folder in the directory that it searches: [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/) so I guess that is why it fails. I just wonder what put the "web" there.

---

### Post by Exonimus on 2007-11-27
guys, I think removing the 'web' might have fixed my problem. Now, there are quite some update available. I'll get back to you soon to see if it actually fixed my problem, but it seems it has! :D:D

edit: it found the manager! woo! thanks for the help :)

---

### Post by rsambuca on 2007-11-27
I'd sure like to know how you guys got that into your sources.list in the first place.  Very curious.

---

### Post by Exonimus on 2007-11-27
to be honest, I have no clue. All I know is that I updated to the 7.10RC the day before it became final. It might have something to do with that. Then again, it might not. Doesn't seem very logical, but I'd really have no clue where it came from otherwise... I mean, updating is basically point and click :P

---

### Post by viking777 on 2007-11-27
If you ever have a problem with sources.list just go to this site and let it write it for you:


[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Couldn't be easier and I have never been aware of it making a mistake.

---


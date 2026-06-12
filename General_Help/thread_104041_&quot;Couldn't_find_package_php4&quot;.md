---
title: "&quot;Couldn't find package php4&quot;"
date: 2005-12-15
forum: General Help
---

### Post by Snackmaster on 2005-12-15
I'm up and running the Breezy Badger and am trying to configure my personal desktop be a testing web server. I've installed Apache successfully but can't get PHP installed.

Following these instructions: [http://ubuntuguide.org/#installphpapache](http://ubuntuguide.org/#installphpapache)

I get this message: "Couldn't find package php4"

<warning> Complete newbie to Linux </warning>
I've tried and tried Linux over the last ten years. Thank you, oh thank you to the Ubuntu team for coming up with a version that was love at first sight!

---

### Post by lutrafobic on 2005-12-15
Perhaps try a: ```
sudo aptitude install libapache2-mod-php4
```

---

### Post by Snackmaster on 2005-12-15
Gave it a shot but no go...

sudo aptitude install libapache2-mod-php4
```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No candidate version found for libapache2-mod-php4
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
```

---

### Post by lutrafobic on 2005-12-15
How does you 'sources.list' look? Can you copy & paste the files contence here, please.

```
nano /etc/apt/sources.list
```

Mine looks like this:

```

deb cdrom:[Ubuntu-Server 5.10 _Breezy Badger_ - Release i386 (20051013)]/ breezy main restricted

deb http://se.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://se.archive.ubuntu.com/ubuntu breezy main restricted

deb http://se.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://se.archive.ubuntu.com/ubuntu breezy universe
deb-src http://se.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://se.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

Note which are comment'ed out and which that aren't.

---

### Post by Snackmaster on 2005-12-15
ah yes mine is very different, and in reading on this issue I saw mention of this file and of using the server 'Universe'.  If I can figure out how to edit the file I'll give it a go.

Thanks for your help!

everything I have is straight out of the box desktop setup
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main $

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted univ$# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted $
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by Snackmaster on 2005-12-15
I tried editing the file with Nano using ctrl + O 
"error writing /filepath/name  Permission denied"

---

### Post by Snackmaster on 2005-12-15
! Ultimate newbie solution 

PHP and MySQl appear to only be available from the repository "universe" which is inactive on the local machine by default. Why is that? (security on power tools through obsfuscation??)

Why did I not have permission to edit the repository file manually?

I'm now left with the feeling I've turned something on I shouldn't have. Should I turn "universe" repository back off? If so how. Hmmmm. 

At any rate on to the Ultimate Newbie Soltuion!
Use "Add Applications" to activate the Universe Repository
- Click Applications -> Add Applications
- Find an application package which is not currently available (grayed out)
- Double click on that unavailable app (very unintuitive, I only did it as a last resort and was surprised by the result)
- You will be informed that the package is only available from the "universe repository" and would you like to enable that ability.
- Say yes!
- App Manager downloads a bunch of files (not the app you requested)
- Close app manager (so the ersource isn't locked)
- Fire up terminal
- Follow these instructions: [http://ubuntuguide.org/#installphpapache](http://ubuntuguide.org/#installphpapache)

---

### Post by kaamos on 2005-12-15
The file is outside your home directory, so you need permission to edit it. Adding the "sudo" command before nano gives you that.

There is nothing wrong with adding universe multiverse, don't worry. :)
Check these out:
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

EDIT: more info here [http://www.ubuntulinux.org/ubuntu/components/document_view](http://www.ubuntulinux.org/ubuntu/components/document_view)

---

### Post by Snackmaster on 2005-12-15
> **kaamos]The file is outside your home directory, so you need permission to edit it. Adding the "sudo" command before nano gives you that.[/QUOTE]

You mean I'm not on Windows where if I'm logged on I own it. 
Me greps for *.spyware  said:**
> 
There is nothing wrong with adding universe multiverse, don't worry. :)
Check these out:
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

EDIT: more info here [http://www.ubuntulinux.org/ubuntu/components/document_view](http://www.ubuntulinux.org/ubuntu/components/document_view)

Excellent links, thanks! it's hard to search for what you don;t know you'er looking for :)

---


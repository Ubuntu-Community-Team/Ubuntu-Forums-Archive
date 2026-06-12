---
title: "CRAN repos broken?"
date: 2007-03-09
forum: Education &amp; Science
---

### Post by David Valentine on 2007-03-09
I believe the Ubuntu CRAN mirrors are broken, and yesterday I sent the following e-mail to [EMAIL="CRAN@r-project.org"]CRAN@r-project.org[/EMAIL].  I have not received a response, and the repos appear still to be broken.  Does anyone have any insight on this?:confused:

Greetings: 

I am using Ubuntu 6.10 (edgy), and previously have been successful using  the CRAN mirrors as a repository to maintain R via apt-get.  However, I  am now getting the following error in response to "apt-get update": >  W: Conflicting distribution: [http://cran.fhcrc.org]("http://cran.fhcrc.org/") edgy/ Release  (expected edgy but got )  This suggests to me that the Release file in the mirror download area  does not specify edgy, and indeed its header reads as follows: >  Date: Wed, 17 Jan 2007 15:00:11 UTC 
MD5Sum:Whereas a typical Ubuntu Release file header reads (from  [http://us.archive.ubuntu.com/ubuntu/dists/edgy/](http://us.archive.ubuntu.com/ubuntu/dists/edgy/)) >  Origin: Ubuntu 
Label: Ubuntu 
Suite: edgy 
Version: 6.10 
Codename: edgy 
Date: Wed, 25 Oct 2006 17:07:09 UTC 
Architectures: amd64 hppa i386 ia64 powerpc sparc 
Components: main restricted universe multiverse 
Description: Ubuntu Edgy 6.10 
MD5Sum:The abbreviated header is also in the Ubuntu dapper Release file,  whereas the Release file for Debian etch contains full headers like  those above. 

I have checked this on 3 mirrors. 

Thus I believe that the CRAN Ubuntu Release files are currently  incorrect and are causing apt-get to fail for all Ubuntu users. 

If I should have sent this e-mail elsewhere, please let me know where,  and accept my apology.  Thank you for the contributions you have been  making to academic data analysis.

---

### Post by akniss on 2007-03-09
I'm using the following mirror as a repo to keep my R up to date, and have had no issues.  maybe give it a try.

```
## CRAN mirrors as repos to get latest R version
deb http://rh-mirror.linux.iastate.edu/CRAN/bin/linux/ubuntu/ edgy/

```

---

### Post by David Valentine on 2007-03-09
I get the same error using that repo, also on a different machine than I reported earlier.  ```
$sudo apt-get update
``` yields > Failed to fetch [http://rh-mirror.linux.iastate.edu/CRAN/bin/linux/ubuntu/edgy/Release](http://rh-mirror.linux.iastate.edu/CRAN/bin/linux/ubuntu/edgy/Release)  Unable to find expected entry  Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Conflicting distribution: [http://rh-mirror.linux.iastate.edu](http://rh-mirror.linux.iastate.edu) edgy/ Release (expected edgy but got )If I'm doing something wrong, I'm doing it consistently across multiple machines.  Is no one else experiencing this?

---

### Post by akniss on 2007-03-09
I get a GPG error, but nothing that interferes with installation or updates...  do you get the same error if you go through synaptic?

---

### Post by David Valentine on 2007-03-10
> I get a GPG error, but nothing that interferes with installation or updates... do you get the same error if you go through synaptic?Synaptic (actually, adept in my case) does not give me that error, or other errors that I need to know about.   I doubt that you're getting the actual CRAN updates, then, unless they're also going to the official Ubuntu repos.  The GPG error comes from not supplying the GPG key (see the README file [here]("http://rh-mirror.linux.iastate.edu/CRAN/bin/linux/ubuntu/")), which I think is pretty much a show-stopper as far as getting updates is concerned.  I think they only recently (January) started using secure repos.

---

### Post by akniss on 2007-03-10
R version 2.4.1 (2006-12-18)
Copyright (C) 2006 The R Foundation for Statistical Computing
ISBN 3-900051-07-0

I successfully used the repo to get the latest version, and its difficult to tell if I'm getting updates since there haven't been any for a couple months.

---

### Post by David Valentine on 2007-03-10
I have that version as well.  While all of the package files in the repos are dated 2007.01.01, all of the files having to do with managing them (Packages.gz, Release, Sources.gz) are dated 2007.01.17, and Release.gpg is dated 2007.03.06.  This suggests to me that some reorganizing of the repos occurred after the most recent update, and those changes are generating the error(s).  I suppose the test will be when they do release an update, unless they also change the Release file.

---

### Post by David Valentine on 2007-03-11
Received 2007.03.10 from the package maintainer:> Thanks to Johannes' scripts and config files, the Release files for Ubuntu Dapper and Edgy should now be fixed. The updated files will start propagating to CRAN in about half an hour. I confirmed that apt-get no longer returns errors.

---


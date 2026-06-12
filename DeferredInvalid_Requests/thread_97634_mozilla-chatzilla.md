---
title: "mozilla-chatzilla"
date: 2005-12-01
forum: Deferred/Invalid Requests
---

### Post by lotusleaf on 2005-12-01
The mozilla-chatzilla fails to install, burping up the following message:

```
mozilla-chatzilla:
  Depends: mozilla-browser (=2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed
```

Does this need to be backported?

I posted about this in the repositories section of the forums but it received no reply and the package still won't install from *.ubuntu.com repositories so I'm asking here. :) Thanks for reading

---

### Post by strikeforce on 2005-12-01
Can you show your sources.list

---

### Post by lotusleaf on 2005-12-04
[QUOTE=strikeforce]Can you show your sources.list[/QUOTE]

I have *.ubuntu.com sources in my sources list. I haven't checked within the past few days to see if the mozilla-chatzilla package has been updated, but it seems that the mozilla browser package was updated without the chatzilla package being updated with it?

---

### Post by lotusleaf on 2005-12-30
looks like this has been resolved! :)

---

### Post by Jave27 on 2006-01-09
I am having this problem on the AMD64 target as well.  Here is my sources.list file:

```
deb http://us.archive.ubuntu.com/ubuntu/ breezy main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ breezy universe  
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy universe  

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu/ breezy-security universe  
deb-src http://security.ubuntu.com/ubuntu/ breezy-security universe  
```

---


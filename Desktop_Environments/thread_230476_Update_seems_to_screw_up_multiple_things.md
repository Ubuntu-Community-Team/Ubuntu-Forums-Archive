---
title: "Update seems to screw up multiple things"
date: 2006-08-06
forum: Desktop Environments
---

### Post by liquideath on 2006-08-06
It seems after updating, a number of problems have popped up:

1. The terminal has changed, it now has a yellow background
2. Backspace doesn't work properly, holding it down does nothing.
3. I cant configure the mouse properly, it moves way too slow now. Adjusting senstitivity doesn't do anything. 
4. The graphical sudo program has changed, has a checkbox for "remember password", but it no longer works. It always "wrong password." Regular sudo still works.

WTF? Is it because of my sources.list has messed things up:

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free

## Latest KDE
deb http://kubuntu.org/packages/kde-latest dapper main

## Latest Amarok
deb http://kubuntu.org/packages/amarok-latest dapper main

## For tunepimp mp3 support
deb http://archive.czessi.net/ubuntu/ dapper main universe

## For automatix
deb http://www.getautomatix.com/apt dapper main

## For wine
deb http://wine.budgetdedicated.com/apt dapper main

```

---

### Post by Jagot on 2006-08-06
Updates from the official repo's are fine for me.  It sounds as though packages have been pulled from those unoffoicial repo's you have there in your sources.list.

---

### Post by liquideath on 2006-08-06
Thats what I figured, but I added those to fix some specific problems. If I comment them out, can a downgrade to the official ones?

---

### Post by liquideath on 2006-08-06
Apparently, the problem doesn't seem to be with my unofficial packages, which are mostly kde, unless it is backports that is causing the problem. I don't get it. Has anyone else experienced these issues? Is there a way to roll back to a package list from a couple of days ago? It seems to be either the 8/4 or 8/1 update that been causing me problems.

---

### Post by liquideath on 2006-08-07
I reloaded ubuntu from the cd and installed all the updates, and now the problems are gone. Strange...

---


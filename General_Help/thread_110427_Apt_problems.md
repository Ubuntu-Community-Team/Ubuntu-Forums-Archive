---
title: "Apt problems"
date: 2005-12-30
forum: General Help
---

### Post by chubsmalone on 2005-12-30
I switched from ubuntu to kubuntu and I have almost everything the way I like it except for one thing.  When I do apt-get upgrade, I get this error:

```
root@Ballard:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libkleopatra0a linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up debtags (1.4+svn20050912-0ubuntu1) ...
Get:1 http://people.debian.org/~enrico/tags/tags-current.gz
Get:2 http://people.debian.org/~enrico/tags/vocabulary.gz
Fetched 6228B in 0s (14.0kB/s)
Reading tag data and vocabulary for http://people.debian.org/~enrico/tags/...
ParserException: /var/cache/debtags/people.debian.org_%7eenrico_tags_vocabulary.gz:1: invalid character `<' expecting `:'.  Ignoring source http://people.debian.org/~enrico/tags/
debtags: ConsistencyCheckException: Unable to use any data source (not even previously cached ones)

dpkg: error processing debtags (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of adept:
 adept depends on debtags; however:
  Package debtags is not configured yet.
dpkg: error processing adept (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on adept; however:
  Package adept is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 debtags
 adept
 kubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried to remove and purge each of the files and reinstall them.  I have tried dpkg --configure each of them and I have had no success.  I have posted on Kubuntu forums, but all I get is "do apt-get remove, then apt-get install".  I'd be a happy man if someone could help me remedy this issue.

---

### Post by sciurus on 2005-12-31
What is in your sources.list? When did this error first occur?

I would manually remove debtags from my system, temporarily remove any third party repositories from my sources, then do an apt-get update and apt-get dist-upgrade.

---

### Post by sciurus on 2005-12-31
The trouble is that during its installation, debtags tries to load the tags from the internet but they're corrupted. Thus its install fails and packages which depend on it report errors.

I would manually remove debtags from my system then do an apt-get update and apt-get dist-upgrade.

---

### Post by chubsmalone on 2005-12-31
By manually remove, I assume you mean:
 
dpkg --remove debtags

I did that.  Then I did apt-get update apt-get dist-upgrade.  

Debtags is not one of the upgraded packages.  I then did apt-get install kubuntu-desktop...it depends on adept...which depends on debtags.  So, for now, I am going to remove debtags, adept and kubuntu-desktop from my system.  

As far as my sources.list, I am using a mirror (ftp://mirror.mcs.anl.gov) for everything and I commented out any other third party stuff.  I did notice, however, that the tags it is verifying come from this source:
http://people.debian.org/~enrico/tags/

Is there any way to get that source somewhere else?  Is this a common problem?

---

### Post by chubsmalone on 2006-01-04
I'm replying to this to bring it up again...I still haven't found a solution to this one.

---

### Post by ztripez on 2007-07-02
bump. i have the same problem.

---


---
title: "firefox 1.5 in .deb"
date: 2006-03-09
forum: Desktop Environments
---

### Post by fly-away on 2006-03-09
On [http://archive.ubuntu.com/.../firefox/]("http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/") 
present package firefox_1.5.dfsg+1.5.0.1-1ubuntu5_i386.deb (24-Feb-2006 18:04  7.5M) and even firefox_1.5.dfsg+1.5.0.1-1ubuntu5_amd64.deb, look very good :))
But i cant catch it in my cache by apt-get update... :( 
So, what is it and how i can use it?
(I'm read [FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion"), its not unix-way i think :\)

---

### Post by cilynx on 2006-03-09
Do you have firefox installed at all?

If not, you can:
Applications->Add/Remove...
to install it.  It's under 'networking'.  You could also use synaptic or 
```

sudo apt-get install firefox

```
if you swing that way.  If you're looking to just update a working version to the bleeding edge version, do you really have a reason to update?  Most likely, the packages you found are for the unstable resease and that's why it's not showing you that version in your list.  I'm running Dapper and have FF 1.5.0.1.

If you really want to upgrade to Dapper (not for the newbie or faint of heart), I'm sure there's an official page, but I can't find it.  One guy wrote it up pretty well here:
[http://www.macewan.org/2006/02/23/upgrading-breezy-to-dapper/](http://www.macewan.org/2006/02/23/upgrading-breezy-to-dapper/)

---

### Post by twigboy on 2006-03-10
Uninstall the old version of FF through synaptic or sudo apt-get remove firefox
then use 
dpkg -i firefox_1.5.dfsg+1.5.0.1-1ubuntu5_i386.deb
to install the file.  That will install it but its not guaranteed to work.  The deb file wasnt around when I installed 1.5.0.1

---


---
title: "Openoffice 2.0 download issues"
date: 2006-01-02
forum: Desktop Environments
---

### Post by ShirishAg75 on 2006-01-02
Hi all,
      Please first refer to       [http://www.ubuntuforums.org/showthread.php?t=110391]("http://www.ubuntuforums.org/showthread.php?t=110391") . As u can see I've been suggested to use this :-

```
 deb [http://people.ubuntu.com/~doko/OOo2]("http://people.ubuntu.com/%7Edoko/OOo2") ./
``` I entered the required entry in /etc/apt/sources.list & 'm getting this output whenever I'm running apt-get update.
  ```

Get:1 [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security Release.gpg [189B]
 Ign [http://people.ubuntu.com]("http://people.ubuntu.com/") ./ Release.gpg
Get:3 [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security Release
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy Release
 Ign [http://people.ubuntu.com]("http://people.ubuntu.com/") ./ Release
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy-updates Release
Ign [http://people.ubuntu.com]("http://people.ubuntu.com/") ./ Packages
Hit [http://people.ubuntu.com]("http://people.ubuntu.com/") ./ Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security/main Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy/main Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security/restricted Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security/main Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy/restricted Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") breezy-security/universe Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy/restricted Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy/universe Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy/multiverse Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy/universe Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy/multiverse Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy-updates/main Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy-updates/restricted Packages
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy-updates/main Sources
Hit [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") breezy-updates/restricted Sources
Fetched 3B in 4s (1B/s)
Reading package lists... Done
```


             Let me make this clear that I haven't tried getting the openoffice 2.o deb as of now. I have two questions :-

Q1. The IGN instead of Hit, is this normal?
             I'm able to look at the site through the browser & also see the 
Packages.gz then why does it Ignore? Also read through ```
https://wiki.ubuntu.com/AddingRepositoriesHowto 
``` especially the Repositery line where it mentions about a similar link.

Q2. Now, in case if the Ignore is normal or something then what command should I give so that it knows that I want the newer Openoffice 2.0 final & not anything to do with Openoffice 1.9. 
                 Please keep in mind that it's just going to be added to a custom repositery. Thanx in advance.

---

### Post by TimelessRogue on 2006-01-02
As I recommended with installing Firefox 1.5, give Arnieboy's Automatix program a shot ... it will also install OpenOffice 2.0 for you ... the easy way.

We keep asking for help with easy installation of many programs and Automatix has made that oh so possible for us ... much thanks to Arnieboy for that!

So why not give it a try?

Check it out at:  [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by ShirishAg75 on 2006-01-03
I don't want to use Automatix as I want to add it for a custom install CD (something like CD2) so that in case I re-format the system I don't have to re-download Openoffice 2.0 final again & again.

---


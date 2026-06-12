---
title: "Is there a guide to install Cedega?"
date: 2005-04-06
forum: Gaming &amp; Leisure
---

### Post by NateC on 2005-04-06
The title says it all  ;-)

---

### Post by jdodson on 2005-04-06
[QUOTE=NateC]The title says it all  ;-)[/QUOTE]

so you mean the cvs version.  and to that i say, yes.  

and my follow up is, "forum search." :grin: 

however if you mean to install from .deb or .rpm, then my answer is yes.

and my follow up is, "forum search." :grin:

---

### Post by leech on 2005-04-06
Well, if you're referring to the .deb, then it's as simple as installing libpng3 and then 'sudo dpkg -i cedega<version>' and you'll be good to go.

I've never installed from CVS though.  Think I tried it once, and it didn't build.

Leech

---

### Post by bored2k on 2005-04-06
Cedega CVS (beware, not for the faint of heart): [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

---

### Post by Sniffer on 2005-04-06
if you have the deb package just

dpkg -i cedega

and then to install games just a cedega setup.exe for instance

---

### Post by NateC on 2005-04-06
I am talking about the tgz version. And the commands to do after I installed it.

---

### Post by bored2k on 2005-04-06
[QUOTE=NateC]I am talking about the tgz version. And the commands to do after I installed it.[/QUOTE]
 A tgz could be anything. Extract it [tar xzf file.tgz or through file roller] and tell us if its an .rpm, a .deb, or a bunch of files.

---

### Post by NateC on 2005-04-07
It is the files. TGZ.

---

### Post by digby on 2005-04-07
The easiest way to install a tgz pagacke is to convert it to deb first.
```
 #alien -d cedega_package_filename.tgz
#dpkg -i cedega_package_filename.deb
```

---

### Post by NateC on 2005-04-08
Nevermind, after an hour of searching I found it.


[http://downloads.transgaming.com/files/Cedega_howto_4.3-1.1.1.1.txt](http://downloads.transgaming.com/files/Cedega_howto_4.3-1.1.1.1.txt)

---

### Post by CowPie on 2005-04-08
Very nice, thx

---

### Post by psychicdragon on 2005-04-09
I found this with google:

[http://homepages.nildram.co.uk/~fcarson/3s6sVtXmxJblp7FYDjEZHdpFDDPY6m/pC7i3Pq1dikAmk/0bc1eff9e4d4489d54817ccfdbd79e49/TransGaming_downloads.html](http://homepages.nildram.co.uk/~fcarson/3s6sVtXmxJblp7FYDjEZHdpFDDPY6m/pC7i3Pq1dikAmk/0bc1eff9e4d4489d54817ccfdbd79e49/TransGaming_downloads.html)

has anyone tried these packages? Are these legal? it kinda looks like they may have been snatched off of transgaming's website.

---

### Post by ninjag5 on 2005-04-11
im on an iBook running the newest version of ubuntu i havnt used linux b4 so i thought id give it a go i bought a subcription to Transgamer bcoz it says they have a mac version THEY DONT  :---) anyways i want to use it on linux but i cant.. it wont let me install it ive gone thru all the right steps and still it wont install it then i try renaming the .deb pack to just cedega.deb and it trys to install but cant bcoz it says its for i386 and not PowerPc ..GRR

---

### Post by NetCutter on 2006-04-27
Can Some body,upload the tgz or deb fail somewhere,and  give me the link,because I cannot install the CVS:-k

---

### Post by NetCutter on 2006-05-01
Yo!Guyes why you don't help me:(

---


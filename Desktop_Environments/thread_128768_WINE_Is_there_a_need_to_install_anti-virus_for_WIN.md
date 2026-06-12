---
title: "WINE: Is there a need to install anti-virus for WINE?"
date: 2006-02-12
forum: Desktop Environments
---

### Post by kenweill on 2006-02-12
Well, do i need an anti-virus installed for WINE?
How about anti-spyware?

---

### Post by public_void on 2006-02-12
You don't really need any anti-malware software. Virus for Linux are rare, and spyware even less, TBH I haven't heard of any spyware for Linux, though I could be wrong. I think most people agree that if your file sharing with Windows users then its best to get AV. Its not to protect yourself, but to stop you passing something on to a Windows user.

---

### Post by ardchoille on 2006-02-12
Yes, a wine environment is just as susceptible to viruses/worm/trojans as a Windows environmemnt is:

[http://blogs.zdnet.com/Ou/index.php?p=146](http://blogs.zdnet.com/Ou/index.php?p=146)

---

### Post by dcstar on 2006-02-13
[QUOTE=ardchoille]Yes, a wine environment is just as susceptible to viruses/worm/trojans as a Windows environment is:

[http://blogs.zdnet.com/Ou/index.php?p=146](http://blogs.zdnet.com/Ou/index.php?p=146)[/QUOTE]
Wine runs under the privileges of the Linux user, and I seriously doubt that any of these things will be able to access the root environment in the same way as a native Windows machine.

The user's wine Windows environment may be affected, but since it is hard enough to get real applications to run under wine, I'd say a lot of these unwanted things wouldn't run anyway!

Unless you are silly enough to constantly use IE under wine, or Outlook Express etc, then your areas of vulnerability are greatly reduced.

---

### Post by ardchoille42 on 2007-03-22
> **dcstar said:**
> Wine runs under the privileges of the Linux user, and I seriously doubt that any of these things will be able to access the root environment in the same way as a native Windows machine.

The user's wine Windows environment may be affected, but since it is hard enough to get real applications to run under wine, I'd say a lot of these unwanted things wouldn't run anyway!

Unless you are silly enough to constantly use IE under wine, or Outlook Express etc, then your areas of vulnerability are greatly reduced.

More than just the wine environment can be affected. See the 8th post in the second thread below:

[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

[http://www.ubuntuforums.org/showthread.php?t=72598](http://www.ubuntuforums.org/showthread.php?t=72598)

Wine will run Windows viruses/trojans/worms and some can affect your Linux files. I consider the files in $HOME more important than the rest of the system.

---

### Post by DouglasAWh on 2008-01-22
so, what anti-virus will work?  I tried Symantec Corporate and AVG Free, and neither installs.  Paying for one is not an option (I get SAV from school).

---

### Post by AsoSako on 2008-01-22
There are ways to install AVG, but I don't think you would really need it unless you like to play around with stuff that could have viruses.  The chance of you getting one that would damage your system is quite low otherwise...  I barely ever needed my antivirus when I used WIndows for example...

---

### Post by steve_waters on 2008-01-23
ClamAV is all good for Linux, it should be in the Add/Remove Applications.

---

### Post by DouglasAWh on 2008-01-23
I installed ClamAV, but does it take care of WINE too?  I also can't figure out how to update my definitions or the program.

---

### Post by stooshbunutu on 2008-02-19
There is a very reliable and free virus scan that now has a .deb all inclusive file for download. AVG anti-virus. it can be useful for scanning files even though the threats are low

[click here]("http://free.grisoft.com/filedir/inst/avg75fld-r51-a1243.i386.deb") to download

Hope this helps:)

---


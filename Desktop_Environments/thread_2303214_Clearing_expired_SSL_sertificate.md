---
title: "Clearing expired SSL sertificate"
date: 2015-11-17
forum: Desktop Environments
---

### Post by BarryD9545 on 2015-11-17
Seems like the right place...

(I'm extrapolating from Windows, so my apologies in advance)

I'm attempting to install an application (BovadaPoker.exe) via Wine, but it locks up while trying to obtain it's updates.  This happens before the application starts, so there's no opportunity to tell it to get the updates later.

In Windows (I know...) the solution was to go into certmgr.msc search out and delete the expired (in 2014) GlobalSign entry.
Here's the [page]("http://www.bovadapoker.com/articles/operating-system-certificate-updates") of instruction.

Seems to me that the solution would likely be the same, but I can't locate anything like a certificate manager in Ubuntu 15.10.

As an additional note, BovadaPoker.exe installed and ran without major issue until the certificate expired...of course.

---

### Post by BarryD9545 on 2015-11-20
Just a bump to see if anyone has seen this....

---

### Post by Habitual on 2015-11-20
> **BarryD9545 said:**
> Seems like the right place...

(I'm extrapolating from Windows, so my apologies in advance)

I'm attempting to install an application (BovadaPoker.exe) via Wine, but it locks up while trying to obtain it's updates.  This happens before the application starts, so there's no opportunity to tell it to get the updates later.

In Windows (I know...) the solution was to go into certmgr.msc search out and delete the expired (in 2014) GlobalSign entry.
Here's the [page]("http://www.bovadapoker.com/articles/operating-system-certificate-updates") of instruction.

Seems to me that the solution would likely be the same, but I can't locate anything like a certificate manager in Ubuntu 15.10.

As an additional note, BovadaPoker.exe installed and ran without major issue until the certificate expired...of course.
The certificate you are looking for is for Windows, so it would be under .wine/
I found Certificates in .wine/system.reg
```
grep Certificate  .wine/system.reg
```
but they aren't named.

Even if Ubuntu had a certificate manager and you deleted the GlobalSign Certificate, I believe that would be a mistake to remove it.
Found this for Internet Explorer using wine. Removal is possible, but re-adding doesn't seem to be easy.
[ATTACH=CONFIG]265696[/ATTACH]

I also noticed the dates on the certs they said to delete are rather dated, so I'm inclined to believe that removing the GlobalSign Cert at this time won't work.
```
7. Scroll down to where the expiration date says either &#8220;**[COLOR=#ff0000]1/28/2014[/COLOR]**&#8221; or &#8220;**[COLOR=#ff0000]28/1/2014[/COLOR]**&#8221;
```
These exist as referenced in a full-blown Windows XP/SP3 installation but not in wine.

I'm not certain this will be successful for you in wine.

---


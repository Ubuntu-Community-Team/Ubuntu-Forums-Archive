---
title: "Repositories fail in Dell Ubuntu 8.04 lpia (Mini 9)"
date: 2009-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kalma on 2009-12-22
Hi there,

for some months I can not donwload the Ubuntu updates on my Dell Mini 9, since it is not able to find the repositories (Ubuntu 8.04 hardy, lpia repos). Have they disappeared or changed? Can I connect to a different place or should I install another version?

Thanx in advance.

---

### Post by MelDJ on 2009-12-22
can you post the output of sudo apt-get update?

---

### Post by Kalma on 2009-12-22
Sure,

These are the original repositories since I have not made any change. One day, unexpectedly, they stopped working. Sorry, it is in Spanish.

"Imposible obtener" means (aprox.) "Not able to reach"
"No pude resolver" means (aprox.) "Could not resolve"

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/Release.gpg)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/Release.gpg)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/universe/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/universe/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/Release.gpg)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/main/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/main/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/universe/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/universe/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/multiverse/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/multiverse/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/restricted/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-base/restricted/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/Release.gpg](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/Release.gpg)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/multiverse/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/multiverse/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  No pude resolver 'archive.ubuntu.com'

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2)  No pude resolver 'archive.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://security.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2](http://security.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2)  No pude resolver 'security.ubuntu.com'

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  No pude resolver 'archive.ubuntu.com'

W: Imposible obtener [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2)  No pude resolver 'archive.ubuntu.com'

W: Imposible obtener [http://apt.wicd.net/dists/hardy/Release.gpg](http://apt.wicd.net/dists/hardy/Release.gpg)  No pude resolver 'apt.wicd.net'

W: Imposible obtener [http://apt.wicd.net/dists/hardy/extras/i18n/Translation-es.bz2](http://apt.wicd.net/dists/hardy/extras/i18n/Translation-es.bz2)  No pude resolver 'apt.wicd.net'

W: Imposible obtener [http://dell-mini.archive.canonical.com/updates/dists/hardy-dell-mini/Release.gpg](http://dell-mini.archive.canonical.com/updates/dists/hardy-dell-mini/Release.gpg)  No pude resolver 'dell-mini.archive.canonical.com'

W: Imposible obtener [http://dell-mini.archive.canonical.com/updates/dists/hardy-dell-mini/public/i18n/Translation-es.bz2](http://dell-mini.archive.canonical.com/updates/dists/hardy-dell-mini/public/i18n/Translation-es.bz2)  No pude resolver 'dell-mini.archive.canonical.com'

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

---

### Post by MelDJ on 2009-12-23
try changing your software server in system-admin- software sources

---

### Post by Kalma on 2009-12-24
Ok, in such a case, which server do you think I should use instead of these ones?

---

### Post by Zoot7 on 2009-12-24
AFAIK there's a little test you can do to determine the optimium server when it comes to updates. Give that a shot.

---

### Post by MelDJ on 2009-12-25
use the select best server option

---

### Post by ugm6hr on 2009-12-25
> **MelDJ said:**
> use the select best server option

This does not work for lpia versions.

lpia repositories are very limited.  I will try and find the Canonical one; but I think it may be the same as the Dell one.

I'm assuming your internet connection is otherwise working OK.

EDIT:
It appears to still be there: [http://dell-mini.archive.canonical.com/](http://dell-mini.archive.canonical.com/)

Maybe show us your sources file:
```
nano /etc/apt/sources.list
```

---

### Post by Kalma on 2009-12-27
Thank you all for the replies.

Yes, they seem to be still there, but there is something in the middle of the URL which seems to be the part which makes it unavailable now. I believe it was "lpia", but not completely sure... It is my daughter's PC, but She's on holidays, so I will come back in a few days to give you a shot of the complete url's inside the sources.lst file.

Merry Xmas!!!

---

### Post by ugm6hr on 2009-12-27
Here's a link to a copy of the original if it has been edited by accident:
[http://www.mydellmini.com/forum/ubuntu-netbook-remix/122-sources-list.html#post1800](http://www.mydellmini.com/forum/ubuntu-netbook-remix/122-sources-list.html#post1800)

---

### Post by Kalma on 2009-12-29
OK. I see.

My repositories are not Netbook Remix, but lpia ones... I guess lpia repos for 8.04 version are no longer supported. Should I use Netbook Remix instead?

Anyway, I will give it a try and will tell you how it was.

Thanx a lot.

---

### Post by ugm6hr on 2009-12-29
> **Kalma said:**
> My repositories are not Netbook Remix, but lpia ones... I guess lpia repos for 8.04 version are no longer supported. Should I use Netbook Remix instead?

Either I'm confused or you are.

I've just noticed the title of this thread - where does Jaunty come into it?

Also, are you still using the Dell original OS, or have you reinstalled?

If the latter, what did you install, and where from?

---

### Post by Kalma on 2009-12-30
Sorry, my fault.

It is Ubuntu 8.04 - Hardy actually, but I made a mistake with the codename. When I realized, I changed the body of my message, but I couldn't change the title. It is the original SO which came with the PC, and I have not installed anything new on it, but just aMSN.

Sorry again, and HAPPY NEW YEAR!!!!

---

### Post by ugm6hr on 2009-12-30
In which case you don't appear to understand the lpia / netbook remix issues:

1. Dell 8.04 for Mini 9 was a mildly modified 8.04 lpia with Netbook Remix.

2. There is no such thing as a "Netbook Remix" repo - Netbook Remix shares repos with the standard Ubuntu.

3. The Dell Ubuntu (Mini 9) repo is almost the same as the standard lpia repo, and is hosted in the same location.

4. As far as I can tell lpia is still supported for 8.04.

Hence, if you replace your /etc/sources.list file with the default one I linked to earlier, I think you will find everything back to normal.  As for how / why it changed, only you will know the answer to that.

PS: I changed the title for you.

---

### Post by Kalma on 2010-01-14
You're asbsolutely right... IN BOTH THINGS!!!

I mean, I didn't know the details of the update you ar mentioning. Thank you for your explanation.

Besides this, the sources.list you recommended is now working... THANK YOU again.

I have discovered something; the sources I had were exactly the same BUT I manually added one source for Wicd module. This was the repository which was failing. Then, in case there is an error, the process doesn't continue (not like in standard Ubuntu). I have eliminated this entry and it seems to be working fine.

Thank you again for your help. I will mark the message as SOLVED.

---


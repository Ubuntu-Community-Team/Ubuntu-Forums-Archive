---
title: "Why Ubuntu does not have sun's java on its non-free repositories?"
date: 2005-11-28
forum: Desktop Environments
---

### Post by lasterra on 2005-11-28
I'm an ubuntu users during last year. I now that java is a non-free software but other linux distribution has java packages on its repositories (redhat, suse, mandrake?). A lot of ubuntu users think that java instalation in ubuntu is quite dificult. 

My question is why Sun's Java is not on Ubuntu repositories and Ubunu has any plans to add this packages to its repositories.

Regards.

---

### Post by az on 2005-11-28
Sun's java has a licencing issue that says that if you distribute their version, you are prohibited from distributing any other kind of java environment.

That would prevent Ubuntu from distributing the free java alternatives (GCJ, Sablevm, Kaffe) that will soon replace proprietary java.

So, non-free licences are usualy evil.


But, Installing Java from Sun is not that hard.  Look here:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Brent Dax on 2005-11-28
[QUOTE=lasterra]I'm an ubuntu users during last year. I now that java is a non-free software but other linux distribution has java packages on its repositories (redhat, suse, mandrake?). A lot of ubuntu users think that java instalation in ubuntu is quite dificult.[/QUOTE]
Ubuntu takes a fairly hardline position on which packages are included--they have to be free software to make "universe" and unambiguously legal to make "multiverse".  Since the Java SDK comes with a license saying that it can't be redistributed, Ubuntu can't place a package in "multiverse".  If you don't like this situation--and I certainly don't--I suggest you write Sun and tell them thaat their license terms are preventing users from easily installing Java technology on Ubuntu systems.

---

### Post by nix4me on 2005-11-28
I have emailed Sun about this several months ago.  I never got a reply but I think everyone here should do the same.

nix4me

---

### Post by az on 2005-11-28
I emailed them in 2002.

Really.


Same response as you.

---


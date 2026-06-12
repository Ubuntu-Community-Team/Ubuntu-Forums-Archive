---
title: "Evolution mail with exchange 2007"
date: 2009-06-04
forum: General Help
---

### Post by inphektion on 2009-06-04
I'd love to be able to not use Outlook in a vm anymore. But checking the corp mail through an OWA setup or IMAP doesn't suit my needs.  
I've read a bit about open Mapi and read it should be in evolution but when I go to configure my evolution for my corp mail it asks for the owa url.  Is there an open mapi plugin stable and useable for evolution yet?
Msft has EWS now too (Exchange web services) which you can use in beta form in Entourage.  Anyone know if thunderbird or evolution will leverage that as its a real API for checking mail as opposed to the OWA cludge.

---

### Post by inphektion on 2009-06-04
ok outlook in vm still it is...  I'll search/check again in 6 months....

---

### Post by glauco.b on 2009-06-07
Evolution has an evolution-mapi plugin based on the libmapi library which is suppesed to work with Exchange 2003 and 2007 natively.

I tried it several times, with many updates and versions of both libmapi and evolution versions, connecting to a regular Exchange 2007 server over an open LAN (no firewalls and other filters)

The result is always the same: SEGMENTATION FAULT of the full evolution application at the login phase ](*,)](*,)](*,)

I tried asking on several forums out there. No way. it does not work.

Other things I tried:
- Installing outlook with Bordeaux or Crossover office (wine): VERY unstable
- Trying to find a COMMERCIAL ActiveSync client for Linux: does not exist (may be a business niche, huh? :p )
- Installing IE6 with Wine and using OWA with the full version (ok, that kind of worked, but very after some hard geeking... Shame to Microsoft for having used that damn VBscript language!!!)


You developer out there! Why did you develop an ActiveSync client for Android (a Linux/ARM system!) and the same client is not available for the full linux/i86 OS? We do not demand for an Open Source client, I mean just a client...

---

### Post by pookiebear on 2009-06-10
this should be the next big project

---


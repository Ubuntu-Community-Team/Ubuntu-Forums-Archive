---
title: "Printing problem (gs segfault)"
date: 2006-01-20
forum: Desktop Environments
---

### Post by pwaldo on 2006-01-20
HI all,
 
I posted this originally on the Kubuntu AMD64 forum and got no response so I'll try my luck here :-)

I've been trying to figure out a printing problem for a while now, with no luck.
 
 I'm running Kubuntu 5.10 Breezy **AMD64** and I'm trying to configure an HP LaserJet 5L. I can print a test page OK, and I can print text (such as an email) OK, but when I try to print anything else (like this page), I get nothing. I think that ghostscript is dying; if I print and ask for a preview, I get a dialog saying 
 
 An error occurred in rendering.
 Process killed or crashed.
 The display may contain errors.
 Below are any error messages which were received
 from Ghostscript (gs) which may help you.
 
 Of course there are no errors  
 
 /var/log/kern.log says this about the matter:
 Jan 16 21:53:18 localhost kernel: [103498.865531] gs[1679]: segfault at 0000000000000008 rip 00000000005f3930 rsp 00007fffffeea9a8 error 4
 
 I saw a similar post on this forum which gave a solution (downgrading a bunch of ghostscript-related packages), but the replacement packages were all i386. Anyone have any ideas on how to get gs into shape?
 
 Any help would be greatly appreciated!
 
 Paul

---


---
title: "CD/DVD Burner Problem"
date: 2009-04-09
forum: General Help
---

### Post by parkbench71 on 2009-04-09
Hi - newly registered - been happily using Ubuntu for 2 years now and this is the first time I've needed help.

For several weeks now, I cannot burn any DVDs or CDs regardless of which application I have used (Brasero, GnomeBaker, Nero for Linux being the main ones). The application _always_ erroneously reports the media as being full. This is the same for brand-new CDRs, DVDRs, CDRWs & DVDRWs. I have tried with 3 different burners, 2 internal and one external and always the same problem. 

I'm running 8.04.2 - all latest security and recommended patches applied.

Any suggestions appreciated!

---

### Post by speedwell68 on 2009-04-09
I had a similar problem, but solely with Brasero.  All I did was upgrade to the latest version of Brasero, which I downloaded from GetDeb.  Here...

[http://www.getdeb.net/search.php?keywords=brasero](http://www.getdeb.net/search.php?keywords=brasero)

Version 0.9.1 worked for me.  I'd uninstall the earlier version first though.

---

### Post by parkbench71 on 2009-04-14
Just to update this thread for the sake of anyone else who inadvertently manages to replicate this issue.

Having tried every burning application I could find with no success, I found that reinstalling the libnautilus-burn4 and nautilus-cd-burner packages in Synaptic completely cured this problem. :)

---


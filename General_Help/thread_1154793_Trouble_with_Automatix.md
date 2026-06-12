---
title: "Trouble with Automatix"
date: 2009-05-10
forum: General Help
---

### Post by m_hayday on 2009-05-10
When I first got Ubuntu, I, for some reason got Automatix and it seems to have mucked up my system. When I went to install wine from software sources, it couldnt reload because it couldnt find some automatix files or something.

Is there a way of just removing it completely??? :)

(Ubuntu n00b)

Thanks in advance!

---

### Post by mb_webguy on 2009-05-10
Yeeeaaahhh...  Yours isn't the first system to be hosed by Automatix.  Since it's no longer actively developed (and never really worked well on Ubuntu to begin with), I'm not sure there's a sure-fire fix.

The first thing to do would be to try to use Automatix to remove everything you've installed with it.  Don't worry, you don't need Automatix to get those things -- that's why we have Medibuntu.  Second, you need to get rid of Automatix.  Hopefully, you installed it using a deb package.  If so, open System > Administration > Synaptic Package Manager, find the automatix package, mark it for complete removal, and click Apply.

Hopefully, this will fix things, but I can't guarantee anything...

---

### Post by m_hayday on 2009-05-10
I don't think I did! Because it doesn't come up with anything in the package manager.  Any other suggestions?

---

### Post by Yellow Pasque on 2009-05-10
What does your /etc/apt/sources.list file contain?

---


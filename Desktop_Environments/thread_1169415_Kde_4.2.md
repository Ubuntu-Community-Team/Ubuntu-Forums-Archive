---
title: "Kde 4.2"
date: 2009-05-25
forum: Desktop Environments
---

### Post by patanjali on 2009-05-25
Is it possible, or wise, to run KDE 4.2 with Kubuntu Hardy?

TIA

p:mrgreen:

---

### Post by krazyd on 2009-05-25
Possible, yes. Wise, no. You will have to compile everything yourself - there are no PPAs I know of for this.

You could also try this, but it looks very dodgy to me. Don't expect full functionality or even for it to work at all.
[http://regenduft.de/article.pl?title=KDE_4.2_for_K-Ubuntu_Hardy_8.04](http://regenduft.de/article.pl?title=KDE_4.2_for_K-Ubuntu_Hardy_8.04)

---

### Post by patanjali on 2009-05-25
> **krazyd said:**
> Possible, yes. Wise, no. You will have to compile everything yourself - there are no PPAs I know of for this.

You could also try this, but it looks very dodgy to me. Don't expect full functionality or even for it to work at all.
[http://regenduft.de/article.pl?title=KDE_4.2_for_K-Ubuntu_Hardy_8.04](http://regenduft.de/article.pl?title=KDE_4.2_for_K-Ubuntu_Hardy_8.04)
krazyd, thanks for that.  You confirm what I think.

p

:popcorn:

---

### Post by cmost on 2009-05-25
It's possible to install KDE 4.2 on Kubunty Hardy, and many people have done so successfully.  Here's a nice tutorial (note, it's for 8.10 but may work on 8.04 as well.)

[http://news.softpedia.com/news/How-to-Install-KDE-4-2-on-Ubuntu-8-10-106118.shtml](http://news.softpedia.com/news/How-to-Install-KDE-4-2-on-Ubuntu-8-10-106118.shtml)

---

### Post by krazyd on 2009-05-26
that won't work for hardy, it's for intrepid

---

### Post by cmost on 2009-05-26
> **krazyd said:**
> that won't work for hardy, it's for intrepid

Yes, I did mention that.  But, I thought it might be worth a shot for you to try the procedure anyway.  You're going to have a hard time finding any info on performing such a major upgrade to Hardy.  Since Hardy is the LTS release, its packages are fairly set in stone (save for the scant few security and bug fix updates that filter in.)  If you want the latest KDE, then you're going to have to bite the bullet and upgrade your OS to Jaunty.  As an alternative, you might check out Linux Mint KDE Community Edition.  It's based on Ibex, but has a lot of extra tweaking and TLC from the Mint community.  Much improved over the stock Ibex Kubuntu.  Here's more information:  [http://www.linuxmint.com/blog/?p=731](http://www.linuxmint.com/blog/?p=731)

---

### Post by krazyd on 2009-05-27
> **cmost said:**
> Yes, I did mention that.  But, I thought it might be worth a shot for you to try the procedure anyway.  No, it won't work.

---

### Post by cmost on 2009-05-27
Have you tried compiling KDE 4.2.2 directly from source?  That's really your only option at this point if you're bent on sticking with Hardy.  This couldn't be that difficult considering the KDE team has some decent guides out there.  Or, you could try using a repository intended for Debian Stable (lenny) which is about the same vintage is Hardy (try Mepis's repo or search for Debian KDE 4.2 repos with Google.)  This could potentially bork your system but it might be worth a shot.

---


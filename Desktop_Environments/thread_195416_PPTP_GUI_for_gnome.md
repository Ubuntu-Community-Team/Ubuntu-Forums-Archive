---
title: "PPTP GUI for gnome"
date: 2006-06-12
forum: Desktop Environments
---

### Post by shredswithpiks on 2006-06-12
Is there a fun and easy package I can install to get some GUI VPN connections happening in 6.06?

I've got the PPTP-linux client installed, but need (would like) a GUI for it.

---

### Post by setenza on 2006-06-12
Hi,

Look at this tutorial for pptpconfig

[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

at : Installing the Configuration Program

I use this on my Dapper 6.06 and works fine :)

Bye

---

### Post by knud on 2006-07-03
I still get error messages discussed in other threads like

The following packages have unmet dependencies:
pptpconfig: Depends: php-gtk-pcntl (>= 1.0.0) but it is not going to be installed
E: Broken packages

how did you manage the installation for 6.06? for 5.10 it works fine

---

### Post by ohgod on 2006-07-03
if you add this to your sources.list file, apt-get will resolve the dependencies for you:  

# James Cameron's PPTP GUI packaging
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./

[QUOTE=knud]I still get error messages discussed in other threads like

The following packages have unmet dependencies:
pptpconfig: Depends: php-gtk-pcntl (>= 1.0.0) but it is not going to be installed
E: Broken packages

how did you manage the installation for 6.06? for 5.10 it works fine[/QUOTE]

---

### Post by knud on 2006-07-03
hi,

of course, the mentioned error message comes up *after* adding those lines to sources.list and entering 'apt-get update'. still ???

[QUOTE=ohgod]
# James Cameron's PPTP GUI packaging
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./[/QUOTE]

---

### Post by Geoff2077 on 2006-07-24
Hi
I hit the same wall too with both 5.10 and 6.06.
How does one get around these dependencies??

Geoff

---

### Post by Geoff2077 on 2006-07-29
its a pity that some of the people offering gratuitous advice, dont try out the things they advise. I had done a stock standard installation of unbuntu 6.06.

After struggling with the same issue of unmet dependencies for a week, I found a reference:

you need to enable the Universe depository (bin) as well (synaptic package manager) as well as adding the entry to the sources.list. then follow the instructions for install. 

hope this assists - it is definitely working now on my installation

Cheers
geoff

---

### Post by snarkhunter on 2006-07-29
Ok, so I'm on an older PowerBook G4.
And the support modules don't seem to be working for a PPC architecture.  Is there any fix for this?
And why is php necessary at all?  Isn't that for the web, not desktop apps?

---

### Post by knud on 2006-08-02
hi Geoff2077,

thats it, i found out yesterday, too. if i would read daily here, i would have saved 3 days ;)

---

### Post by ohgod on 2006-08-02
> **snarkhunter said:**
> Ok, so I'm on an older PowerBook G4.
And the support modules don't seem to be working for a PPC architecture.  Is there any fix for this?
And why is php necessary at all?  Isn't that for the web, not desktop apps?

pptp config was written in php for some strange reason...

---


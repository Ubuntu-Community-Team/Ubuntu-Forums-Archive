---
title: "Sage"
date: 2008-01-14
forum: Education &amp; Science
---

### Post by artesian_spring on 2008-01-14
I've seen [SAGE]("http://www.sagemath.org/") recommended on this forum as a good math package, so I downloaded it. I didn't install it, though, since I already have many of the packages it includes (Maxima, Octave, R, and others). Is there a way to just install the SAGE environment and then direct it to the programs I already have, or would I need to uninstall them and then install SAGE? 

Thanks.

---

### Post by jonas_e on 2008-01-16
Is there a reason why Sage is neither in Applications->Add/Remove... nor in Synaptic? Is it not "popular" enough?

---

### Post by AlanRogers on 2008-01-16
Isn't it a little dangerous naming a Linux program, especially one that's a numeric utility, a little short-sighted when one of the best known accounting packages carries the same name?
 
Rhetorical question really. It just struck me as courting disaster.

---

### Post by Spike the Dingo on 2008-12-03
Nope, you can install sage from their website. It has not (yet) been packaged for Ubuntu, and this is why it is not in the repository.

See for an update:
[http://wiki.sagemath.org/DebianSAGE](http://wiki.sagemath.org/DebianSAGE)

I'm looking forward to seeing it in the repository!

---

### Post by msrk on 2009-03-24
I very much want to install Sage on my Ubuntu 8.10 Interped system.  I'd like to use Synaptic to manage the installation.  Is anyone working on an Ubuntu package?

Thank you,
Marc

---

### Post by rolandrock on 2009-03-24
@AlanRogers,

SAGE (the accounting package) is mainly marketed at local government (at leat it used to be) and is based in Newcastle (NE England).  The people who write SAGE the maths package have probably never heard of SAGE the acounting package.

I only reply to your rhetorical question because it caused me confusion in the past.  And I have a friend who is senior programme manager at Sage in Newcastle.  And I used to work for Oracle where Sage would occasionally be bidding for contracts against us.  And I am an amateur mathemetician.  And I like sage and onion stuffing,

Rock

---

### Post by zasdfgbnm on 2009-05-10
sudo apt-get install sagemath

---

### Post by nflamel on 2009-06-12
> **zasdfgbnm said:**
> sudo apt-get install sagemath

Thanks a lot, I was looking for the package name for this, but couldn't find it anywhere.

---

### Post by gra2uitous on 2009-07-12
Is anyone having trouble with the display of Jmol 3D graphs?

When I run the Sage Tutorial (localhost server) as a notebook, Section 2.5.2 Three-Dimensional Plots, will not evaluate any of the examples on the page. Instead the following message appears:

"ReferenceError: jmolSetDocument is not defined".

Examples on the Jmol Website work OK(e.g. [http://jmol.sourceforge.net/demo/jssample0/](http://jmol.sourceforge.net/demo/jssample0/)), ruling out Firefox I think. After a bit of Google research I suspect that Jmol.js and some other clever java files (*.jar) are missing from my computer.

The following reference was the only relevant info found:

[http://groups.google.com/group/sage-forum/browse_thread/thread/04681880d624b22d/dae1c4fd9a5d30c4](http://groups.google.com/group/sage-forum/browse_thread/thread/04681880d624b22d/dae1c4fd9a5d30c4)

Suggesting that the installed version of SAGE is too old (3.0.5). Anyone else with the same problem or am I doing something really dumb?

The solution suggested above: "sage -upgrade" didn't want to work, so I'm now thinking about building from source. :(


Firefox Browser: 3.11 
Ubuntu: 9.04
Sage installed with Synaptic Version: 3.0.5dfsg-4

Thanks, any help appreciated.
[B][SIZE=+1]
[/SIZE][/B]

---

### Post by ahmatti on 2009-07-20
> **gra2uitous said:**
> 
The solution suggested above: "sage -upgrade" didn't want to work, so I'm now thinking about building from source. :(


Actually there is precompiled binary (not a deb, but still its already compiled) of sage available from their website. Go here: [http://ftp.sh.cvut.cz/MIRRORS/sagemath/index.html](http://ftp.sh.cvut.cz/MIRRORS/sagemath/index.html) and choose "Download for Linux &#8212; binary distribution for Linux"

Choose the correct platform and mirror download file called sage-4.1-linux-Ubuntu_9.04-xxx-Linux.tar.gz, extract the archive and execute sage from the directory using:

```
./sage
```

Now you should have the latest version up and running!

---

### Post by ahmatti on 2009-07-20
> **artesian_spring said:**
>  Is there a way to just install the SAGE environment and then direct it to the programs I already have, or would I need to uninstall them and then install SAGE? 


The binary archive mentioned in my post above contains Sage and all of the depencies so it install copies of the software you may already have (e.g. R and Maxima), but you don't need to uninstall what you already have.

I don't really know if there is way to point Sage to your existing installations in case you don't want duplicates, but at least they can coexist peacefully :) e.g the R version that comes with Sage is 2.61 and I have 2.91 installed from CRAN.

---

### Post by WhiteHorse on 2009-09-26
Could someone please update the Ubuntu repo version of sage to 4.x? I get the same jMol error but after upgrading to 4.1.1 it works fine...

---

### Post by Chronon on 2009-09-26
Developers don't hang out on forums much.  None of us, that I know of, has the power to change this.  It looks like the version slated to be in Karmic is 3.0.5.  You're probably better off just getting it from the sagemath download mirror if you want a 4.x version.

[http://www.sagemath.org/download-linux.html](http://www.sagemath.org/download-linux.html)

Karmic is already in feature freeze, so I am quite sure that no official version changes will be permitted in this cycle.  You should get in early for the next release and make suggestions on launchpad, though.

---

### Post by littlemog on 2009-09-27
and there's always self compile and build from source. that's something ubuntu's good for too, if it has to be done that way.

---


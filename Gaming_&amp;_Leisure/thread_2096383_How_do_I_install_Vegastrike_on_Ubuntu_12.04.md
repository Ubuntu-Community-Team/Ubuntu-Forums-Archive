---
title: "How do I install Vegastrike on Ubuntu 12.04?"
date: 2012-12-19
forum: Gaming &amp; Leisure
---

### Post by pythonscript on 2012-12-19
I download Vega Strike 0.5.1.r1 from this link:

[http://sourceforge.net/projects/vegastrike/files/vegastrike/0.5.1/vegastrike-data-0.5.1.r1.tar.bz2/download](http://sourceforge.net/projects/vegastrike/files/vegastrike/0.5.1/vegastrike-data-0.5.1.r1.tar.bz2/download)

I extracted the archive and ran

```

sudo sh vsinstall.sh

```

I get the following output when I answer "yes" to all the installation questions:

> 
                     ==== VEGA STRIKE 0.5.0 ====


I am installing 64-bit binaries.

This script needs your password to link the following commands 
 into '/usr/bin': vegastrike vegaserver vssetup mesher

Do you wish to grant administrator access to install these binaries?
Type yes or no: yes
Installation successful!

Do you want to run 'vssetup'? [yes]/no? yes
vsinstall.sh: 108: vsinstall.sh: vssetup: not found
Settings should now be configured.

Type 'vegastrike' at a terminal to play VS!  Press any key to exit.


I looked on Vega Strike's site, but I don't see anything about vssetup. How do I install this program on Ubuntu? It isn't in the repositories.

---

### Post by V13 Noob on 2012-12-25
Have you visited the VS wiki site? 
[http://vegastrike.sourceforge.net/wiki/Manual:Install#Linux]("http://vegastrike.sourceforge.net/wiki/Manual:Install#Linux")

I don't have that program anymore but do you want to install? I would just run it from a link I put in the menu.

---

### Post by holastickboy on 2012-12-26
This was in the playdeb repositories which are currently down at the time of writing this post.  Nonetheless, a simple apt-get install guide is found here:
[http://www.webupd8.org/2009/10/free-open-source-space-simulation-game.html](http://www.webupd8.org/2009/10/free-open-source-space-simulation-game.html)

---

### Post by AR_Kozz on 2012-12-29
> **holastickboy said:**
> This was in the playdeb repositories which are currently down at the time of writing this post.  Nonetheless, a simple apt-get install guide is found here:
[http://www.webupd8.org/2009/10/free-open-source-space-simulation-game.html](http://www.webupd8.org/2009/10/free-open-source-space-simulation-game.html)

That install guide is obsolete, because the ubuntu repo's contain only vegastrike-data and vegastrike-music. The binaries aren't there and haven't been since at least 10.04.

---


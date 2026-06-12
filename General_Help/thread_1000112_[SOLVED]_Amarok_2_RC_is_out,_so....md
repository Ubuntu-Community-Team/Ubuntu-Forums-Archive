---
title: "[SOLVED] Amarok 2 RC is out, so..."
date: 2008-12-02
forum: General Help
---

### Post by Gonz_91 on 2008-12-02
Hi everyone!

I'm looking for a way to install Amarok 2 in Ubuntu Intrepid.
Is there any way to do this?
Are there any special repo's?

(please note that I'm posting as a last resort, and after some serious time google-ing)


Thanks

---

### Post by Gonz_91 on 2008-12-03
Anyone?

---

### Post by infinitejones on 2008-12-03
Well there's [this link]("http://download.kde.org/download.php?url=unstable/amarok/1.98/src/amarok-1.98.tar.bz2") if you want to have a go at compiling it yourself... or [Project Neon]("http://amarok.kde.org/en/node/482"), which was supplying nightly builds from a repository via aptitude/apt-get/synaptic. I don't know if Project Neon has the RC yet though.

I've just downloaded the tarball - the installation instructions are [here]("http://amarok.kde.org/wiki/Compiling:2.0") and look simple enough. I'll also try the Project Neon repository and report back in a few minutes...

---

### Post by hyper_ch on 2008-12-03
you can, of course, try to compile it from source...

---

### Post by MickS on 2008-12-03
I got it from here [http://www.kubuntu.org/amarok2-beta2](http://www.kubuntu.org/amarok2-beta2)
presuming that's the same thing, didn't like it at first but it's growing on me.

Mick

---

### Post by infinitejones on 2008-12-03
> **MickS said:**
> I got it from here [http://www.kubuntu.org/amarok2-beta2](http://www.kubuntu.org/amarok2-beta2)


Yeah, ignore my last post, trying to do it that way got very confusing very quickly! This way I had it installed and working in about 3 minutes.

Add those repositories and ```
sudo apt-get install amarok-kde4
```

---

### Post by Gonz_91 on 2008-12-03
> **infinitejones said:**
> Yeah, ignore my last post, trying to do it that way got very confusing very quickly! This way I had it installed and working in about 3 minutes.

Add those repositories and ```
sudo apt-get install amarok-kde4
```

Done it, and it's installing.
Thank you all very very much for your help!

:D

---

### Post by hachel on 2008-12-04
hmm i tried that but it tells me this:
```
The following packages have unmet dependencies:
  amarok-kde4: Depends: kdelibs5 (>= 4:4.1.3) but 4:4.1.2-0ubuntu11 is to be installed
E: Broken packages
```
any help?
thanks

---

### Post by BrownieMan on 2008-12-07
> **hachel said:**
> hmm i tried that but it tells me this:
```
The following packages have unmet dependencies:
  amarok-kde4: Depends: kdelibs5 (>= 4:4.1.3) but 4:4.1.2-0ubuntu11 is to be installed
E: Broken packages
```
any help?
thanks

Try this

```
sudo apt-get install kdelibs5
```

What your error message is telling you is that "amarok-kde4" (amarok) needs certain "programs" (they actually are called libraries) and that they aren't installed. The library that is missing is called "kdelibs5". What might be an easier way is to try installing amarok is throught eh package manager (Less chance of ******* things up... too much)

---


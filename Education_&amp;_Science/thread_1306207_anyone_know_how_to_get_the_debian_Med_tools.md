---
title: "anyone know how to get the debian Med tools?"
date: 2009-10-30
forum: Education &amp; Science
---

### Post by coolgenes on 2009-10-30
I was looking at Bio-Linux and was able to successfully apt-get some of those pachages (don't get the handlebar, it hangs).  But found that the Debian MedTools holds a lot of molecular type tools I could use but am having trouble gaining access to them.  I contacted the tools moderator but no reply.  Also, if anyone has any success getting Samtools and Staden to install on Ubuntu please let me know.

---

### Post by coolgenes on 2009-11-13
bump?

---

### Post by Chronon on 2009-11-14
Sorry, I don't have any special info, but if package versions for dependencies are not consistent between Debian and Ubuntu then you could consider trying to build these tools from source.

---

### Post by ajt on 2009-11-14
> **coolgenes said:**
> I was looking at Bio-Linux and was able to successfully apt-get some of those pachages (don't get the handlebar, it hangs).  But found that the Debian MedTools holds a lot of molecular type tools I could use but am having trouble gaining access to them.  I contacted the tools moderator but no reply.  Also, if anyone has any success getting Samtools and Staden to install on Ubuntu please let me know.

Hello, coolgenes.

Bio-Linux 5.0 is based on Ubuntu 8.04 LTS, and there are some 'hardy' dependencies. Have you tried installing the Bio-Linux Staden?

```

# add to /etc/apt/sources.list:
# deb http://nebc.nox.ac.uk/bio-linux/ unstable bio-linux

aptitude install bio-linux-staden

```

Bye,

  Tony.

---

### Post by coolgenes on 2009-11-16
Thanks AJT, yes I've tried that.  the problem with the BioLinux lib is that they aren't up to date.  both the PhredPhrap and the Staden are out of date enough I think I have to install them myself,  I just don't think they have enough help there to continue to compile all the updates to the molecular and evolution type analysis programs.  I was hoping the Med tools would be better or at least compliment what BioLinux has

---

### Post by parktownprawn on 2009-11-17
The debian med packages are in Ubuntu since Ubuntu is derived from Debian


Try typing ```
sudo apt-get install med-bio
```.

If you want to see what packages are available check out 

[http://debian-med.alioth.debian.org/tasks/bio]("http://debian-med.alioth.debian.org/tasks/bio")

To see what Debian med packages there are in Ubuntu try typing 

```
apt-cache search med-
```

I have no idea how up to date these are.

---


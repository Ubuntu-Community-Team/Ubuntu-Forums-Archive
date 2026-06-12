---
title: "Octave 3.2"
date: 2010-05-03
forum: Education &amp; Science
---

### Post by banerjeerupak on 2010-05-03
hi,

I have recently updated to Ubuntu 10.04. I have been working on a project using Octave. Suddenly i'm required to install Octave 3.2. It is not part of the package and I have to upgrade it. I was previously using 3.0. Now I am most comfortable installing programs using .deb installers. However, I did go online and got myself the .tar.gz file as .deb was not available for Octave 3.2. 

Now the first step in installing using .tar.gz is supposed to be *./configure*

On using that, i get a bash response. 

*bash: ./configure: No such file or directory*

Please help me. What do i do? I have been using alternate computers for the time being, but i want to be able to work on my system at the earliest.

---

### Post by banerjeerupak on 2010-05-03
Managed to install using the software centre. I had both 3.0 and 3.2 installed, which was giving trouble. Now with 3.0 removed, i can work peacefully on my system.

---

### Post by gunksta on 2010-05-03
**Disclaimer - **I have never used Octave and I know practically nothing about it.

That being said, this looks like a fairly easy problem to solve. (I'll just go ahead and count this as my good deed for the day.)

> It is not part of the package and I have to upgrade it.I'm honestly not sure what you mean by this, but I looked in the repos and Octave 3.2 is in there. Unless you need a specific point release that's not in the repos, this should work for you (if your needs are that specific, you already know it. If you don't have a clue what I'm talking about here, just assume the version in the repos is good)

Since you got as far as ./configure, I assume command line instructions are appropriate.

```
sudo apt-get install --install-recommends octave3.2
```On my system, it looks like I need to download a little more than 30 MB of archives and once installed will take about 103 MB of space on my hard drive. Depending on what you already have installed, this may look a bit different for you.

If you would like a nice GUI front-end to Octave, I have heard nice things about qtoctave. The above should install everything you need if you are an Emacs user.

```
sudo apt-get install --install-recommends qtoctave
```

---

### Post by gunksta on 2010-05-03
Oops. Nevermind. Looks like I dallied too long.

---


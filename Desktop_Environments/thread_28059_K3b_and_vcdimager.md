---
title: "K3b and vcdimager"
date: 2005-04-18
forum: Desktop Environments
---

### Post by Morimando on 2005-04-18
I have the problem that the vcdimager version in the repositories are to new.. I had the same problem with Gentoo, where i just told Gentoo to use the last version before the newest one (0.7.19), Now with Ubuntu i do apt-get install vcdimager and it installs 0.7.20 once again --> K3B won't burn SVCD/VCD :(
So my question is: How do i get Ubuntu to use the previous version? In Synaptic if i select the Preferences of the vcdimager package it doesn't show me another version of it, so i can't select the previous version.
Also if i want to install it from source i would also have to install libcdio from source since the ./configure of vcdimager doesn't realize that libcdio is installed as an Ubuntu package (maybe because it is called libcdio0 in Ubuntu, don't know)

 :roll:

---

### Post by diebels on 2005-04-18
Better if you tell us what error messages you get, so we can help you fix it.

---

### Post by Morimando on 2005-04-19
[QUOTE=diebels]Better if you tell us what error messages you get, so we can help you fix it.[/QUOTE]
It's not a problem with vcdimager afaik it's just the k3b+vcdimager combination, k3b isn't working with the new version (maybe vcdimager changed in syntax?)..
however: K3B's output:
```

charset conversion failed
vcdxbuild returned an unknown error code (code 1).
Operation not permitted.

```

---

### Post by diebels on 2005-04-20
You need to apply charset parameters to vcdxbuild in k3b configuration. The line "--filename-encoding=iso8859-1" in:
settings
 configure k3b
  programs
   user parameters
    vcdxbuild --filename-encoding=iso8859-1

---

### Post by Morimando on 2005-04-21
[QUOTE=diebels]You need to apply charset parameters to vcdxbuild in k3b configuration. The line "--filename-encoding=iso8859-1" in:
settings
 configure k3b
  programs
   user parameters
    vcdxbuild --filename-encoding=iso8859-1[/QUOTE]
vcdxbuild still gives an unknown error ^^

---

### Post by diebels on 2005-04-21
Screenshot of settings

---

### Post by Morimando on 2005-04-25
[QUOTE=diebels]Screenshot of settings[/QUOTE]
t'was what i did, same error.

---

### Post by Morimando on 2005-04-27
[QUOTE=Morimando]t'was what i did, same error.[/QUOTE]
Does nobody know how to insert the 0.7.19 version of vcdimager?
if i had the .deb all would be fine.
unfortunately i can't build from source since i t doesn't recognize all versions due to the naming schemes Ubuntu applies (at least i think that's the problem vcdimager has)

---

### Post by grakker on 2005-06-26
Has anyone done anything with this?  I'm having the same problem...

---

### Post by DuncanR on 2005-06-30
I had the same problem in K3b today when trying to burn an MPG file into an SVCD.

I got around it by using 'vcdimager' from the command line to create .cue and .bin files from the MPG. I then used K3b to burn the resulting image. A little messy, but worked fine this way.

---


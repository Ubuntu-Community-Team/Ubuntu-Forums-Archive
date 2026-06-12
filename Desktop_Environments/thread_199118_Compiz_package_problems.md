---
title: "Compiz package problems"
date: 2006-06-18
forum: Desktop Environments
---

### Post by monkeyhelper on 2006-06-18
I've had compiz/xgl running for a while now but after some recent updates I find a dependancy problem when upgrading/installing compiz-vanilla-gnome.  When trying to install via synaptic I see :

compiz-vanilla-gnome:
  Depends: libpango1.0-0 (>=1.12.3) but 1.12.2-0ubuntu3 is to be installed

There doesn't seem to be any libpango 1.12.3 in the ubuntu repositories - anybody else seen this problem or know how to fix it ?

---

### Post by purfier on 2006-06-18
Use compiz source, deb http://www.beerorkid.com/compiz dapper main
hope it works;)

---

### Post by monkeyhelper on 2006-06-18
I already have the compiz/xgl repositiories in my sources.list, so this won't solve the problem.

---

### Post by Evilsmevil on 2006-06-27
Yeah im having the same problem, is there any way to download the newer version from somewhere other than the repos?

---

### Post by Styles on 2006-07-10
I'm having the same issues with compiz-gnome and libpango, anybody have a fix yet with out going to edgy?

---

### Post by stryderjzw on 2006-07-11
Exact same problem here.  ](*,)

---

### Post by stryderjzw on 2006-07-11
I got it!  You have to enable dapper-updates repository.  It's in synaptic.  Very easy.

---


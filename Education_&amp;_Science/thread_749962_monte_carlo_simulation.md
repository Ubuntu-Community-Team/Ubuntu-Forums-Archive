---
title: "monte carlo simulation"
date: 2008-04-09
forum: Education &amp; Science
---

### Post by veloce on 2008-04-09
Does anyone know of any good open source monte carlo simulation tools for linux?  

I'm sick of using @risk on a windows machine - with their latest upgrade, I can't use an rdp session to connect to the windows machine.  It's reached the threshold where I'd rather use something else.

I'd love something that integrated with ooo calc, but I'm happy to work with what's available.

I see R now has some limited integration with calc, does it do simulations?

---

### Post by thisismalhotra on 2008-04-09
> **veloce said:**
> Does anyone know of any good open source monte carlo simulation tools for linux?  

I'm sick of using @risk on a windows machine - with their latest upgrade, I can't use an rdp session to connect to the windows machine.  It's reached the threshold where I'd rather use something else.

I'd love something that integrated with ooo calc, but I'm happy to work with what's available.

I see R now has some limited integration with calc, does it do simulations?

A shot in the dark but worth trying..

Use octave(use version 3.0 and not the older ones in repos).. It is fully matlab compatible and if you find a code online for Monte Carlo simulation for matlab most like it will work without any changes in octave.

GL

---

### Post by plvera on 2008-04-10
I'm not familiar with calc.

R, however, has very powerful and reliable bootstrapping functions. Perhaps those would be useful to you, depending what you are looking for in your Monte Carlo simulation.

I hope this helps.

---

### Post by euler_fan on 2008-04-10
I'd suggest R. There are some excellent MCMC and bootstrap packages available and it is possible to code up custom MCMC algorithms to fit your specific context. I'm writing a package for one such context--Single Photon Emission Computed Tomography--right now in fact.

---

### Post by jsampaio57 on 2011-05-24
This is an old thread, but if somebody reaches this point and needs some additional idea, please try gnumeric. The gnome office spreadsheet has a simulation engine using monte carlo that may serve for some problems. It also has 154 functions in addition to what is found in MSExel and OO Calc, including 48 statistical functions form the project R. Cheers... Jorge

---


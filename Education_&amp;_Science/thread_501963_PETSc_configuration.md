---
title: "PETSc configuration"
date: 2007-07-16
forum: Education &amp; Science
---

### Post by Gabriel Wu on 2007-07-16
Hi, I am trying to configure PETSc for magpar.

And I am facing an annoying problem with running the configuration script with the command ```
./config/PETSc-config-magpar.py. 
```

When I try to run it, I get the error message 
```
: No such file or directory
```

There are loads of other configuration files in the config directory, and I don't get such error messages with any of the other config files. 

I suspect that the reason is the file wasn't in the directory by default (I copied it over from another magpar directory, following directions on the [magpar installation documentation]("http://magnet.atp.tuwien.ac.at/scholz/magpar/doc/html/install.html#c_petsc").) But I cannot figure out how to get it to work still.

Any help on this would be greatly appreciated. 

Thanks.

---

### Post by aNtO83 on 2008-02-23
HELLO!!

I have to install magpar with petsc too and i have to face a similar problem whit petsc-config-magpar.py.

Have you solved it?


thanks!

---

### Post by Gabriel Wu on 2008-06-20
hi, I installed it according to the instructions for single processor PETSc, given [here]("http://magnet.atp.tuwien.ac.at/scholz/magpar/doc/html/faq.html#singleproc").

Argh, i'm reinstalling Magpar after a year, and it's really irritating!

---

### Post by magpar_author on 2008-10-08
Hi all!

I am the author of magpar and I would be happy to help you solve your installation problems.

The first posting is from July 2007, so I assume Gabriel was using magpar version 0.5. I tried to simplify and improve the installation procedure with version 0.7 and the current 0.8pre4 with the "Makefile.libs".

Did you have a chance to try the new magpar versions and the automated installation with the Makefile.libs?

[http://magnet.atp.tuwien.ac.at/scholz/magpar/doc/html/install.html#c_autoinst]("http://magnet.atp.tuwien.ac.at/scholz/magpar/doc/html/install.html#c_autoinst")

The manual installation is also described in the documentation and still works:
[http://magnet.atp.tuwien.ac.at/scholz/magpar/doc/html/install.html#c_petsc]("http://magnet.atp.tuwien.ac.at/scholz/magpar/doc/html/install.html#c_petsc")

Could it be that you missed one of the steps, where you change into the PETSc directory
```

cd $PD  # assuming PD has been set before
lib=petsc-2.3.3-p8  # update for the version you use - current is 2.3.3-p15
cd $lib

```

set the environment variables
```

PETSC_DIR=$PD/$lib  # assuming PD has been set before
export PETSC_DIR
PETSC_ARCH=PETSc-config-magpar
export PETSC_ARCH

```

and then copy the PETSc-config-magpar.py script from the magpar src directory into the PETSc config directory
```

# assuming you set the MAGPAR_HOME variable correctly
cp $MAGPAR_HOME/src/PETSc-config-magpar.py $PETSC_DIR/config/

```

Then you should be able to run the configuration script:
```

# NB: you must be in the $PETSC_DIR directory when you run the script
./config/PETSc-config-magpar.py

```

I hope this helps.

If you still have problems, reply to this post and email me at the magpar email address below.

Cheers,

Werner

-- 
magpar - Parallel Finite Element Micromagnetics Package
WWW:    [http://magnet.atp.tuwien.ac.at/scholz/magpar/](http://magnet.atp.tuwien.ac.at/scholz/magpar/)
email:  [email]magpar@magnet.atp.tuwien.ac.at[/email]

---

### Post by shahab1363 on 2008-10-23
Hi Guys
Have any one successfully installed magpar on hardy (ubuntu 8.04) without mpi?! :confused:
I've tried...but got nothing in several days... :(

Thanks,
Shahab

---

### Post by magpar_author on 2008-10-31
Dear shahab1363,

> 
Have any one successfully installed magpar on hardy (ubuntu 8.04) without mpi?!
I've tried...but got nothing in several days... 


I have heard from other users who successfully installed magpar on recent versions of Ubuntu without major issues. Here are a few hints, which might be helpful:

[http://magnet.atp.tuwien.ac.at/scholz/magpar/doc/html/faq.html#debpack](http://magnet.atp.tuwien.ac.at/scholz/magpar/doc/html/faq.html#debpack)

If you really want to compile magpar without MPI (even though it is probably easier to install it with than without MPI on Ubuntu) this should help:

[http://magnet.atp.tuwien.ac.at/scholz/magpar/doc/html/faq.html#singleproc](http://magnet.atp.tuwien.ac.at/scholz/magpar/doc/html/faq.html#singleproc)

Please let me know if your installation still does not work and which problems/error messages you run into.

If you still have problems, reply to this post and/or email me at the magpar email address below.

Hope this helps,

Werner

-- 
magpar - Parallel Finite Element Micromagnetics Package
WWW: [http://magnet.atp.tuwien.ac.at/scholz/magpar/](http://magnet.atp.tuwien.ac.at/scholz/magpar/)
email: [email]magpar@magnet.atp.tuwien.ac.at[/email]

---


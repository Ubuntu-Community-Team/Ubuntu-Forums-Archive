---
title: "OpenFVM"
date: 2008-09-16
forum: Education &amp; Science
---

### Post by xflow on 2008-09-16
OpenFVM is a general CFD solver released under the GPL license. It was developed to simulate the flow in complex 3D geometries. Therefore, the mesh can be unstructured and contain control volumes with arbitrary shape. The code uses the finite volume method to evaluate the partial differential equations. As well as solving the velocity and pressure fields, the code is capable of solving non-isothermal multiphase flow.

The code has two implementations: serial and parallel. The serial version uses LASPACK as the linear matrix solver and the parallel one uses the PETSc library. Both implementations use the open source tool Gmsh for pre- and -post processing. 

[http://openfvm.sourceforge.net/](http://openfvm.sourceforge.net/)

---

### Post by hubie on 2008-09-16
How does it compare to OpenFOAM (features, ease of use, etc.)?  I'm at the point where I want to play around with CFD simulations and I haven't committed myself to anything yet (other than downloading OpenFOAM and installing it).

---

### Post by xflow on 2008-09-16
OpenFOAM is very powerful and extensible but also very difficult to understand since it is a very large code.

On the other hand, OpenFVM is small, easier to understand and the equations are well documented in the manual. It is also based on other open source tools such as Gmsh, LASPACK, PETSc and METIS.

---

### Post by xflow on 2008-09-18
BTW, the project is looking for a packager. If anyone interested please contact me.

---

### Post by xuwuju on 2008-09-20
I am interesting your software -- OpenFVM from your introduction and have downloaded it and am reading it. But where is the manual you said? I think a brief manual is necessary at least to describe the basic equations, the algorithms, and the frames.

> **xflow said:**
> OpenFOAM is very powerful and extensible but also very difficult to understand since it is a very large code.

On the other hand, OpenFVM is small, easier to understand and the equations are well documented in the [COLOR="Red"]manual[/COLOR]. It is also based on other open source tools such as Gmsh, LASPACK, PETSc and METIS.

---

### Post by xflow on 2008-09-22
Hi,

You can download the Reference Manual in PDF format at sourceforge:

[http://sourceforge.net/project/showfiles.php?group_id=142103&package_id=281271](http://sourceforge.net/project/showfiles.php?group_id=142103&package_id=281271)

---

### Post by shirazbj on 2010-04-12
I just found this code. It's very good. I like to read the detailed equations and see how they are coded(for example building the momentum matrix). Good to learn. 

Just wondering is there any possible it could output VTK file to be viewed by paraView. 

I haven't figured out how to post precess with gmsh's pos file. It is an old format.

Regards

Cean

---


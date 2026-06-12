---
title: "FEM mesh generator needed"
date: 2010-01-13
forum: Education &amp; Science
---

### Post by vocs on 2010-01-13
Hello,

I need an easy to use software to generate 3D meshes for a program based on a finite element method. I just need to draw a simple perimeter and then automatically create a mesh just by specifying the number of nodes. I also need to export the mesh data through some text files. I tried some softwares in the ubuntu repositories but they are very user unfriendly and I don't know how to use them...

Thank you

---

### Post by alexfish on 2010-01-13
hi

it may help if we know which ones you have tried

---

### Post by vocs on 2010-01-13
Hi,

I tried elmer and z88 because I've read that they have a mesh generator. Now I'm trying to use gmsh and it is much better for my purpose. However I can't understand how to create meshes with only triangles (gmsh uses monodimensional elements on the boundary by default). Do you know how to use gmsh?

---

### Post by alexfish on 2010-01-13
have you looked at wings

also have a look around this site

[http://cookerspot.tuxfamily.org/wikka.php?wakka=ProgramsScientific](http://cookerspot.tuxfamily.org/wikka.php?wakka=ProgramsScientific)

---

### Post by vocs on 2010-01-13
I've just tried it but it seems too much complex and difficult to use. Moreover it's focused on drawing while I need something for finite elements...

---

### Post by alexfish on 2010-01-14
don't see any easy roads to your quest

try looking here

[http://www.caelinux.com/CMS/](http://www.caelinux.com/CMS/)

[http://www.caelinux.org/wiki/index.php/Doc:GettingStarted](http://www.caelinux.org/wiki/index.php/Doc:GettingStarted)

it also has a forum

[http://caelinux.com/CMS/index.php?option=com_joomlaboard&Itemid=52&func=showcat&catid=17](http://caelinux.com/CMS/index.php?option=com_joomlaboard&Itemid=52&func=showcat&catid=17)

---

### Post by not_a_phd on 2010-01-16
Have you looked at salome? [http://www.salome-platform.org/about](http://www.salome-platform.org/about)

---

### Post by vocs on 2010-01-16
Thank you very much! However I managed to solve the problem I had with Gmsh. I only had to use a physical group to select the geometrical elements that I wanted.

---


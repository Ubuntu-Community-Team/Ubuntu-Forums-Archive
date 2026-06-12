---
title: "abaqus tennis racket tutorial error"
date: 2010-11-22
forum: Education &amp; Science
---

### Post by blackeagle1245 on 2010-11-22
Hello, I'm learning abaqus . I'm tring to make a tutorial in abaqus. I'm
doing everything right but when I submit the job I'm taking this error
message. Thanks to everyone.
Error in job Job-1: 1 improperly defined surface(s). Please check your
surface definitions. Make sure that all surface normals point outward.
Error in job Job-1: Node-based surface ASSEMBLY_FRAME-1_STRINGS_CNS_ belongs
to the rigid body with reference node 1 instance         . A rigid
node-based surface cannot be used in a kinematic contat pair. This
node-based surface is currently paired with surface
ASSEMBLY_BALL-1_BALL-OUTER in a kinematic contact definition.
Job Job-1: Abaqus/Explicit Packager aborted due to errors.

---

### Post by tgalati4 on 2010-11-22
It's been a while since I have used abaqus.  Your first error indicates that your surface elements have normals pointing in and out.  They should all be pointing the same direction.  I don't know what you are using to create your mesh, but turn the normals on in the visualizer and you will probably see some reversed elements.

As far as the second error, it looks like you are using the incorrect Finite Elements for a kinematic contact pair--I presume the racket and the ball.  You are modeling the racket with a rigid body mesh element and that can't be used for kinematics.  Go through the abaqus mesh element catalog and choose a kinematic element for both the racket and the ball.  

That will fix those initial errors.  There may be other errors, but they won't be revealed until you fix the big ones.

---

### Post by blackeagle1245 on 2010-11-23
Thanks for the answer. I opened the normals as you can see in the picture. What should I do now? How can I change their directions? For the other problem I dont know which one and how should I change the constraint type ( tie, rigid body,display body, coupling, mpc constraint, shell to solid coupling, embedded region, equation ) ?. I'm doing what it says in the official tutorial. If you need I can send and we can check together for the errors. It is very important for me to finish this project.
 
[picture]("http://yfrog.com/n4normalsrj")

---

### Post by tgalati4 on 2010-11-26
Normally, to change the normals, you have to remesh in the problem region.  The racket normals look OK, but there may be a few inverted normals on the ball.  You will have to zoom in and check for degenerate elements (ones that collapse or are too small) and carefully check the surface of the ball to ensure that all the element normals are pointing out.

As far as the element type, normally you specify the type of elements in the mesher, so the mesh that is created has the appropriate placeholders for the contraints to come later.  The contraints are then applied--you will get errors if you try to apply contraints to the wrong type of elements.  The same mesh can be used to perform several different types of analyses as long as you choose the correct element type.  I don't have a recent copy of abaqus to walk you through the procedure.  I don't know what tutorial you are using.  I presume the tutorial is correct for the version of abaqus that you are using.  

It's also possible that the tutorial has errors.

---

### Post by blackeagle1245 on 2010-11-27
[LEFT]I'm using this [tutorial]("http://www.fkm.utm.my/~arahim/workshop-tennis-racket.pdf") but my version is 6.8.1 I have never thought that would create problem. I couldnt find this tutorial for my version. I'll try to change the element type I hope I can find the problem. Thanks for your interest.[/LEFT]

---

### Post by blackeagle1245 on 2010-12-05
I checked for the normals. All of them shows the same direction. I dont know what should I do? I'm still tring to solve these problems. Could you please help ?

---

### Post by blackeagle1245 on 2010-12-09
Does anybody know this problem? It is very urgent for me.

---


---
title: "Trouble with K3D and Blender3D in Intrepid"
date: 2009-02-27
forum: General Help
---

### Post by ianchristie on 2009-02-27
First, I really haven't used K3D before but I assume some controls are the same as in Blender3D.

With that said, here's the problem I'm having.

In Blender3D and it appears to be in K3D also, when you select an object it shows a control for the available action (Move Rotate Scale) on the object and you are supposed to be able to click on a part of the control and then adjust the object in the axis indicated.

Well in Blender3D on Hardy that worked great, but recently I upgraded to Intrepid and for some reason that control doesn't work.

I have Compiz turned off and no other compositing manager running.

I'm using Blender3D 2.48 which isn't available in the intrepid repositories and have tried 2.46 from the repositories. K3D is from the repository. None of them work properly. So I assume it's not a Blender3D problem because it is doing this in K3D also.

Anyway, any ideas why in Hardy this works, but not in Intrepid?

---

### Post by ianchristie on 2009-02-27
Forgot, I'm running the AMD64 version of Intrepid and this problem has been there from the start.

---

### Post by ianchristie on 2009-02-27
A little more information, it seems the left click also doesn't work properly in Wings3D. It only seems to be happening in 3D apps. I can't use the control widgets and inWings, you can't even select with the mouse.

This is on a Dell Inspiron 1501 with an AMD Athlon 64 X2, using the OSS ATi driver because the regular driver causes crashes with Blender.

---

### Post by ianchristie on 2009-02-27
Problem solved, I had to use the FGLRX (official ati) drivers.

I guess I assumed they would have the same problem as they did in Hardy.

---

### Post by caddict on 2009-03-27
Hi Ian

what version of K3D are you running?

---


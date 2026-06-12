---
title: "GL_POINT_SMOOTH having no effect with Ivy Bridge (Nvidia working fine)"
date: 2012-10-17
forum: Education &amp; Science
---

### Post by timvg on 2012-10-17
I wasn't too sure which section to put this in, programming or science, but since I am trying to use and OpenGL function for science, I thought that I would put it here. Apologies if this is wrong.

I am trying to make use of Psycho-Physics software such as PsychToolBox3 for MATLAB, and PsychoPy, and I noticed that any function that would be called to draw dots, would in fact be drawing squares. I had a look around and found that the problem was with the OpenGL driver, as this sometimes renders GL_POINTS as circles, and sometimes as squares, depending on the hardware.

I found out that adding the line "glEnable(GL_POINT_SMOOTH)" should solve the problem. But... this is not working at all. I am using a System76 Lemur with an Intel HD4000  Ivy Bridge for graphics using Ubuntu 12.04. Of note, my older Vaio which has an Nvidia 310m card, running Kubuntu 12.04, is drawing the dots as circles with exactly the same code.

If anyone knows of a way to solve this problem, then I would be very grateful.

---


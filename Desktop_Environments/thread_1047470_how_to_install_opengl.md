---
title: "how to install opengl??"
date: 2009-01-22
forum: Desktop Environments
---

### Post by hockey97 on 2009-01-22
Hi, I am trying to install opengl and blender properly.


When I installed opengl and blender I would try to run blender and it won't even pop up  a window.

I looked at the command prompt.

I found out it fails at the part where it implements opengl.

before that phython 2.5 works and then failes at where it tries using opengl.

any ideas of what I should do. I played around with this and the package manager at one point deleted alot of system files which when I restarted my computer it would only boot in server mode I would have the console prompt.

any ideas what I should do??


do you want me to post anything here... if so what and where to get it.

Thanks for your time.

---

### Post by Simian Man on 2009-01-22
What graphics card do you have?  Are you using the restricted drivers, or the default ones?

What is the output of:
> glxinfo | grep rendering

Basically OpenGL is implemented in your graphics card along with the drivers, not as a regular library package.

---

### Post by mnlmrn on 2009-02-12
Hello 

I have the same problem, i dont know how to install openGL in ubuntu8.10.

After:
glxinfo | grep rendering
I got: yes

Where do i have to find the package to install it?
thx

---


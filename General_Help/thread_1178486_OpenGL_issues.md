---
title: "OpenGL issues"
date: 2009-06-04
forum: General Help
---

### Post by decion on 2009-06-04
I am running Ubuntu 9.10 and I am having all sorts of problems getting OpenGL to work.  My latest problem is trying to run ParaView.  Upon execution I get:

> ERROR: In /build/buildd/paraview-3.2.3/VTK/Rendering/vtkXOpenGLRenderWindow.cxx, > line 398
> vtkXOpenGLRenderWindow (0x1e16650): Could not find a decent visual
> 
> ERROR: In /build/buildd/paraview-3.2.3/VTK/Rendering/vtkXOpenGLRenderWindow.cxx, > line 398
> vtkXOpenGLRenderWindow (0x1e16650): Could not find a decent visual
> 
> Segmentation fault

I have a NVIDIA GeForce GTX 260 card that I have set up with the CUDA drivers by following a set of instructions found in the forums.  I am thinking the CUDA setup might of broke the OpenGL functions, but I am not that knowledgable on OpenGL.  I can get CUDA programs to run on the GPU but they do not work when anything needs to visualize with OpenGL. 

Looking at the nvidia-setting control panel under OpenGL/GLX Information I have "Fail to query the GLX server vendor."  I am using the NVIDIA 180.44 drivers.  

Any insight into the source of my OpenGL problems is appreciated.

---


---
title: "Unity 3D Will Not Start... other issues"
date: 2012-02-22
forum: Desktop Environments
---

### Post by vladverzeni on 2012-02-22
So, the basic problem is that Unity 3D does not run even when I choose it at the login screen.  Ubuntu loads Unity 2d every time.

I've been researching this for a couple hours and have not been able to figure it out.  

When I run the basic test:

> /usr/lib/nux/unity_support_test -p


I get:

> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  21
  Current serial number in output stream:  21
james@cora:~$ /usr/lib/nux/unity_support_test: -p
bash: /usr/lib/nux/unity_support_test:: No such file or directory
james@cora:~$ /usr/lib/nux/unity_support_test -p
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  21
  Current serial number in output stream:  21



Some known issues I'm having.  I think this all has something to do with my additional drivers?  I currently have the proprietary driver ATI/AMD proprietary FGLRX graphics driver installed.

I am running Ubuntu 11.10 and have had Unity 3D working before, I just installed 11.10 again.

Another strange thing, when I open Tweak Ubuntu I noticed that there are no options for changing around the launcher or other unity settings like there usually are.

---

### Post by Frogs Hair on 2012-02-22
Have you installed the CCSM , Which includes the Unity 3D Plug-in ? The Unity Plug-in options that appear in Ubuntu Tweak are not available in Unity 2D. If you open the CCSM in Unity 2D The Unity Plug-in will not be active.

---

### Post by vladverzeni on 2012-02-22
> **Frogs Hair said:**
> Have you installed the CCSM , Which includes the Unity 3D Plug-in ? The Unity Plug-in options that appear in Ubuntu Tweak are not available in Unity 2D.** If you open the CCSM in Unity 2D The Unity Plug-in will not be active.**

Yeah, I have CCSM.  How do I open it in Unity 3D?

---

### Post by Frogs Hair on 2012-02-23
If Unity 3D worked on the same hardware with a different installation I suspect a problem with the installation of the OS or the driver . Remove the driver and try the support test . It should look as follows except that I use Nvidia .```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 280.13

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

---

### Post by raphifix on 2012-02-23
> **vladverzeni said:**
> Yeah, I have CCSM.  How do I open it in Unity 3D?

Run CCSM in Unity 2D and enable the Unity plugin.

---

### Post by vladverzeni on 2012-02-23
Frogs Hair:

So, I'm in Ubuntu now, with the additional drivers disabled.  The unity launcher/unity-lens-thing are not showing up.  I was able to succesfully run the test though, thank you.  Here are the results:

> james@cora:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.11

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes



raphifix:
I ran unityshell plugin (also when I had disabled the additional driver) and nothing showed up except my background when I logged into Ubuntu.  I couldn't pull up terminal even. I've gone back to disabling it.  I'm not sure what happened?  I had rechecked the automatic plugin after moving Unityshell to enabled, was this correct? I would fool around more but I have to go to school now.  Thanks for your help, I'll be back later!

---


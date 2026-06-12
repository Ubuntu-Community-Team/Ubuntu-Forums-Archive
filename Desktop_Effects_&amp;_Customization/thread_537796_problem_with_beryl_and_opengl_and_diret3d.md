---
title: "problem with beryl and opengl and diret3d"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by benny999 on 2007-08-29
well i follow this guide [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
using method 2 and direct 3d and opengl work so says cedega . it passes video tests then i do this guide [http://ubuntuforums.org/showthread.php?t=488385&highlight=x1300](http://ubuntuforums.org/showthread.php?t=488385&highlight=x1300)
then i go into xgl works fine but my opengl and direct3d are failed any ideas what could be causing this any help would be great oh im running 256mb ati x1300 pci-e thank you

---

### Post by Steveway on 2007-08-29
XGL is a fullscreen OpenGLapplication.
You can't get direct rendering in such an app.
You have to change to a normal session if you want to use other 3Dapps.

---

### Post by benny999 on 2007-08-29
so it's either desktop effects or playing 3d games etc with opengl and direct3d

---

### Post by Steveway on 2007-08-29
Yes. 
And there is no direct3d in Linux, if you use Cedega or Wine to play Windowsgames those direct3d calls get redirected to OpenGL calls, so your using in fact only OpenGL.
And by the way, you want to have the best performance in your games, don't you? So it's best to switch of everything unnessecary.

---

### Post by benny999 on 2007-08-29
could i use something other than beryl on a normal session to get desktop effects?

oh by the way im new to everything linux just thought id give it a try

---

### Post by benny999 on 2007-08-29
mm ok now to figure out how to unistall beryl and all it's other junk and go back to the original desktop controller do you know of a guide thanks you

---

### Post by Steveway on 2007-08-29
It's better to use Compiz-fusion.
Since Beryl is discontinued and merged into Compiz to makeCompiz-fusion.
But you'll get the same problem.
The only way is buying an Nvidia card (Fx series or newer) and use them, because they have their own implementation of GLX_ext_texture_from_pixmap and so they don't need XGL and you can use those Desktop effects while using other 3Dapps.
EDIT: You don't need to remove your Desktopeffects, you just need to log into a non-XGL session.

---

### Post by michael37 on 2007-08-29
I don't know if I understand what you mean since Direct3D is Linux can be provided only by Wine.  If so, here is a snippet from [Wine FAQ](http://wiki.winehq.org/FAQ#head-f1ef104fbe61a4f294662f26e09f325c9271e671):

> 
I'm using Beryl/XGL/Compiz and get poor performance/odd messages/broken applications

Using composite display managers in Linux tends to cripple OpenGL performance or break OpenGL entirely which is why we recommend that you disable them and remove composite from XOrg entirely before trying to use Wine. If you are using one and experiencing slow performance then DO NOT FILE BUGS as this is not a Wine bug. Just because TuxRacer runs fine doesn't mean it is Wine's fault, Windows games normally require a little more umph than basic Linux native games. Also to make sure, run glxinfo and make sure that it says "Direct Rendering : Yes".


If that's not what you mean, sorry.

---


---
title: "How-to Xgl/Beryl in Feisty?"
date: 2006-12-16
forum: Desktop Environments
---

### Post by dirtvoyles on 2006-12-16
Can anyone point me to how to install Xgl/Beryl on Kubuntu Feisty?

I have googled and searched hear for a couple of hours and cannot find anything. Maybe no one has done it yet.

---

### Post by dirtvoyles on 2006-12-17
So no one has tried this, or no one cares to help?

---

### Post by gluxoid on 2006-12-24
I found this link and will try it now:

[http://www.imbrandon.com/packages/dists/feisty/beryl/](http://www.imbrandon.com/packages/dists/feisty/beryl/)

---

### Post by dirtvoyles on 2006-12-24
Excellent. Since you're trying it, care to let me/us know how it goes?

---

### Post by gluxoid on 2006-12-24
Most plug-ins I tried (wobbly windows, scale, animations) all work perfectly stable for some hours of usage now. The GUI is responsive, even when playing video. Full screen video works also but not if the "Unredirect fullscreen windows" setting is turned on.

The only problem I found is that the desktop cube has drawing problems: only the front side of the cube is drawn. I tried to search for solutions on forums but I cannot find any. My graphics card is a GeForce Ti4400 128MB.

I followed the [Edgy AiGLX guide]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX") but instead used the feisty packages on [http://www.imbrandon.com](http://www.imbrandon.com). So basically:

[LIST=1][*]If necessary install a video driver. In any case check you have the GLX_EXT_texture_pixmap extension required to run AiGLX. AiGLX is already installed.
```
myaccount@myhost:~$ glxinfo | grep GLX_EXT_texture
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample,
```
 [*]Add this to /etc/apt/sources.list:
```
deb http://www.imbrandon.com/packages feisty beryl
deb-src http://www.imbrandon.com/packages feisty beryl
```
[*]Install Beryl
```
sudo apt-get install beryl emerald-themes
```
[*]Run Beryl the first time
```
beryl-manager
```
[*]Add beryl-manager to the Sessions start-up programs: System->Preferences->Sessions, Startup Programs, Add "beryl-manager"
[/LIST]

---

### Post by dr-nix on 2007-02-02
I suggest that you use the source below instead, also don't forget to visit the frontpage to get the gpg key --> [Beryl Project](http://ubuntu.beryl-project.org/)
> 
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main 

---

### Post by gluxoid on 2007-02-05
That one was not available when I made my previous post. Guess it is out-of-date now.

---


---
title: "beryl doesn't run (linux noob)"
date: 2006-11-21
forum: Desktop Environments
---

### Post by ShadowVlican on 2006-11-21
```
calvin@calvin-desktop:~$ glxinfo | grep direct
direct rendering: Yes
calvin@calvin-desktop:~$ beryl-manager
calvin@calvin-desktop:~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension

calvin@calvin-desktop:~$ 

```
that's the code... seems like i don't have XGL running?

according to this guide:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)
> If you don't see the beryl splash screen immediately, you may need to tell the manager to load Beryl - right-click on the red gem, go to "Select Window Manager" and choose "Beryl". If that doesn't work, there's a problem somewhere! Often, useful debugging output will show in the terminal window you used to start beryl with.

well here i am... i have no idea wtf is happening...
i bet it's something retarded i've overlooked as usual with linux

---

### Post by ShadowVlican on 2006-11-21
[http://ubuntuforums.org/showthread.php?t=304169](http://ubuntuforums.org/showthread.php?t=304169)

ok.. so seems like they changed stuff and guides weren't updated to reflect that.. great...

so now i see the beryl startup screen after doing this:

```
calvin@calvin-desktop:~$ beryl
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
calvin@calvin-desktop:~$ beryl-manager
calvin@calvin-desktop:~$ XGL Present
Initiating splash
beryl-xgl: water: GL_ARB_fragment_program is missing
Reloading all options.

calvin@calvin-desktop:~$ 

```
good.. took like 1min to load the damn thing... so now i see flashy animation, BUT MY WINDOWS are messed up

window EDGES to be exact... they flash ](*,) (not to mention everything is dog slow, not my system's fault since many youtube videos were made with even slower systems...)

lol... changing themes in Emerald Themer... my themes are flashing... windows are flashing. hahahah... this is great... ](*,)

---

### Post by ShadowVlican on 2006-11-21
LOL after **doing nothing** and just searching this forum.. seems like my borders/windows have stabilized?!?!

borders are no longer flashing and animations are nice and smooth now

in fact.. it's very fast!! no more lag!

i wonder how it fixed itself...

---

### Post by ShadowVlican on 2006-11-21
ok back from school

so i turn on this computer run this:

```
calvin@calvin-desktop:~$ beryl
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
calvin@calvin-desktop:~$ beryl-manager
calvin@calvin-desktop:~$ XGL Present
Initiating splash
beryl-xgl: water: GL_ARB_fragment_program is missing

calvin@calvin-desktop:~$ 

```
beryl now loads fast and i think everything works as it should now

i might want to reformat and install edgy again, then try beryl once again... maybe i can write a better guide than those folks, since i'm a noob writing for a noob

well of course unless there's an updated guide out there... anyone?

---

### Post by Rajiv_Nair on 2006-11-21
even i have this prob of window borders flashin when i fire up beryl. But it gets solved if i logout and log back in:D

---

### Post by ShadowVlican on 2006-11-22
as i said, i formatted and reinstalled ubuntu 6.10 edgy

this time, i followed this version to install beryl:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

why? i read about XGL being sh!t, and AIGLX isn't needed or wutever... anyhows...

i used method one (Installing from repository) then configured X.org to use the nVidia driver

then continued with section 2, 3, and 4 of the guide

reboot. BAM!! IT WORKS!!! OMG!!

```
calvin@calvin-desktop:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW!
calvin@calvin-desktop:~$ 

```

i haven't got around to tweaking and customizing it yet though... however i must say this is very impressive that programmers could think of using the graphics card like this while Microsoft wasn't able to (they use pixel shaders for their aero interface, while beryl uses opengl extensions?)

well there you go... from a noob linux user ;) 

lesson: if someone as "die hard windows user" as me can do this, so can you!

---

### Post by Rajiv_Nair on 2006-11-22
nice.....im also plannin on upgradin to edgy as soon as i get da time.coz net  speeds in my part of the world aint nythin to brag abt:D.......

---


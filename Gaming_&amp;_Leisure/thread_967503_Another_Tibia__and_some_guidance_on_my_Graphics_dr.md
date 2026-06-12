---
title: "Another Tibia ? and some guidance on my Graphics driver?"
date: 2008-11-02
forum: Gaming &amp; Leisure
---

### Post by Chinasgotrice on 2008-11-02
Hi folks I'm Alex and I am super new to Ubuntu.

I installed Tibia the game following instructions posted here
[http://gaming.gwos.org/doku.php/guides:32bit:tibia#tibia]("http://gaming.gwos.org/doku.php/guides:32bit:tibia#tibia")

Only exception is instead of "tar zxfv tibia800.tgz"
I used "tar zxfv tibia831.tgz" 
(Update of course)

I also have it install via Wine.

The client doesn't work in neither of them. In the link The first thing it said was make sure your graphics card driver is up to date. So I went on a search rampage and tried some commands/terminal things
(All new to me btw, I failed in High School C++ class)
And now I am lost in some translation. I think I was trying to update the driver and ended up rolling back or something odd.

If someone could hold my hand and walk me through this, I would be jammin':guitar:

Btw, when I run it with wine typing
> cd ~/.wine/drive_c/Program\ Files/Tibia
wine Tibia.exe engine 0
(or any other engine number. 1 or 3)
I get this load:
....x356 of disabling OpenGL line....
>  
!
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:ddraw:IDirectDrawImpl_QueryInterface (0x134840) The App is requesting a D3D device, but a non-OpenGL surface type was choosen. Prepare for trouble!
err:ddraw:IDirectDrawImpl_QueryInterface  (0x134840) You may want to contact wine-devel for help
err:ddraw:IDirectDrawSurfaceImpl_QueryInterface No interface
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
^Cfixme:d3d:IWineD3DDeviceImpl_Release (0x134de8) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x135c40 with type 1,WINED3DRTYPE_SURFACE

And this pop-up

> 
Video surface allocation failed. (Error Code 13)

Please choose another video graphics mode.

And it use to not say that before I started tinkering with the graphics driver. yeeks
and just fyi I searched a shitton! haha I just had to throw it in there to save my own hiney. :)

Thanks guys!

btw..The guy with shades isn't suppose to be in the quote hahah!

---

### Post by Chinasgotrice on 2008-11-02
O stoopid me Forgot to mention.
I have the Intel Mobile X3100. and I am running Ubuntu 8.10

---

### Post by Chinasgotrice on 2008-11-02
Bump... 8)

---

### Post by Chinasgotrice on 2008-11-03
BumpY! 
Okay maybe I am not getting help cause...
1 No one knows?
2 "its just that stoopid guy asking about tibia again..he should search"
3 This place shucks!

anways its fine if tibia doesnt work...i can manage...:( haha
but when I turn on my my laptop in the morning and it does its bios check thing whatever I do get a "fail" around the nvidia part. I think something I did with the tinkering messed it up. Everything else runs fine though.
Any input?

---

### Post by HittingSmoke on 2008-11-03
> **Chinasgotrice said:**
> BumpY! 
Okay maybe I am not getting help cause...
1 No one knows?
2 "its just that stoopid guy asking about tibia again..he should search"
3 This place shucks!

anways its fine if tibia doesnt work...i can manage...:( haha
but when I turn on my my laptop in the morning and it does its bios check thing whatever I do get a "fail" around the nvidia part. I think something I did with the tinkering messed it up. Everything else runs fine though.
Any input?

1. WINE questions arent supposed to be posted here
2. You should post a new thread for unique problems
3. What is the "Nvidia part"? A standard BIOS post checks the CPU, RAM and HDD connection. Be more specific
4. If you have Intel integrated graphics you shouldn't have an Nvidia anything

---

### Post by Chinasgotrice on 2008-11-04
Okay I know I'm new Mr.
but...

1. I'm trying to work the Linux Native version of Tibia. I posted that in my first post of the thread.
2. The title  of this thread is labeled Tibia and guidance on my Graphics driver. Doesn't that knock out two birds with a one stone?
3. At startup with the black screen and it runs the checks...theres a part it mentions something about Nvidia, and in Bright Red Blood colors says [FAIL] just like this thread...
Ill try to recall what exactly it says later but it shows up for a moment then continues to boot the laptop.
4.I HAVE no idea....I'm just as lost as pedophile in Disney land, maybe someone could point me to the little kid with the ice cream, and I'll try do the rest of the dirty work ;)

My computer is running the Intel x3100 and I've been trying to update the driver but I have no idea where to start.

Thanks for the criticism, I'll try to correct myself as I learn

But so far I haven't really gotten help...and I don't know why? I don't even know what was the reasoning to switching to Ubuntu anymore. :(

---

### Post by HittingSmoke on 2008-11-06
Well without the specific error I cant help. Maybe take a gander at your BOIS settings to see if anything is out of place.

---

### Post by Ferrat on 2008-11-06
Do you have a 64bit version of Ubuntu? 

post output of 
```

glxinfo | grep "render"

```

nvidia doesn't only make graphic cards but a lot of other stuff.

---

### Post by HittingSmoke on 2008-11-06
> **Ferrat said:**
> Do you have a 64bit version of Ubuntu? 

post output of 
```

glxinfo | grep "render"

```

nvidia doesn't only make graphic cards but a lot of other stuff.

Graphics chip or chipset, neither of which I've ever seen produce a POST error.

---


---
title: "Unreal Tournament 2004 only blob shadows"
date: 2007-08-17
forum: Gaming &amp; Leisure
---

### Post by quadomatic on 2007-08-17
For some reason, Unreal Tournament 2004 options only allow me to select shadows up to Blob shadows. Is there a way to turn up shadows further?

---

### Post by cjl2301 on 2007-08-17
All I can tell you is that's the only option (other than none) that I have ever seen when running the linux vesion.

Perhaps you could try altering the config (.ini?) files directly, but I'm guessing the dev's did that on purpose.

---

### Post by Lathilde on 2008-11-25
**Full, dynamic shadows are available for UT2004 for Linux!** Icculus seemingly made a mistake in the latest patch (3369.2) for UT2004, in both the Linux and Mac versions. Follow these instructions for full shadows and note, you'll need that patch (3369.2) for this:


First of all, ensure that UT2004 isn't running.

Go to the .ut2004 directory in Home, by opening the file manager and pressing Ctrl + H. .ut2004 will appear. Then navigate to the System directory.

Edit the UT2004.ini file - in the [OpenGLDrv.OpenGLRenderDevice] section, ensure that 'UseRenderTargets=True'.

Then edit the User.ini file - in the [UnrealGame.UnrealPawn] section, ensure that 'bPlayerShadows=True' and 'bBlobShadow=False'; and ensure that in the [Engine.Vehicle] section, 'bVehicleShadows=True'.

With these changes, you can now run UT2004. Edit any of the in-game settings as you wish, however, and this is quite important, **DO NOT** edit the Shadow settings. You'll see that it is a menu list with nothing in it, where it would say 'None, Blob', originally. Just leave it as it is - empty. Then run your favourite map, press F4 for third-person view.... 

Et voila! Full shadows are now yours! People, cars and even Static Meshes all cast shadows!

_EDIT:_
Find a screenshot below presenting full dynamic shadows in UT2004 for Linux! Also, according to the Linux Questions wiki, the UT2004 client for Linux is incapable of 'rendering-to-texture', leaving car license plates, among other (more important) things, un-rendered and blank. Well, not if you set UseRenderTargets to True, as above - see below! Enjoy.

[IMG]http://i77.photobucket.com/albums/j61/karma_pill/dynshadow.png[/IMG]

[IMG]http://i77.photobucket.com/albums/j61/karma_pill/licenseplate.png[/IMG]

Furthermore, for extra quality in OpenGL rendering, assuming your computer is capable of handling it, edit these settings in the aforementioned UT2004.ini file:

[Engine.Engine]
DetectedVideoMemory=(Number in MB, usually set to 0 by default)

[Engine.GameEngine]
CacheSizeMegs=(Number in MB, usually set to 64. Set higher for better performance)

[OpenGLDrv.OpenGLRenderDevice]
UseVSync=True   (Set False by default. 'True' provides a more consistent framerate.)
UseVBO=True     (Gives access to the OpenGL [VBO]("http://www.songho.ca/opengl/gl_vbo.html"). Set True for performance gain.)
UseVSync=True   (This appears twice in the settings, for some reason. Set this to True as well.)
UsePixelShaders=True    (Set to False by default. Gives access to, well, pixel shaders.)

---

### Post by jhansonxi on 2009-03-25
Setting UseVBO=True may have the opposite effect depending on hardware.  On a 3.2GHz P4 system with an 875P chipset and an AGP HD2600 (ATI) running Jaunty Alpha 6 it slowed it down to a crawl.

---


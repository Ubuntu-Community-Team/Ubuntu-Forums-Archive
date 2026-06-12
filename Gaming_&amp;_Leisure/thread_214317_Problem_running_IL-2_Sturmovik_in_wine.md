---
title: "Problem running IL-2 Sturmovik in wine"
date: 2006-07-12
forum: Gaming &amp; Leisure
---

### Post by Towncivilian on 2006-07-12
Hello.

I'm trying to get IL-2 Sturmovik (first one) to run under Wine.

I've installed Wine 0.9.16 using [this](http://www.ubuntuforums.org/showthread.php?t=185557&) howto, and 8762 NVIDIA drivers using [this](http://www.ubuntuforums.org/showthread.php?t=139264) howto.

I'm running under Ubuntu 6.06 AMD64.

glxgears shows all three gears.

When I type wine il2, it retorts back: Error in mount sfs file.

I did not actually install IL2, but it is not neccessary to install to get it to run (at least in Winblowze).

Being new to Linux and wine, I'm kind of stumped.

Thanks.

EDIT: I just noticed that IL-2 uses sfs files, perhaps it's not related to wine but something else.

How would I go about installing IL-2 in wine?

EDIT2: I can't set a drive C:\. If I make a windows and windows/system32 in my FAT32 partition and say that's where drive C:\ is, it can't access it. What am I doing wrong?

---

### Post by xenomorph99 on 2006-08-01
Hi,

You still checking this? If so, I'll reply in detail.

Ta,
Xeno

---

### Post by Scrappy_D on 2006-08-17
Hi,

I have no problem getting IL2fb.exe to run in wine, but I do have a problem with the mouse not working. I dont know if this is a wine, ubuntu, or java issue (as I believe the il2 frontend is java) ... Ubuntu lists the mouse as a generic input device, the wine errors I get when loading il2 are:

fixme:dinput:SysMouseAImpl_SetProperty Unknown type 0x9 (<guid-0x0009>)
fixme:dinput:SysMouseAImpl_SetProperty Unknown type 0x9 (<guid-0x0009>)
fixme:dinput:SysMouseAImpl_SetProperty Unknown type 0x9 (<guid-0x0009>)
fixme:dinput:IDirectInputDevice7AImpl_EnumEffectsInFile (0xc3aeea8)->(z:\games\il2\ForceFeedback\punch.ffe,0x122b4a0,0x33fae8,00000010): stub !
fixme:dinput:IDirectInputDevice7AImpl_EnumEffectsInFile (0xc3aeea8)->(z:\games\il2\ForceFeedback\shake.ffe,0x122b4a0,0x33fae8,00000010): stub !
fixme:dinput:IDirectInputDevice7AImpl_EnumEffectsInFile (0xc3aeea8)->(z:\games\il2\ForceFeedback\spring.ffe,0x122b4a0,0x33fae8,00000010): stub !
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored

And when I quit the main il2 screen we get this error:
err:dinput:SysMouseAImpl_Unacquire this(0xb660a60) != current_lock((nil))

Before I start hacking things to death does anyone have a clue on how to fix this?

Cheers in advance.

---

### Post by Saubazi on 2006-09-25
I am trying to get il2fb to run under 64bit ubuntu 6.06 so far no luck. However, I have now read several success reports so I'd appreciate if anyone can help...

I have read that OpenGL has a better chance of succeeding - well this is what I get:

/c/Games/IL-2 Sturmovik Forgotten Battles$ wine il2fb.exe
err:ole:CoGetClassObject class {25e609e4-b259-11cf-bfc7-444553540000} not registered
err:ole:CoGetClassObject no class object {25e609e4-b259-11cf-bfc7-444553540000} could be created for context 0x1
err:dinput:DirectInput8Create CoCreateInstance failed with hr = -2147221164; Try running wineprefixcreate to fix it.
RTS Version 2.1
Core Version 2.0
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored
OpenGL provider: Opengl32.dll
err:wgl:X11DRV_ChoosePixelFormat glXChooseFBConfig returns NULL (glError: 0)
Main begin: ChoosePixelFormat failed
com.maddox.opengl.GLContextException: ChoosePixelFormat failed
        at com.maddox.opengl.GLContext.CreateWin32(Native Method)
        at com.maddox.opengl.GLContext.createWin32(GLContext.java:130)
        at com.maddox.il2.engine.Config.createGlContext(Config.java:530)
        at com.maddox.il2.engine.Config.createGlContext(Config.java:553)
        at com.maddox.il2.game.Main3D.beginApp(Main3D.java:351)
        at com.maddox.il2.game.MainWin3D.beginApp(MainWin3D.java:212)
        at com.maddox.il2.game.Main.exec(Main.java:306)
        at com.maddox.il2.game.GameWin3D.main(GameWin3D.java:235)
Main end: null
java.lang.NullPointerException
        at com.maddox.il2.game.Main3D.viewSet_Get(Main3D.java:788)
        at com.maddox.il2.game.Main3D.viewSet_Save(Main3D.java:778)
        at com.maddox.il2.game.MainWin3D.endApp(MainWin3D.java:167)
        at com.maddox.il2.game.Main.exec(Main.java:335)
        at com.maddox.il2.game.GameWin3D.main(GameWin3D.java:235)

So obviously something is wrong with Java? il2setup.exe runs and if I change to directx I get a messy window but it seems to be running a bit further...hmmm

---

### Post by Saubazi on 2006-09-26
I need to find a self-help-group :) Well two secs of chat on winehq channel - took wine version 0.9.20 and voila. It runs - winXP, landscape to Excellent from Perfect. Sounds to emulated I think and graphics hardware...

---


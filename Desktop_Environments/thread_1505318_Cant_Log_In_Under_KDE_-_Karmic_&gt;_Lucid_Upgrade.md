---
title: "Cant Log In Under KDE - Karmic &gt; Lucid Upgrade"
date: 2010-06-09
forum: Desktop Environments
---

### Post by Kat of Zion on 2010-06-09
Well, I upgraded to Lucid from Karmic.  Im now using gnome but would like to get back to KDE.  Sadly it seems that even with kdm and plasma-desktop packages installed, I run into a problem at login.

If I choose from the downwards facing arrow on the botttom left of the screen, and pick "KDE".  Then when I log in, it shows the first icon (a hard disk), goes black and plunks me back on the login screen.

This is a Karmic>Lucid upgrade process and I wonder if something got borked in the process.  The simple solution of uninstall-reinstall did not fix the problem.

---

### Post by Kat of Zion on 2010-06-09
Update:

Looks like this has happened to my partner's computer.  In his case, he didnt do an upgrade. He did a full install (i.e. from scratch).  In his case, he installed 64 bit whereas I have been using 32 bit.  It seems that he has the same exact end result with trying to log in under KDE, getting the black screen for a few seconds, before getting dumped back to KDE.  

So yeah, he is installing the GNOME packages so he can at least use his computer for now.  Him and I cant really complain about GNOME's aesthetics but we would like to get KDE working all the same.

---

### Post by Kat of Zion on 2010-06-09
Looks like some packages for KDE did not install in tandem to the main KDE packages.  I now have installed kde-full and kdebase. It has not fixed my problem but I am a bit farther.  Now upon attempted KDE login, I get the hard drive icon as well as almost getting the second one next to it.  However, it still blacks out and takes me back to the login prompt. :/

---

### Post by Kat of Zion on 2010-06-17
This problem still exists for me. With Lucid being out a bit longer now, can anyone advise me on what might be the problem.  Is there a way I can enact KDE through command line for better debugging?

Of the things I did try, I looked at this older thread to see if it had a clue:
[http://ubuntuforums.org/showthread.php?t=984019&highlight=black+screen+start+KDE+session](http://ubuntuforums.org/showthread.php?t=984019&highlight=black+screen+start+KDE+session)

I tried both of those changes and it did not yield me results.  Here is what the /home/username/.kde/share/config/kwinrc file had in it.  Note that I am running a Nvidia GTX 260M for my video card

```
[$Version]
update_info=kwin.upd:kde3.0r1,kwin.upd:kde3.2Xinerama,kwin_on_off.upd:kwin_on_off,kwin_focus1.upd:kwin_focus1,kwin3_plugin.upd:kde3.2,kwin_focus2.upd:kwin_focus2

[Compositing]
AnimationSpeed=3
Backend=OpenGL
DisableChecks=false
Enabled=false
GLDirect=true
GLMode=TFP
GLTextureFilter=1
GLVSync=true
HiddenPreviews=5
XRenderSmoothScale=false

[Desktops]
Name_1=
Name_2=
Name_3=
Name_4=
Number=4

[Effect-Cube]
BorderActivate=9
BorderActivateCylinder=9
BorderActivateSphere=9

[Effect-DesktopGrid]
BorderActivate=9

[Effect-MagicLamp]
AnimationDuration=0

[Effect-PresentWindows]
BorderActivate=9
BorderActivateAll=7
TabBox=false

[ElectricBorders]
Bottom=None
BottomLeft=None
BottomRight=None
Left=None
Right=None
Top=None
TopLeft=None
TopRight=None

[Plugins]
kwin4_effect_boxswitchEnabled=false
kwin4_effect_coverswitchEnabled=false
kwin4_effect_cubeEnabled=false
kwin4_effect_cubeslideEnabled=false
kwin4_effect_desktopgridEnabled=true
kwin4_effect_dialogparentEnabled=true
kwin4_effect_diminactiveEnabled=false
kwin4_effect_dimscreenEnabled=false
kwin4_effect_explosionEnabled=false
kwin4_effect_fadeEnabled=true
kwin4_effect_fadedesktopEnabled=false
kwin4_effect_fallapartEnabled=false
kwin4_effect_flipswitchEnabled=false
kwin4_effect_highlightwindowEnabled=false
kwin4_effect_invertEnabled=false
kwin4_effect_loginEnabled=true
kwin4_effect_logoutEnabled=true
kwin4_effect_lookingglassEnabled=false
kwin4_effect_magiclampEnabled=true
kwin4_effect_magnifierEnabled=false
kwin4_effect_minimizeanimationEnabled=true
kwin4_effect_mousemarkEnabled=false
kwin4_effect_presentwindowsEnabled=true
kwin4_effect_scaleinEnabled=false
kwin4_effect_shadowEnabled=true
kwin4_effect_sharpenEnabled=false
kwin4_effect_sheetEnabled=false
kwin4_effect_showfpsEnabled=false
kwin4_effect_showpaintEnabled=false
kwin4_effect_slideEnabled=true
kwin4_effect_slidebackEnabled=false
kwin4_effect_snaphelperEnabled=false
kwin4_effect_snowEnabled=false
kwin4_effect_taskbarthumbnailEnabled=true
kwin4_effect_thumbnailasideEnabled=false
kwin4_effect_trackmouseEnabled=false
kwin4_effect_translucencyEnabled=true
kwin4_effect_wobblywindowsEnabled=false
kwin4_effect_zoomEnabled=true

[TabBox]
ListMode=0
ShowTabBox=true

[Windows]
BorderSnapZone=10
CenterSnapZone=0
ElectricBorderCooldown=350
ElectricBorderDelay=150
ElectricBorders=1
GeometryTip=true
MoveMode=Opaque
MoveResizeMaximizedWindows=false
ResizeMode=Opaque
SnapOnlyWhenOverlapping=false
WindowSnapZone=10

```

---

### Post by Kat of Zion on 2010-06-17
Okay...not so smooth upgrade from Karmic, to Lucid

Looks like I just had to follow this thread over at Kubuntu forums to fix my problem.  This will teach me to give it a matter of a few days/weeks from a new distro before I start worrying about my problem not being solvable. :lolflag:

[http://kubuntuforums.net/forums/index.php?topic=3111391.msg227515#msg227515](http://kubuntuforums.net/forums/index.php?topic=3111391.msg227515#msg227515)

---


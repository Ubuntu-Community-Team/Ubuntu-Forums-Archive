---
title: "Maya 2008 + Kubuntu / KDE 4.1 ?"
date: 2008-10-20
forum: Desktop Environments
---

### Post by skullmunky on 2008-10-20
Usually I post a topic like this because I'm having crashes or problems.  This time it's the opposite - I CAN'T produce any crashes.  As every 3D artist learns on their mother's knee, you have to disable the composite extension and desktop effects to use Maya, otherwise there are severe crashes caused by focus problems with the hotbox menu, among other things.

Just for kicks I tried it out in KDE 4.1 with all the eye candy enabled, and I can't make it crash anymore !!!!  My world has become very uncertain.  Can anyone else verify this?

EDIT: ok, phew, I knew I could find something weird if I tried hard enough.  You can get tearing in the UI by scrolling up and down e.g. in the attribute editor.  Also if you try to resize panes the whole screen goes black and you just get a thin red line to show you what you're resizing.  That's a nice new one.

---

### Post by slegrand on 2009-04-23
Hey mate. Have you ever gotten Maya to crash when middle click dragndropping in the hypershade?
With KDE 3.5 I can't seem to find a fix, is it working with kde 4?

---

### Post by GrinKestrel on 2009-04-23
Have you had any problems with pan and tilt? I've noticed some odd problems that I can't seem to resolve. I checked a few places and found ways to fix it, but apparently the previous version of Ubuntu that I used (7.10) doesn't seem to have the option that needs to be changed. Anywhere.

Sorry for the odd post, I'm at work and in a hurry.

---

### Post by inobe on 2009-04-23
> **skullmunky said:**
> Usually I post a topic like this because I'm having crashes or problems.  This time it's the opposite - I CAN'T produce any crashes.  As every 3D artist learns on their mother's knee, you have to disable the composite extension and desktop effects to use Maya, otherwise there are severe crashes caused by focus problems with the hotbox menu, among other things.

Just for kicks I tried it out in KDE 4.1 with all the eye candy enabled, and I can't make it crash anymore !!!!  My world has become very uncertain.  Can anyone else verify this?

EDIT: ok, phew, I knew I could find something weird if I tried hard enough.  You can get tearing in the UI by scrolling up and down e.g. in the attribute editor.  Also if you try to resize panes the whole screen goes black and you just get a thin red line to show you what you're resizing.  That's a nice new one.

kde 4.1 is about the buggiest of kde's, i suggest upgrading to kde4.2 if you are running intrepid or later...

[http://ubuntuforums.org/showpost.php?p=7123834&postcount=3](http://ubuntuforums.org/showpost.php?p=7123834&postcount=3)

---

### Post by skullmunky on 2009-04-25
hey folks,

Yes, 4.2 is SO much better :)

MMB-drag in Hypershade: 

ah, yes, I'm familiar with that one.  Does it freeze up completely when you MMB-drop?  Try Alt-Tab, to switch focus to another window, and then Alt-Tab back.  That used to work for me.  

If you're having this problem, it may be from the nvidia drivers - it's probably not related to KDE.

check which version you have, see if it's the latest or not, and see if you can upgrade them.  There was one version of the nvidia driver that actually caused this bug for a while.  Search on the nvidia linux forum, too, I have a thread there from a year or two ago about this.

Pan/Tilt: what kind of problem?  If the problem is that when you try and pan or tilt, you instead move the whole stupid window around, it's because ALT+drag is a window movement command in almost every Linux window manager.

In KDE3, turn it off by going to System Settings->Window Behavior->Window Actions Tab.  In the "Inner Window..." panel, change "Modifier Key" from "Alt" to "Meta".  Then you get Alt key back for Maya, and can use the Meta/Windows key to drag windows around.  

If you want to disable this behavior completely, change the other menus to "None" for the action.  

In the version of Gnome that comes with 7.04 I have no idea where you turn this off, which is one reason I started using KDE.

---

### Post by andrea000 on 2009-04-25
> **inobe said:**
> kde 4.1 is about the buggiest of kde's, i suggest upgrading to kde4.2 if you are running intrepid or later...

[http://ubuntuforums.org/showpost.php?p=7123834&postcount=3](http://ubuntuforums.org/showpost.php?p=7123834&postcount=3)

just a quick question are you talking about autodesk maya
and if so i didn't know that autodesk made linux software
do they make autocad as well that would solve my problems.

---

### Post by skullmunky on 2009-04-27
Yes, Autodesk Maya (aka Alias Maya, aka Alias|Wavefront Maya, etc...)

Maya's been on linux for a very long time, perhaps since the beginning.  I think I started with 3.5 or 4.0 on RedHat 6 or 7.  Maya's main target platform back in the day was IRIX, so Linux was an obvious move, and is part of the reason why a lot of big studios use Linux.  

The only thing that's tough with Maya on Ubuntu is that the maya devs tend to build for a more conservative linux flavor; their qualified OS's are usually slightly older, stable versions of RHEL and SuSE.  Ubuntu moves so fast that you'll sometimes have to do some fiddling around because Maya isn't keeping pace with the kernel, C++ libraries, and graphics drivers.  But I have no real complaints except that the Motif file browser is ancient and decrepit.

Some people are annoyed that there's no ability to batch render to an AVI or Quicktime, but on the other hand I always like to keep all my frames anyway.  

No such luck for AutoCAD, sadly.  Autodesk chose Windows as their platform early on, hence AutoCAD and 3DSMax are Windows.  They have all those Linux compositing/editing/FX products, but I think those are ones they got by buying other companies.

And now that they bought SoftImage they have an almost complete monopoly on 3D software, except for Blender.

---

### Post by indigo42 on 2009-08-18
I have trouble with middle mouse useage in the Workarea of hypershade. Nothing I do will unlock the display, not alt-tab (yes I let Maya have ALT), not even incesant cursing.

I'm on Jaunty using KDE 4.3. I have the newest NVIDIA driver for my 9500GT. But it just started doning it. It may have something to do with some plasma stuff I set up. I also am getting an error when closing Maya from time to time complaining about how it cannot find a window decorator and Xgl.

And...here's some Maya nostalgia...

Maya first came out around 1998 and it was on SGI Irix only. It was a synthesis of 3 the platforms Silicon Graphics purchased. Nobody but SGI had the boxes to run it back then.[INDENT]Modeling => Alias PowerAnimator/Studio
Mel and Particles => Wavefront Dynamation (used Sophia, a C like language that evolved into MEL)
IK animation => Wavefront Kinemation
Rendering, IPR, and Shaders => TDI Explore

[/INDENT]I wish they would have kept Composer. I still can't find a compositor that was as flexible and easy to use as that was.
TDI Explore shader editor was better then what we have in Maya. The Work area comes close.TDI looked like a NEAT and ORDERLY circuit  board when you were done. Details areas were easily collapsed into nodes.
TDI has this really cool plant generator called AMAP. You had a lib of hundreds of plants it would build for you based on inputs. Made some v

 I think the Winblows and Linux versions didn't come out till after SGI sold off Alias Wavefront to Autodesk.

---

### Post by skullmunky on 2009-08-21
@indigo42, make sure you have desktop effects turned off.  Having any compositing window manager (KWin 4 with desktop effects, or Compiz) running will lead to total hard freezes either with MMB in hypershade or with the r-click quadrant menus from the hotbox, probably other things as well.

Mmmm .. maya nostalgia ... I still have an O2 with Maya 4 on it ... the first version for Linux I used was also 4, or maybe 4.5, though I think that was when they were still Alias|Wavefront ...

---

### Post by indigo42 on 2009-08-21
@skullmunky

Thanks! I'll give that a whirl. I've been using gnome all this time up til now. I really am starting to like KDE.

I loved the O2! The Little Toaster That Could! Just curious, how does it stack up to today's stuff?

---

### Post by indigo42 on 2009-08-27
Here is a neat plasmoid that lets you suspend compositing. So far so good. I'll post if it craps out.

[http://www.kde-look.org/content/show.php/Toggle-Compositing?content=78299](http://www.kde-look.org/content/show.php/Toggle-Compositing?content=78299)

It only works for KWin though.

---

### Post by krazyd on 2009-08-27
<Alt>+<Shift>+<f12> also works.

---

### Post by simonyee on 2009-09-06
> **skullmunky said:**
> Usually I post a topic like this because I'm having crashes or problems.  This time it's the opposite - I CAN'T produce any crashes.  As every 3D artist learns on their mother's knee, you have to disable the composite extension and desktop effects to use Maya, otherwise there are severe crashes caused by focus problems with the hotbox menu, among other things.

Just for kicks I tried it out in KDE 4.1 with all the eye candy enabled, and I can't make it crash anymore !!!!  My world has become very uncertain.  Can anyone else verify this?

EDIT: ok, phew, I knew I could find something weird if I tried hard enough.  You can get tearing in the UI by scrolling up and down e.g. in the attribute editor.  Also if you try to resize panes the whole screen goes black and you just get a thin red line to show you what you're resizing.  That's a nice new one.

Cant you use Blender ?

---

### Post by indigo42 on 2009-09-06
@Simonyee,
There are plenty of other venues to compare Blender to Maya. I doubt anyone reading this thread will just say.."Oh wow! Why didn't I think of completly ditching Maya and start all over with a new product!" Let's stick to the subject at hand.

On that note...I have been very happy with the lack of crashes using KWin with the compositing turned off. I see KDE 4.3 stuff is out. I'm tempted to upgrade as I still get a few odd 'sticky spots' in Maya.

I'll post if I do.

---


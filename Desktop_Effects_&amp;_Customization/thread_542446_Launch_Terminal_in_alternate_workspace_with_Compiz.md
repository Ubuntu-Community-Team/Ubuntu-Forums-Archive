---
title: "Launch Terminal in alternate workspace with Compiz"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by Bogus83 on 2007-09-03
Hi all,

I'm running Feisty with an NVIDIA 5200, 1.5Gig of RAM, Athlon 2400, Compiz Fusion using Emerald.

I followed these directions to get a terminal "embedded" in the desktop:

[http://ubuntuforums.org/showthread.php?p=3287347]("http://ubuntuforums.org/showthread.php?p=3287347")

It worked perfectly, no problems.

Now what I'd like to do is make it so that when the Terminal launches, it loads in the fourth workspace/desktop I have.  I'm a little confused on how to make that happen.  I've added an entry to the "Viewports" section in Place Windows to have "title=trans1" and the name of the terminal profile I'm launching is "trans1".  I'm using "gnome-terminal --window-with-profile=trans1" to launch it.

When the Window Position is 0,0, it does not launch at all.  When it is anything else (1,0 or 5000,0) the terminal launches, positioned as close to correctly as possible without allowing it to extend to the next workspace.  

When the Viewport position is 0,0, the terminal is visible on ALL workspaces.  When the X value is negative, it also appears on all workstations.  When the X value is positive, or the Y value is ANYTHING other than 0, it does not launch at all.

In the General settings for CCSM I have:

Horizontal Virtual Size  = 4
Vertical Virtual Size = 1
Number of Desktops = 1

Any ideas on what's going on?  Despite having one super-wide "desk", I can still click on four seperate sections as if they were seperate workspaces.  I've tried setting the "number of desktops" to 4, which does give me four distinct sections in the taskbar, but the terminal still behaves the same way.

---

### Post by Inxsible on 2007-09-04
The link given in this [thread]("http://ubuntuforums.org/showthread.php?t=542404"), explains how you can create Window rules in Compiz Fusion to achieve what you want.

---

### Post by Bogus83 on 2007-09-04
Thanks for that link.  It was very informative and will come in handy, but unfortunately it doesn't address the specific problem that I'm having.  If you look at my post above, I have defined window rules for a Terminal with "trans1" in the title.  I don't want it to appear on all faces of the desktop cube, I would like it to launch always on the fourth face.  I'm having difficulty with the "Viewport" settings (under the Placement section).  As I'd mentioned, if I set the x,y coordinates for that window to 0,0, it appears on all faces of the cube.  Removing the window rule from Sticky corrected this, but if I change the coordinates to anything else, when I launch the Terminal it doesn't launch at all.  It would stand to reason that 4, 0 would be the fourth viewport or "desk page"... but it doesn't appear to work that way.

---

### Post by Bogus83 on 2007-09-04
Should have figured it was something right under my nose all along.  If you're going to create a window that Skips the Taskbar, you probably shouldn't "Hide Skip Taskbar Windows" (in the General settings of CCSM).

That being unchecked allows me to launch the terminal on the fourth "Viewport" (which I now understand to be "where the fourth desk area WOULD be, if Compiz didn't create one super-wide area for all desks").  Here's my latest problem.

When Compiz loads before the terminal, and then the terminal is launched, it launches on the correct viewport, but looks like this:

[http://ubuntuforums.org/attachment.php?attachmentid=42583&stc=1&d=1188942923]("http://ubuntuforums.org/attachment.php?attachmentid=42583&stc=1&d=1188942923")

When I launch the terminal FIRST, and then launch Compiz, it stays on the first viewport, but renders correctly, like this:

[http://ubuntuforums.org/attachment.php?attachmentid=42584&stc=1&d=1188942970]("http://ubuntuforums.org/attachment.php?attachmentid=42584&stc=1&d=1188942970")

My dilemma is that since Compiz essentially recreates the "viewport/desk" area when it runs with one long workspace, there is no way to launch the terminal in the correct viewport before it runs.  If anyone can figure out why the terminal launches with incomplete rendering that'd be awesome, and would solve the last piece of my puzzle.  Ideas?

---


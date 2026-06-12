---
title: "OpenGL Does Not Have Window Frame"
date: 2008-08-30
forum: Desktop Environments
---

### Post by kuloch on 2008-08-30
I just compiled the example1.c from [an old '98 article]("http://www.linuxfocus.org/English/March1998/article29.html") (which took realizing that Ubuntu hadn't created the libXmu.so and libXi.so symlinks - *after* posting a question on linuxquestions.org), but neither it nor some other simple GL/GLUT programs have any sort of frame.  I would specifically like a title bar and close button.

The [screenshot]("http://www.linuxfocus.org/common/March1998/glut1.jpg") (which looks like it's just the X window environment) shows a title var and minimize/close buttons.  Mine displays all of the inner-window contents, but none of the window frame.  So I can't move it around, and I have to close it by right-clicking the taskbar item and selecting close.

Is this due to everything having been written for X while I'm using Gnome?  Can I rewrite or add anything to make it display the Gnome windowing stuff?

---

### Post by kuloch on 2008-08-31
Playing around with it a bit more, I've found that there *is* a window frame - it's just invisible.  I can resize (although it's pretty clunky) and close (by guessing where the close button is).  Moving the window (via grabbing the invisible title bar) also works, but I have to minimize and restore the window via the taskbar to get it to redraw the OpenGL contents.

Also, when I load any of the example programs (I have 8), sometimes other windows sitting behind will have their frames (with some padding) blank out the window displaying the OpenGL content.  Minimizing and closing tend to leave the OpenGL contents still painted on the screen, until I move something around to repaint the area.  If I maximize and then unmaximize, then the entire screen (aside from Ubuntu's top and bottom bars) will keep the OpenGL contents painted, but with the smaller-sized OpenGL contents painted on top.

I'm running freeglut 2.4.0-6 on Ubuntu 8.04.1, and I'd really like to know why my system is so buggy with OpenGL.

---

### Post by ceti331 on 2008-08-31
I dont know exacly whats going on here but have observed similar:-
compiling opengl/???glut samples runs them in un-managed windows, they dont repaint their backgrounds when they're deleted.
This was under Fedora i think. Blender was also a bit screwy.

Conversely I found OpenSDL/openGL samples that compiled on my system (now ubuntu 8 ) run just fine in propper managed windows .. although its slow hence i suspect it maybe running in SOFTWARE ?
[http://www.codesampler.com/linuxsrc.htm]("http://www.codesampler.com/linuxsrc.htm")

i dont know exactly whats going on behind the scenes - i think it might be possible to create an application's own X window in such a way that it is NOT controlled by the WM.. (apps have to manually pass on hints to the WM?) so this could be down to very old sample code?

Personally I'm not using linux for serious 3D programming, just tinkering with open-source, but I would like to.

Whats the most elaborate open-source linux compilable GL based program? I've been unable to run GtkRadiant (compiled it but it wont find game-files & quits!)

I think i read that the REAL, original "Glut" isnt actually open-source, and subsequently some people wrote bits of emulators which were. As such it seemed OpenSDL was a better place to start.. more recent, more actively maintained.

Anyone got any experience of wxwidgets/gl ? does this do the same job as glut's window-manager interface? 
[http://www.wxwidgets.org/docs/tutorials/opengl.htm]("http://www.wxwidgets.org/docs/tutorials/opengl.htm")
looks like that would be a good framework for writing crossplatform 3d tools as opposed to games/demos.

---

### Post by kuloch on 2008-08-31
It looks like OpenSDL is an alternative to OpenGL.  I'd be game for giving OpenSDL a shot, but the class I'm taking uses OpenGL (with VisualC++, but I'm trying to avoid that one).

Is Blender a linux distro?  I don't believe I've heard of it, but I haven't read even a partial distro list for a few years.

Yes, the developer for GLUT stopped in '98.  freeGLUT (and perhaps others) was created due to his license, which allowed free distribution as long as no one modified his code.  I imagine that freeGLUT is reverse-engineered from GLUT, and its [API]("http://freeglut.sourceforge.net/docs/api.php") notes the differences from the original.

Back to my issue, my invisible frames do seem to be using the Gnome windowing system.  I just confirmed that clicking the upper-left-hand corner (just what looks like the corner) opens the menu with "minimize", "Always on top", "Close", etc.  Everything looks and acts like Gnome - except that it's invisible, and the OpenGL-drawn stuff is pretty screwy about when and where it'll display.

---

### Post by kuloch on 2008-09-02
It's hardly a fix, but it turns out that Xfce (which I think I prefer over Gnome) displays the window frames just fine, and all OpenGL content is kept properly within the window even if moved, minimized, or closed.

---


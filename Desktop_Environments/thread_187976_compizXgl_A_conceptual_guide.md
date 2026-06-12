---
title: "compiz/Xgl: A *conceptual* guide"
date: 2006-06-03
forum: Desktop Environments
---

### Post by cyrus7580 on 2006-06-03
Preface: Some of this is wrong. Notice I didn't say “probably wrong”. If you find errors or need to make clarifications or corrections, please do so. I'll edit the original post to reflect these changes.

Disclaimer: Although this is a top-level conceptual walkthrough, I refer to nvidia and gnome mostly because that's what I used. Sorry ATI and KDE users. This should still be helpful, though.

Most of us have seen the Compiz + Xgl demo video floating around on the internet. Most of us have seen the HOWTOs on this forum that simply state “execute this command” and “install this package” without bothering to explain WHY you're doing it or even WHAT you're doing. It seems to me that the assumption of expertise is always *way* too high in most chat rooms, forums and help documents. After many hours of frustration trying to follow 5 different hackish walkthroughs, I thought it would be helpful to have a *conceptual *walkthrough of the process so that you can understand what you're doing and better troubleshoot the issues as they arise.

First, the alphabet soup:

[LIST]
[*]X  or X server - The X Window System (commonly X11 or X) is a windowing system for bitmap displays. It is the standard toolkit and protocol to build graphical user interfaces on Unix 
[*]Xorg – The X.org open source implementation of X on most linux distros. 
[*]OpenGL - a low-level graphics library specification. OpenGL makes available to the programmer a small set of geometric primitives - points, lines, polygons, images, and bitmaps. OpenGL provides a set of commands that allow the specification of geometric objects in two or three dimensions, using the provided primitives, together with commands that control how these objects are rendered into the frame buffer.
[*]Xgl - “X running on OpenGL” or “GL-based X server” That is, Xgl is an X server architecture layered on top of OpenGL. Xgl can perform intricate graphical operations--such as rendering antialiased fonts--noticeably faster than other available Xservers that do not use OpenGL. The current implementation is Xglx but the future implementation of Xgl will be Xegl.
[*]glx - "OpenGL Extension to the X Window System" provides the glue connecting OpenGL and the X Window System: it enables programs wishing to use OpenGL to do so within a window provided by the X Window System. It consists of 3 parts – 
1.The extension of the X server allowing it (the X server) to render 3D images to a display
2.The extension of the X protocol to allow the client to send rendering commands to the server
3.API (Application Programming Interface) that allows an Xwindow application to execute OpenGL functions
[*]window manager - An X-Windows System program that determines how 'X' deals with your desktop (typically KDE or GNOME) and client windows. Kwin is the default window manager for KDE. Metacity is the default window manager for GNOME. compiz replaces Kwin or Metacity. (SEE FOOTNOTE 1)
[*]compiz – window manager + compositing manager (the thing that manages the combination of two or more images on the screen to create effects) to the Xorg project . Xgl must be used in combination with a compositor/window manager to expose all of its capabilities. Compiz is the compositor utility that was developed in conjunction with Xgl.
[*]DRI - Direct Rendering Infrastructure (DRI) is an interface used in the X Window System to securely allow user applications to access the video hardware without requiring data to be passed through the X Server. Its primary application is to provide hardware acceleration of the Mesa implementation of OpenGL. Nvidia owners will want to comment out the “dri” module in xorg.conf.
[*]Mesa - Mesa 3D is an open source graphics library that provides a generic OpenGL implementation for rendering three-dimensional graphics on multiple platforms.
[*]Gconf - a system used by the GNOME desktop environment for storing configuration settings for the desktop and applications.
[*]Gconf-editor - an application for gnome that gives users the ability to access settings stored in the XML-based GConf configuration database. This is where you configure compiz and add fancy stuff such as “zoom”, “wobbly”, and “cube”. (SEE FOOTNOTE 2)
[*]gdm - GDM is the GNOME Display Manager, a graphical login program. When you boot up your Ubuntu distro and see the big UBUNTU logo and a field asking for your login name, that's GDM. 
[*]gdm.conf-custom – the configuration file that lets you add new selections in order to load different window managers. Gdm.conf has a whole bunch of info in there. Gdm.conf-custom is not a replacement for gdm.conf. It is much smaller and contains information supplemental to gdm.conf.
[*]kdm – the K Desktop Environment Display Manager, a graphical login program.
xorg.conf – the xorg X Window System server configuration file. Contains info about screens (and their resolutions and color depths), input devices (keyboards, mice), monitors, graphics extension modules, fonts, etc. In Ubuntu, it is created with dexconf, the Debian X configuration tool but is already there, so recreating it usually isn't necessary. Nvidia provides a xorg.conf generation tool called nvidia-glx-config and also provides a tool for modifying xorg.conf called nvidia-xconfig. See the help info for those programs for more info.
[*]nv – the open source nVidia driver packaged with most linux distros
[*]nvidia – the proprietary – but better performing – nVidia driver you can get from nvidia.com
[/LIST]

The Process (no commands here, just the concepts):

Chances are, you've probably got a relatively clean Ubuntu distribution set to use GNOME and Metacity. You're trying to get Gnome to use the compiz window/compositing manager and all its cool effects built on the Xgl framework. 

The first step is to use a graphics griver that supports glx (so that Xgl can talk to OpenGL). That's what getting the proprietary nvidia module is all about. The nv module doesn't support it yet (or at least not well). (?) Switching to nvidia from nv involves changing the “nv” line of xorg.conf.

Try restarting X at this point to see if you're using the nvidia driver. An “nvidia” splash screen will appear as X loads and /sbin/lsmod will show the “nvidia” module loaded.

Next, you need to get X (Xgl) to use “glx” instead of the older “Glcore” module by editing xorg.conf. Nvidia users should also comment out “dri”.

Restart X again to make sure Xgl is running. None of the effects will work yet since we haven't done anything with compiz.

Now get compiz and edit gdm.conf-custom to start a gnome session using compiz instead of metacity as the window manager. This involves setting up a script to start compiz when gnome starts and changing gdm to execute this script. See a more detailed walkthrough for your hardware/software combinations for more info.

Restart X to make sure compiz is running.

Edit gconf with gconf-editor to insert all the fun stuff into the compiz area. Look under compiz, allscreens, pluigins. Once you click OK, the changes should be instant. If not, restart X.

Other walkthroughs can provide more detail for your graphics card/desktop environment/architecture combination. 


FOOTNOTE 1: One of the confusing things about at least one of the walkthroughs I've read was changing the GDM screen to give you options between “GNOME” and “Compiz”. The problem there is that Gnome is a desktop whereas compiz is a window-manager+compositing manager. The choices should instead be labeled “GNOME with Metacity” or “GNOME with compiz”. 

FOOTNOTE 2: One of the walkthroughs had some important information about this part the other walkthroughs failed to mention. The order in which you add the compiz features MATTERS. There are dependencies between them. Getting the order mixed up breaks these features.

---

### Post by nudicles on 2006-07-31
bookmarked. Great overview of a lot of basic linux info, that I would have never picked up otherwise. I agree, a lot of these "n00b" guides assume too much from the users. The first time I ever read "simply enter this command..." I thought, how do I enter text commands on my desktop? ;)

---

### Post by tacubuntuforums on 2007-06-27
Thanks! It is very clarifying...

I see that, among other, there are these two driver packages (i show part of the description):

**1) nvidia-glx**
[I]These XFree86 4.0 / Xorg binary drivers provide optimized hardware
 acceleration of  OpenGL applications via a direct-rendering X Server.....
Please see the nvidia-kernel-source package for building the kernel module
 required by this package....[/I]

** 2) xserver-xorg-video-nv**
[I] X.Org X server -- NV display driver
 This driver for the X.Org X server (see xserver-xorg for a further description)
 provides support for NVIDIA Riva, TNT, GeForce, and Quadro cards......
 Note that this is not the same as the binary-only 'nvidia' driver, which
 adds 3D support, but is binary-only and not supported.....[/I]
 
 I have installed the xserver-xorg-video-nv package. The other on seems to work with glx but also to be used with the previus Xfree86 Xserver.

[COLOR="Sienna"]Question:
As for today, is the proprietary nvidia driver still required or recommendable?
 
Also:
How do I know which drivers I'm using? (I suppose that looking to installed packages list is not the correct way and
my lsmod output doesn't display anything about video stuff).
Which is the correct way to change drivers.[/COLOR]

---


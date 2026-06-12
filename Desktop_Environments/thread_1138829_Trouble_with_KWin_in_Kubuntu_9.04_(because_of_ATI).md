---
title: "Trouble with KWin in Kubuntu 9.04 (because of ATI?)"
date: 2009-04-26
forum: Desktop Environments
---

### Post by arigram on 2009-04-26
I have been searching around the forums but is hard to track down a problem like this.

I am running Kubuntu 9.04, KDE for the first time after a few years with Ubuntu. Since the beginning I noticed some trouble, possibly a disagreement of KWin with my ATI 4850 card:

1) When enabling effects in the Desktop Settings the window decorations will get messed up, the screen will freeze and will go black. It may or may not stay black for a few seconds, then come back again to a frozen and slightly messed up desktop then back to black for usually more than a couple times. The pointer will remain movable.
2) Booting up, during the desktop initialization with the icons, the screen will flash black more than a dozen times.
3) Sometimes it will boot after the above sequence to a black screen with just the mouse pointer movable as mentioned before.
4) Resizing the windows is painfully slow yet other things are fine, such as window moving with solid contents (and wobble enabled).
5) Sometimes graphic artifacts may appear, either abstract or mirrored pieced from the desktop, always at the bottom fifth of the screen.

Is this a known compatibility issue or a bug, or is it just me?

---

### Post by inobe on 2009-04-26
it's always a "ati driver" issue.

i am not much help in that category' but if you search the the forum i am certain you will find issues with ati and compiz too.

i don't think it has anything to do with compiz or kwin.

example: [>>click<<]("http://ubuntuforums.org/search.php?searchid=58581692")

you may find a topic that will help, possibly someone that installed the latest ati driver.

that is what i would do !

goodluck

---

### Post by marco1986 on 2009-04-26
I also have huge problems with Kubuntu 9.04.

I was reluctant with upgrading from 8.10 to 9.04 because of my experience with newly released versions of *ubuntu.

Getting to my problem: Kubuntu after upgrading suddenly got slower. Every single program affects cpu usage very strongly. I have opened firefox (about 4 tabs) and konsole (with 4 terminals) and it runs worse then microsoft vista... When I open skype it also gets a huge kick to cpu usage. When I want to call someone with video enabled kwin crushes and restarts. It's impossible to use. I have a sony vaio notebook with intel gma video card. So I don't thing the horrible performance is caused by some video driver.

If there is anybody with similar problems, please let me know. Maybe we'll come up with some kind of cure for Kubuntu 9.04

---

### Post by inobe on 2009-04-26
marco check this [>>click<<]("http://ubuntuforums.org/showthread.php?t=1130582")

and this [>>click<<]("http://ubuntuforums.org/showthread.php?t=1136738")


those guides look very promising.

---

### Post by marco1986 on 2009-04-26
@inobe: thank you for a very fast reply. I'll look into those links.

It's very frustrating when watching youtube becomes a challenge...

---

### Post by arigram on 2009-04-26
Marco, I don't want to seem rude, but why you are posting on this thread that is about a completely different problem and not search for similar to yours or start a new thread?

And Inobe, thank you, but I don't see it as a general problem with ATI. For one thing, there is no confirmation that the trouble is indeed the specific graphics card, or it is any of the software components, such as the driver, KWin, KDE 4 or something else in Kubuntu. Secondly, I didn't have any problems (atleast of that degree) with the same card and Ubuntu (Gnome) 8.10 but I've had trouble with both Ubuntu and Kubuntu and an older NVidia card.
So, unless one knows or has a clue about the specific technical matters that would cause the graphics corruption, then any broad generalizations don't really help. After all, there could be others with the same problem and looking for help.

---

### Post by inobe on 2009-04-26
9.04 is an entirely different beast, newer kernel, newer xorg/ xserver, for each xorg release ati must release a newer compatible driver.

nvidia would need to do the same.

---

### Post by inobe on 2009-04-26
hi again arigram

just trying to help :)

give you an example, unrelated to ati but a graphics driver regardless of vendor.

i had these same issues with my nvidia card prior to nvidia 180.44 release.

here is what was fixed for 180.44

> # Fixed a problem that could cause Xid errors and display corruption in certain cases when OpenGL is used to render to redirected windows, for example when Java2D is used with the -Dsun.java2d.opengl=true option.
# Updated glGetStringi(GL_EXTENSIONS, i) to no longer return NULL in OpenGL 3.0 preview contexts.
**# Fixed OpenGL crashes while running KDE4's Plasma.**

[http://www.nvidia.com/object/linux_display_ia32_180.44.html](http://www.nvidia.com/object/linux_display_ia32_180.44.html)

after i updated it has been rock solid, my cube affect use to crash kwin.

i hope you find a way to fix the issue, i have noticed ati driver version 4.9 was released on 4/17/09.

---

### Post by marco1986 on 2009-04-26
this thread help me totally!
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

regards!

---

### Post by mkmk on 2009-12-12
I installed driver from ATI, but without success.
But there is some solution for my Kubuntu 9.10.
1. Install proprietary ATI drive.
2. Uninstall (/usr/share/ati/fglrx-uninstall.sh).
3. Install ATI drive with option --buildpkg Ubuntu/karmic
4. Check "aticonfig --initial" (and install xorg-driver-fglrx)
5. Check "aticonfig --initial" again
6. If still it is not OK then install ATI drive again but this time without --build.....  option
7. "aticonfig --initial" and it works, why, I do not know.

Best regards

---


---
title: "remapping alt+resize button in metacity?"
date: 2006-07-26
forum: Desktop Environments
---

### Post by numerodix on 2006-07-26
As you may know, in KDE, on a three button mouse, it's alt+right button. In metacity it's alt+middle button. That's very awkward if you have a wheel as the middle button, to press it in and drag the mouse. I want to use the right button on the mouse to resize windows, just like in kde. The question is how?

---

### Post by georgo on 2006-09-19
Hello,
this is exactly the question a have been asking myself (and around). No answers were given to me, so I decided to make a small research. As I studied the metacity's sourcecode and I found out that the button code for the resize action is hardcoded...
More in my post on [URL="http://gnomesupport.org/forums/viewtopic.php?t=11581"]
http://gnomesupport.org/forums/viewtopic.php?t=11581[/URL].
The idea is to have the ability to swap the functionality of the 3rd and 2nd button from "resize"/"window menu" to "window menu"/"resize".
If there is still someone interested in this feature (or has a better idea) please reply.

---

### Post by chavo on 2006-09-19
Back when I used Gnome I just downloaded the source code and fixed it myself. Along with a few other things like the hideous minimize animation. But I've since moved on to greener pastures, a place where you have options and choices.

---

### Post by georgo on 2006-09-19
Actually this is not about Gnome, but about the structure and design issues of metacity. Some time ago we could just configure our sawfish... I think if we can, we should give the chance, to change these settigs to everybody - I saw a lot of questions about this "feature".

---

### Post by chavo on 2006-09-19
> **georgo said:**
> Actually this is not about Gnome, but about the structure and design issues of metacity. Some time ago we could just configure our sawfish... I think if we can, we should give the chance, to change these settigs to everybody - I saw a lot of questions about this "feature".

It is about gnome actually. Metacity is the WM for Gnome, it must follow the gnome HIG. It's structure and design is built to follow the Gnome desktop's standards. You get no configuration options, you get to use the desktop that they imagined. This is the reason I no longer use gnome.

---

### Post by Endolith on 2007-10-23
I'd like to change this as well since I'm emulating the third mouse button by pressing both at once.  If you go in gconf-editor there's an entry in /apps/metacity/general/mouse_button_modifier, but not to change the button that I can see.

---

### Post by georgo on 2007-10-25
> **Endolith said:**
> I'd like to change this as well since I'm emulating the third mouse button by pressing both at once.  If you go in gconf-editor there's an entry in /apps/metacity/general/mouse_button_modifier, but not to change the button that I can see.

Well, the property you mentioned is "Movement key" which can be also configured in the "Window preferences" dialog (control/alt/super are allowed). Behavior I mentioned in my previous post is only experimental thing. I do not know if there will be ever enough pressure by community for this feature.
If you use compiz or beryl shortcuts are fully configurable, unfortunately I still use metacity :(. If you are interested maybe I can create this patch.

---

### Post by georgo on 2007-11-12
Ok, I have patch for this. If you have time take a look at it and give me response [http://tarvid.kallimagarden.com]("http://tarvid.kallimagarden.com"). I would like to put this also on Launchpad wish list, but I am afraid it will never reach upstream.

---


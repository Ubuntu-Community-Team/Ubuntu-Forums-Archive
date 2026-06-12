---
title: "detection of resolution screen"
date: 2014-08-22
forum: Desktop Environments
---

### Post by rafdrepublic on 2014-08-22
Hello,
I have a little bit strange issue on Lubuntu (with Openbox), which I installed yesterday. What I can say is: similar issues (with resolution) I have faced with openSuse.
I hope somebody can tell me what is wrong.
As first, please see this picture:

[http://postimg.org/image/iwurwf7zf/d738baec/](http://postimg.org/image/iwurwf7zf/d738baec/)

The window (Firefox) was maximized (using the buttons on Window Title). For some reasons it does not fill the whole screen.
I have observed that this happens for many applications, but not for all. Some application can fill the whole screen, and some not.

What I have noticed is: when I point with the cursor on window title and hold it, then moving the mouse extend the window (fill the whole screen).

Now I am not sure, whether this is some kind of standard behavior in OpenBOX or application has issues with detection of maximal size of the screen.
Any ideas ?

Regards
Rafal

---

### Post by rafdrepublic on 2014-08-22
I forgot to add that my display manager is SLIM

---

### Post by ajgreeny on 2014-08-22
I don't know slim, but it is described as a login-manager, not a display-manager, so I wonder if that is relevant.  Have you tried with the usual display-manager for lubuntu which is now lightdm, I believe.

---

### Post by vasa1 on 2014-08-22
So you installed Lubuntu and within one day you changed to SLiM? Why is that? What other changes did you make? 

@ajgreeny, it looks like the terms maybe interchangeable.

---

### Post by ajgreeny on 2014-08-23
> **vasa1 said:**
> So you installed Lubuntu and within one day you changed to SLiM? Why is that? What other changes did you make? 

[COLOR=#ff0000]@ajgreeny, it looks like the terms maybe interchangeable.[/COLOR]Yes, I though perhaps that was the case; it's just that I have not noticed the term login-manager before, so I wondered if it was an important difference.

---

### Post by rafdrepublic on 2014-08-24
Hello,

The issue is somehow related to my monitor. System detects two monitors: standard VGA plus DVI. For both different resolutiion is set. Thats the issue. 
I reinstalled the PC (without SLIM). Now I have lightdm. When I see the first log in screen , the it does not take full screen (only part). After I log in into LXDE I can use the whole size of the monitor. I think that linux is somehow switching between two monitors: VGA and DVI.

When I connect to my monitor via HDMI, then everything works fine. All the time I work with 1280x720 without any issues.

Few months ago (when I used OpenSuse on the same machine) I have faced some issues with the same root cause - system sees two monitors:
[http://www.linuxquestions.org/questions/linux-desktop-74/background-for-lxdm-and-in-fluxbox-4175477880/](http://www.linuxquestions.org/questions/linux-desktop-74/background-for-lxdm-and-in-fluxbox-4175477880/)

The point is:
why my Linux thinks that I have two monitors, though I am connected with VGA cable only to one monitor ? isn't it something wrong here?

cheers
Rafal

---


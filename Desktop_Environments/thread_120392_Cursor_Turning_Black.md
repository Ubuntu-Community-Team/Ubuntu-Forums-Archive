---
title: "Cursor Turning Black"
date: 2006-01-21
forum: Desktop Environments
---

### Post by engla on 2006-01-21
I have  a cursor problem on my Ubuntu Breezy install that I just can't solve. I have searched and searched on the web and here in the forum, so it's about time I describe my problem and ask you about it.

When I use my normal ubuntu gnome desktop and type in an application, the cursor often vanishes (as it should), however, when it comes back it is inverted, almost totally black. After that all the different cursors (move, insertion cursor, drag etc) are inverted, _until_ you click a window title bar.

Installing a different mouse theme, I also noticed that it doesn't depend on the theme, and that regardless of the cursor being inverted or not, it is always monochrome (black and white), so most themes look awful.

I've actually always had this problem on this machine, since my first Hoary install when it came out (Didn't use ubuntu before that). I don't remember if the specifics where exactly like this from the beginning but it was sort of the same problem.


I don't know what this is about, but I think it's a problem with the X configuration. I don't know anything about this, so I can't do much.

Any help, hints and suggestions on what to try are greatly appreciated; this is really my only big "compatibility" issue I have on my setup.
Thanks

---

### Post by connellr on 2006-01-21
I haven't figured this out yet, but i have noticed it also on one of my computers running breezy (was upgraded from Horray).  If I find anything I'll let you know.

By the way thanks for the tip about clicking on a title-bar to get the cursor back, I hadn't really even put 2 and 2 together to figure that out yet ... I was just frustrated seeing sometimes it looked normal, and sometimes it was just black.

Also of note, Im using i686, so this is not a PPC specific bug.

---

### Post by engla on 2006-01-23
During the last days I at least found out a way to avoid this: It seems this bad cursor graphics thing is not triggered at all if you avoid using xscreensaver.

Not quite a loss, but still a loss for me.

This leads me to think it's very much related to my graphics card.. running glxgears triggers sort of the same cursor problem but only temporarily. Perhaps this extra information can help us sort this all out.

I have a very old ATI Rage 128 card (PCI)

---

### Post by jmeadows111 on 2006-01-23
[QUOTE=engla] I have a very old ATI Rage 128 card (PCI)[/QUOTE]

I have seen the exact same thing and I also have a rage 128 card on the affected PC; it hasn't been a priority for me to fix, so I don't have any more that that, but it does help establish the pattern

---

### Post by connellr on 2006-01-30
[QUOTE=engla]During the last days I at least found out a way to avoid this: It seems this bad cursor graphics thing is not triggered at all if you avoid using xscreensaver.

Not quite a loss, but still a loss for me.

This leads me to think it's very much related to my graphics card.. running glxgears triggers sort of the same cursor problem but only temporarily. Perhaps this extra information can help us sort this all out.

I have a very old ATI Rage 128 card (PCI)[/QUOTE]

Yep, the computer Im having a problem on also has the 16MB Rage 128 
(Its a Dell 4300S).  Looking like a trend.

---

### Post by connellr on 2006-01-30
Ok, dispite the revolution of us all having ATI Raige 128 cards, I have found a solution (or at least work-around)

Create the following file:
/usr/share/icons/default/index.theme (the default directory won't exist at first) 

In that file add the following:

[Icon Theme]
Inherits=kubuntu

(you can change 'kubuntu' to whatever theme you want to use I think, but haven't tested this).

Worked for me anyhow ... the mouse may momentarily turn black still, but as soon as you move the mouse it is back to the way it should be. \\:D/

---


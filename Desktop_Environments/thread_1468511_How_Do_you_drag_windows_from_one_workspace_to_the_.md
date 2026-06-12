---
title: "How Do you drag windows from one workspace to the next?"
date: 2010-05-01
forum: Desktop Environments
---

### Post by DeusExM1 on 2010-05-01
I was wondering how to do this? I did not install CSSM, just enabled extra effects. I can switch between workspaces, but i cant drag windows from one to the next. Any help would be appreciated.

---

### Post by helicase on 2010-05-01
I've got the desktop cube enabled and I can drag my windows to the left or right, "off the screen" as it were. Don't know if that works for you. What should work, however, is to right-click on the title bar and choose "Move to Workspace Right", or "Move to Another Workspace".

---

### Post by DeusExM1 on 2010-05-01
yeah i know it works with the cube for some reason i thought it would work with the regular viewport switcher too. What you said works by the way (right click and choose where to send the program).

---

### Post by chriswyatt on 2010-05-01
[http://www.google.com/search?client=ubuntu&channel=fs&q=drag+window+to+workspace+gnome&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=drag+window+to+workspace+gnome&ie=utf-8&oe=utf-8)

Not sure if dragging's possible at a quick glance of the search results on Google, but you can use Shift-Ctrl-Alt left and right to move windows.

[http://ubuntuforums.org/showthread.php?t=447419](http://ubuntuforums.org/showthread.php?t=447419)

Someone here mentioned something about Brightside.

---

### Post by sendblink23 on 2010-05-01
> **DeusExM1 said:**
> I was wondering how to do this? I did not install CSSM, just enabled extra effects. I can switch between workspaces, but i cant drag windows from one to the next. Any help would be appreciated.

The only way to drag windows to another workspace is with CSSM (having cube enabled)
But without CSSM, you do exactly what has been mentioned on the other replies.

---

### Post by DeusExM1 on 2010-05-01
actually there is a lot that can be done. This guy in the video knows a million methods.

[http://www.youtube.com/watch?v=PgLK8eYAg0A&playnext_from=TL&videos=6o03PuNlGew&feature=sub](http://www.youtube.com/watch?v=PgLK8eYAg0A&playnext_from=TL&videos=6o03PuNlGew&feature=sub)

I learned a lot by watching it. Expo is what im gonna use.

---

### Post by uiberto on 2010-05-01
Changing these settings allowed me to draw windows between workspaces at the desktop level while still using Desktop Wall.

CompizConfig Settings Manager -> Desktop Wall -> Edge Flipping -> Enable Edge Flip Move (windows) & Edge Filp DnD (objects).

---

### Post by DeusExM1 on 2010-05-01
thats even better! exactly what iwas looking for.Cheers

---

### Post by timzak on 2010-05-03
> **helicase said:**
> I've got the desktop cube enabled and I can drag my windows to the left or right, "off the screen" as it were. Don't know if that works for you. What should work, however, is to right-click on the title bar and choose "Move to Workspace Right", or "Move to Another Workspace".

Appreciate this!  I was just wondering how to do this.  There used to be buttons on the left of the title bar in some themes that did this (where the close, min, and max buttons have been moved).

---

### Post by baynes on 2010-05-04
An alternate way (if you don't want to install any optional software) is to disable desktop effects. Then you can drag windows between workspaces by dragging the window outlines as visible at the bottom right Workspaces "ribbon".

System -> Preferences -> Appearance -> Visual Effects (tab) -> chose "None" rather than the default "Normal"

---

### Post by johnnybeem on 2010-05-05
In case it helps anybody, I just found this and checking it enabled the window dragging to other workspaces in 10.04... It must be disabled by default.

1) Run gconf-editor
2) Check the box:
/apps/compiz/plugins/wall/screen0/options/edgeflip_move

---

### Post by limpangel on 2010-05-05
> **johnnybeem said:**
> In case it helps anybody, I just found this and checking it enabled the window dragging to other workspaces in 10.04... It must be disabled by default.

1) Run gconf-editor
2) Check the box:
/apps/compiz/plugins/wall/screen0/options/edgeflip_move

This solved it for me. Thanks!

Weird that it was disabled by default in 10.04. 
I think this was one of the few really usefull compiz features.

---

### Post by jac_tict on 2010-05-06
Thank you johnnybeem!
It should be the default setting as before!

---

### Post by MrVas on 2010-06-01
> **johnnybeem said:**
> In case it helps anybody, I just found this and checking it enabled the window dragging to other workspaces in 10.04... It must be disabled by default.

1) Run gconf-editor
2) Check the box:
/apps/compiz/plugins/wall/screen0/options/edgeflip_move
THANK YOU!!! If I didn't know any better, I'd say Canonical is selling training classes, just like Microsoft, and moves/disables features between releases to fill them... :)

Vas

---

### Post by exodus_ on 2010-06-01
> **baynes said:**
> an alternate way (if you don't want to install any optional software) is to disable desktop effects. Then you can drag windows between workspaces by dragging the window outlines as visible at the bottom right workspaces "ribbon".

System -> preferences -> appearance -> visual effects (tab) -> chose "none" rather than the default "normal"

+1

---


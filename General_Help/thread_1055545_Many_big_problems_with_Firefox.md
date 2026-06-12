---
title: "Many big problems with Firefox"
date: 2009-01-30
forum: General Help
---

### Post by wizardStan on 2009-01-30
I apologise, but I wasn't exactly certain where to put this.  I can only reproduce these problem in my Ubuntu install with the version of Firefox downloaded from the repository.  When I use the official binary from the mozilla website, they all go away.
My setup:
Ubuntu 8.10 64 bit, 2.4 Ghz quad core, 4 gigs ram.
Nvidia GeForce 8600 GT, two monitors: Primary is 1024x768 CRT which I call "top" because it is on top; Secondary is 1680x1050 LCD which is "bottom" because it's on the bottom.  Despite the naming, it is actually the secondary screen on the bottom which I use as primary.  I've yet to figure out how to switch these, but that's a different problem.
So here's the problems I have been having the last few days.

1) When I open up Firefox for the first time, it always appear on the top screen (which is acceptable, since it is my primary) but it's always too large for the screen.  It's sized such that the title bar is above the top of the visible area, with the file menu being the first thing to appear.  I found a way around this by hitting F11 to full screen it, and then F11 again to get it back to normal, at which point I can resize and move it as normal.  The strangest part is that, unless I do the F11 trick I just mentioned, I can't even super-click-drag to move it, nor does alt-F7 shortcut work to move it.  It is stuck, whatever is wrong with it.  Otherwise it functions normally.

2) When I open a new window, it does the exact same thing.  First, it appears on the top screen, even after I've managed to get it to my secondary screen, and it does the weird "too large and stuck" thing I just mentioned.  This is unacceptable.  This version of Ubuntu was supposed to have the fix that made new windows open on the same screen, and for a while it did that exactly perfect.  It was only the last few days or so that it has been causing problems.

3) clicking a link from another application (something someone sends me in Pidgin or xchat, for example) causes the current Firefox window to suddenly do the "too big" thing mentioned previously, regardless which screen it currently is on.  That is, it maximizes so the title is above the top of the screen, even when it wasn't maximized to begin with.

As I said, this only happens when using the version of Firefox downloaded from the repository, and only in the last few days.  When I download and use the official binary directly from the Mozilla web site, all of these problems go away: Firefox opens on whichever screen I executed it from at the exact size expected, ditto new windows, opening links from other programs doesn't change the size at all, etc...

Was there any kind of update the last few days?  Is anyone else experiencing any of these problems, or is it just me?

---

### Post by Crafty Kisses on 2009-01-30
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager and find "Windows Decorations" add the following line to "Decoration Windows":
```
(any) | class=Firefox
```
Once you've done that close out CCSM, then open CCSM back up again, then change that to:
```
any
```
Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```
metacity --replace
```
I've also found another fix, what you want do to is press F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal. The issue really only occurs when Firefox crashes and you reboot it, but those are the fixes and I've tested them myself and they do actually work.

---

### Post by wizardStan on 2009-02-01
Interestingly enough, that worked.  I didn't mess with any settings or anything, I just went through the motions of resize, minimize, move around, maximize.  I'll keep that in mind if it happens again, thanks!

---

### Post by binbash on 2009-02-01
1- Hit F11 or open compizconfig settings manager go to workarounds plugin and untick legacy fullscreen support

2 - Read the first , compizconfig one but.

3-same

---


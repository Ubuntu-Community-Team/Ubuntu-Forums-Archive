---
title: "window manager themes empty?"
date: 2012-09-02
forum: Desktop Environments
---

### Post by lazylew on 2012-09-02
On my friend's machine the windows don't have the -X- thingies anymore to maximize minimize and close, so I wanted to install another window manager's theme to see if it would solve that.
There's no themes there anymore though - it's completely empty.

Is there a way to get thems in there again, or at least get the mini-maximize, close-buttons back?

---

### Post by vasa1 on 2012-09-02
> **lazylew said:**
> On my friend's machine the windows don't have the -X- thingies anymore to maximize minimize and close, so I wanted to install another window manager's theme to see if it would solve that.
There's no themes there anymore though - it's completely empty.

Is there a way to get thems in there again, or at least get the mini-maximize, close-buttons back?

I'd suggest installing the Greybird theme as described [here]("http://www.webupd8.org/2012/08/greybird-default-xubuntu-theme-gets.html"). It's complete and has what you need for your friend's machine.

---

### Post by lazylew on 2012-09-02
> **vasa1 said:**
> I'd suggest installing the Greybird theme as described [here]("http://www.webupd8.org/2012/08/greybird-default-xubuntu-theme-gets.html"). It's complete and has what you need for your friend's machine.I followed the instructions and once installed choose greybird-git. 
The problem still persists.

edit- alt-F4 doesn't work anymore either.

---

### Post by vasa1 on 2012-09-02
Hmmm...
Okay, assuming we're talking Xfce here,
Click on the Applications Menu, Settings, then Settings Manager, then Windows Manager. There, you should see a list of WMs available. If you don't see a list, please put up an image of what you see.

Based on your edit, the problem seems more complex and you'll have to wait for more experienced members to see this thread.

---

### Post by lazylew on 2012-09-02
> **vasa1 said:**
> Hmmm...
Okay, assuming we're talking Xfce here,
Click on the Applications Menu, Settings, then Settings Manager, then Windows Manager. There, you should see a list of WMs available. If you don't see a list, please put up an image of what you see.

Based on your edit, the problem seems more complex and you'll have to wait for more experienced members to see this thread.As you can see in the attachment, there's nothing there to select.
Another strange thing is that in eg Firefox the menus do drop down when clicking them, but when I want to go down in that dropped down list it disappears immediately so nothing can be selected.

I'm already thinking of a complete reinstall, or maybe an upgrade to 12.10

---

### Post by lazylew on 2012-09-02
Solved in a drastic manner:
fresh install .

---

### Post by lazylew on 2013-05-05
8 months later now, and exactly the same is happening!
I hope someone can tell me what the problem is, because once again doing a fresh install isn't an option; if it comes to that then I'd rather change distro.

---

### Post by lazylew on 2013-05-05
> **lazylew said:**
> 8 months later now, and exactly the same is happening!
I hope someone can tell me what the problem is, because once again doing a fresh install isn't an option; if it comes to that then I'd rather change distro.I found one temporary solution here:
[http://softsolder.com/2013/02/01/xfce-window-manager-recovery/](http://softsolder.com/2013/02/01/xfce-window-manager-recovery/)
where the trick is to type in terminal ```
xfwm4 --replace
```
The rest of that article, which makes clear it's an XFCE-flaw and not an Ubuntu-issue, is unclear to me (I have never used SSH), but I'll try and sort it via searching the web.
I'm glad I found this temporary work-around :)

---


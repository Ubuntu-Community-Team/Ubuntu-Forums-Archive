---
title: "Oh Boy! I did something to my window manager!"
date: 2010-03-24
forum: Desktop Environments
---

### Post by Joe Awsome on 2010-03-24
Hey all, I was customizing my xfce desktop and eliminated panel 2 thinking the window list on the bottom would automaticly go to panel 1. I was wrong! Now I have no window manager, I was able to put panel 2 back to the way I had it for the most part but I don't have the little thing were my windows popup, any help is apreciated. (Here is are a few screen shots to help u know what I'm talking about.) As you can see I am curently using the window list as a substitute.

---

### Post by Alan James on 2010-03-24
This is an easy fix. Right click on the bar you want to add the window list to. Click “Add New Items” then scroll down to window list and add it.
 

 By the way, a “window manager” is something very different then a window list applet. Here is a Wikipedia page about window managers.
 

[http://en.wikipedia.org/wiki/Window_manager](http://en.wikipedia.org/wiki/Window_manager)


I hope this helps.

---

### Post by Joe Awsome on 2010-03-29
what I mean is I deleted the part of my lower panel that displays the windows I curently have open on the bottom of the screen without having to click on an applet to view them. The part that displays the programs that I have open like gimp, chrome, thunar, and others. How do I restore that feature to my taskbar/panel?](*,)

---

### Post by drreed on 2010-04-18
I have something similar going on. I was trying to customize panel 2 and now when I minimize a program, it disappears. I wonder how many I have open right now that I can't see?

---

### Post by drreed on 2010-04-18
> **Joe Awsome said:**
> what I mean is I deleted the part of my lower panel that displays the windows I curently have open on the bottom of the screen without having to click on an applet to view them. The part that displays the programs that I have open like gimp, chrome, thunar, and others. How do I restore that feature to my taskbar/panel?](*,)

First, you do have a panel down there don't you? If not, right click on the top one and choose 'customize panel' in that dialog, there is a '+' button next to the panel 1 at the very top. Use that to add back panel 2.

Then right click on panel 2 and choose 'customize panel'.
Make it fixed and full width.

to get your minimized windows to show, follow the advice above on how to add an item, and choose 'window list' from the pre-configued applets (or w/e they're called) to add that feature back.

I got mine working, now it's broken again. No I can choose a minimized window ok, but it doesn't display. Choosing it doesn't do anything. I assume it's something I have in compiz, but I haven't found it yet.

---

### Post by airtonix on 2010-04-19
if you add a new panel-applet and it doesn't appear, the first thing you should do is kill the panel process : 

in gnome its : 
```
sudo killall gnome-panel
```

in xfce i imagine it's : 

```
sudo killall xfce-panel
```

Then by the rules of the session manager it should automatically restart, if not manualy start it.

Then assess whether or not the panel applet is actually running or not.

---

### Post by Joe Awsome on 2010-04-19
just tryed that and all I got was.

joe@joe-desktop:~$ sudo killall xfce-panel
[sudo] password for joe: 
xfce-panel: no process found
joe@joe-desktop:~$

---

### Post by lightstream on 2010-04-19
just do what Alan James said originally, right click the panel, Add New Items...

---

### Post by Joe Awsome on 2010-04-22
i solved it! I think what Allen meant to say was to add the [B]Task List[B], not the [B]Window List[B]. Sorry for all the trouble guys, but at least somebody else who had the problem can solve it now. Now on to round two, my xfce4 desktop loads really slow, I'm talking 3-4 min at best. Any solutions?

---


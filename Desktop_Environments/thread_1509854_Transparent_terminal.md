---
title: "Transparent terminal"
date: 2010-06-14
forum: Desktop Environments
---

### Post by xtracool_protik on 2010-06-14
Hi,
 It seems really old topic, however I can't really seem to be able to setup transparent terminal on my workspace.
 I'm trying to setup something like [http://tombuntu.com/index.php/2007/08/27/transparent-terminal-on-your-desktop/](http://tombuntu.com/index.php/2007/08/27/transparent-terminal-on-your-desktop/) Following these directions doesn't really work, to start with my terminal simply doesn't have options which he is talking about.
 Then I tried devilspie method [http://ubuntuforums.org/showthread.php?t=1414998](http://ubuntuforums.org/showthread.php?t=1414998) which works but puts terminal on each workspace moreover all my windows seems to lose decoration.
 To make it as unique as possible my terminal profile is "GrrTransBrr" without quotations.
 I'll appreciate any help
 Thanks

---

### Post by towheedm on 2010-06-14
I created a transparent terminal for my desktop using Cairo-Dock because I use this dock all the time.  My terminal is not fullscreen but windowed because I did not want a fullscreen terminal.  This has been working pretty well for me for the last couple of months or so.

---

### Post by gingivere0 on 2010-06-14
I don't know if this is what you are talking about, but you can make your terminal transparent by opening up a terminal, going to Edit>Profile Preferences. Then, in the new window that opens up, go to the background tab and set the transparency level to none.  Hope this is what your looking for.

---

### Post by Breambutt on 2010-06-14
Basically this is what should be enough. You can disable the taskbar and scrollbar from the terminal settings and other additional parameters that might prove handy such as *keep below* can be found in Compiz settings under Window Rules.

The downside of this method is that if you take a screenshot of your terminal alone with Alt + Print Scrn, the title will include "GrrTransBrr" and if you open it with Eye of Gnome or GIMP, they won't have the borders either. Same goes for the GrrTransBrr profile settings in terminal. On the other hand since I doubt you'll come across too many windows with "GrrTransBrr" in the title, it should be okay.

Another annoyance is that if you keep the terminal on the upper left corner of your desktop, new icons will appear under the layer. This is pretty much why I stopped using the embed terminal, but there are workarounds for this too.

Oh yeah, you might want to make sure you're using Gnome-terminal instead of xterm or somesuch.

---

### Post by Shazzam6999 on 2010-06-14
Lxterminal has default transparency... if you're not feeling motivated.

---

### Post by xtracool_protik on 2010-06-15
Hey Breambutt, Thanks.
 Thats what I did, and assumed I'll get result as I wished for (same as your screenshot). However here is how I see it. As u can see it still have borders, I'll try again with some new name from scratch.
 Shazzam6999, I didn't try/see Lxterminal. I'll check it and let u know 
 Thanks again guys

---

### Post by xtracool_protik on 2010-06-15
ohh if that helps, I'm using emrald for decorating windows rather than compiz-decoration. I think that is the one causing issues but I am not very knowledgeable so will like some inputs, Thanks :)

---

### Post by xtracool_protik on 2010-06-18
ok finally I got it. Well I was being stupid as usual :P
Title of my terminal was never set to "GrrTransBrr" I needed to set it through Menu -> Terminal -> Set Title
 Hope that helps someone

---

### Post by xtracool_protik on 2010-06-18
well now next issues are:
 I need to set title everytime I start terminal :-o even when I use '--window-with-profile' which is kinda puts me off. 
 And now I see terminal on all viewports How can I fix it to one viewport, at least how can I fix to only viewport which invokes it?

---

### Post by xtracool_protik on 2010-06-19
bump

---

### Post by xtracool_protik on 2010-06-21
Hey guys,
 Doesn't anyone have a suggestion about fixing window to one workspace. The window which doesn't have title bar so eventually I can't right click and say on this viewport etc.

 Regards

---

### Post by Breambutt on 2010-06-21
Related to post #9, are you sure you have these set correctly in the terminal's profile settings:

Title and Command tab > Initial title: GrrTransBrr
Title and Command tab > &#8220;Keep initial title&#8221; from the first dropdown menu

And have you possibly used the "sticky" option in Compiz window rules for your Grr-terminal, that would place it on all desktops?

Now that I'm here once again, if you want to launch the trans-terminal every time you boot up use this line in the Startup Applications so that your slowputer has time to load Compiz and all the other necessary garbage - otherwise it will probably load a partly decorated terminal with borders:

```
bash -c "sleep 5; gnome-terminal --window-with-profile=GrrTransBrr"
```

Adjust the sleep value (in seconds) depending on how long it takes for other stuff to load. Kind of a crude way, but who cares since it works. (Oh well, looks like the old guide covered that too.)

---

### Post by xtracool_protik on 2010-06-21
Hey Breambutt,
 Thanks again, having it sticky was the issue. I'm not sure yet if I want it to start on startup but if I do I'll keep 
 Code:
 ```
bash -c "sleep 5; gnome-terminal --window-with-profile=GrrTransBrr"
```
 in mind.

 Here is screenshot of wat it looks like as of now, I get terminal as well as slick screen :)

 Thanks all those helped

---


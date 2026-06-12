---
title: "Fluxbox on Ubuntu 12.04 - mouse problems"
date: 2012-07-11
forum: Desktop Environments
---

### Post by Patb on 2012-07-11
Following installation of Ubuntu 12.04 over a previous install of 10.04, I have found odd behaviour in the Fluxbox windows manager. If I 'tab' two windows together (as one can in Fluxbox) I cannot change focus from one tabbed window to another using the mouse. To focus on the other window I have to use the alt-tab method with the keyboard. Further, if I try to drag a window by clicking on the title bar, it does not move. Control-click-drag moves the window but it then 'tabs' onto any window behind it if one is open. (Previously, to tab onto another window, I had to drag the title bar right up onto the title bar of the window behind it, which is logical). 

All other mouse click actions seem to be okay. I have tried a clean install of Fluxbox to no avail, so it does not appear to be due to my particular fluxbox settings. 

I would be grateful for any suggestions. Do other Fluxbox users have the same behaviour in Ubuntu 12.04? 

Cheers, Pat.

---

### Post by Patb on 2012-07-13
Bump. This glitch seems very significant to me. Are there Fluxbox enthusiasts using Ubuntu 12.04 who do *not* have this problem? There might be some mileage in discussing setups. My hardware is an Acer Aspire One D255 netbook with a screen resolution of 1024x600. 

Another problem not mentioned in my original post is that I cannot resize windows. I can maximise and minimise but not resize. 

I have tried removing compiz and unity in an attempt to get around the problem but that makes no difference. 

Any suggestions would be very welcome. 

Cheers, Pat.

---

### Post by Patb on 2012-07-18
Bump again. Sorry to whine but I'm surprised there is not more reaction to this post. The problem is significant enough for me to look at an alternative to Ubuntu. Are there any Fluxbox enthusiasts using Ubuntu 12.04 who can share their experiences, good or bad? I would really like to know whether other Fluxbox users have the same problems. I have tested the Blackbox window manager (on which Fluxbox is based) and it does not suffer the same problems. 

I would appreciate any comments or suggestions. 

Cheers, Pat.

---

### Post by Rick.B9 on 2012-07-18
Pat, 
I'll look into this later tonight, if you can hold on.  I just saw it, but I have to leave for the afternoon.  I just set up flux on 12.04, and haven't had the chance to fully configure/play with it yet to have run into this problem.  I usually use ctrl-0 thru ctrl-6 to mess with tabbed windows.

---

### Post by Rick.B9 on 2012-07-18
Pat,

I couldn't recreate the problem; it worked as expected after changing the default OnTitlebar mouse2 behavior in ~/.fluxbox/keys.  I'm running a stock Xubuntu 12.04 install from a couple days ago with Fluxbox1.3.2-2.  I hadn't configured Fluxbox yet, since I haven't used xfce in a long time and wanted to try it out.

Anyway, I can't see there being a difference in the behavior of fluxbox between the two *buntus as flux uses the keys file for the mouse config.  

All I did was change the wallpaper and the default middle click behavior in  ~/.fluxbox keys from:
```
OnTitlebar Mouse2 :Lower
``` to ```
OnTitlebar Mouse2 :StartTabbing
```It worked as expected w/ clicking on the tabs changing to that tab.
(OTOH, I got my left arrow key back, per my help request,  so it wasn't a total loss for me.  At least until I tweak it til I break it again.

The left click drag on the titlebar to move also worked OK.  Last thing, if you want to resize or move the window w/ the mouse, alt+left click on the window will move it, and alt+right click will resize it.  There are further tweaks, ```
OnWindow Mod1 Mouse3 :MacroCmd {Raise} {Focus} {StartResizing NearestCorner}
```will allow resizing in any direction, not just lower right.   If you have any questions, I'll do my best to answer them.

Regards

---

### Post by Patb on 2012-07-19
Rick,

Thanks so much for the response. You have got me out of trouble. Tinkering with the file ~/.fluxbox/keys fixed the problem. I created one with 'factory settings' by temporarily renaming my ~/.fluxbox directory, then logging out and back in and the problems were solved. Then I edited the 'factory set' version to include my preferred settings from my own file. I can now focus on a window by clicking on the relevant title bar and I can resize windows as normally. The problem was of my own making - Fluxbox had updated the default ~/.fluxbox/keys file but when I upgraded to Ubuntu 12.04, I had kept my old version of the file. 

I must say I'm feeling decidedly red-faced though because I seem to have made some error when I previously did that "clean install of Fluxbox" (by which I mean I went back to 'factory settings' as described above). It seems that I must have somehow inadvertently adopted my old ~/.fluxbox/keys file on that occasion.  When I repeated just now though with the correct 'factory set' file, mouse behaviour was normal. 

Thanks again. Cheers, Pat.

---

### Post by Rick.B9 on 2012-07-19
Pat,

Sounds about right; I keep my old configs of Fluxbox and drop them in on new installs, and there's always some retweaking needed.  Glad it all worked out.

Regards,
Rick

---


---
title: "Problem rotating cube with rdesktop/tsclient in fullscreen"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by ZeroVerteX on 2007-11-04
I haven't found an answer to this one yet. I have Gutsy installed. The rotating cube works great. I do alot of RDP sessions and I like to run rdesktop or tsclient in fullscreen. When rdesktop/tsclient is in full screen, I can not rotate the cube via Ctrl+Alt+Left/Right or Ctrl+Alt+Left Mouse. Any ideas?

Solved it on my own! There is a  check box to "Enable windoe manager's keybinding" in the Terminal Server Client or I guess in rdesktop. That got it! Hope this helps anyone else.

---

### Post by Nem1976 on 2007-11-05
Where you able to get the fullscreen mode to only show up on 1 desktop? 

Currently if I try to do this I get the same TS session on all my desktops.

---

### Post by ZeroVerteX on 2007-11-05
Yes. I have on a machine running Compiz, but not on a machine not running compiz. I have a machine at work that is older and won't do Compiz and when I switch desktops, the fullscreen tsclient windows moves with it. Kind of a pain but not horrible.

---

### Post by ralph_walden on 2007-11-07
> **ZeroVerteX said:**
> Yes. I have on a machine running Compiz, but not on a machine not running compiz. I have a machine at work that is older and won't do Compiz and when I switch desktops, the fullscreen tsclient windows moves with it. Kind of a pain but not horrible.

I am running Compiz, and I get the same thing - the fullscreen terminal server on all desktops.  The cube rotates now, thanks to the keybinding setting suggestion, but the same screen shows up on all desktops.


Hmm...

---

### Post by DasFx on 2007-11-09
Had the same issue for a long time (back in the days it was no issue on beryl)

Just found a nice solution/workaround.


Rdesktop and Compiz playing nicely together
While playing around with Compiz in Gutsy Gibbon I hit an age-old chestnut about how to operate Windows Remote Desktop client in full screen while retaining all the neat 3D desktop features of Ubuntu, like switching viewports.

The problem is that in fullscreen mode rdesktop grabs the keyboard input, so none of the shortcuts work. Of course, there's the -K option, but that causes problems if your Windows and Linux key shortcuts are the same. Also, if you try to switch viewports you'll find the rdesktop screen on every one of them. Your compiz cube will just repeat the fullscreen terminal service session on each face.

So, a bit of lateral thinking had me running the following command:

rdesktop -a 16 -k en-gb -g 1024x720 -D my_rdp_server

On my 1024x768 screen the top and bottom menu bars occupy 48 lines, so subtracting those from 768 leaves me with a desktop geometry for rdesktop of 1024x720. I then use the -D option to strip the window decorations. The result is an rdesktop session that fills the screen, leaving the top and bottom Gnome panel bars visible. It's much more usable than fullscreen since it leaves the Gnome/Compiz desktop exposed.


SOURCE : 
[http://gothgems.livejournal.com/216980.html](http://gothgems.livejournal.com/216980.html)

---

### Post by UbUsOsOlik on 2008-01-15
The answer is simple, after you enable the "Enable window manager's keybinding" option go in full screen mode and press alt+ctrl+enter. This will enable the tserver session to be on a single side and then you can rotate your cube to the linux ubuntu desktop. Hope i helped. Best of luck SoSolik.

---


---
title: "Terminal Server Client + Beryl Opacity Issue"
date: 2007-01-17
forum: Desktop Environments
---

### Post by charon79m on 2007-01-17
I am experiencing an issue with my Terminal Server Client window being semi-transparent.

[IMG]http://www.mrknisely.is-a-geek.org/resized.jpg[/IMG]

I have turned off each module one at a time, and none of them allow it to go back to full opacity.  When I disable beryl though, it is fine.

Does anyone have any suggestions on this?

Versions:
Beryl:  1.14~0beryl1 (edgy) 
Terminal Server Client:  0.148-1ubuntu4
xorg: 1:7.1.1ubuntu6.2
fglrx: 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.6234 (8.32.5)

If anything else is required, just let me know.  

This is so impacting my day-to-day opperation I'm using VMWare and actually RDPing from (GULP) windows.  This feels SO wrong.

---

### Post by Lord Illidan on 2007-01-17
Just don't use Beryl for production work. It's not like it is necessary, and it **is** alpha software.

---

### Post by charon79m on 2007-01-17
That does not assist in tracking down this bug.  If I'm having this issue, it's for a reason, and it will help others beyond myself if we are able to fix it.

Thanks for your suggestion.  I do realize that Beryl is not considered production stable... but I'd like to do my part to help it get there.

---

### Post by dabl on 2007-01-17
I'm far from any kind of Ubuntu or Beryl expert, but on my Beryl installation on Kubuntu, the upper-left corner window icon contains a menu that includes "Opacity", and enables setting it to different percentage levels.  I also recall from the Beryl user information that there is a combination of key and mousewheel that allows you to do 10% increments of opacity.  That may or may not be a Beryl feature -- I'm also using the Aquamarine window decorator, so I'm not sure who is controlling opacity.

---

### Post by charon79m on 2007-01-17
I neglected to mention trying that.  Sorry.  The opacity is set to 100%.

Great idea though, dabl!

Mike K.

---

### Post by mcduck on 2007-01-17
Looks like ARGB visuals problem..

In Beryl Manager find the 'Set' plugin (now called 'Set Window Attribs by various criteria') and add your application to 'Disable ARGB Visuals'-list. I suppose the right entry would be something like 'p:Terminal Server Client:1' but I can't really test it so you need to try yourself what works..

---

### Post by apakun on 2007-01-28
I am having the same problem. Is there anybody can help?

---

### Post by DarkN00b on 2007-01-28
It uses the standard non-Beryl settings. Click Edit>Current Profile, click the Effects tab. Under Background tick the None (use solid color) radio button. Click the close button and you'll have a black terminal window.

---

### Post by apakun on 2007-01-29
Thanks a lot for your reply, but I didn't mean the problem of terminal window. I am  having problem with Terminal Server Client window.

---

### Post by Lampshade on 2007-01-29
Has anyone found a solution for this?  I'm having the same problem.  The terminal server client is the only app that appears so see through, making it unusable.  Everything else in Beryl seems to be working correctly.

---

### Post by Lampshade on 2007-01-29
Never mind I found the answer on the Beryl forums.  It is:

if you are using beryl svn go to beryl-settings manager > window management > set window atrribs by varius criteria > disable ARGB visual > and add > c:rdesktop:1

Probably have to restart the window manager after that, I did and now the terminal server is working correctly.

---

### Post by DarkN00b on 2007-01-30
> **Lampshade said:**
> Never mind I found the answer on the Beryl forums.  It is:

if you are using beryl svn go to beryl-settings manager > window management > set window atrribs by varius criteria > disable ARGB visual > and add > c:rdesktop:1

Probably have to restart the window manager after that, I did and now the terminal server is working correctly.

Thank you! I've had the same problem with a program I use for photo manipulation called XNview and now it is fixed! :guitar: No manager restart required!

---

### Post by apakun on 2007-01-30
Very good solution. Thanks a lot!

---

### Post by nelsong on 2007-02-08
Indeed, was looking for this for a couple of hours till I found this thread. Helps a lot. 
Keep up the good work guys.

---

### Post by Cirrocco on 2007-02-08
not sure I understand what needs to be done here.

Beryl (0.1.9999.1) is asking: "Select the window attribute. Click the Grab button to select a window, then choose a value for the setting"

how are you supposed to define a program here?

---

### Post by loopjeremyloop on 2007-02-09
> **Cirrocco said:**
> not sure I understand what needs to be done here.

Beryl (0.1.9999.1) is asking: "Select the window attribute. Click the Grab button to select a window, then choose a value for the setting"

how are you supposed to define a program here?

I just figured it out - 

basically, go into the window management menu, put a check next to "set window atrribs by varius criteria", click the PLUS button on the right.

In the popup window, make sure that Disable ARGB Visual is checked, choose "Window Class" in the left dropdown menu, and type rdesktop in the blank area.  When you click OK, you'll note that the correct value has been added into the window for you, saying "c:rdesktop:1"

Let me know if that wasn't clear enough.

Thank you, by the way, Lampshade, for bringing the answer here!!

---

### Post by maxrisc on 2007-02-12
Thanks for the help Jeremy.

I have been looking for this answer for a while.

It also works for various other apps including Java, WINE, Frostwire/Limewire and Parallels/VMware/QEMU.

Tried posting this three times but had to fix that stupid Shift Backspace problem.  Simply go into System > Preferences > Keyboard and Choose 105 (INTL) PC keyboard.

Still getting used to this interface.  I have only been using it for 2 days now and I LOVE IT!

---

### Post by theProf on 2007-02-23
Thank you for this solution.  My wife will use RDP to do work from home, so this was a "deal breaker" if you know what I mean.

---

### Post by Khaos on 2007-04-14
I tried doing the commands there but my XnView still won't work properly; it opens the picture and is transparent as well.:(

edit: nvm i fixed it :p

---

### Post by gruhland on 2007-05-01
I tried it the way it was explained - without success! XnView is completely transparent (Ubuntu Feisty, Beryl 0.20). Restarting the window manager did not make any difference. :(

---

### Post by Hibbelharry on 2007-05-01
try starting your app with:
XLIB_SKIP_ARGB_VISUALS="1" appname

---


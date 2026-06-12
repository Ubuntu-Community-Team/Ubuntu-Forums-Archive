---
title: "problem with window display"
date: 2009-06-16
forum: Desktop Environments
---

### Post by JBA2337 on 2009-06-16
I am using Ubuntu 9.04, Jaunty Jackalope. For several weeks, after I reboot my computer, I have been having a strange problem with the way windows are displayed on my screen. At least once or twice I received an error message that said I am not running a valid window manager, but that message eventually went away.  Here is a screen shot of an openoffice word processor document in a window.

[[img]http://g.imagehost.org/t/0646/error_Screenshot.jpg[/img]](http://g.imagehost.org/view/0646/error_Screenshot)


Notice on this window there is no colored title bar above the toolbar. Since the title bar is missing, there are no maximize & minimize buttons, and I cannot click on the titlebar and drag the window anywhere. Also, I cannot resize the window by dragging the arrow in the corners. I can't do much anything with this window.

By accident, I discovered that if I click on System > Preferences > Appearance > Visual Effects and then click on Normal, the computer tries to install Visual Effects. I get a message that says “searching for available drivers”, and then another message that says "Desktop Effects Could Not Be Enabled".  Going through this procedure fixes the display of the windows on my computer, but if I restart the computer, the problem with the windows returns. 

I thought that perhaps, the problem was in my window manager, so I changed it twice. I changed the window manager from Metacity to Compiz and finally to Fluxbox, which I am using now. Changing the window manager made no difference. I still have the same problem no matter which window manager I am using.

Does anyone have an idea how to permanently fix this problem?

JBA2337

---

### Post by Amilo1718 on 2009-06-16
posting the error message would be helpful

---

### Post by ~sHyLoCk~ on 2009-06-16
This might sound stupid, but did you try > metacity --replace& ? Usually what happens is that, when you don't have your proper video card driver installed you can't enable desktop effects.

---

### Post by JBA2337 on 2009-06-17
Thanks for your suggestion. In a terminal I ran the code:
metacity --replace&. This didn't do anything to help me because I rebooted my computer and I still have the same problem with the display of windows. 

I fixed the window display problem, at least until my next restart, by clicking on System > Preferences > Appearance > Visual Effects > Normal.

Do you have any other ideas?

JBA2337

---


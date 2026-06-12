---
title: "Huge title-bar font with Beryl (or GDM)"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by mrborisguy on 2007-07-04
When I log on and run Gnome through GDM, the font on my title bar is huge. Like, I open a terminal and it shows "b..." because that is all it can show, instead of "bryan@mycomp ...". I would estimate something like a font size of 40 or so. However, when I kill GDM/X and then do a startx, my title bar font is a normal size.

Also, in GDM, the text I input as my name and password is huge (only an eighth of a character can fit in the text box), and when I try to change the session, those options are also huge and the menu takes up the entire screen.

When I first installed Ubuntu, this was working fine. I think it may have occurred when I installed Beryl; I'm not sure.

Does anybody know why this would be or how to fix it?

Thanks in advance,

Bryan

---

### Post by cseljatib on 2007-07-06
hi!
i do have a similar problem, but in my case the fonts are too small!!!. (see my post in [http://ubuntuforums.org/showthread.php?t=493542&highlight=window+font](http://ubuntuforums.org/showthread.php?t=493542&highlight=window+font))

I have also installed Beryl, but inclusive when I run a normal session (not as xgl) still I have that problem.

Unfortunately I have no idea how to fix this problem, i am also waiting for some help about it.

---

### Post by avik on 2007-07-06
What does System->Preferences->Fonts say about this?

---

### Post by mrborisguy on 2007-07-06
My fonts settings were correct. I found out that the problem was not exclusive to GDM. KDM was also affected. I'm not sure if the problem had anything to do with Beryl or not.

After some reading, I suspected that my problem was actually a switch from the xserver-xorg-video-i810 driver to the xserver-xorg-video-intel driver. It was something to do with DPI or something, but I never figured it out, and switched back to the xserver-xorg-video-i810 driver, which fixed my problem.

---

### Post by avik on 2007-07-06
If it's an issue with DPI, then go back to the Font Settings, click Details at the bottom, and adjust the DPI.  That is, of course, if you're willing to go back to the intel driver.

---

### Post by mrborisguy on 2007-07-06
> **avik said:**
> If it's an issue with DPI, then go back to the Font Settings, click Details at the bottom, and adjust the DPI.  That is, of course, if you're willing to go back to the intel driver.

I did. Adjusting that made the huge fonts bigger or smaller, but also the normal fonts bigger or smaller. So it was not really an option. DPI was set on 96, which was reasonable for all of the other fonts, but the title bar font was still huge (even though it was set to Sans 10, just like the other fonts).

---

### Post by ela04cz on 2007-08-18
I got the same problem after tried beryl, now although uninstalled, still doesn´t work, all fonts are tiny!

Any ideas to help us......:confused:

---

### Post by ela04cz on 2007-08-18
Guys, I got it back following another thread on this forum: it is in the ¨login window¨>Security>Configure Xserver> then in the ¨command line¨field, add ¨ -dpi 96¨ (no quotes) in the end. Thanks to the guy who wrote this!!:popcorn:

---


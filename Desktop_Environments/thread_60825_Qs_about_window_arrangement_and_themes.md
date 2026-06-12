---
title: "Qs about window arrangement and themes"
date: 2005-08-29
forum: Desktop Environments
---

### Post by helwitch on 2005-08-29
I want to be able to cascade and tile all open windows. How do I do this? Is there a plug in? Or a window manager other than metacity?
I'd also like the option of minimizing a window to the system tray, or notification area, or whatever. GAIM does this, if you have the systray plugin activated. Is there a plug in that will give me this option for all my windows?
I'd also like to get rid of some of the control themes I don't like, but keep their associated window borders. Which files are which?
I googled and searched the forums for all these things, but was entirely unable to find answers. Any help would be greatly appreciated.

---

### Post by arnieboy on 2005-08-29
[QUOTE=helwitch]I want to be able to cascade and tile all open windows. How do I do this? Is there a plug in? Or a window manager other than metacity?
I'd also like the option of minimizing a window to the system tray, or notification area, or whatever. GAIM does this, if you have the systray plugin activated. Is there a plug in that will give me this option for all my windows?
I'd also like to get rid of some of the control themes I don't like, but keep their associated window borders. Which files are which?
I googled and searched the forums for all these things, but was entirely unable to find answers. Any help would be greatly appreciated.[/QUOTE]
answer to question 1:

use expocity (a patch for metacity)
[http://www.ubuntuforums.org/showthread.php?t=42365](http://www.ubuntuforums.org/showthread.php?t=42365)

answer to the second q:
[http://prdownloads.sourceforge.net/alltray/alltray-0.60.x86.package?download](http://prdownloads.sourceforge.net/alltray/alltray-0.60.x86.package?download)
alltray can dock almost any app to the system tray (like thunderbird, xmms etc)
run it as ```
alltray xmms
``` for example.

answer to question3:
u can make a custom theme by going to system-->preferences-->themes and then choosing a custom application theme, a window border theme and an icon theme from three different sets and make a theme of your own.

---

### Post by varunus on 2005-08-29
Strange, I thought metacity could cascade and tile.  I can't remember, though..can you do it by right clicking a window title bar?

---

### Post by helwitch on 2005-08-29
Arnieboy, thanks for the info on window arrangement and minimizing to the systray. I'll try out those plugins when I get home.
Varunus, if there is any way native to metacity to cascade and tile and such, I have been unable to find it, and goddess knows I looked.
About the themes tho, I know how to make a custom theme. I wanted to know, in the themes folder, I think it's /usr/share/themes in the individual folders, for example, the human theme folder, which file is the file for the control part of the theme, and which is the file for the window border? Because I want to get rid of the aspects I don't like, which in most cases is the control, while keeping the aspects I do like, in many cases the window border. Just to save some disk space. Yes, I realize, it probably won't even buy me 1MB, but nonetheless, this is what I want to do. I suppose I could try cut/pasting one file at a time to somewhere else, but since to make the theme manager refresh the list of themes requires logging out and back in, I'd rather just know which files are which, if anyone knows that info and is willing to take a moment to pass it on.

---


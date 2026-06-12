---
title: "How to disable window snap-to-screenbounds?"
date: 2010-09-26
forum: Desktop Environments
---

### Post by dewdrop_world on 2010-09-26
How can I disable gnome's behavior of snapping windows to screen bounds or other windows?

When I'm programming in supercollider, I have some GUI windows I can pop up to expose some real-time controls. For maximum use of screen space, some of the blank space at the windows' edges should be "out of bounds." On the Mac, and also when I've used supercollider in puredyne (an Ubuntu derivative for multimedia that uses xfce4 as the window manager), GUI windows are placed at the exact coordinates specified in my code.

But, gnome is "extra helpful" and says, "Oh, that window is going to be out of bounds. You couldn't possibly have meant that. Let me move the window inside the screen bounds for you." Well, actually I DID mean that and I don't want the window manager "correcting mistakes" that I fully intended. So then I have to move the windows by hand, even though my software put them where I wanted them in the first place. :mad:

I searched all the preference panes under the System menu, couldn't find anything. There must be a way to tell gnome to stop helping me :)

Thanks,
James

---

### Post by roggenschrotbrot on 2010-09-26
in case you are using compiz you should disable the "snapping windows" plugin

---

### Post by dewdrop_world on 2010-09-26
Nope, I disabled compiz effects a long time ago.

Is there another option somewhere?
James

---

### Post by dewdrop_world on 2010-10-08
Bump... is there no way to configure this?

It's not just windows in my code. It's other windows too. I like to have firefox *not* flush left (and not full screen width), but when I launch ff, gnome says, "No, I think you *don't* want to have a window some 50 pixels away from the left. I'm going to put it flush left even though the last position of the window when you quit was away from the border."

I really very strongly dislike this behavior and I'm a bit stunned that I can't find a way to make it stop.

---

### Post by ruskamsf on 2010-12-29
I second dewdrop_world's sentiments.  I'd love to have a solution for this...err more like I will stop hating everything when there is a solution for this :/.

---

### Post by NorthernSuze on 2011-02-16
Has anyone a solution? I sat down at my computer this morning to find the windows now open 1/4 - 1/3 sized and snap to the borders. 

I have Lucid installed with no special effects are enabled.

Googling seems to have plenty of how-to enable for Windows 7 snapping style. 


Suze ~ 
(Since I left Windows years ago, why on earth would I like Ubuntu to look and act like the OS I left behind with no regrets?)

Edited to add sort of work around:
In following directions to disable snappy windows ([http://kevin.vanzonneveld.net/techblog/article/disable_snapping_windows_in_compizfusion/](http://kevin.vanzonneveld.net/techblog/article/disable_snapping_windows_in_compizfusion/))
sys > preferences > appearance > visual effects  -- to find the settings to enable/disable plugins. Not found under Visual Effects tab...

Checked Normal instead of my preferred NONE. and the windows are back to normal with no snap.... What is happening? I prefer no effects.... but I'm glad to be rid of the snappy windows.

---

### Post by Krytarik on 2011-02-17
When "None" is selected in "Visual Effects", "Metacity" is run as window manager. I just yet tested it to see if I also get the snapping, and yes, it is enabled by default and there is apparently no way to disable it.

So, if you therefore have to run Compiz, just disable all effects/plugins you don't need/want.

---

### Post by NorthernSuze on 2011-02-17
Thank-you, Krytarik, for explaining what is happening. It really helps to know I was on the right track (may-be ](*,) )   I hate it when defaults are decided for me and then give me no way of changing them.  And I wonder why nobody else wants to use my computer at family gatherings ):P  ?

---

### Post by Krytarik on 2011-02-17
> **NorthernSuze said:**
> And I wonder why nobody else wants to use my computer at family gatherings?
LOL :p

I convinced my mom to use Ubuntu a couple of years ago, and she is very happy with it, although she uses Windows7 in dual boot to play games.

EDIT: For anyone who wants to stick with Metacity: Enable "compositing_manager" in "gconf-editor", it's working a lot better then (found that option upon searching for one to control the snapping)
- press Alt+F2
- enter "gconf-editor"
- browse to "/apps/metacity/general"
- tick "compositing_manager"

---

### Post by killerbng on 2011-11-23
thank you thank you thank for this! 

This feature is so stupid! I hated it on win7 so why would I want this crap on linux :P I mean come on its almost impossible to have 30+ windows up at once and try to move them AS NEEDED with this damn bs lame snap :P

(srry for the rant im just frustrated)

---

### Post by gbozo on 2012-06-21
Here's something that worked for me. Not perfect but adequate. This is from my Ubuntu notes. Using Ubuntu 12.04 with gnome-classic, if that matters:

Problem: Window is intentionally moved partially off-screen but it snaps back fully onto the screen when one clicks elsewhere on the desktop.
    Solution or workaround:
    (1) Install "compizconfig-settings-manager" (if not already installed)
        sudo apt-get install compizconfig-settings-manager
(2) Open CompizConfig Settings Manager. 
 With gnome-classic, it is under Applications -> System Tools -> Preferences
    (3) Under "Window Management", unselect "Place Windows"
    Comments: Some windows may open with the title bar hidden under the top panel, precluding one from closing the window. In most cases, one can easily move the window with the mouse. In some cases, however, (e.g., xterm), one must grab and move the window with <alt><left button> (press and hold alt, then press and hold left mouse button)

---

### Post by oldos2er on 2012-06-21
Old thread closed.

---


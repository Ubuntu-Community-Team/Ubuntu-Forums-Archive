---
title: "Light grey line under my mouse"
date: 2006-09-29
forum: Desktop Environments
---

### Post by wenzlicker on 2006-09-29
I get this line under my mouse cursor. It's not always there, but its there enough to aggravate me. It started after my update to edgy. I've tried changing the theme of my mouse cursor, but it still persists. I've attached an image. Any ideas?

---

### Post by roostishaw on 2006-09-29
Sorry, but I can't offer you anything more than a bump and a quick question: Did you take that with a film/digital camera, or just the printscreen?

---

### Post by wenzlicker on 2006-09-29
I had to take that with a digital camera because print screen doesn't capture the mouse.

---

### Post by wenzlicker on 2006-10-01
So, the light gray line under my mouse still persists. Any ideas?

---

### Post by havenoclu on 2006-10-07
I am having the same problem....started after installing a good amount of updates..any ideas?

---

### Post by wenzlicker on 2006-10-08
I posted a bug report. Perhaps if you let them know that the problem is not isolated to just me, it would help. The bug report can be found here:

[https://launchpad.net/distros/ubuntu/+bug/63741](https://launchpad.net/distros/ubuntu/+bug/63741)

---

### Post by wenzlicker on 2006-10-10
After looking into other problems I'm having, I found that this problem is related to fglrx. Apparently, the fglrx driver doesn't load properly.

fglrxinfo 

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

For what ever reason, the Mesa drivers are loaded. I've tried various fixes that I found on the forums (none worked). Also the ati drivers (the ones from there website - ati-driver-installer-8.29.6.run) gives me the following error when I try to install them:

sudo sh ./ati-driver-installer-8.29.6.run 
Password:
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.29.6.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 176: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

I am going to post this information on the bug report too. Any ideas of what else to do?

---

### Post by wenzlicker on 2006-10-10
Adding:

Section "Extensions"
        Option "Composite" "Disable"
EndSection

:to my xorg.conf allows me to use the fglrx driver; however, when I type ctrl+alt+f<any>, I get a messed up screen (lots of lines and colors). Any ideas?

---

### Post by bi9kahuna on 2006-10-26
Did you find a solution for this?  I'm experiencing the same issue since I upgraded to Edgy 2 weeks ago.

---

### Post by wenzlicker on 2006-10-26
Is your problem the line under the mouse or the tty (Ctrl+Alt+f1)?
Do you have a T60 as well?

---

### Post by bi9kahuna on 2006-10-26
My problem is under X only, not on the TTYs.  I have a Thinkpad T43, which has an ATI Radeon Mobility M300 in it.  My screen resolution is 1400x1050.  This was not a problem under Breezy, and I have not figured out how to make this happen -- it is only occasional.

The line is not always gray; sometimes it is a copy of a portion of the screen, but the shape and size of the artifact is the same as the post in this thread.  Most often it looks like a gray line.  If I can get a screen shot of it I will post it.

---

### Post by wenzlicker on 2006-10-27
Editing the xorg.conf didn't work? After I did that the line disappeared.

---

### Post by Rubbing Alcohol on 2006-10-27
I'd venture the two behaiours might be unrelated. I added the "Extensions" section to my xorg.conf and it solved my "bar" problem, but I can still go to TTY without any problems.

---

### Post by bi9kahuna on 2006-10-30
Ah, I am ok after having added this to xorg.conf:
```
Section "Extensions"
        Option      "Composite" "0"
EndSection
```
I do not have problems switching to the TTYs either.  Thanks for the help.

---

### Post by TrashmanL on 2007-08-11
My problem is not exactly the same, but very similar. While I'm using Ubuntu, I randomly get a grey line either all the way across my desktop, or inside of the active window. I can clear it when it's on the desktop by highlighting the area with my mouse. If it happens within an active window, it's there to stay until that program does something to refresh the window. 

An interesting twist that doesn't make sense to me, is if it's a browser window it occurs in, and it happens across and image file, it's sticky... unless I close and reopen the browser, the picture keeps the grey line in it, even if it's displayed individually or on another page.

One thing in common, is I also have an ATI video card. It's a Radeon All-In-Wonder 7200. I'm not using the fglrx drivers, however.

I have used the Dapper Drake Live CD and currently have a full Feisty Fawn install. Both have the same problem.

---


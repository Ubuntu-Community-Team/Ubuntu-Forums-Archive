---
title: "Desktop wallpaper no longer displayed after failed Desktop sharing session session"
date: 2008-11-07
forum: Desktop Environments
---

### Post by HappySpaceInvader on 2008-11-07
I had been sharing my desktop with a colleague, with the feature to disable the background wallpaper while connected.  We had some problems with the connection and my Desktop Sharing program became unresponsive so I killed its running process (with SIGTERM).

No, regardless of whether I have desktop sharing enabled, my desktop wallpaper is not displayed.  I have tried rebooting my machine, (making sure that desktop sharing isn't started in my default session) but although the wallpaper is briefly display, as soon as my panels are being drawn, the wallpaper disappears and all I can see is the solid background colour.  Changing desktop wallpapers does not fix the problem - the solid colour sometimes changes (depending on the wallpaper's settings), but the actual picture is not displayed. 

Any ideas how I can fix this?

(Using Ubuntu 8.10).

---

### Post by unique on 2008-11-09
I have the same porb but what I did was check the box that said "Disable the Wallpaper when connected" in the Remote Desktop Preferences.  Reboot doesent fix this.

---

### Post by chavita on 2008-11-11
I'm having the same problem, I shared the desktop too, and I enable and then disable the option in the remote desktop config for the wallpaper, nothings happens stills witout wallpaper any sugestion please help us!

---

### Post by chavita on 2008-11-11
I've solved the wallpaper issue, I make a test disabling the option in the System->Preferences->Remote Desktop and disabled in advanced Disable wallpaper. Then I open a image in firefox and sends to wallpaper and MAGIC the wallpaper is in the desktop, then I try to change the wallpaper with the rigth click over the desktop and MAGIC I can change again the wallpapers, hope this helps you pals! grets!

---

### Post by mocha on 2008-11-15
I experienced this same bug.  To fix it, open the gconf-editor, then go to desktop - gnome - background and put a checkmark on draw_background.

---

### Post by sarath_it on 2009-01-12
Happens in my Intepid.. I just resolved using the last advice.. but where should this bug be logged?

---

### Post by LordNouda on 2009-02-19
Thanks guys, this worked for me, too. Hope this won't happen again on the next NX session. Otherwise, any of you have found NX client settings that work?

---

### Post by popfish11 on 2009-02-25
Thanks so much!! this bug bothers me a long time~~:lolflag:

---

### Post by frederik.nnaji on 2009-03-17
> **chavita said:**
> I've solved the wallpaper issue, I make a test disabling the option in the System->Preferences->Remote Desktop and disabled in advanced Disable wallpaper. Then I open a image in firefox and sends to wallpaper and MAGIC the wallpaper is in the desktop, then I try to change the wallpaper with the rigth click over the desktop and MAGIC I can change again the wallpapers, hope this helps you pals! grets!



THANKS, shis one works!
where did anyone log the BUG ? somebody got a proper launchpad link on this?

---

### Post by SuperM on 2009-03-17
This used to happen with me..

> To fix it, open the gconf-editor, then go to desktop - gnome - background and put a checkmark on draw_background. 

Thanks buddy...gonna check it out :P

---


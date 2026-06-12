---
title: "Kubuntu KDE 4.12 &quot;Walk Through Windows of Current Application&quot; fails+strange symbol"
date: 2014-04-02
forum: Desktop Environments
---

### Post by Tim_Banchi on 2014-04-02
I upgraded from Ubuntu with unity 13.04 to 13.10 and recently installed kde 4.12 (according to [http://ubuntuhandbook.org/index.php/2013/12/install-kde-4-12-ubuntu-1310-1204/](http://ubuntuhandbook.org/index.php/2013/12/install-kde-4-12-ubuntu-1310-1204/)) to try out a new DE. The shortcut Alt+` to switch between windows of same application didn't work and I had a look in the system settings where it was set correctly to Alt+` (and Alt+~ for reverse order).

I reset it again just to make sure and instead of ` I got &#6084; 

I found the file where it seems shortcuts are set:  ~/.kde/share/config/kglobalshortcutsrc and changed the shortcut manually  to Alt+` but that doesn't matter for the GUI (see screenshot  [IMG]http://666kb.com/i/cn5p4pb730s4yskki.jpg[/IMG]). It just shows the shortcut I set via the GUI before

I also cannot get the ASCII/HEX/Octal code via vi because as soon as I run the cursor over the symbol it disappears (and the screen crimps a bit), so the line reads
Walk Through Windows of Current Application=Alt+,Alt+`,Naaviguer parmi les fenêtres de l'application courante
instead of 
Walk Through Windows of Current Application=Alt+&#6084;,Alt+`,Naaviguer parmi les fenêtres de l'application courante
I changed the file outside my KDE session (at the login screen) and set the shortcut in the config file to Alt+` and then it is shown correctly in the GUI but it still doesn't work.

So I checked my keyboard layout and everyting seems fine (I type ` now under kubuntu). If I set the shortcut to example Alt+1 it works (but Alt+` would just be nicer)

can someone tell me how I get rid of the strange symbol of how I can set the shortcut manually?

---

### Post by su:bhatta on 2014-04-02
I don't understand the language of your install, but I am using KDE and there the hot keys you mention are behaving correctly. 

My only solution would be to see that the Desktop Effect "Apercus" which is 'checked in the screenshot you have given above is also checked under 'Desktop Effects'-->All Effects.

---

### Post by Tim_Banchi on 2014-04-03
Hello bhattabhishek,

thanks for your reply.

The language is set to french but I have a qwerty keyboard which is  correctly configured (french is set just to learn french  computer-related words).

I will try it out as soon as I get back to this computer which is about mid april.

---

### Post by su:bhatta on 2014-04-03
> **Tim_Banchi said:**
> Hello bhattabhishek,

thanks for your reply.

The language is set to french but I have a qwerty keyboard which is  correctly configured (french is set just to learn french  computer-related words).

I will try it out as soon as I get back to this computer which is about mid april.

No problemo, Tim :)
I have subscribed to the thread, it will keep me up to date .

---

### Post by Tim_Banchi on 2014-05-15
Hello bhattabhishek,          

just now coming back to the kde installation.          In the meantime I have upgraded to ubuntu 14.04, thus using kde     4.13.  I deleted ~/.kde to make sure everything is default and clean. And when starting kde the first time the shortcuts are shown correctly[IMG]http://666kb.com/i/cod8erup99p2xpjqa.jpg[/IMG]

but still the shortcut Alt+` doesn't work, it just does nothing. When I try to set the shortcut again, I get the same problem as in     4.12 with ubuntu 13.10. with the strange character. 

I changed the language back to american english hoping that this woud do something, logged-out&logged-in but the error persists ...  

I also checked the that the apercus effects are as well under "Desktop Effects" -> All     Effects where both options are enabled (one was disabled before)

I freshly installed kubuntu 14.04 on another computer and there wasn't the Alt+` problem, so it seems to be related to my ubuntu 13.04 from last august installation which I upgraded to 13.10 and installed kubuntu-desktop upon - or probably that I changed the language long time ago from English to French... I never changed my keyboard layout and everything else works just fine ... 

 Well, I'm currently helping myself with Alt+1 to switch between windows of the same application. 

 thank you again,

---


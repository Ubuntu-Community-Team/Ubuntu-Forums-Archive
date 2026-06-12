---
title: "ICA client: invisible text"
date: 2009-03-06
forum: General Help
---

### Post by PeterVR on 2009-03-06
Citrix ICA client doesn't show text unless when selected.

When starting published applications, both text in menu's and editable text are simply invisible. 
I'm running Ubuntu 8.04 LTS and installed libmotif3 and the latest Citrix ICA client 11, but was having the same problem with 10. 
Since version 11 asks for libXm.so.4 I simply linked it in /usr/lib:
```
peter@viking:/usr/lib$ ls -l *Xm.so*
lrwxrwxrwx 1 root root      14 2009-03-06 18:27 libXm.so.3 -> libXm.so.3.0.2
-rw-r--r-- 1 root root 2349356 2007-04-30 11:42 libXm.so.3.0.2
lrwxrwxrwx 1 root root      10 2009-03-06 18:08 libXm.so.4 -> libXm.so.3
peter@viking:/usr/lib$ 
```
I reckon this doesn't cause the problem though - like I said I experienced the same problems before.

Any suggestions? 
See also screenshot: I opened Firefox local (browsing to the published apps), started IExplorer and MSWord Citrix published. I changed the Word text color into red but still you can only see selected text.

---

### Post by PeterVR on 2009-03-11
bump

---

### Post by TenDollarMan on 2009-03-14
If you RTFM for the Citrix Receiver guide, it tells you:
> 
The Citrix Receiver for Linux supports Red Hat 7.1 or above, and other
distributions that include the standard C library, glibc, Version 2.2.2 and above.
***The client also requires OpenMotif 2.3.1***.

This is how you get libXm.so.4

I have had a world of pain trying the install.  My errors are type 1.

I fail.

---

### Post by lunatico on 2010-03-11
Did you ever got this fixed?

I have used it on many Ubuntu 9.04 and 9.10 systems and never had a problem until now that I installed on a VMWare VM 9.10 and when I launch Excel 2003 for example the menus and text are blank, replaced with a dash.

---

### Post by PeterVR on 2010-03-11
> **lunatico said:**
> Did you ever got this fixed?

I have used it on many Ubuntu 9.04 and 9.10 systems and never had a problem until now that I installed on a VMWare VM 9.10 and when I launch Excel 2003 for example the menus and text are blank, replaced with a dash.

Nope.
I just used an other (9.04) laptop. When I occasionally needed a Citrix app on the 8.04 I just selected all of the text - it became visible while selected.

Good luck.

---

### Post by ostromark on 2010-06-03
I encountered this problem on another linux, not Ubuntu, but I suspect that the solution may be the same.  I was using the nvidia display driver with 16-bit color depth, and found that for the citrix client to display text properly I had to set the color depth on the connection properties to 16-bit (32 thousand colors).  If it was set to 24-bit/16 million colors the text was invisible.  I couldn't find this documented anywhere.

---

### Post by Mid West Kevin on 2010-06-07
[COLOR=black][FONT=Arial]Legacy Video Cards will sometimes fail to show the resolutions needed when opening a published application.  The degradation shows up in the “Radio Buttons”, “Checkboxes” displays only the mouse target area not any of the details.  It doesn’t look like its suppose to.  The “Child Windows” won’t display text an example would be e-mail.  Main page shows your inbox listing of e-mails.  When I opened an e-mail the text is missing.  The “Windows Minimize”, “Windows Maximize” and “Windows Close”  on the top right corner only shows the mouse target area in a box, not the symbol (-,X)  I was using an older 16M VooDoo Video Card when this occurred.[/FONT][/COLOR]
[COLOR=black][FONT=Arial][/FONT][/COLOR] 
[COLOR=black][FONT=Arial]I swapped out the video card with a [/FONT][/COLOR][COLOR=black][FONT=Arial]Rage ATI card and now the text and such display.   I'm not saying this is the right fix, but it did work for me. [/FONT][/COLOR]
[COLOR=black][FONT=Arial][/FONT][/COLOR] 
[COLOR=black][FONT=Arial]I trying to bet a bunch of old Dell 450's, 500's and 550's running Ubuntu and the Citrix Web Interface.  So; I have plenty of old video cards to try.[/FONT][/COLOR]

---

### Post by Mid West Kevin on 2010-07-14
If you change the "Window Color" in the Citrix Receiver.  This is done as follows, With the Citrix Receiver opened. Highlight the published application.  Select Connections from the Main Menu.  Properties from the drop-down menu and then click on the button at the top left of the properties dialog.  Select Window and then "Window Color"  I found 32 Thousand works for me.
In the Citrix Web Interface I found High Color 16 bit works.

I hope this helps.

---

### Post by PeterVR on 2010-09-25
Hiya
Thanks for your response.
I only got to test this today... No success unfortunately.

---


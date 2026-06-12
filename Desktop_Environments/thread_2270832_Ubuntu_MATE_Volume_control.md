---
title: "Ubuntu MATE Volume control"
date: 2015-03-25
forum: Desktop Environments
---

### Post by Joe_Johnston on 2015-03-25
Hi All,

Is there a way to control the volume in Ubuntu MATE with the mouse scroll via hover and not having to open the volume control to adjust it? Almost every other distro allows mouse hover volume control except Ubuntu MATE and I wondered if anyone knew the answer. Thank you.

---

### Post by Dennis N on 2015-03-27
You can if you use Ubuntu Mate 14.10 or the upcoming 15.04 (now in beta). These both lack the sound menu of Ubuntu Mate 14.04, but do allow you to adjust the sound with the mouse wheel when hovering on the panel icon.

(The difference is 14.04 by default uses indicator applets, while the other two by default do not. I think the indicator applet for sound in 14.04 is at fault.)

---

### Post by Joe_Johnston on 2015-03-27
Thank you for the input! I was just surprised to see other MATE distros with it working properly but not in Ubuntu MATE. I would love if I could get it working with mouse scroll as it would be the perfect distro for me.

---

### Post by Dennis N on 2015-03-27
There almost certainly must be a way to revert to the "good" volume control for Ubuntu Mate 14.04. Martin Wimpress (Ubuntu Mate Developer) reconfigured Ubuntu Mate 14.04 to use indicator applets, but didn't do that in 14.10 and 15.04. So 14.10 and 15.04 use the "old" volume control which works like you (and I) would like (but without a sound menu). Linux Mint Mate 17.1, which is also a LTS, uses the old volume control as well. I have it installed on one of my computers and like it. So that is a good option if you want long term support.

I may see if I can get directions how to fix 14.04, but I have been using the 15.04 beta1 which is working well.

---

### Post by Joe_Johnston on 2015-03-27
Thank you for the input, Dennis. I used the LM MATE and it works perfectly but I imagine there is a way to make this work for Ubuntu MATE.

---

### Post by Joe_Johnston on 2015-03-27
Okay, figured out how to get mouse scroll volume control back!

Go to Control Center, then into MATE Tweak, then Interface and from the Panel layouts dropdown select a different layout such as I did with Redmond with MATE Menu and then you have mouse scroll volume control. 

Apparently it is not available with the default layout but is available in a few of the other layouts. Hopefully this will help others out who were curious or looking for answers.

---

### Post by v3.xx on 2015-03-27
Nice find :)

But changing this setting has wiped out my custom panel.  It can be rebuilt, just a heads up for others.

Edit
Also wiped out my custom menus .. crap ..

---

### Post by Joe_Johnston on 2015-03-27
Yes, I realized after switching them around it does make you reconfigure the new menu settings. It is a pain but should only need to be done once. Thanks for pointing that out.

---

### Post by v3.xx on 2015-03-27
I should of had backup in place, that won't happen again :)

---

### Post by Dennis N on 2015-03-27
Thanks for finding the Mate Tweak method, but after considering the warning, I looked for another way that would not alter my panel setup and customizations. This is the procedure I came up with (actually easier than I thought):

1) Add **mate-volume-control-applet** to startup applications (Control Center > Startup Applications). You need to create the entry: Click "Add". Name: Volume Control; Command: mate-volume-control-applet; Description: whatever you like. Close the dialog.

2) Unlock and remove "indicator applet complete" from panel by right-click and select "remove from panel" (right-click in area of network and volume icon).

3) Restart.

4) Result shown in attached images. Other than the volume control, the panel setup and user customizations are unchanged.

---

### Post by Joe_Johnston on 2015-03-27
Very nice, thank you, Dennis!!

---


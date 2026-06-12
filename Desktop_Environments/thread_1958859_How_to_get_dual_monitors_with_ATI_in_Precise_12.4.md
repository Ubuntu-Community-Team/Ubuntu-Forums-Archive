---
title: "How to get dual monitors with ATI in Precise 12.4"
date: 2012-04-15
forum: Desktop Environments
---

### Post by Dscottmc7 on 2012-04-15
I have **Precise 12.4**...won't take ATI/AMD Prop...but I have **dual monitors** in **Precise 12.4** (“OneWideScreen”).  Here is what I had to do:

Boot to the "Recovery Mode."  You'll see the Menu, (Resume... Network, etc.)

Scroll down to "Network" ENTER
-you should then get back to the menu, but if not, hit Ctr-d

Scroll to "Drop to Root..."  Enter the following commands:
$ rm xorg.conf

$ apt-get install FGLRX (Ubuntu Supported Binary driver -ATI-base)

$ reboot

Reboot to full graphics  mode.  
Once both screens are live go to "Settings" and click on "Display"
You see both of your displays.  

Click "ON" for each.  Two (2) things to note:
 1.  Check the resolution for each one.  Normally you'll want this to be the same setting for each monitor.  However I have a 1920x1200 ("24" DIV) and a 1920x1080 (23" HDMI) so I have each monitor configured to its maximum resolution.  Be careful, however, with that setup as when you drag a folder/file from the larger screen to the lessor it can get "stuck" (bothersome...but if so, just double click to get it back).
2. I chose my Left (Acer) Monitor for my "Launcher Placement."  This gives a full wide screen display and the icons only show on the far left (Acer)
/home/dscottmc1/Documents/Ubuntu-All-Things/Desktop.gif

---


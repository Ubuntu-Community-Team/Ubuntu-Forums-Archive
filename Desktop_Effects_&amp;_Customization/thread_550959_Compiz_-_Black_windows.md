---
title: "Compiz - Black windows"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by chadford on 2007-09-14
I recently got my compiz-fusion install to work ( thanks to a script I found on these forums )...most of the effects are working spot on....but sometimes when i open new windows ( ie. mozilla, openoffice, even terminal sometimes ) the window will be entirely blacked out.  If i go to resize the window smaller the text will appear...but once i make it larger again the black returns.   I did a search, but couldn't seem to find any answers.... ideas anyone?
thanks,
-chad

---

### Post by smartboyathome on 2007-09-14
Try doing this with compiz running in a terminal (use compiz --replace, let compiz completely load, and then try to duplicate this error and post the result here.

---

### Post by chadford on 2007-09-14
> **smartboyathome said:**
> Try doing this with compiz running in a terminal (use compiz --replace, let compiz completely load, and then try to duplicate this error and post the result here.

Compiz is completely loaded.  Once a window is expanded beyond a certain size it goes black...i can't make the window viewable again until i shrink the window to a certain size.  This even works with the maximize button in the upper right corner of the window...if i maximize firefox it is black until i restore to its normal size.
-chad

---

### Post by smartboyathome on 2007-09-14
Running compiz in the terminal will give an error message. We will need this error message to help you. Please run it in the terminal.

---

### Post by FuturePilot on 2007-09-14
This is most likely the Nvidia black window bug. You won't find any errors from this. It's a Nvidia bug, not a Compiz bug.

---

### Post by chadford on 2007-09-14
> **FuturePilot said:**
> This is most likely the Nvidia black window bug. You won't find any errors from this. It's a Nvidia bug, not a Compiz bug.

compiz --replace didn't  yield any errors....are there any workarounds to the nvidia prob?
-chad

---

### Post by Rupertronco on 2007-09-14
> **chadford said:**
> compiz --replace didn't  yield any errors....are there any workarounds to the nvidia prob?
-chad

Start by making sure your driver is the most recent. If the problem persists please post after you've updated or confirmed you have the newest driver.

---

### Post by FuturePilot on 2007-09-14
The workaround with Compiz-Fusion is to use Indirect Rendering. I'm not sure of the command though to start it with indirect rendering.

---

### Post by atoma on 2007-09-17
I'm running Feisty on a laptop with a Mobility Radeon 7500 and experiencing the same problem (except that windows are white instead of black). Is it really an NVidia bug? I found that, in order to start Compiz-Fusion with indirect rendering, it is enough to add the option "--indirect-rendering" to the command line. I'll give it a try and let you know (unless you have your installation at hand and don't want to wait).

---

### Post by atoma on 2007-09-19
Hi guys,

the situation has now completely changed. No blank windows anymore when I logged back into my Feisty installation. I'm also able to open a wealth of windows at the same time with no problem. No need to add the '--indirect-rendering' option. Still wondering what's changed :confused: . I remember I had a similar problem after installing metisse on the same laptop (a P4 Sony Vaio with 256 MB of RAM and 16 MB of video RAM). I'll let you know if something comes out.

Regards.
Antonio.

---


---
title: "Beryl installed...but I'm not seeing any eye candy"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by matches on 2007-07-30
Hello all,

I have Beryl installed but I am not seeing any Beryl goodness. The BSM is there...but there is no make it go button :). I am thinking that it my be my video card driver. Which brings me to my second Q: Where do I find info on my video card? I looked at System/preferences/Hardware Information but didn't see anything for the video card. Thanks for any help!

---

### Post by srhlefty on 2007-07-30
Beryl manager running doesn't mean Beryl is active.  This is because it allows you to switch between the ordinary window manager (metacity) and the Beryl window manager.

To check, right-click on the Beryl manager icon in the tray, go to "Select Window Manager",  and then see which of the radio buttons is selected.  Click the "Beryl" option to activate the Beryl WM.

If, after a few screen flickers, you check the setting again and it has returned to "Metacity", that means the Beryl WM is crashing.  Such a topic is discussed on many other threads, so I won't go in to it here.

To see some information about the capabilities of your video card, try opening up a terminal and executing the command glxinfo

---

### Post by matches on 2007-07-30
Thanks for the quick reply. However, I am not seeing Beryl in any tray. All there is is the network manager and a volume icon.  Is there another place to find the window manager? Thanks

---

### Post by Technoviking on 2007-07-30
Try this.
```
Alt-F2
```
then
```
beryl-manager
```
and see if beryl eye candy starts.

---

### Post by matches on 2007-07-30
Nope, said file could not be found. Besides the obvious; what does that mean?

---

### Post by smartboyathome on 2007-07-31
You don't have Beryl Manager installed. Simply run:
```
sudo apt-get update | sudo apt-get install beryl-manager
```
And then run Beryl Manager via the System Tools GNOME menu (Applications > System Tools).

---

### Post by matches on 2007-07-31
Cool, I am a step closer! Now when I right click on the Berly Manager icon in the tray I choose Beryl instead of Gnome and nothing happens and it just goes back Gnome. What do I need now? Thanks a lot for all this quick help!

---

### Post by srhlefty on 2007-07-31
At this point you're in the same boat as many others...beryl is crashing on you, and you need to figure out why.  There are lots of threads that deal with this issue, I'd do some searching around.

---


---
title: "Maximize and cube problem on Gusty RC"
date: 2007-10-16
forum: Desktop Environments
---

### Post by ericmitz on 2007-10-16
Hello all, 

I recently installed Gusty (after having Fiesty) from scratch on my Dell latitude D610. For the most part everything is working great. But there is one big problem I am having a hard time dealing with.

Whenever I maximize a window, it only fills an area of about 800x600 pixles, and not the whole screen! Whenever I rotate my cube, It looks like I have a smaller desktop within my Desktop. A screen shot is attached.

Anyone have any ideas? this is getting more annoying the more I use my computer.

Thanks.

---

### Post by ericmitz on 2007-10-18
please help...

i know everyone is busy with the big release today, but i could really use some help on this. its super annoying.

---

### Post by WakkiTabakki on 2007-10-18
Hmm... weird...
Try starting the compiz config manager and check under "General" and make sure "Detect outputs" is checked (not entirely sure what it says, I'm not on Ubuntu atm)

Edit:
Ok, got Ubuntu up and running:
1. Start compiz config manager
2. General Options
3. Display Settings tab
4. Make sure "Detect outputs" is chekced

If it doesn't fix it, add you resolution to the list of "Outputs" and make sure it's on top (I'm guessing it says 800x600+0+0 there now, right?)

/N

---

### Post by ericmitz on 2007-10-18
I actually had to UNCHECK "Detect output". simply adding my resolution did not help.

oh well, its working now.

many thanks.

---


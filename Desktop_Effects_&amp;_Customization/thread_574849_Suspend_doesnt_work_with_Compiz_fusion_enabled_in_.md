---
title: "Suspend doesnt work with Compiz fusion enabled in Gutsy Gibbon, worked on feisty"
date: 2007-10-13
forum: Desktop Effects &amp; Customization
---

### Post by climatewarrior on 2007-10-13
My suspend works perfectly on gutsy when I dont have compiz enabled. When I have compiz enabled the computer goes to sleep and when I start it again the dialog box for entering the password d appears. I enter the password and after that the screen stays completely blank and the only thing that appears is the mouse cursor, which I can stil move around.

I already tried 

 in General Options of Compiz Config going  to Display Settings and disabling Sync to VBlank

and 

"If problem persists also try changing some values in /etc/default/acpi-support

most notable change should be changing POST_VIDEO=true to POST_VIDEO=false"

My video card is an Intel integrated graphics card and im using the experimental modesetting driver. My laptop is a dell latitude x300

I also had compiz fusion in feisty fawn and suspend worked perfectly with that.

Any help with this is appreciated thanks!

{update}

Now suspend works sometimes. It is very random, I dont see any connection to what I do an why it works sometimes 

{/update}

---

### Post by rorzer on 2007-10-13
I have the same problem here.  This problem persists with i810 driver + compiz.

My workaround for the present is to disable compiz.  

This bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/150109](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/150109)

describes the problem we're having.  You might want to comment on that too.

---


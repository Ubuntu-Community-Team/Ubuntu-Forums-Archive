---
title: "[SOLVED] Cannot view video with advanced desktop effects enabled"
date: 2008-01-29
forum: Desktop Effects &amp; Customization
---

### Post by spleencheesemonkey on 2008-01-29
Hi All,

Any suggestions?  I'm running Gutsy on a ATI Radeon 9800 pro, drivers installed by envy.  With no desktop effects I can run video and see it fine using a variety of players.
With desktop effects enabled however it will only play sound.  It is the same for any visualisations within music players.

Any help would be appreciated.

---

### Post by ScottKidder on 2008-01-29
try enabling the Video Playback plugin in ccsm?

---

### Post by spleencheesemonkey on 2008-01-29
Thanks for your reply Scott,

How do I go about that? and What is CCSM?

---

### Post by ReddogOne on 2008-01-29
I get the same problem (I have onboard graphics... not sure which one but its a Dell) but only with full screen video. 

As you suggest it seems to be a problem is having desktop effects on. I had a quick search related to the possible solution posted but the bits I could find were not quite the same problem. 

May need to investigate (look at the web) more later as I like videos AND wobbly windows ;)

---

### Post by spleencheesemonkey on 2008-01-29
Nice to know I'm not the only one with this problem reddog.
Let me know if you find anything.  I will have a look this evening when I get back from work.
Right now this is the only thing that's stopping me from having my OS exactly as I want it. :)

---

### Post by Cochise on 2008-01-29
Have a look at VLC. In the preferances / options you'll see an option to enable advanced settings click this. Then select video output (i think) and select X, worked for me, at work at the moment so i'll post proper instructions when im home

---

### Post by Cochise on 2008-01-29
OK This worked for me:

1. Click Settings and then Preferances
2. Tick the box in the buttom right saying "Advanced Options"
3. Expand Video
4. Click Output Modules
5. For modules select "X11 VIdeo Output"
6. Click OK
7. Restart X

Hope it helps..................

---

### Post by spleencheesemonkey on 2008-01-29
Cochise,

You're an absolute Gem! It worked.  How on earth did you find this out?

Thank you so much.  

The monkey of cheesey spleen-ness.:)

---

### Post by Cochise on 2008-01-30
figured it out months ago when i was unemployed and wanted cmpiz and video at the same time :lolflag:

---

### Post by dbqp on 2008-02-16
This solved my problem as well! Thanks for taking the time to post the solution...

:)

---


---
title: "Vostro 1400 nvidia 8400gs svideo out nightmare"
date: 2009-03-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by diectus on 2009-03-24
Ive been trying to find an answer to this for months but it's driving me nuts now. When I try to connect my laptop via s-vid to my rca 50" projection tv the edges are cutoff. cant find a way to fix. If I had some form of OVERSCAN control somewhere, that could do it, but I cant find a way to control that. which seems odd because from what Ive read in other situations it is available. The real problem is I assured my GF that when I TOTALLY switched both our laptops to linux for the good of the world that I could get everything to work due to the great support, I havent heard the end of it since this situation. Her laptop is a whole other thread but this comes first. thanks for you help.

---

### Post by sirjoebob on 2009-03-24
Are you using the nvidia settings applet? It is installed from Synaptic and automatically adjusts my screen resolution, etc on multiple TVs and external displays I have used. May solve your issue.

---

### Post by diectus on 2009-03-24
yeah I tried that with no luck. Ive tried adjusting with no luck. I feel if I could set the resolution for the tv to 1280x800 it would work but it only lets me set the tv to 1024x768. I've had no luck trying to force it to a higher res.

---

### Post by sirjoebob on 2009-03-24
TV probably doesn't support any higher resolution through s-video. It isn't the best video cable.... I have a vostro 1500 and use the nvidia settings applet just fine. Explain a little more about what is happening when you enable the tv? Did you make any custom changes to the xorg.conf file?

---

### Post by diectus on 2009-03-24
so here is some info-
   the xorg.conf file is basic... no change
   I plug the s-vid into my comp run nvidia-settings from the terminal
   click detect displays
   it pops up- config is set to twinviw
   resolution 1024x768
   position absolute
   my laptop screen is set to 1280x800
   but even if I set it to 1024x768 it still doesnt match the tv
   Im on intrepid and my driver for nvidia is the 180.11
   any ideas

---

### Post by sirjoebob on 2009-03-24
Alright, thanks for the info. When you say doesn't match the screen what is going on? When you maximize a window on the TV, does it extend off the screen or what?

Also, are you using any kind of zooming or stretching on the TV? It may be that you have it stretched/zoomed for watching standard-def television and have not taken away the zoom. I had that issue a couple times before I figured it out. Also, is this an HDTV/standard TV?

---

### Post by diectus on 2009-03-24
whats happening is the picture is getting chopped on both sides as well as top and bottom. For example with firefox maximized I cant see the maximize or close buttons on the tv that I can see on the laptop. Same amount cut on the left side as well as the top and bottom. I can barely see the panels on the top and bottom. thats why I was led to believe it was an overscan issue. Yes the tv is an HD tv. This probably doesnt help but it worked on windows. Any ideas?

---

### Post by diectus on 2009-03-24
also no zoom or stretch... just checked.

---

### Post by sirjoebob on 2009-03-24
Dang... this is getting potentially above my head then...

---

### Post by sirjoebob on 2009-03-24
Try going to the advanced option for that display and make sure the panning or any other options are set to the same resolution. It may be easier (and provide better resolution) if your tv has a monitor hookup (vga, div, etc) and you use that method instead.

---

### Post by diectus on 2009-03-24
yeah panning is all the same. I think your right that the best best is gonna be a vga and get rid the damn s-vid. Ive been think that, I just wanted to see if anyone had any ideas. Thanks for your help though.

---

### Post by sirjoebob on 2009-03-24
I have been battling the same thing for a while. I already HAVE an s-vid cable, so I don't want to buy a longer VGA but the quality would be worth it. I wish I had HDMI out....

---

### Post by diectus on 2009-03-24
Yeah same that the only qualm I have with this laptop. besides that its been a tank. I wish I could just add an HDMI out to it.

---


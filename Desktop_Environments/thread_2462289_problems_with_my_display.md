---
title: "problems with my display"
date: 2021-05-17
forum: Desktop Environments
---

### Post by jgw on 2021-05-17
I have been having a problem with my display. I have two machines sitting here. One is justs fine and one has its home screen lower than the other by about a quarter of an inch. I have studied the settings on both machines and they seem the same.  I am using a acer a231h monitor and my screen size is 1920x1080. I can't figure out why one of my machines has a display which is a quarter of an inch lower than the other. I have my dock at the bottom of the screen and my icons are cut in half. I have tried to move the screen up and failed.  This is very strange in that it was working just fine.  This leads me to believe that I have screwed something up but I can't find it.

I checked my two machines again. Neither one is using a display driver.   The first machine is using a geforce gt 440/pcie/ssp2 for graphics/display (I think this one is a display card).  This machine has a display that fits the monitor.  The other machine is using AMD® Rs780 (from the motherboard) and I cannot make the display fit the monitor screen (output is about 1/4 inch down from top of display). Neither machine is using an additional driver. I also have some display cards which I think all work.  They are:
geforce 8500 gt hdcp, ;p/n 256 p2n741-i-pl 256mb pci-e
geforce 210 512mb ddr2 w/crt/dvi/hdmi/pcie
geforce 8600gt (pci-e) 512mb ddr2+dvi+hdtv out+crt+hdcp

I would appreciate any thoughts on this one.  Perhaps I should stop using the graphic output of the motherboard and move to one of the display cards.  I guess I could sit here and try everything but, I suspect, there is somebody who knows the answer to my mess.

Thank you.....................

Thoughts?

---

### Post by jgw on 2021-05-19
bump

This morning I turned on my machines. One of them booted to 1024x768.  I then rebooted and it came up correctly - 1920x1080.  This has happened before, have no idea why, thought I would add it to this. 
At 1024x768 the display fit the monitor.

---

### Post by Autodave on 2021-05-19
You should not be using the MB graphics output along with a graphic's card output.  Hook all monitors to the graphics card and see if that cures the issue.

---

### Post by jgw on 2021-05-19
Thanks for the reply.  I currently don't have a display card and am using the MB graphics. I think you are telling me to put in a display card which I will do today. Just finished installing the graphic card and, now, the problem is solved.  it may seem strange but I needed somebody to tell me, basically, to get off my butt and just fix it.  There are still no additional drivers. This graphics card was the geforce 8600gt (pci-e) 512mb ddr2+dvi+hdtv out+crt+hdcp.

Thanks again!

---

### Post by him610 on 2021-05-19
> This graphics card was the geforce 8600gt 
Yes, I used to have one of those, mine was passively cooled with a heat sink. I think I wound up donating it. Several years ago, Nvidia quit supporting that particular GFX with updated drivers, and a short while later the open source community also quit its support also. 

What you currently see is what you get; I don't believe there is any way to update it. On the bright side though, you said it solved your problem.
You can probably can get a used GT710 or GT730 fairly cheap.

---

### Post by jgw on 2021-05-25
bump

I installed 21.04 on the machine that had 20.10 on it.  Then I went to a backyard sale and somebody had a samsung syncmaster 2494hm for sale for 10 bucks which I bought.  Now both my machines have the new monitor filed up and all that is dandy.  But, I have a new display problem. I run both these machines through a kvm.  If I try and start them at the same time the one connected to the monitor is fine but the other one's resolution, normally 1920x1080 magically goes to 1280x720. If i reset it, whilst connected to the modem its 1920x1080.  So, the machine needs to be conected to the modem to but up the display properly. I have never had this happen before.  I also rebooted the machines, one at a time. Didn't make any difference. If either one is not connected to a monitor they boot up with 1280x720.

Thoughts?

---

### Post by jgw on 2021-06-07
I thank everybody for the help.  

I installed a video card, hooked up the new monitor, turned everything back on and everything worked!  

I will mark this one as solved - thanks again!

---


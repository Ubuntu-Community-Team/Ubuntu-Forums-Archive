---
title: "Need help, hardware issue"
date: 2009-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Yaakke on 2009-05-22
Hello,
I'm pretty new to Ubuntu and this is my first post on these forums ever, so I apologize in advance for any lack of knowledge in either of these areas. A couple months ago Ubuntu was made the sole OS on this system (version 8.10), and it has been running fabulously. I really am a Ubuntu afficianado now. 

Anyway, the problem came when my monitor started showing strange white lines that ran all the way through it. The screen would occasionally quiver. I would reset the computer and everything would be fine. About a week later the problem got worse and the white lines got bolder. About another week later everything totally crashed, random symbols were everywhere and solid blocks of color would appear on the screen. I could not make out anything on screen. I first tried switching out the monitor, but that wasn't the issue. I then figured it was the video card, and to test this I first tried resetting it, but it didn't help any. So then I went to borrow a friends old video card, and when using theirs everything worked fine (albeit I had to run in and am still running in low graphics mode). However, their video card uses a PCI slot, and the video card my system came with was in the PCI-E slot. I didn't think to test if it was the port that was broken unfortunately, and I went on to buy a nVidia GeForce 9600 GT.

The current driver I had listed that the new model I bought was covered. I also checked this forum and the compatability list said this model would be fine when working with Ubuntu. When I first tried the new graphics card the fan turned on but nothing showed up on screen. I tried resetting the video card, and this time the fan did not turn on when I started the computer. It's at this point that I decided to upgrade to 9.04 Ubuntu thinking maybe there was some chance it had something to do with the drivers, and that I could try reinstalling the drivers upon upgrading. I then thought of trying out a new test while the system was upgrading. I plugged in the broken video card, and the working video card at the same time and went to the boot menu after changing the priority to PCI. The boot menu recognizes the broken cards existence in the port, but its still impossible to load from that card. I did the same test but with the new video card and the boot menu says that there is nothing populating that slot (Note, the fan turned on during that test, and has continued to each time I start the computer, it seems like it was just that one time it failed earlier). 

In addition to this, ever since I've upgraded to 9.04, I always get a blue screen with this message which I've never seen before and have no idea what it means, "There already appears to be an X server running on display :0. Should another display number be tried? Answering no will cause GDM to attempt starting the server in :0 again (You can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go to console 7. X servers usually run on console 7 and higher)."

So that's where I am now. I am led to believe that I might have goofed on the compatibility issue between the card and my motherboard, though I originally thought it was fully compatible. The card: nVidia GeForce9600 GT (PCI express x16). My system: Dell Dimension 9200 small business desktop computer (with a 2gb RAM upgrade I did myself at a later date).

So based on these tests I did, what seems to be the most likely problem and solution? Is it possible the port or new video card or motherboard is broken? Or maybe is there some sort of software issue or settings I need to alter to make it recognizable/usable? Or did we mess up and order an incompatible video card? In which case I might rather be interested in upgrading the motherboard rather than replace the video card (and what would be a compatible motherboard?).

Sorry for the long post. I am grateful for those who took the time to read through it all. Any suggestions would be greatly appreciated.

---


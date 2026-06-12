---
title: "Why is X11VNC incredibly slow on a gigabit lan?"
date: 2009-03-16
forum: General Help
---

### Post by sofakng on 2009-03-16
I'm new to Ubuntu (and Linux) but I've installed x11vnc (sudo apt-get install x11vnc) and then I run "x11vnc -display :0 &" to start the server.

After that I use RealVNC VNC Viewer on my Windows Vista machine to connec to x11vnc and it works but it's incredibly slow.  (eg. it's unusuable)

I've checked my RealVNC settings and it's only requesting low color (8 colors) and it's definitely not a bandwidth issue since I'm on a gigabit lan so what else is going on?

Do I need to configure something else?

Also, how do I get x11vnc server to start with X?

---

### Post by krunge on 2009-03-16
> **sofakng said:**
> I'm new to Ubuntu (and Linux) but I've installed x11vnc (sudo apt-get install x11vnc) and then I run "x11vnc -display :0 &" to start the server.

After that I use RealVNC VNC Viewer on my Windows Vista machine to connec to x11vnc and it works but it's incredibly slow.  (eg. it's unusuable)

I've checked my RealVNC settings and it's only requesting low color (8 colors) and it's definitely not a bandwidth issue since I'm on a gigabit lan so what else is going on?


How fast is your graphics card's *read* rate? (not write rate)

x11vnc prints out how fast your read rate is:
```

16/03/2009 13:17:07 Autoprobing TCP port 
16/03/2009 13:17:07 Autoprobing selected port 5900
16/03/2009 13:17:08 fb read rate: 10 MB/sec
16/03/2009 13:17:08 screen setup finished.
```
Please post what it prints out for your card.

Most Xorg drivers are slow like the above (10 MB/sec). This will be the bottleneck on fast LAN. E.g. it takes 0.5 seconds to read in a single 1280x1024x32 screen, so the most you could expect is 2 of those frames per second.

Nvidia drivers can be 400+ MB/sec and this makes a very big different for LAN usage.  Also, if one must use Xorg drivers and he doesn't care much for very fast local performance, he can set the ShadowFB option in xorg.conf.

More info [Here.]("http://www.karlrunge.com/x11vnc/#limitations")

---

### Post by Berserker v7 on 2009-03-16
maybe you can try out tightvnc... i have not tried x11vnc, but on this one, i get reasonably good performance on a 100Mbps line..

---

### Post by krunge on 2009-03-17
> How fast is your graphics card's *read* rate? (not write rate)


If the read rate limitation is not the problem here are some other things one can check.

1) Try adding the option "-noxdamage" to the x11vnc command.  In compiz/Xorg the XDAMAGE extension is broken (changes happen to the screen but are not reported to apps who are interested in changes like x11vnc.)

2) Make sure the connection is not using the "raw" or even "hextile" encoding. The "raw" encoding has no compression and can be slow even on LAN.  Here is x11vnc output showing this problem:

```

17/03/2009 20:18:24 Pixel format for client 127.0.0.1:
17/03/2009 20:18:24   32 bpp, depth 24, little endian
17/03/2009 20:18:24   true colour: max r 255 g 255 b 255, shift r 16 g 8 b
17/03/2009 20:18:24 Enabling X-style cursor updates for client 127.0.0.1
...
17/03/2009 20:18:24 **Using raw encoding** for client 127.0.0.1

```

---

### Post by sofakng on 2009-03-18
Thanks for the replies!

I'll try "-noxdamage" when I get home but noticed two things from my logfile:

1) The fb read rate is 362 MB/sec.
2) It appears as though I'm using ZRLE encoding but for some reason it switches to hextile.

Can somebody check my log file?  It's located here: [http://pastebin.com/mf0088e4](http://pastebin.com/mf0088e4)

EDIT: I'm using RealVNC on Windows Vista to connec to x11vnc and I have the encoding set to "Auto select" (and ZRLE is an available option so it should work...?)

---

### Post by krunge on 2009-03-18
> **sofakng said:**
> 
I'll try "-noxdamage" when I get home but noticed two things from my logfile:

1) The fb read rate is 362 MB/sec.

That's a good read rate, so it shouldn't be the problem.  Using Nvidia drivers, correct?

> 2) It appears as though I'm using ZRLE encoding but for some reason it switches to hextile.

Hextile should be OK on fast LAN. I did a test and it seems a bit faster than ZRLE (but it uses a lot of bandwidth.)

> Can somebody check my log file?  It's located here: [http://pastebin.com/mf0088e4](http://pastebin.com/mf0088e4)

Your log looks pretty reasonable.

Can you define and quantify which activities are slow, your estimate how long they are taking, etc.? Thanks.

> I'm using RealVNC on Windows Vista to connec to x11vnc and I have the encoding set to "Auto select" (and ZRLE is an available option so it should work...?)

You probably don't need to play with that, but you can if nothing else works.  I hope the problem is the xdamage bug...

BTW, in the past I have noticed slower than expected response running vnc viewers on Windows machines over a LAN.  Do you have a 2nd Linux machine you could run the viewer on as a test? Maybe boot the windows machine with a Linux live-cd?

---

### Post by sofakng on 2009-03-19
I've tried the -noxdamage parameter and it solved my problem!

Thanks so much for the help.

One last question though...

How can I get x11vnc to always run in the background and not exit after I disconnect a vnc session?

My system is setup so that tty2 uses autologin and "startx" is executed using .bash_profile.  (eg. it's a home theater PC that uses Ubuntu)

---

### Post by krunge on 2009-03-19
> **sofakng said:**
> I've tried the -noxdamage parameter and it solved my problem!

Great, I am glad it is working for you!

It is unfortunate that Xorg hasn't fixed this bug going on 3 years now. Feel free to add yourself to the bug report.

The main problem seems to be the X server's interaction with the (very silly IMHO) compiz/beryl, etc. compositing window managers. I think going back to a normal window manager would allow x11vnc to work with XDAMAGE (this gives a nice performance improvement.)
> 
How can I get x11vnc to always run in the background and not exit after I disconnect a vnc session?

My system is setup so that tty2 uses autologin and "startx" is executed using .bash_profile.  (eg. it's a home theater PC that uses Ubuntu)

Have a look at these:

    [http://www.karlrunge.com/x11vnc/faq.html#faq-service](http://www.karlrunge.com/x11vnc/faq.html#faq-service)

    [http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

It is the '-forever' option that keeps it waiting for more connections.  Perhaps there is a 'xclients' or 'startup' script you can add the x11vnc command to.

Search these forums for 'x11vnc forever' and I think you'll get some useful ideas.

---

### Post by swarup on 2009-06-01
> **krunge said:**
> How fast is your graphics card's *read* rate? (not write rate)

x11vnc prints out how fast your read rate is:
```

16/03/2009 13:17:07 Autoprobing TCP port 
16/03/2009 13:17:07 Autoprobing selected port 5900
16/03/2009 13:17:08 fb read rate: 10 MB/sec
16/03/2009 13:17:08 screen setup finished.
```
Please post what it prints out for your card.

Most Xorg drivers are slow like the above (10 MB/sec). This will be the bottleneck on fast LAN. E.g. it takes 0.5 seconds to read in a single 1280x1024x32 screen, so the most you could expect is 2 of those frames per second.

Nvidia drivers can be 400+ MB/sec and this makes a very big different for LAN usage.  Also, if one must use Xorg drivers and he doesn't care much for very fast local performance, he can set the ShadowFB option in xorg.conf.

When you talk about the graphics card's read rate, is that referring to the graphics card in the server computer or the viewer computer? The fact that you are referring to this in relation to x11vnc, makes me think it may be the server computer's read rate to which you refer-- but then the server computer is *sending* and the viewer computer is *reading*, so it doesn't completely make sense that one would be concerned about the *read* rate on the *sending* computer.

---

### Post by krunge on 2009-06-01
> **swarup said:**
> When you talk about the graphics card's read rate, is that referring to the graphics card in the server computer or the viewer computer? The fact that you are referring to this in relation to x11vnc, makes me think it may be the server computer's read rate to which you refer-- but then the server computer is *sending* and the viewer computer is *reading*, so it doesn't completely make sense that one would be concerned about the *read* rate on the *sending* computer.

A better term I have seen used (and should use myself) is 'readback rate'.  I.e. what is the rate at which pixels rendered in the graphic hardware's framebuffer memory (Video RAM) can be read back into the computer's main memory (main RAM, where x11vnc accesses it.)

Yes, this rate is on the x11vnc side (VNC server), and is a rate local to that computer (i.e. on the "DAN": Desktop Area Network.)

Having this local-rate high makes a noticable difference in VNC response, except perhaps when connecting to x11vnc over the slowest network links.

I'm building a new desktop for myself and one constraint is to use nvidia and its proprietary drivers because I access the desktop alot via x11vnc.  I'm not too keen on proprietary drivers, but it doesn't look like Xorg drivers will ever reach this level of performance.

---

### Post by swarup on 2009-06-01
I see, thanks very much for the clarification. -- One follow-up question to this: how can one find out the 'readback rate'? I generally start and stop x11vnc using its gui, so there is no terminal window output. Is there a specific command for requesting the 'readback rate'?

---

### Post by krunge on 2009-06-01
> **swarup said:**
> One follow-up question to this: how can one find out the 'readback rate'? I generally start and stop x11vnc using its gui, so there is no terminal window output. Is there a specific command for requesting the 'readback rate'?

Not too many people use the x11vnc gui... but there actually are a couple ways:

1) Go to Misc -> all-settings.  In the popup scroll down to the bottom and look for 'readrate'

2) Or do Misc -> remote-cmd and enter "Q:readrate" in the entry box and then click on OK.

In both cases the units will be MegaBytes/sec.  5-10 is pretty slow (but tolerable), while 200 or more is pretty fast.

---

### Post by swarup on 2009-06-01
Mine says 309. (Video card is NVIDIA)

But still, the transfer of info from one computer to the other seems slow to me. I think xllvnc is buggy on my computer for some reason. I first started using it a month ago, and then about a week ago, I noticed the copy-paste functions in my text editor became very sketchy when connected via xllvnc. If I would try to highlight anything--in order to copy it--the highlighted item would not remain highlighted long enough to copy it. So I could not copy anything. And along with that, the "add to spellchecker" function similarly became sketchy. I would have to try adding a new word five times or more before it would add. Or sometimes, it wouldn't add at all. 

I don't know what the above problem is all about. Any thoughts?

---

### Post by krunge on 2009-06-01
> **swarup said:**
> 
I don't know what the above problem is all about. Any thoughts?

Are you using the "-noxdamage" option?

---

### Post by swarup on 2009-06-01
> **krunge said:**
> Are you using the "-noxdamage" option?

No, I am not-- although I've seen it written about alot. Do you think it could help to solve this copy-paste problem? It seems to be a problem with the clipboard. I can certainly try it and see if it helps.

By the way, what are the pros and cons of using [x11vnc + tightvncviewer] vs [vino + vinagre]?

---

### Post by krunge on 2009-06-02
> **swarup said:**
> Do you think it could help to solve this copy-paste problem? It seems to be a problem with the clipboard. I can certainly try it and see if it helps.


I'm not I understood your copy-paste problem given your other statements: was it really not happening or did you just not see it.  Try -noxdamage to rule it out.

**Answer This Question Too:**  Does the "-nosel" option make your problem go away?

---

### Post by swarup on 2009-06-02
> **krunge said:**
> I'm not I understood your copy-paste problem given your other statements: was it really not happening or did you just not see it.  Try -noxdamage to rule it out.
Copy-paste does not happen. Means, it is quite dysfunctional. The main problem seems to be that whatever I highlight, doesn't remain highlighted long enough for me to do the "copy" command. Or if I am highlighting an entire line of text, for example, then in the process of highlighting the line, as I draw my cursor across the page to highlight, the beginning of the line I highlighted loses its highlight by the time I get the cursor across the page! So I can't even highlight a whole line of text.

If I am typing in English, then I can highlight short sections of text and copy them if I do it very quickly. But if it is for example Hindi (which uses complex characters), then when I try to paste what I copied, it just comes out as the 4-number code for each character, rather than the actual character. So it is all a mess.

Today when I start my work, I'll try the -noxdamage option and see if it helps. Although I thought that was being used for people who have problems with screen update freezing.

> **krunge said:**
> **Answer This Question Too:**  Does the "-nosel" option make your problem go away?

I can try this as well and see if it helps.

The whole reason I was using x11vnc was because in Jaunty, as you may know, there is a bug which causes vino to not refresh after the initial image is sent, for anyone having System>Appearance>Visual Effects tab set to anything other than: "None". The bottom line is vino is not being told that the screen has been updated so no screen updates are sent down stream. Because of that, I was using x11vnc. But now, because I am having the copy-paste problem with x11vnc, I have just turned my Visual Effects to "none", and so my vino-vinagre connection is again working perfectly. That is, the refresh problem is not there-- and with vino-vinagre there is no copy-paste problem.

But still, I am curious as to why the xllvnc copy-paste problem developed.

---

### Post by krunge on 2009-06-02
> **swarup said:**
> 

**Answer This Question Too:** Does the "-nosel" option make your problem go away?

I can try this as well and see if it helps.


Post back here what you find with "-nosel".

This is part of the troubleshooting in case you hadn't noticed.

---

### Post by Anthon berg on 2009-08-13
Hi,

I must recommend you try Nomachine or NX.

nomachine.com is free-as-in-beer
FreeNX is open-source AFAIK, and the same thing

It's a much smarter protocol than VNC. It's local-speed over a LAN, and very very fast even over a modem link. You wouldn't believe how fast it is.

The drawback is that there isn't a server for Windows or Mac OS, only standard UNIX, including Linux.

---

### Post by doas777 on 2009-08-13
I've been using XVNC4Viewer for exactly that reason, and that the default one has terrible scroll bars. logging into a desktop with a 1980 res is a problem if you can't scroll reliably.

---


---
title: "Display Settings in Karmic Koala"
date: 2010-01-05
forum: Desktop Environments
---

### Post by kannanjagadeesan on 2010-01-05
Hi Experts,

I have installed Karmic Koala version of Ubuntu. Now, I see that the pixels are set by around 640 by 480 pixels. How can I change it?

Kindly guide me.

Thanks in advance,
Kannan

Note: I have an LG Flatron W2043T Monitor. Should I load any drivers for it? Then, where to find any Linux drivers for it?

---

### Post by SalahTr on 2010-01-05
```
System -> Preferences -> Screen Resoultion
```

---

### Post by SusieSA on 2010-01-21
Hello all you lovely people.

I've just upgraded my pc and installed Karmic Koala.  I'm totally impressed that it's taken me less than 5 hours to move everything from my old pc to my new one and get everything working tip top... except for my screen resolution.  

I have a LG Flatron L1718S and it worked with Hardy Heron, but I do seem to remember having a few issues with it a couple of years back and I can't remember what I did to fix it!

The Answer to the post says:

System -> Preferences -> Screen Resolution

I don't have this as an option in preferences.  I do have System -> Preferences -> Display.  When I go into this option, there really are no choices available.  I have a big pink 'Unknown' box displaying and no options to pick a monitor.  I'm stuck on 800 x 600!  The 'Detect Monitors' button does nothing.  

Please help.

---

### Post by Objekt on 2010-01-21
Are you perhaps connecting to the monitor through a KVM switch?  I once had the problem you're describing for that reason.  It seemed that that the Xorg server (or was it Nvidia's drivers?  maybe both?) was unable to correctly detect the monitor's available display modes through the switch.  It defaulted to 640x480 @ 60 Hz and offered no other choices.  After I plugged the monitor directly into the system's video card and restarted xserver, I had the monitor's true abilities available.  I was also able to save the setting, so that I could later reconnect the KVM switch while preventing a repeat of the problem.

Xorg will try to automagically detect your display & set it to something reasonably high-res and high refresh rate by default.  That works well most of the time, but  can occasionally go wrong, as we've both seen.  Hope this helps.

---

### Post by bamdl001 on 2010-01-21
> **Objekt said:**
> Are you perhaps connecting to the monitor through a KVM switch?  I once had the problem you're describing for that reason.  It seemed that that the Xorg server (or was it Nvidia's drivers?  maybe both?) was unable to correctly detect the monitor's available display modes through the switch.  It defaulted to 640x480 @ 60 Hz and offered no other choices.  After I plugged the monitor directly into the system's video card and restarted xserver, I had the monitor's true abilities available.  I was also able to save the setting, so that I could later reconnect the KVM switch while preventing a repeat of the problem.

Xorg will try to automagically detect your display & set it to something reasonably high-res and high refresh rate by default.  That works well most of the time, but  can occasionally go wrong, as we've both seen.  Hope this helps.
I also have this problem with my monitor resolution. Karmic Koala only offers up to 800x600 and I'm not connected to any switch. Are you able to advise as to how I can increase my screen resolution? I'm sure it's probably straight forward I'm just a beginner... Thanks

---

### Post by SusieSA on 2010-01-22
Hi

Thank you for your response bamdl001.  I'm not sure what you mean by a KVM switch and plugging directly into the video card.  There is only one port available on my pc that will take my monitor....

---

### Post by bamdl001 on 2010-01-22
> **SusieSA said:**
> Hi

Thank you for your response bamdl001.  I'm not sure what you mean by a KVM switch and plugging directly into the video card.  There is only one port available on my pc that will take my monitor....

Hi SusieSA, That's is not my response.. I was only replying to that particular post. I too have a problem with display settings. My Karmic Koala only allows up to 800x600 so I'm not sure what to do to increase my resolution.. I need at least 1280x768... What about you? A KVM switch is some type of box that you can hook up 2-3 diferent printers or monitors or whatever to one computer... I think!
Cheers

---

### Post by SusieSA on 2010-01-22
oops - my thanks were due to Objekt!  Yip - we're in the same boat!

---

### Post by luffy_chan_19 on 2010-01-22
In general with any operating systems, what i ahve noticed as of problems with screen resolution, is that the Video card driver was not installed correctly or just not installed at all.  i dont know if this is the case, but i hope this suggestion helps. try reinstalling the graphics card drivers. also it could be a third party driver, so click system-> administration->hardware drivers . this will check for any hardware attached to your computer that uses third party drivers.

 your probably wondering to yourself, how would the monitor work in the first place if the drivers were not installed... well if the drivers for the video card were not found, the system will use a generic driver, untill you find and install the right driver for the card.

hopefully my suggestion helps.

---

### Post by SusieSA on 2010-01-22
Thank you for the suggestion luffy_chan_19.  I did as you said, but the Hardware Drivers window says "No Proprietary drivers are in use on this system" and that's that... there are no more options available in this window.

---

### Post by SusieSA on 2010-01-22
Well Well.... this is working now and I've done seemingly nothing!  I followed the previous post about the Hardware Drivers and didn't do anything.  Then, when I went back to System -> Preferences -> Display, I could choose 1280 x 1024 which wasn't available previously.  So now I'm all sorted.  Thank you!

---

### Post by luffy_chan_19 on 2010-01-22
well than.....

---

### Post by Objekt on 2010-01-22
KVM is "keyboard, video, mouse."  A KVM switch lets you have one set of controls (keyboard, monitor, mouse) connected to more than one computer.  I use it at home when I'm building a new machine for someone, because I don't have room for two complete sets of controls for the 2 machines.

KVM switches come in a large range of capabilities and prices.  Some of the cheaper ones - like mine, apparently! - do not work all that well, and will sometimes not allow the connected computers to properly detect the display.  That's what happened to me.

Doesn't sound like it applies here anyway, but FYI.

---

### Post by SusieSA on 2010-01-23
Thank you for the explanation Objekt.  You're right - it doesn't apply to me.

Now that my PC has had a nights sleep...THE PROBLEM IS BACK AGAIN!  I've tried going to System -> Administration -> Hardware drivers and then to System -> Preferences -> Display, but still I only have very pathetic resolutions available.

---

### Post by buyit1986 on 2010-01-23
Im Having the same problem my nvidia video card drivers are upto date and my resolution isn't correct i've even tried editing xorg.conf and that didnt work and ideas would be verry appreciated. also im using a 6 year old kds xflat crt monitor (never had a problem before) this isnt the problem i hope.

---

### Post by SusieSA on 2010-01-24
I have fixed this problem and I thank everybody for their help both in this thread and others.  

Have a look at:
[http://ubuntuforums.org/showthread.php?t=1388613&highlight=monitor+resolution](http://ubuntuforums.org/showthread.php?t=1388613&highlight=monitor+resolution)

and

[http://ubuntuforums.org/showpost.php?p=8144910&postcount=1](http://ubuntuforums.org/showpost.php?p=8144910&postcount=1)

I had to modify the xorg.conf in the etc/X11 directory.  I was not allowed to edit the file innitially because it was owned by root, but I changed the ownership to myself by using the chown command.  

Then I could edit the file and replace it as suggested in the above postings and I amended the default to 1280X1024 which is my monitor's maximum resolution.

Then I restarted my PC and now I'm v happy!

---


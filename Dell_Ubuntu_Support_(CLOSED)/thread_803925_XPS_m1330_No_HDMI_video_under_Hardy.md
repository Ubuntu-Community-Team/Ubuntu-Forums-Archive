---
title: "XPS m1330: No HDMI video under Hardy"
date: 2008-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bobertf on 2008-05-22
My XPS m1330 came with Dell's install of Gutsy, and HDMI (video at least) worked just fine.  I recently put Hardy Heron on the computer so that I could partition it myself.  Now HDMI is broken, it seems.  My output from  "xrandr -q" is as follows:

```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 connected 1280x720+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1280x720       60.0*+
   720x480        59.9 
```

So it seems that my laptop is recognising the TV.  I used the commands

```

$ xrandr --output TMDS-1 --off
$ xrandr --output TMDS-1 --auto
```

in hopes of resetting something, but that didn't work.  I popped in an 8.04 live CD and HDMI also didn't work; same with 7.10.  I seem to be missing something.  Anybody know what?

Thanks a lot!

Bob

---

### Post by trjonescp on 2008-05-31
I am having the exact same issue except I have never gotten HDMI to work with any Ubuntu version. Anyone have any advice?

---

### Post by stedi on 2008-06-09
I have the same issue as well.
hardware: dell xps1330 (intel graphics)
```
xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1680 x 1850
VGA connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   75.0     59.9
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       60.0*+   60.0
TMDS-1 connected (normal left inverted right x axis y axis)
   1680x1050      60.0 +

```

connecting the VGA screen does work, but the TMDS-1 screen (via hdmi) does not.

Any help is appreciated, thanks

---

### Post by B0SS on 2008-06-11
I still have the same problem... I am wondering where these Dell Support guys are.

These are the problems that switchers face. Imagine wanting to switch from xp/vista to ubuntu and when googleing m1330 Ubuntu HDMI gives this [http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=6fR&q=m1330+Ubuntu+HDMI&btnG=Search&meta=](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=6fR&q=m1330+Ubuntu+HDMI&btnG=Search&meta=)

---

### Post by nanog on 2008-06-15
Try installing the new 174 nvidia driver using envy.

---

### Post by clauslund on 2008-06-21
I just want to say what I did to get the HDMI video working on my Dell XPS m1330.

I have the nVidia gfx so this will be different for the ones with integrated gfx.

But I just installed the nVidia driver (the one "atomagically" suggested), then installed the nvidia-settings tool (also available through synaptic/apt-get).

Then run the nvidia-settings tool:

```
gksudo nvidia-settings
```

The XServer display configuration screen should have both the laptop and external display.
Configure things how you like them (I used TwinView and set things up as clones) and then you probably just need to restart X (Alt+Ctrl+Backspace).

Voila!

---

### Post by pormogo on 2008-06-28
I'm having he exact same issue. When I connect the HDMI cable to my laptop it's cable to recognize the TV however it never seems to output any video to it no matter what I do. I unfortunately have the intel GMA956 version).

---

### Post by jbrice on 2008-07-04
> **pormogo said:**
> I'm having he exact same issue. When I connect the HDMI cable to my laptop it's cable to recognize the TV however it never seems to output any video to it no matter what I do. I unfortunately have the intel GMA956 version).

Same here. It's a Dell 1525 with the Intel '965 video - the external TV screen (Panasonic 32lxd52) is discovered correctly by X setup -TV screen flickers momentarily when resolution is changed etc. - but displays a continuous black-level.

Anyone with thoughts on this?

James B.

---

### Post by ajonat on 2008-07-05
I can confirm this. HDMI does not work on ubuntu hardy with 965GM intel card (dell inspiron 1525).
I'm trying to connect using HDMI with a 32" samsung LCD TV, and it says "mode incompatile" (in the TV), though I'm using the correct resolution (1280x720).

Anyone from dell can help us please?

---

### Post by maryyeta on 2008-07-17
> **ajonat said:**
> I can confirm this. HDMI does not work on ubuntu hardy with 965GM intel card (dell inspiron 1525).
I'm trying to connect using HDMI with a 32" samsung LCD TV, and it says "mode incompatile" (in the TV), though I'm using the correct resolution (1280x720).

Anyone from dell can help us please?

The same with medion akoya laptop using intel GM965.
TV shows the orange-coloured desktop background for a moment, but goes black immediately, saying "mode incompatible" again and again...

Can anyone help please?

---

### Post by FTBPrimeEvil on 2008-07-18
I have the Alienware m15x, and the 8700M/GT vid card, my HDMI external monitor works fine. But only after i install the Nvidia drivers from nvidia.com.

---

### Post by zeus77 on 2008-08-03
Same problem here -- can't get HDMI output to work on a laptop with Intel 965GM graphics.  There's a post [here]("http://ubuntuforums.org/showthread.php?t=875929") which offers a .deb of the latest 2.4 driver from Intel, and the post claims it has HDMI support.  Has anyone tried?  Maybe I will if I get some time later today...

zeus77

---

### Post by maryyeta on 2008-08-09
hey zeus77, 

have you tried it? I've installed the new driver and I've lost my desktop effects... and no way to have HDMI running. 

When I reboot with HDMI cable connected to my LCD Samsung LE32S86DBX (32" TV), ubuntu starts with 640x resolution and unable to see TV screen anywhere. If I unplug the cable and reboot, all seems correct (without desktop effects, but at normal resolution).

Any ideas? Thanks in advance...

---

### Post by zeus77 on 2008-08-19
Nope, I never did try it.  I read some stuff somewhere about that driver which scared me off... something related to kernel version, if I recall.  From this [launchpad entry]("https://launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-intel/") it looks like the updated driver has made its way into intrepid, though, so maybe in another 2 months it will be working... keep your fingers crossed.
zeus77

---

### Post by crogers45 on 2008-08-22
I am not sure why but I can get my XPS M1330 to switch the display by closing the lid while Ubuntu is running and then opening it again.  It switches to the HDMI display and then I can close the lid and it stays active.

---

### Post by tankerkevo on 2008-08-23
Has anyone gotten S-Video working?

---

### Post by deja on 2008-10-06
Don't suppose this has been solved, has it?  I'm in Gutsy and this still isn't working for me, with all the same described problems above (m1330 with Intel graphics over HDMI). 

Note to above: m1330 doesn't have S-Vid out. Don't suppose this has been solved, has it?  I'm in Gutsy and this still isn't working for me, with all the same described problems above (m1330 with Intel graphics over HDMI). 

Note to above: m1330 doesn't have S-Vid out.

---

### Post by burnstony on 2008-10-21
called dell support - they said HDMI not working is not a hardware issue - the software the dell ships with does not support HDMI - for any further support I would have to call canonical which cost money - has anyone figured out if there is a driver for this anywhere

---


---
title: "Poor dvd playback"
date: 2005-03-25
forum: Desktop Environments
---

### Post by paul.hendrick on 2005-03-25
I've just installed hoary on a new machine, and installed the libdvdcss2 libs from the marillat repo. I've checked that dma is enabled on the dvd drive, but I'm still having trouble.
The video looks/plays fine unless it's in full screen mode, when it becomes choppy, and the video quality looks blurred and poorly scaled. 
This is using the xine backend with totem, and gxine.

What else should I look for to try and fix this?

---

### Post by wernst on 2005-03-25
for starters, DMA isn't enabled for optical drives by default in Hoary for some reason.

You can enable it with:

sudo hdparm -d1 /dev/hdb

where hdb is your optical drive.

Hopefully this will be fixed in the future...

-Warr

---

### Post by wmcbrine on 2005-03-25
Yes, and to make the change permanently, I did this:

Edit /etc/hdparm.conf appropriately... in my case, I put this:

```

# multcount for the hard drive
/dev/hda {
        mult_sect_io = 16
        dma = on
}

# dma for the burner
/dev/hdc {
        dma = on
}

```

Then, in /etc/rcS.d, I copied S07hdparm to S99hdparm. This was necessary because the optical drive isn't recognized by the time S07hdparm is run. The multiple invocations are harmless, and it's good to retain S07hdparm to ensure a fast boot.

I also had a problem with MPlayer not using xv by default (edit in /etc/mplayer/mplayer.conf); but xine, totem, etc. were not affected. If DMA doesn't help (as you say you already checked it), see if you can figure out what kind of video output mode they're using on your system. Make sure MTRR is enabled (I really doubt that this is it, but it was something I had to do manually with Mandrake back in 2000). Look for errors related to your video card in dmesg, /var/log/syslog, /var/log/messages, etc.

---

### Post by paul.hendrick on 2005-03-26
I've made sure dma is enabled, but i'm still getting the choppy playback with totem-xine.
the look of the video in a small window is very clear and sharp, but as soon as i put it in fullscreen, it becomes very blurred, as if it's not scaled properly. 

hdparm /dev/hdb gives:
```

/dev/hdb:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```
it maybe because Xv isn't being used for the video driver, but I can't remember how to check this. i've tried with xine-ui with the xv driver selected, but i get the same results.

---

### Post by wernst on 2005-03-26
The Xine site has pretty much all the startup flags you'd ever need.

To force Xine to run with Xv, the command is:

xine -V Xv

try this to see what Xine thinks of your config:

xine-check

-Warr

---

### Post by paul.hendrick on 2005-03-26
xine-config tells me that i have no Xv extension. if i run xine -V Xv, xine starts for a second, then quits with no output to the terminal at all. 
cat /var/log/Xorg.log |grep xv gives:
```

(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation

```
I can't figure out why Xv isn't being used

---

### Post by wbeck85 on 2005-03-26
I have DVDs running in xine (Well, totem and Kaffiene technically) but the comptuer really chugs to render video at full screen and I get very choppy video, at full screen. (1680X1050 if thats importnat) Windoes never had this trouble, so i Know tis not a problem with my hardware capabilities. I have a Mobile Radeon 9700, which seems to run everything else fine (including Unreal 2004). I have turned on that DMA thing, but i do no think it is the drive's fault. I wonder if the comptuer is trying to render video using software. It would be nice if the video card would render it, i bet I would get better framerates. Any insight?

Sorry, this is a double post from a thread in the Warty forum. I did'nt really intend to post there. Please forgive me :/

---

### Post by paul.hendrick on 2005-03-26
i've narrowed it down to an Xv problem.
xine --verbose=2 -V Xv, gives:
```

video_out_xv: Xv extension is present but I couldn't find a usable yuv12 port.
              Looks like your graphics hardware driver doesn't support Xv?!
main: video driver <xv> failed

```
I've added this to my xorg.conf
```

Option          "VideoOverlay"          "on"
Option          "OpenGLOverlay"         "off"

```
but i still get the same error. any ideas?

---

### Post by wmcbrine on 2005-03-26
[QUOTE=paul.hendrick]Looks like your graphics hardware driver doesn't support Xv?![/QUOTE]
What is your video card?

---

### Post by paul.hendrick on 2005-03-27
ati x600 using the fglrx driver.

---

### Post by lukem on 2005-03-27
Please excuse the intrusion, but you both seem to know a great deal more about this than I do so I thought this might be a good place to ask this question.

With warty I was able to play dvds both commercially produced and home recorded.

Since upgrading to Hoary I've installed totem-xine and w32codecs and am able to play commercially produced dvds but not home recorded.  Error is "There is no plugin to handle this movie".  

Any ideas as to what is different in the Hoary setup vs the Warty?

Thanks and good luck

---

### Post by pbow9 on 2005-04-02
I have found a solution to my DVD playback problems. I switched the video output setting in VLC to OpenGL output instead of default and now I get crystal-clear video output instead of the pixelated video I was getting before. I would imagine all the other players have the option to use gl output as well.

---

### Post by HellionDarkLord on 2006-10-19
I too have issues with DVD playback.  I have also narrowed it down to video driver issues because this is the result when the dvd player is queried.

[PHP]/dev/dvd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
[/PHP]

Just to make sure i ran this:
[PHP]$ sudo hdparm -d1 /dev/dvd

/dev/dvd:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
[/PHP]

So I am fairly certain that my DMA is on. I did have some warnings, but they go away before i can finish reading them because knotify crashes.

My video card is a chaintec volari3 XGI.  Do I need a new vid card in order to run linux sucessfully?  In the device manager I find that it thinks that my video card is an XGI Volari XP5. How would I set it up to recognize the card for what it actually is?  I cannot find drivers because the company who manufactured the card does not write linux drivers for this card.

Would it be worthwhile to buy a new video card? (provided I had the money)

Thanks for any advice.

---

### Post by lunarcloud on 2008-06-07
the fglrx driver may be interfering with dma, limiting it. compare the open source drivers performance.

---


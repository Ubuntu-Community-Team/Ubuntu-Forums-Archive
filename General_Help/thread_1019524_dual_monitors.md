---
title: "dual monitors?"
date: 2008-12-23
forum: General Help
---

### Post by alec868 on 2008-12-23
I have ubuntu 8.10 and I am having problems with dual monitors, i would like to solve this without editing the xconfig file as I worry i may skrew somehting up beyond repair. i have an asus eee 900, the GUI, screen resolution recognizes the second monitor and i can use it but the options im give for resolution and such are extremely limited, and usually on one screen or the other my menus disappear, also the screen on the laptop gets stretched out and the graphics are terrible. what i want is an as easy as possible way to hook up a dual monitor and have it function just as another workspace on my desktop would, without changing the screen settings on the laptop and with decent resolution on the other monitor. any help?

---

### Post by redilyn on 2008-12-23
To help with your screen resolution problem try this:

Open a terminal and type
```

xrandr

```

You should see an output similar to this

```

 Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 2048 x 2048
  VGA connected 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
     1680x1050      59.9*+   60.0  
     1600x1200      59.9  
     1280x1024      75.0  
     1152x864       75.0  
     1024x768       84.9     75.1     70.1     60.0  
     1024x600       60.0  
     832x624        74.6  
     800x600        84.9     72.2     75.0     60.3     56.2  
     800x480        60.0  
     640x480        84.6     75.0     72.8     66.7     60.0  
     720x400        70.1  
  LVDS connected 1024x600+0+0 (normal left inverted right x axis y axis) 195mm x 113mm
     1024x600       60.0*+   60.0  
     800x600        60.3  
     800x480        60.0  
     640x480        59.9

```

First try

```

xandr --auto

```

this should set both monitors (internal and external) at the maximum resolution of the external monitor.

If this does not yeild the result you are looking for you can manually set the resolution on the external screen with this command

```

xrandr --output <Screen> --mode <Resolution>

```

For example. Using the example print out from about. To set the external monitor to 1680x1050 you would do the following

```

xrandr --output VGA --mode 1680x1050

```

Hope this helps.

For more info see: [http://wiki.eeeuser.com/howto:external_monitor](http://wiki.eeeuser.com/howto:external_monitor)

---

### Post by bvidinli on 2008-12-23
Worked for Ati Radeon 2400 pro
should work for all ati cards.. 


for normal dual head monitor, with xinerama on ati,

open console,
run followings:

aticonfig --initial=dual-head --screen-layout=right
aticonfig --dtop=horizontal --overlay-on=0
aticonfig  --xinerama=on


this will setup an xorg.conf with dual head, one large desktop, you can drag a windows from one monitor to another...

---

### Post by CHaoSlayeR on 2009-01-10
^^ nice try...

...but the ASUS EEE PC 900 has an Intel graphics chip, not an AMD/ATI one.

So I think xrandr should work fine on Intel chips. If it doesn't you'll have to deal with the xorg.conf manually.

I have some guys with similar netbooks at work that are actually doning the things you want to achieve here. I could ask them for their configs if you need one.

C]-[aoZ

---

### Post by Mr_Knuckles on 2009-01-29
I have ATI Mobility Radeon HD 2300. 

Can Compiz run with Xinerama on?

When I try to enable compiz I get the error "The Composite extension is not available".

---

### Post by zorrek on 2009-01-31
> **Mr_Knuckles said:**
> I have ATI Mobility Radeon HD 2300. 

Can Compiz run with Xinerama on?

When I try to enable compiz I get the error "The Composite extension is not available".

I had compiz on then enabled Xinerama as a test. Compiz stoped working, check the settings it was still enabled. So as an answer I would have to say no! Compiz does not work with Xinerama.

Best bet is "separate X screen setting. I'll post a link to a screen shot.

Frak me, compiz will not start working now. Turned Ximerama off but it's stuffed compiz completely.  Grrrr

---


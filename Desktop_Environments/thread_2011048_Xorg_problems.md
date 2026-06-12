---
title: "Xorg problems"
date: 2012-06-26
forum: Desktop Environments
---

### Post by Theredbaron1834 on 2012-06-26
So, I have an ATI Radion HD 5770 using the FGLRX driver. I have 2 monitor's set up, 1 via hdmi and one via dvi, with openbox on both. All is well and good for a while after booting/loging in. After a while things stop opening however. I checked and it seems whenever I run a gui program, it gives me this error;
```
Maximum number of clients reachedMaximum number of clients reachedError: unable to open display :0

```

I looked it up, and it seems there is a hard limit of 100 windows. However, I am no where near that limit. I have 2 firefox's open, one on each monitor, xbmc, 4 term emu's, and then a few things that start up when I login, such as nautilus, wally, ect.

I have checked out top, and can't see anything that is holding some windows. I have no idea why this is happening. Anyone have some help?

---

### Post by gordintoronto on 2012-06-26
I'm not sure why you described this as an Xorg problem.

When I Google the error you got, I find that "the minimize to tray plugin of thunderbird" or lastpass in Chrome might cause this problem.

There are lot more hits in Google.

---

### Post by Theredbaron1834 on 2012-06-26
I did google, alot. And that is why I think it is a xorg problem. I don't even have chrome, lastpass, or thunderbird installed.

And with my google searching, I couldn't find an answer.

---

### Post by gordintoronto on 2012-06-26
What version of Ubuntu is on the computer?

Do you tend to use a lot of tabs in Firefox?

---

### Post by Theredbaron1834 on 2012-06-26
I use Lubuntu 12.04, sorry, thought I mentioned that.

And I wouldn't say a lot of tabs. Max of 4 on my main screen, though normally just 1, and only 1 on the other.

---

### Post by gordintoronto on 2012-06-27
Puzzling.

What does Lubuntu use as its email program?

---

### Post by Theredbaron1834 on 2012-06-28
Honestly, I am not sure. The first thing I do after a fresh install is to purge all the programs I don't use. 

Hm, looked it up. The site says it uses  Sylpheed.

---

### Post by marinara on 2012-06-28
post the output of the commands listed on this page
[http://askubuntu.com/questions/4499/how-can-i-diagnose-debug-maximum-number-of-clients-reached-x-errors](http://askubuntu.com/questions/4499/how-can-i-diagnose-debug-maximum-number-of-clients-reached-x-errors)

---

### Post by Theredbaron1834 on 2012-06-29
xlsclients
```

LXDE-desktop  lxsession
LXDE-desktop  xfce4-panel
LXDE-desktop  lxpanel
LXDE-desktop  xfce4-power-manager
LXDE-desktop  polkit-gnome-authentication-agent-1
LXDE-desktop  notification-daemon
LXDE-desktop  nm-applet
LXDE-desktop  wally
LXDE-desktop  firefox
LXDE-desktop  blueman-applet
LXDE-desktop  nautilus
LXDE-desktop  terminator
LXDE-desktop  transmission-gtk

```xrestop > log.log
```
[?1049h[1;41r(B[m[4l[?7h[H[2Jxrestop - Display: :0[2;11HMonitoring 251 clients. XErrors: 0[3;11HPixmaps:  752910K total, Other:[48G89K total, All:  753000K total 

(B[0;1;7mres-base Wins  GCs Fnts Pxms Misc   Pxm mem  Other   Total   PID Identifier     
(B[m3e00000    72   42    1  216  516     7639K     15K   7654K  1953 xorg - How can I diagnose/debug "maximum number of clients reached" X errors? - Ask Ubuntu - Mozilla 
1fc00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1f400000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1f200000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1ee00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1ec00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1e800000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1e600000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1e200000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1de00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1dc00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1d800000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1d600000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1d400000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1d000000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1ce00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1cc00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1ca00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1c800000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1c400000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1c200000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1be00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1bc00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1ba00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1b800000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1b400000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1b200000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1b000000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1ae00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1ac00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1aa00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1a800000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1a400000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1a200000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
1a000000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown> 
19c00000     0    0    0    1    0     4080K[51G0B   4080K   ?   <unknown>[41;1H[?1049l [?1l>
```Why all the unknown, I am not sure. That kinda sucks.

xwininfo -root -children
```

xwininfo: Window id: 0x153 (the root window) (has no name)

  Root window id: 0x153 (the root window) (has no name)
  Parent window id: 0x0 (none)
     52 children:
     0x2800002 (has no name): ()  16x16+0+0  +0+0
     0x14105c5 "lxpanel": ("lxpanel" "Lxpanel")  211x144+725+598  +725+598
     0x1f00445c "Transmission": ("transmission-gtk" "Transmission-gtk")  277x349+431+376  +431+376
     0x108000d2 "terminator": ()  10x10+-100+-100  +-100+-100
     0x1f0002b4 "Transmission": ("transmission-gtk" "Transmission-gtk")  195x168+54+98  +54+98
     0x1f000338 "Transmission": ()  10x10+-100+-100  +-100+-100
     0x1f00029d "Transmission": ("transmission-gtk" "Transmission-gtk")  234x89+88+98  +88+98
     0x1f000002 "Transmission": ("transmission-gtk" "Transmission-gtk")  10x10+10+10  +10+10
     0x1400d61 "lxpanel": ("lxpanel" "Lxpanel")  219x167+179+552  +179+552
     0x140867d "lxpanel": ("lxpanel" "Lxpanel")  208x98+179+529  +179+529
     0x140861b "lxpanel": ("lxpanel" "Lxpanel")  175x29+179+575  +179+575
     0x1400c46 "lxpanel": ("lxpanel" "Lxpanel")  181x259+0+483  +0+483
     0x10800002 "terminator": ("terminator" "Terminator")  10x10+10+10  +10+10
     0x1400d32 "lxpanel": ("lxpanel" "Lxpanel")  146x75+179+506  +179+506
     0x1408571 "lxpanel": ("lxpanel" "Lxpanel")  362x535+179+233  +179+233
     0x1600005 "Desktop": ("desktop_window" "Nautilus")  1360x768+0+0  +0+0
     0x1600004 "nautilus": ()  10x10+-100+-100  +-100+-100
     0x1600002 "nautilus": ("nautilus" "Nautilus")  10x10+10+10  +10+10
     0x1f800002 "blueman-applet": ("blueman-applet" "Blueman-applet")  10x10+10+10  +10+10
     0x14085b1 "lxpanel": ("lxpanel" "Lxpanel")  265x397+179+371  +179+371
     0x140d72e "lxpanel": ("lxpanel" "Lxpanel")  217x121+179+621  +179+621
     0x14078f9 "lxpanel": ("lxpanel" "Lxpanel")  240x259+179+509  +179+509
     0x1800002 "screensaver": ("xscreensaver" "XScreenSaver")  1360x768+0+0  +0+0
     0x1400026 "lxpanel": ()  10x10+-100+-100  +-100+-100
     0x200002a "wally": ("wally" "Wally")  200x200+0+0  +0+0
     0x2000004 "wally": ("wally" "Wally")  200x200+0+0  +0+0
     0x2000002 "wally": ("wally" "Wally")  10x10+10+10  +10+10
     0x2200002 "NetworkManager Applet": ("nm-applet" "Nm-applet")  10x10+10+10  +10+10
     0xc00002 "notification-daemon": ("notification-daemon" "Notification-daemon")  10x10+10+10  +10+10
     0x1c00002 "polkit-gnome-authentication-agent-1": ("polkit-gnome-authentication-agent-1" "Polkit-gnome-authentication-agent-1")  10x10+10+10  +10+10
     0x1e00002 "xfce4-power-manager": ("xfce4-power-manager" "Xfce4-power-manager")  10x10+10+10  +10+10
     0x1400004 "lxpanel": ()  10x10+-100+-100  +-100+-100
     0x1400002 "lxpanel": ("lxpanel" "Lxpanel")  10x10+10+10  +10+10
     0x1200002 "xfce4-panel": ("xfce4-panel" "Xfce4-panel")  10x10+10+10  +10+10
     0x800004 (has no name): ()  10x10+0+0  +0+0
     0xa00002 (has no name): ()  10x10+0+0  +0+0
     0x800002 "lxsession": ("lxsession" "Lxsession")  10x10+10+10  +10+10
     0x400002 (has no name): ()  10x10+-20+-20  +-20+-20
     0xe000ac "Openbox": ("" (none))  1x1+-100+-100  +-100+-100
     0xe000ff (has no name): ()  1x1+0+0  +0+0
     0xe000fd (has no name): ()  1x1+0+0  +0+0
     0xe000fa (has no name): ()  1x1+0+0  +0+0
     0xe000f6 (has no name): ()  1x1+0+0  +0+0
     0xe000f3 (has no name): ()  1x1+0+0  +0+0
     0xe000f2 (has no name): ()  1x1+0+0  +0+0
     0xe000f1 (has no name): ()  1x1+0+0  +0+0
     0xe000f0 (has no name): ()  1x1+0+0  +0+0
     0xe000ef (has no name): ()  1x1+0+0  +0+0
     0xe00101 (has no name): ()  1360x26+0+742  +0+742
     0xe000fc (has no name): ()  1x1+0+0  +0+0
     0xe06b2c (has no name): ()  1360x742+0+0  +0+0
     0xe06c31 (has no name): ()  581x527+50+50  +50+50

```And I want to say thanks for trying to help, as I would much rather not go multi-seat.

---

### Post by campaigner444 on 2012-10-02
I am having a similar problem with Ubuntu 12.04. I have looked through some other links and I keep seeing that Wally is one of the processes that is running. I am running Wally too. Could it be causing these problems?

---

### Post by gecegezen on 2012-10-21
> **campaigner444 said:**
> I am having a similar problem with Ubuntu 12.04. I have looked through some other links and I keep seeing that Wally is one of the processes that is running. I am running Wally too. Could it be causing these problems?

same things for me and I think problem is wally and I remove it then eveythins is fine for me.

---


---
title: "unity fails..."
date: 2011-08-27
forum: Desktop Environments
---

### Post by xhaowu on 2011-08-27
i was using dual screens with unity desktop , and it was crashed when I switched to KDE 4.6. After restarting my machine, unity desktop just not showing even I choose it in the login screen.  Now I can only use ubuntu classic.  any ideas?

---

### Post by wildmanne39 on 2011-08-27
Hi, check your video card driver it may have got updated.

---

### Post by moorhead98 on 2011-08-27
What happens when you try to login in unity? does it just show a messed up screen, or does it send you to classic desktop?

---

### Post by Jeepty on 2011-08-28
you could try resetting unity to default settings:

code:
unity --reset

followed by a restart (if needed).

This will _modify whatever settings_ are preventing unity from starting.

---

### Post by hyper2hottie on 2011-08-28
Sounds like your video driver is doing something weird.  You could try to reinstall it.

---

### Post by xhaowu on 2011-09-01
Even after I removed my ATI driver, it still gives me the classic desktop.  I booted up into the recovery mode and it is still the same. I am wondering some settings for desktop environment have been changed...
  
By the way, when I switch to KDE it gives me a black screen.  I can see the window showing the progress when I am once in but after that the desktop is just totally black.
 
I think there is nothing to do with my ATI driver, any ideas?

---

### Post by wildmanne39 on 2011-09-01
Hi,post the results of 
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by xhaowu on 2011-09-01
now my desktop is very werid...there is no taskbar...at all 
 
```
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
binfmt_misc            17565  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi           13324  0 
snd_hwdep              13604  1 snd_hda_codec
snd_rawmidi            30486  1 snd_seq_midi
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
fglrx                2929050  95 
dcdbas                 14438  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17606  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  2 
tg3                   141750  0 
libahci                26642  1 ahci

```

---

### Post by Mia1990 on 2011-09-01
Check and see if unity will run on your pc.

copy and paste in the terminal

> /usr/lib/nux/unity_support_test -p

then copy the output and paste the it on here

---

### Post by wildmanne39 on 2011-09-01
Hi, here is a link for the ati drivers, I do not believe you can get the unity desktop properly without it installed, you do need to get rid of the flgrx driver though they conflict with each other.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

Hi, Mia1990, I am in New Mexico Too.

---

### Post by xhaowu on 2011-09-02
```
Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```

My desktop is still a big mess...

---

### Post by xhaowu on 2011-09-02
This drives me crazy...even the theme is changed to something weird (I changed theme to Ambiance but the folders and icons are Ambiance and the title bar for the windows is something else.)...what happened to my unity.  No taskbar showing at all in my desktop...
 
My graphic card is ATI-HD4350, and I connect two monitors (different types) with it. 
One monitor was set to resolution 1650x1050 the other was set to 1900x1440.
It was running fine under 10.04, after upgrading to 11.04 three weeks ago, it was crahsed for once when it booted into system (the problem was launcher bar was shown instead of some weird strings saying objects not found).  I am pretty sure my graphics card was running the latest version of the drivers.  
 
Now 2 days ago, when I switched to KDE desktop environment, everything starts to get crazy...I don't know what's worng with 11.04?

---

### Post by wildmanne39 on 2011-09-02
Hi, try this link.
[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)
Thank you

---

### Post by xhaowu on 2011-09-02
it does not work for me... :-(

---

### Post by xhaowu on 2011-09-02
I don't know if it is a bug or not...it leaves me no choice but reinstall my system...which is really annoying...

---

### Post by wildmanne39 on 2011-09-02
Hi, did you remove kde? if so how?

---

### Post by xhaowu on 2011-09-02
No i didn't remove KDE...

---

### Post by wildmanne39 on 2011-09-02
Hi, and you did not uninstall anything in ubuntu? 

You may want to open disk utility and run a smart check on your hard drive.
Thank you

---

### Post by xhaowu on 2011-09-02
I remove and reinstall fglrx for serveral times apart from that i didn't remove anything except the compiz manager.

---

### Post by wildmanne39 on 2011-09-02
Hi, you need to reinstall it and make sure the unity plug in is checked.

Unity is just a plugin in compiz.

---

### Post by xhaowu on 2011-09-02
i dont think compiz is going to help my problem...i think something messed up when I logged into KDE...

---

### Post by wildmanne39 on 2011-09-02
Hi, it is possible but compiz must be installed and working for unity to work.

I am sorry but I am out of ideas.

---

### Post by xhaowu on 2011-09-03
I think it's the problem of fglrx, i had a clean installed 11.04 and then I installed the driver, when I enable single display(multiplay desktop), it went totally crazy...something worng with the graphics driver...???

---

### Post by xhaowu on 2011-09-03
after i removing all fglrx and reset unity, it now goes fine...sigh...

---

### Post by wildmanne39 on 2011-09-03
Hi, I am glad you got it working and yes that is what I thought too, as I stated in post 10.

Enjoy ubuntu and be careful somethings are hard to recover from once they have been changed, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---


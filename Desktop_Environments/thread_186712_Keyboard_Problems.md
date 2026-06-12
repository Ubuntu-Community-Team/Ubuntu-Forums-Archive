---
title: "Keyboard Problems"
date: 2006-06-02
forum: Desktop Environments
---

### Post by the_witch_king on 2006-06-02
Hi,  I have a samsung mulitmedia keyboard and there seems to be some problem with the  special keys . When i press the volume up and down keys in GNOME i get a small bar on my screen which keeps going up and down but nothing actually happens to the volume. I ran ALSAMIXER and pressed the volme up and down keys and the PCM volume  was increasing and decreasing whereas i observed increasing asn decreasing the bar beside PCM , the one lablled FRONT actually changed the volume. Next i typed XEV in the termial as was suggested in the tutorial ( i hope somebody tells me what XEV does) on pressing the PLAY button i got this message


KeyPress event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 11770215, (424,315), root(434,408
    state 0x0, keycode 162 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2c00001,
    root 0x48, subw 0x0, time 11770385, (424,315), root(434,408
    state 0x0, keycode 162 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes:

i got similar messages for PAUSE and PLAY NEXT and PLAY PREVIOUS where as for the volume up and down i got this kind of messages :


FocusOut event, serial 30, synthetic NO, window 0x2c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x2c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0


Please tell me what to do , it is very inconvienient every time i Play anything, i have to open the application and use its shortcuts to change the volume. It gets worse in Mplayer , Pressing the keyboard sound keys for Mplayer makes a bar appear which goes UP and Down but nothing actually happens to the volume, i have to manually increase or decrease the volume of the speakers

---

### Post by SuperSlug on 2006-06-02
XEV effectively shows you how a input source in interpreted.  It shows the value of the keystroke or key press or what have you.  This is useful for mapping a new input device to some piece of software.

In my case I used it to capture the values of key-presses on a USB remote so I could use the values to reconfigure Xine to work with the remote.  I hope this makes sense. 

As for the other problem it sounds to same as mine, you just happen to be using a keyboard.  Xev is not gonig to help you because there is only one set of volume control hot keys defined in Ubuntu and in our case they are tied to the wrong volume control.

If anybody knows how to tie or bind the desktop volume to a difference volume control in the mixer please speak up!!  If you are having the same issue please make some noise to we can get this fixed.

Cheers,

SuperSlug

---

### Post by Dice on 2006-06-07
I am having a similiar problem. When I use my keyboard volume control, it adjusts the senter channel instead of the front channel.  Setting volume control to analog front track does nothing.  Adjusting keyboard shortcut does nothing.  I have seen this come up more and more on a variety of hardware setups. The only commonality so far is Ubuntu/alsa and possibly sblive. This issue is seen even on a fresh install.

In effort to provide as much info as possible:

Logitech Elite Keyboard LE PS2; Soundblaster Live! 24bit; Ubuntu with automatix; AMD xp 3200+ on nvidia nforce2 mobo; nvidia 6800 video card.  

I hope someone finds a fix for this. :)

---

### Post by JakobWelner on 2006-06-07
My volume controls adjusts the Master, but as I usually uses the headphone out for better speakers, the adjustments dosn't influence this volume. Am I wrong to think it most logical that the Master volume should adjust the headphone volume as well as any other volumen on output sound devices, instead of just the computer speakers?
Or have I done something wrong?

I'm on a Dell Inspiron 9300 with Ubuntu Dapper

[EDIT]
Hmm.. Seems that it's the PCM that works as a master. If this is the one you are talking about, sorry that I ask again, but my issue would then be to move the multimedia keys from adjusting the Master to adjust the PCM volumen.

---

### Post by SuperSlug on 2006-06-09
And it you succeed in doing this, please let us know.  Changing what the default volumn control does is exactly what I would like to do.  In my case it controls that master mono, I would like for the desktop volume to control the PCM volume.

---

### Post by Maci_01 on 2006-06-09
I guess that makes five of us . . only way to change the volume is to go to the terminal and type sudo alsamixer.  :-(

---

### Post by Sammi on 2006-06-19
I'm using a Inspiron 9300 too and I also want to change the volume buttons' bindings from master channel to PCM... there has to be a way...

---

### Post by Sammi on 2006-08-04
I may have found a viable workaround for you guys :D

Just check out [this tread]("http://www.ubuntuforums.org/showthread.php?p=1336764#post1336764")

---


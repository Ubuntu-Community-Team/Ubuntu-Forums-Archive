---
title: "ATI FGLRX driver wont come out of 'video suspend'"
date: 2007-05-08
forum: Desktop Environments
---

### Post by ba5e on 2007-05-08
Hi I have a X1950 Pro linked by DVI to a 1680x1050@75 monitor with no screensaver and the fglrx drivers installed from this howto:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C)

and Beryl installed by this howto:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

Yes, all standard fare and it works like a dream however if I leave the pc alone and the monitor goes to standby,  then I wake it with a key press or mouse shake - I see the green light come on, then the monitor just goes straight back to standby again.

The only way to bring the pc back (CTRL ALT F1 etc does not work) is to do a CTRL ALT BACKSPACE. This reloads X and the screen reinitialises.

I found the error 

```
[fglrx:firegl_lock] *ERROR* Process 5774 is using illegal context 0x00000005
```

in ```
dmesg | grep fglrx
```

Full results as follows:

```
[   31.142958] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   31.145906] [fglrx] Maximum main memory to use for locked dma buffers: 1899 MBytes.
[   31.145999] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   32.108832] [fglrx] total      GART = 130023424
[   32.108839] [fglrx] free       GART = 114032640
[   32.108841] [fglrx] max single GART = 114032640
[   32.108844] [fglrx] total      LFB  = 268304384
[   32.108846] [fglrx] free       LFB  = 244305920
[   32.108848] [fglrx] max single LFB  = 244305920
[   32.108849] [fglrx] total      Inv  = 0
[   32.108851] [fglrx] free       Inv  = 0
[   32.108852] [fglrx] max single Inv  = 0
[   32.108854] [fglrx] total      TIM  = 0
[ 1913.175059] [fglrx:firegl_lock] *ERROR* Process 5774 is using illegal context 0x00000005
[ 1916.229280] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 1916.241378] [fglrx] total      GART = 130023424
[ 1916.241385] [fglrx] free       GART = 114032640
[ 1916.241387] [fglrx] max single GART = 114032640
[ 1916.241389] [fglrx] total      LFB  = 268304384
[ 1916.241390] [fglrx] free       LFB  = 244305920
[ 1916.241392] [fglrx] max single LFB  = 244305920
[ 1916.241394] [fglrx] total      Inv  = 0
[ 1916.241395] [fglrx] free       Inv  = 0
[ 1916.241397] [fglrx] max single Inv  = 0
[ 1916.241398] [fglrx] total      TIM  = 0
[ 3349.643261] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 3349.655618] [fglrx] total      GART = 130023424
[ 3349.655626] [fglrx] free       GART = 114032640
[ 3349.655628] [fglrx] max single GART = 114032640
[ 3349.655630] [fglrx] total      LFB  = 268304384
[ 3349.655632] [fglrx] free       LFB  = 244305920
[ 3349.655634] [fglrx] max single LFB  = 244305920
[ 3349.655636] [fglrx] total      Inv  = 0
[ 3349.655637] [fglrx] free       Inv  = 0
[ 3349.655639] [fglrx] max single Inv  = 0
[ 3349.655641] [fglrx] total      TIM  = 0
```

Please let me know if you have any ideas what is causing this, or if I can supply some more information, thanks in advance :)

---

### Post by ba5e on 2007-05-09
BUMP! someone must have an idea what is going on?

---

### Post by ba5e on 2007-05-14
bump?

---

### Post by agentc0re on 2008-01-07
I know that this thread is old but i was experiancing the same issue but on a different OS.  I don't think it is OS specific.

I wanted to post an answer in this forum because this is the fire post that google pops up with when you do a search for fglrx:firegl_lock error.

The fix that i've found so far is that it happens when you have your Vertical Refresh set to ON in the ATI CCC.  Turning it off seems to have fixed this issue.  

[http://ati.cchtml.com/show_bug.cgi?id=971](http://ati.cchtml.com/show_bug.cgi?id=971) has been submitted.

---


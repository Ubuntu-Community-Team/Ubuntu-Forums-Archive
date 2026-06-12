---
title: "X/OS crashes when I close a terminal with a root session"
date: 2008-12-03
forum: General Help
---

### Post by petereddy on 2008-12-03
This is so strange I'm not sure how to classify it. I open a terminal in X and become root ("sudo bash -l") then close the terminal with the window close button. This will either cause my machine to hang, or X to crash, or for X to completely blank both my monitors for a second or two.

I'm using a newly installed 8.10 on AMD 64, dual CPU, two monitors and 4G of RAM and an ATI Radion 200G video card. This happens both with the ATI driver and the xorg driver.

---

### Post by SPr on 2008-12-03
Strange. Does anything appear in the system logs at the time of the crashes?

---

### Post by petereddy on 2008-12-03
[edit: these messages were from an instance where the screen went blank for a few seconds, but neither the OS nor X crashed this time.]

in /var/log/messages I see:

Dec  3 15:06:25 asdf kernel: [ 1384.881251] [drm] Num pipes: 3
Dec  3 15:06:25 asdf kernel: [ 1385.411696] [drm] Loading R300 Microcode
Dec  3 15:06:25 asdf kernel: [ 1385.411778] [drm] Num pipes: 3

when it happens, in Xorg.log I see:

(II) AIGLX: Suspending AIGLX clients for VT switch
(II) RADEON(0): RADEONRestoreMemMapRegisters() :
(II) RADEON(0):   MC_FB_LOCATION   : 0xafffa800 0xafffa800
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 107996667
best_feedback_div: 181
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() :
(II) RADEON(0):   MC_FB_LOCATION   : 0xafffa800 0xafffa800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xb1ffb000
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
init memmap
init common
init crtc2
init pll2
freq: 154000000
best_freq: 153940000
best_feedback_div: 43
best_ref_div: 2
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() :
(II) RADEON(0):   MC_FB_LOCATION   : 0xafffa800 0xafffa800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xb1ffb000
restore common
restore crtc2
restore pll2
finished PLL2
restore FP2
i2c write: 0x8, 0x31
(EE) RADEON(0): Unable to write to DVO Slave 136.
i2c write: 0xa, 0x0
(EE) RADEON(0): Unable to write to DVO Slave 136.
i2c write: 0xc, 0x89
(EE) RADEON(0): Unable to write to DVO Slave 136.
MMIO mask: 0x288 0xfffffffd 0x2000004
(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(II) Macintosh mouse button emulation: Device reopened after 10 attempts.
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) AT Translated Set 2 keyboard: Device reopened after 10 attempts.
(II) Logitech Optical USB Mouse: Device reopened after 10 attempts.
(**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) CHICONY HP Basic USB Keyboard: Device reopened after 10 attempts.

---

### Post by SPr on 2008-12-04
Do you have any problems with your graphic card (other than this?) When the screen blanks it sounds as if the card is the cause but the question would be why? I'm afraid that the xorg log doesn't mean much to me except that the card is being initialised,

Hit Ctrl+Alt+f1 and enter:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.my_backup
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```
and work through each screen answerng the questions. Does it help? If it doesn't or it's actually worse then:
```

sudo cp /etc/X11/xorg.conf.my_backup /etc/X11/xorg.conf

```
will put the old file back.

---


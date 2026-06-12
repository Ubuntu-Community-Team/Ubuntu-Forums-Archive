---
title: "Right Alt key on US:Dvorak does not work Kubuntu 8.10"
date: 2008-11-05
forum: Desktop Environments
---

### Post by at165db on 2008-11-05
Basically the problem is the right Alt does not work.  I cannot use it to trigger shortcuts.  I can't even map it using the keyboard shortuct "custom" tool.  Left alt works just fine.

I think this is a US Dvorak only issue, as a co-worker with the same Kubuntu 8.10 64bit install uses normal US QWERTY without issue.  

When the Kubuntu installer autodetected what keyboard I have based off p and d, it picked Dvorak.  I have a "normal" US keyboard that has the windows buttons, no extra multimedia stuff.  I'm just hooked on Dvorak.

If I run xev, right alt generates the following:
```
KeyPress event, serial 34, synthetic NO, window 0x4600001,
    root 0x1a6, subw 0x4600002, time 20732378, (38,42), root:(1963,67),
    state 0x10, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92                                       
    XLookupString gives 0 bytes:                                               
    XmbLookupString gives 0 bytes:                                             
    XFilterEvent returns: False                                                

KeyRelease event, serial 34, synthetic NO, window 0x4600001,
    root 0x1a6, subw 0x4600002, time 20732474, (38,42), root:(1963,67),
    state 0x90, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92                                       
    XLookupString gives 0 bytes:                                               
    XFilterEvent returns: False        
```

Left Alt generates:
```
KeyPress event, serial 34, synthetic NO, window 0x4600001,
    root 0x1a6, subw 0x4600002, time 20819980, (44,53), root:(1969,78),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,    
    XLookupString gives 0 bytes:                                       
    XmbLookupString gives 0 bytes:                                     
    XFilterEvent returns: False                                        

KeyRelease event, serial 34, synthetic NO, window 0x4600001,
    root 0x1a6, subw 0x4600002, time 20820060, (44,53), root:(1969,78),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,    
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

```

I know I've already had issues with Kubuntu and keys mapping into vmware.  I solved that with this thread [http://ubuntuforums.org/showthread.php?t=966070](http://ubuntuforums.org/showthread.php?t=966070) .

Any ideas?

Thanks!

---

### Post by Salvar Fawkes on 2009-03-14
Hey, I've just been trying to adopt Dvorak, and I had this same problem (as well as a few others). For some reason the "double alt" switch doesn't work for me, but for some reason it was still checked. When I unchecked it, my right alt key started working again.

---


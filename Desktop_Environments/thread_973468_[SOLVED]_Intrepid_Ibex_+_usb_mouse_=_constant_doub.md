---
title: "[SOLVED] Intrepid Ibex + usb mouse = constant double clicks"
date: 2008-11-06
forum: Desktop Environments
---

### Post by drumz on 2008-11-06
I upgraded a few days ago from 8.04 to 8.10, and the whole upgrade went smoothly for both Gnome and KDE except for one small item that's driving me nuts.

On my laptop I have a USB mouse plugged in and every time you click the left mouse button it registers as a double click close to 100% of the time.

I've read many posts, tried adding configuration information to /etc/X11/xorg.conf until I found that it's now supposed to be done via HAL, but I haven't found the magic incantation.

The built-in Synaptic pad works fine - no double click issue.  I know the mouse is fine because it worked perfectly prior to the upgrade and it still works fine when I reboot into Windows <bleh>.

Below is the output from xinput list:

```
xinput list                           
"Virtual core keyboard" id=0    [XKeyboard]                                                                                                                                       
        Num_keys is 248                                                                                                                                                           
        Min_keycode is 8                                                                                                                                                          
        Max_keycode is 255                                                                                                                                                        
"Virtual core pointer"  id=1    [XPointer]                                                                                                                                        
        Num_buttons is 32                                                                                                                                                         
        Num_axes is 2                                                                                                                                                             
        Mode is Relative                                                                                                                                                          
        Motion_buffer is 256                                                                                                                                                      
        Axis 0 :                                                                                                                                                                  
                Min_value is 0                                                                                                                                                    
                Max_value is -1                                                                                                                                                   
                Resolution is 0                                                                                                                                                   
        Axis 1 :                                                                                                                                                                  
                Min_value is 0                                                                                                                                                    
                Max_value is -1                                                                                                                                                   
                Resolution is 0                                                                                                                                                   
"Configured Mouse"      id=2    [XExtensionPointer]                                                                                                                               
        Num_buttons is 9                                                                                                                                                          
        Num_axes is 2                                                                                                                                                             
        Mode is Relative                                                                                                                                                          
        Motion_buffer is 256                                                                                                                                                      
        Axis 0 :                                                                                                                                                                  
                Min_value is -1                                                                                                                                                   
                Max_value is -1                                                                                                                                                   
                Resolution is 1                                                                                                                                                   
        Axis 1 :                                                                                                                                                                  
                Min_value is -1                                                                                                                                                   
                Max_value is -1                                                                                                                                                   
                Resolution is 1                                                                                                                                                   
"Synaptics Touchpad"    id=3    [XExtensionPointer]                                                                                                                               
        Num_buttons is 12                                                                                                                                                         
        Num_axes is 2                                                                                                                                                             
        Mode is Relative                                                                                                                                                          
        Motion_buffer is 256                                                                                                                                                      
        Axis 0 :                                                                                                                                                                  
                Min_value is 0                                                                                                                                                    
                Max_value is -1                                                                                                                                                   
                Resolution is 1                                                                                                                                                   
        Axis 1 :                                                                                                                                                                  
                Min_value is 0                                                                                                                                                    
                Max_value is -1                                                                                                                                                   
                Resolution is 1                                                                                                                                                   
"Macintosh mouse button emulation"      id=4    [XExtensionPointer]                                                                                                               
        Num_buttons is 32                                                                                                                                                         
        Num_axes is 2                                                                                                                                                             
        Mode is Relative                                                                                                                                                          
        Motion_buffer is 256                                                                                                                                                      
        Axis 0 :                                                                                                                                                                  
                Min_value is -1                                                                                                                                                   
                Max_value is -1                                                                                                                                                   
                Resolution is 1                                                                                                                                                   
        Axis 1 :                                                                                                                                                                  
                Min_value is -1                                                                                                                                                   
                Max_value is -1                                                                                                                                                   
                Resolution is 1                                                                                                                                                   
"SynPS/2 Synaptics TouchPad"    id=5    [XExtensionPointer]                                                                                                                       
        Num_buttons is 12                                                                                                                                                         
        Num_axes is 2                                                                                                                                                             
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is 0
                Max_value is -1
                Resolution is 1
"AT Translated Set 2 keyboard"  id=6    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"HID 1241:1166" id=7    [XExtensionPointer]
        Num_buttons is 32
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
"Video Bus"     id=8    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Video Bus"     id=9    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255

```

Any help on this before I go mad is greatly appreciated.

---

### Post by drumz on 2008-11-12
After reviewing similar threads, someone suggested changing the mouse button settings from right to left handed to see if the button was bad in another thread.  I did that and the right button worked perfectly fine.

So the left mouse button went bad at the same time I performed the upgrade to Intrepid Ibex.  Replaced the mouse with a new one and the new mouse is working perfectly fine.  I'm no longer going nuts.

---


---
title: "Emulate3Buttons intrepid"
date: 2008-12-21
forum: General Help
---

### Post by Benjamin_Vedder on 2008-12-21
Hi

I just cant figure out how to disable the Emulate3Buttons option for the mouse in intrepid, and i have tried a lot of things.

I have figured out xorg.conf is ignored now and hal is used.

I have created */etc/hal/fdi/policy/mx518.fdi*, and it looks like this:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
	<device>
		<match key="info.capabilities" contains="input.mouse">
			<merge key="input.x11_options.Emulate3Buttons"type="strin g">false</merge>
		</match>
	</device>
</deviceinfo>

```
But it does not work. I have also tried
```

xinput set-int-prop "Logitech USB-PS/2 Optical Mouse" "Emulate3Buttons" 8 0

```
And this also refuses to work.

here is the output of xinput list:
```

benjamin@benjamin:~$ xinput list
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
"Logitech USB-PS/2 Optical Mouse"       id=2    [XExtensionPointer]
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
"Macintosh mouse button emulation"      id=3    [XExtensionPointer]
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
"Logitech Logitech BT Mini-Receiver"    id=4    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
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
"Logitech Logitech BT Mini-Receiver"    id=5    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Logitech Logitech Gaming Keyboard"     id=6    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Logitech Logitech Gaming Keyboard"     id=7    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255

```

The reason i dont think Emulate3Buttons is disabled is when i play open arena and bind something to mouse3, that bind is triggered when i press both mouse buttons at the same time.

Thanks for help.

---


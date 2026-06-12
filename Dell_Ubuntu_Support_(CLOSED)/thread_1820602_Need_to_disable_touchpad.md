---
title: "Need to disable touchpad"
date: 2011-08-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aaronsharpe on 2011-08-07
I have a new Dell Inspiron 15R but I am having trouble typing on it as the touchpad is far too sensitive.

I am using 11.04 with classic mode, and I cannot find a setting to disable the touchpad while typing in Mouse Preferences (there is not even a tab for Touchpad).

Pressing the dissable touchpad key combination also doesn't do anything other that show a notification suggesting the touchpad has been disabled.

If anyone could help me out it would be much appreciated. Even just how to disable the thing entirely would help.

Thanks

```
aaron@aaron-Inspiron-N5110:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD             	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]

```

---

### Post by HunterDX77M on 2011-08-07
I am fairly new to command-line, so you'll have to forgive me for giving you a GUI-related solution attempt.

I am using 11.04, too, (albeit, with Unity) and here is what I think will work for your particular situation.
Under the System's Preferences menu, there should be an entry just called "Mouse." Clicking that should open up a window with General, Accessibility and Touchpad tabs. Click the Touchpad tab and have "Disable touchpad while typing" selected. Let me know how it goes. 

(You can also reduce sensitivity on the General tab.)

---

### Post by mikewhatever on 2011-08-08
Check out the link ->[http://askubuntu.com/questions/14178/how-to-disable-touchpad-on-dell-latitude-e-series-e5510-e6510](http://askubuntu.com/questions/14178/how-to-disable-touchpad-on-dell-latitude-e-series-e5510-e6510)

The second answer seems to be what you want.
> xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 0

xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 1

---

### Post by aaronsharpe on 2011-08-08
Thanks Mike, that worked great.

But if anyone knows how to get Ubuntu to recognize the touchpad as a such that would be great.

---


---
title: "KDE4 synaptics horizontal scroll?"
date: 2009-07-19
forum: Desktop Environments
---

### Post by 67GTA on 2009-07-19
I am looking to migrate to KDE4 once 4.3 goes final. I am checking off my list of things I',m not sure how to do yet. I'm playing with the Karmic live CD, and can't seem to find any way to enable horizontal scrolling. With Gnome, there is an option to turn it on. How do I turn it on with KDE4?

---

### Post by Zorael on 2009-07-19
Well, there's a xinput command to fix that, but it only lasts for your current X session. Perhaps there's a GUI app to take care of this too, that I just don't know of. The man page for synaptics deals with xorg.conf/HAL .fdi settings, such as [this example](http://ubuntuforums.org/showpost.php?p=7217419&postcount=4), but after having messed up and broken my X when I tried to make changes to my .fdi, I favor this alternative (and safe) route. I'll use color markups for legibility.

Pop up a terminal and enter the following command. Make note of the id number of the touchpad. (Just make it **xinput list** for a full listing of all your connected input devices.)
```
$ **xinput list | grep -i synaptics**
"SynPS/2 Synaptics TouchPad"    id=**[COLOR="RoyalBlue"]7[/COLOR]**    [XExtensionPointer]
```
Mmkay, so mine is id [COLOR="RoyalBlue"]**7**[/COLOR]. Enter the following and replace [COLOR="RoyalBlue"]**7**[/COLOR] with whatever id yours has.
```
$ **xinput list-props [COLOR="RoyalBlue"]7[/COLOR]**                                
Device 'SynPS/2 Synaptics TouchPad':                               
        Device Enabled (90):            1                          
        Synaptics Edges (237):          1632, 5312, 1575, 4281     
        Synaptics Finger (238):         24, 29, 255                
        Synaptics Tap Time (239):               180                
        Synaptics Tap Move (240):               221                
        Synaptics Tap Durations (241):          180, 180, 100      
        Synaptics Tap FastTap (242):            0                  
        Synaptics Middle Button Timeout (243):          75         
        Synaptics Two-Finger Pressure (244):            280        
        Synaptics Scrolling Distance (245):             100, 100   
**[COLOR="Lime"]        Synaptics Edge Scrolling (246)[/color]:         [COLOR="DarkOrange"]1, 0, 0[/COLOR]            **
        Synaptics Two-Finger Scrolling (247):           1, 0
        Synaptics Edge Motion Pressure (248):           29, 159
        Synaptics Edge Motion Speed (249):              1, 401
        Synaptics Edge Motion Always (250):             0
        Synaptics Button Scrolling (251):               1, 1
        Synaptics Button Scrolling Repeat (252):                1, 1
        Synaptics Button Scrolling Time (253):          100
        Synaptics Off (254):            0
        Synaptics Guestmouse Off (255):         0
        Synaptics Locked Drags (256):           0
        Synaptics Locked Drags Timeout (257):           5000
        Synaptics Tap Action (258):             2, 3, 0, 0, 1, 2, 3
        Synaptics Click Action (259):           1, 1, 1
        Synaptics Circular Scrolling (260):             0
        Synaptics Circular Scrolling Trigger (261):             0
        Synaptics Circular Pad (262):           0
        Synaptics Palm Detection (263):         0
        Synaptics Palm Dimensions (264):                10, 199
        Synaptics Pressure Motion (265):                29, 159
        Synaptics Grab Event Device (266):              1
```
Those are the available properties your device has, and you can modify them at any time without root access. Setting **Device Enabled (90)** to **0** would turn the pad off, obviously, as does setting **Synaptics Off (254)** to **1**. Regardless, [COLOR="Lime"]**Synaptics Edge Scrolling (246)**[/COLOR] seems to be what you want to modify. Looking at the syntax help for xinput;
```
$ **xinput**
usage :
        xinput get-feedbacks <device name>
        xinput set-ptr-feedback <device name> <threshold> <num> <denom>
        xinput set-integer-feedback <device name> <feedback id> <value>
        xinput get-button-map <device name>
        xinput set-button-map <device name> <map button 1> [<map button 2> [...]]
        xinput set-pointer <device name> [<x index> <y index>]
        xinput set-mode <device name> ABSOLUTE|RELATIVE
        xinput list [--loop || --short || <device name>...]
        xinput query-state <device name>
        xinput test [-proximity] <device name>
        xinput version
        xinput list-props <device> [<device> ...]
[B]        xinput set-int-prop [COLOR="RoyalBlue"]<device>[/COLOR] [COLOR="Lime"]<property>[/COLOR] [COLOR="Red"]<format (8, 16, 32)>[/COLOR] [COLOR="DarkOrange"]<val>[/COLOR] [[COLOR="DarkOrange"]<val>[/COLOR] ...]
        xinput set-float-prop <device> <property> <val> [<val> ...]
        xinput set-atom-prop <device> <property> <val> [<val> ...][/B]
        xinput watch-props <device>
        xinput delete-prop <device> <property>
```
Now, [COLOR="Lime"]**Synaptics Edge Scrolling (246)**[/COLOR] apparently takes three values, my current setting being **[COLOR="DarkOrange"]1[/COLOR]**, **[COLOR="DarkOrange"]0[/COLOR]**, **[COLOR="DarkOrange"]0[/COLOR]**. This *suggests* that it's an integer property, and as such you'd need to use **set-int-prop**. As for the [COLOR="Red"]**format**[/COLOR], I can only imagine this being related to the size of the property value, but as we're dealing with ones and zeroes, we'll use the lowest; [COLOR="Red"]**8**[/COLOR].

The values [COLOR="DarkOrange"]**1, 0, 0**[/COLOR] (or [COLOR="DarkOrange"]**enabled, disabled, disabled**[/COLOR]) are the default after installation, with which only vertical scrolling is enabled. Again, this *suggests* that the first value toggles vertical scrolling (which you can confirm by changing the settings to [COLOR="DarkOrange"]**0, 0, 0**[/COLOR] -- which correctly disables it). A minor bit of testing shows that the second value toggles horizontal scrolling. I still don't know what the third does; toggling it doesn't seem to have any effect. Regardless!
```
$ xinput set-int-prop **[COLOR="RoyalBlue"]7[/COLOR] [COLOR="Lime"]246[/COLOR] [COLOR="Red"]8[/COLOR] [COLOR="DarkOrange"]1 _1_ 0**[/COLOR]

[I]### you can refer to the device and property via their numbers
### or via their full names between quotes as below
### the numbers seem to change from time to time,
### so perhaps the latter approach is more appropriate[/I]

$ xinput set-int-prop **[COLOR="RoyalBlue"]"SynPS/2 Synaptics TouchPad"[/COLOR] [COLOR="Lime"]"Synaptics Edge Scrolling"[/COLOR] [COLOR="Red"]8[/COLOR] [COLOR="DarkOrange"]1 _1_ 0**[/COLOR]
```
You could make that into a script and save it in **~/.kde/Autostart/** (and make it executable), to have it be run automatically after logging in.


Drive-by readers are encouraged to point to the documentation and/or GUI alternatives.

---

### Post by 67GTA on 2009-07-19
I had to change "props" to "prop". It works perfectly now. Thanks for the tip. Are you talking about a bash script? I'm script stupid:-)

```
#! /bin/bash
###script to turn on horizontal scroll
xinput set-int-prop 8 244 8 1 1 0
```

---

### Post by Zorael on 2009-07-19
> **67GTA said:**
> I had to change "props" to "prop".
Yeah, typo, edited now. >.<

Yep, save that file and make it executable, either via Dolphin or in a terminal with 'chmod +x *<filename>*'. Copy/move it to **~/.kde/Autostart/** to make KDE start it automatically after logging in.

---

### Post by 67GTA on 2009-07-19
That done it! Thanks for the lesson. I'm excited about moving back to KDE. I think 4.3 will be the one. I moved to Gnome when KDE4 hit the streets. Gnome gets boring pretty quick. I never learn anything. I mostly use KDE apps in Gnome anyway. I'm going to play with the format value to see what happens:-)

---

### Post by scunc_dvl on 2009-09-03
Oh dear, it works! and my laptop touchpad doesn't even have the region marked! Awesome! I totally wasn't expecting a quick fix that works *laugh*

---

### Post by huck416 on 2009-12-28
I've been searching a long time for a solution to the horizontal scroll not working. This works; thank you very much. There is only one problem with putting the command in a script for autostart. The ID and the 3 digit Edge Scrolling number change each time.

```
$ xinput list | grep -i synaptics
"SynPS/2 Synaptics TouchPad"    id=9    [XExtensionPointer]
~$ xinput list-props 9
....
Synaptics Edge Scrolling (242): 1, 1, 0
...
```

The previous time it was ID 10 and (253)

So I still have to run through the commands on each restart to activate horizontal scrolling. At least it works.

---

### Post by Zorael on 2009-12-29
> **huck416 said:**
> I've been searching a long time for a solution to the horizontal scroll not working. This works; thank you very much. There is only one problem with putting the command in a script for autostart. The ID and the 3 digit Edge Scrolling number change each time.

Again, you can refer to the device and the property by their names instead of their numbers.
```
$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 1 1 0
```

I'm not sure what you mean by "I have to run through the commands on each restart", but the change will only last for your current session, so in a sense it has to be done after each login no matter what. The easiest way to automate it is to set up a script and place it in your autostart directory.

---

### Post by huck416 on 2009-12-29
Thanks for the quick response, Zoreal. I saw that after I'd written my post; should've read a little deeper. That works every time if I run the script manually however it doesn't run automatically from the Autostart folder on system boot. I've also tried putting a delay of 30 seconds in; no help. I've also named the file with a .sh extension. It appears in the GUI dialog Autostart under Advanced System Settings. I have another one that I created to unmount a couple network drives so I wouldn't get the CIFS error during the shutdown process which delays the shutdown. That one I set via the GUI to run on shutdown. It doesn't work either. I can run them from konsole when I need them but kind of defeats the purpose of having an "Autostart" function. Code below of my hscroll.sh script.

```
#! /bin/bash
###script to turn on horizontal scroll
sleep 30
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 1 1 0
```

Thanks

Ran chmod 755 on the files and the horizontal scroll works now.

---


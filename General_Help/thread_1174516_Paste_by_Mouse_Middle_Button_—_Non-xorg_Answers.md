---
title: "Paste by Mouse Middle Button — Non-xorg Answers"
date: 2009-05-31
forum: General Help
---

### Post by riutaro on 2009-05-31
Hi forum,

I have just upgrated to Intrepid (hoping to catch up with Jaunty soon).  I have a problem with disabling "paste upon middle-click" function of the mouse.  The following are previous discussions on the same problem but I find they are outdated since xorg does not seem to configure mouse properties any more.

[http://ubuntuforums.org/showthread.php?p=336190](http://ubuntuforums.org/showthread.php?p=336190)
[http://ubuntuforums.org/showthread.php?t=431712](http://ubuntuforums.org/showthread.php?t=431712)

To be precise with the reason I am asking for a non-xorg solution, I see Section "InputDevice" where 
Identifier is "Configured Mouse" and Driver is "mouse" commented out by update-manager in xorg.conf file (/etc/X11).

 A new instruction I found on the 'Net is [this]("https://wiki.ubuntu.com/X/Config/Input#Example:%20Disabling%20middle-mouse%20button%20paste%20on%20a%20scrollwheel%20mouse").
I was told to view the current mouse button mapping by: ```
$ xinput get-button-map "Logitech USB-PS/2 Optical Mouse"


1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 10
```The numbers in the second line are the expected outcome of the terminal input on the first.

No, no.  I cannot get the numbers.  Instead the terminal tries to explain how to use xinput commands:
```
foo@bar:~$ xinput get-button-map "TPPS/2 IBM TrackPoint"
usage :
    xinput get-feedbacks <device name>
    xinput set-ptr-feedback <device name> <threshold> <num> <denom>
    xinput set-integer-feedback <device name> <feedback id> <value>
    xinput set-button-map <device name> <map button 1> [<map button 2> [...]]
    xinput set-pointer <device name> [<x index> <y index>]
    xinput set-mode <device name> ABSOLUTE|RELATIVE
    xinput list [--short || <device name>...]
    xinput query-state <device name>
    xinput test [-proximity] <device name>
    xinput version 
    xinput list-props <device> [<device> ...]
    xinput set-int-prop <device> <property> <format (8, 16, 32)> <val> [<val> ...]
    xinput watch-props <device>
    xinput delete-prop <device> <property>

```

The command used for turning the middle button off results in the same usage notes:
```
$ xinput get-button-map "TPPS/2 IBM TrackPoint" 1 0 3
```


I thought my system does not have HAL working because I cannot access Device Manager from System &#8212;> Administration.  (HAL is the thing I should use from now on instead of xorg, right?)  After successfully enabling vertical scrolling middle button and [TrackPoint]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Vertical_Scrolling"), however, I am not sure about that at all.

Finally, I see a few threads about similar problems unanswered for a few days.  Please, help!

---

